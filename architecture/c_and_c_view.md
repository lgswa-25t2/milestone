# RUI Resiliency C&C View

```
Heartbeat 기반 Popup 구현을 위한 추가 필요사항:
Heartbeat 타이머 추가
마지막 heartbeat 시간 추적
일정 시간 동안 heartbeat 없으면 popup 표시
연결 상태 시각적 표시
현재는 heartbeat을 감지는 하지만 활용하지 않고 있어서, Raspberry Pi 연결 상태 모니터링 기능이 제대로 작동하지 않습니다.

네, 3번과 4번 기능(일정 시간 동안 heartbeat 없으면 popup 표시 + 연결 상태 시각적 표시)만 구현한다고 했을 때 C&C View를 그릴 수 있습니다.
 
```

![image](https://github.com/user-attachments/assets/cd5ddb0e-a15b-4324-8ee3-dc6046bbed5f)

---
PlantUml
```
@startuml heartbeat_popup_cc_view
!define RECTANGLE class

title ADS-B Display System - Heartbeat Popup C&C View
subtitle Components & Connectors for Heartbeat Monitoring and Popup Alert

' ==== COMPONENTS ====
RECTANGLE "DisplayGUI\n(Main Form)" as DISPLAY_GUI {
  + Timer1 : TTimer
  + Timer2 : TTimer  
  + HeartbeatTimer : TTimer
  + ConnectionStatusLabel : TLabel
  + LastHeartbeatTime : __int64
  + HeartbeatTimeout : int
  --
  + Timer1Timer()
  + Timer2Timer()
  + HeartbeatTimerTimer()
  + ShowHeartbeatPopup()
  + UpdateConnectionStatus()
}

RECTANGLE "TCP Client Thread\n(Raw Data Handler)" as TCP_THREAD {
  + StringMsgBuffer : AnsiString
  + UseFileInsteadOfNetwork : bool
  --
  + Execute()
  + HandleInput()
  + StopTCPClient()
}

RECTANGLE "DecodeRawADS_B\n(Message Decoder)" as DECODER {
  + MODES_RAW_HEART_BEAT : #define
  + MsgHeartBeat : enum
  --
  + decode_RAW_message()
  + detect_heartbeat()
}

RECTANGLE "Popup Dialog\n(Alert Window)" as POPUP_DIALOG {
  + Message : AnsiString
  + Buttons : TMsgDlgButtons
  --
  + ShowMessage()
  + ShowModal()
}

RECTANGLE "Connection Status\n(Visual Indicator)" as STATUS_INDICATOR {
  + StatusColor : TColor
  + StatusText : AnsiString
  + LastUpdate : __int64
  --
  + SetConnected()
  + SetDisconnected()
  + SetHeartbeatMissing()
}

RECTANGLE "Raspberry Pi\n(Data Source)" as RASPI {
  + readsb process
  + TCP Server (Port 30002)
  --
  + send_heartbeat()
  + send_ads_b_data()
}

' ==== CONNECTORS ====
interface "TCP Connection" as TCP_CONN
interface "Heartbeat Monitor" as HB_MONITOR  
interface "Popup Trigger" as POPUP_TRIGGER
interface "Status Update" as STATUS_UPDATE
interface "Timer Events" as TIMER_EVENTS

' ==== CONNECTIONS ====
RASPI -down-> TCP_CONN : "Raw ADS-B Data\n+ Heartbeat Messages"
TCP_CONN -down-> TCP_THREAD : "Receive Messages"

TCP_THREAD -right-> DECODER : "decode_RAW_message()\nStringMsgBuffer"
DECODER -up-> HB_MONITOR : "MsgHeartBeat Status"

HB_MONITOR -left-> DISPLAY_GUI : "Update LastHeartbeatTime"
DISPLAY_GUI -down-> TIMER_EVENTS : "HeartbeatTimer.Enabled = true"
TIMER_EVENTS -up-> DISPLAY_GUI : "HeartbeatTimerTimer() Event"

DISPLAY_GUI -down-> POPUP_TRIGGER : "Check Heartbeat Timeout"
POPUP_TRIGGER -down-> POPUP_DIALOG : "ShowMessage()\n'Raspberry Pi 연결 끊김'"

DISPLAY_GUI -right-> STATUS_UPDATE : "UpdateConnectionStatus()"
STATUS_UPDATE -right-> STATUS_INDICATOR : "Set Visual Status"

' ==== INTERACTION FLOW ====
note right of RASPI
  **Heartbeat Source**
  - Sends "*0000;*0000;*0000;*0000;*0000;" 
  - Every ~30 seconds (configurable)
  - Via TCP Port 30002
end note

note top of DECODER
  **Heartbeat Detection**
  if (!strcmp(hex, MODES_RAW_HEART_BEAT))
    return MsgHeartBeat;
end note

note left of DISPLAY_GUI
  **Timeout Logic**
  if (CurrentTime - LastHeartbeatTime > HeartbeatTimeout)
    ShowHeartbeatPopup();
    UpdateConnectionStatus(DISCONNECTED);
end note

note bottom of POPUP_DIALOG
  **User Alert**
  "Raspberry Pi와의 연결이 끊어졌습니다.
   Heartbeat 신호를 받지 못했습니다."
end note

note right of STATUS_INDICATOR
  **Visual Feedback**
  - Green: Connected + Heartbeat OK
  - Yellow: Connected + Heartbeat Missing  
  - Red: Disconnected
end note

' ==== CONFIGURATION ====
RECTANGLE "Configuration" as CONFIG {
  + HEARTBEAT_TIMEOUT_MS : 60000
  + CHECK_INTERVAL_MS : 5000
  + POPUP_AUTO_CLOSE : true
}

CONFIG -up-> DISPLAY_GUI : "Timeout Settings"

' ==== STYLING ====
skinparam rectangle {
  BackgroundColor<<main>> LightBlue
  BackgroundColor<<thread>> LightGreen  
  BackgroundColor<<decoder>> LightYellow
  BackgroundColor<<ui>> LightPink
  BackgroundColor<<external>> LightGray
}

DISPLAY_GUI <<main>>
TCP_THREAD <<thread>>
DECODER <<decoder>>
POPUP_DIALOG <<ui>>
STATUS_INDICATOR <<ui>>
RASPI <<external>>

@enduml 
```

## **C&C View 주요 구성 요소**

### **1. 핵심 컴포넌트들**

- **DisplayGUI**: 메인 폼 (HeartbeatTimer 추가, popup 및 상태 업데이트 담당)
- **TCP Client Thread**: 기존 스레드 (메시지 수신)
- **DecodeRawADS_B**: 기존 디코더 (heartbeat 감지 기능 활용)
- **Popup Dialog**: 새로운 알림 창
- **Connection Status**: 새로운 시각적 상태 표시기

### **2. 주요 커넥터들**

- **Heartbeat Monitor**: heartbeat 감지 → 시간 업데이트
- **Popup Trigger**: 타임아웃 감지 → popup 표시
- **Status Update**: 연결 상태 → 시각적 피드백
- **Timer Events**: 주기적 heartbeat 체크

### **3. 구현해야 할 핵심 기능**

#### **3번: 일정 시간 동안 heartbeat 없으면 popup 표시**
```cpp
// DisplayGUI.h에 추가
TTimer *HeartbeatTimer;
__int64 LastHeartbeatTime;
int HeartbeatTimeout; // 60000ms (60초)

// DisplayGUI.cpp에 추가  
void __fastcall TForm1::HeartbeatTimerTimer(TObject *Sender)
{
  __int64 CurrentTime = GetCurrentTimeInMsec();
  if ((CurrentTime - LastHeartbeatTime) > HeartbeatTimeout)
  {
    ShowHeartbeatPopup();
    UpdateConnectionStatus(DISCONNECTED);
  }
}

void __fastcall TForm1::ShowHeartbeatPopup(void)
{
  ShowMessage("Raspberry Pi와의 연결이 끊어졌습니다.\nHeartbeat 신호를 받지 못했습니다.");
}
```

#### **4번: 연결 상태 시각적 표시**
```cpp
// 상태 표시 레이블 색상 변경
void __fastcall TForm1::UpdateConnectionStatus(TConnectionStatus status)
{
  switch(status) {
    case CONNECTED_WITH_HEARTBEAT:
      ConnectionStatusLabel->Font->Color = clGreen;
      ConnectionStatusLabel->Caption = "연결됨 (정상)";
      break;
    case CONNECTED_NO_HEARTBEAT:  
      ConnectionStatusLabel->Font->Color = clYellow;
      ConnectionStatusLabel->Caption = "연결됨 (Heartbeat 없음)";
      break;
    case DISCONNECTED:
      ConnectionStatusLabel->Font->Color = clRed;
      ConnectionStatusLabel->Caption = "연결 끊김";
      break;
  }
}
```

### **4. 기존 코드와의 통합 지점**

1. **TTCPClientRawHandleThread::HandleInput()** 수정:
   ```cpp
   else if (Status==MsgHeartBeat)
   {
     Form1->LastHeartbeatTime = GetCurrentTimeInMsec();
     Form1->UpdateConnectionStatus(CONNECTED_WITH_HEARTBEAT);
   }
   ```

2. **DisplayGUI 생성자**에 HeartbeatTimer 초기화 추가

3. **연결/해제 이벤트**에서 상태 업데이트 호출

이 C&C View는 **최소한의 변경**으로 heartbeat 모니터링과 popup 알림 기능을 구현할 수 있는 아키텍처를 보여줍니다. 기존 heartbeat 감지 기능을 활용하고, 새로운 타이머와 UI 요소만 추가하면 됩니다.
