# Module View

## Objective
Eliminate current cyclic dependencies in the system to improve maintainability and modifiability.

---

## Current Issues Analysis
//TODO: 그림 삽입 예정
### Key Cyclic Dependencies
1. **DisplayGUI ↔ AreaDialog**: Bidirectional dependency  
2. **DisplayGUI → SBS_Message → DisplayGUI**: Indirect cycle  
3. **DisplayGUI → DecodeRawADS_B → DisplayGUI**: Indirect cycle  

### Root Causes
- **God Object pattern**: DisplayGUI takes on too many responsibilities  
- **Lack of Layered Structure**: Business logic and UI logic are mixed  
- **Tight Coupling**: UI directly accesses data models  

### Issue to be solved
1. Resolve the issue where DisplayGUI directly depends on concrete classes. -> Phase1&2
```cpp
// current implementation (DisplayGUI.h)
class DisplayGUI {
private:
    Aircraft* m_aircraft;           // Direct dependency on a concrete class.
    SBS_Message* m_sbsMessage;      // Direct dependency on a concrete class.  
    DecodeRawADS_B* m_decoder;      // Direct dependency on a concrete class.
    AircraftDB* m_aircraftDB;       // Direct dependency on a concrete class.
    CPA* m_cpaCalculator;           // Direct dependency on a concrete class.
};
```
2. The bidirectional dependency issue between DisplayGUI and AreaDialog. -> Phase3

```cpp
// current implementation
class DisplayGUI {
    AreaDialog* m_areaDialog;  // DisplayGUI has a reference to AreaDialog
};

class AreaDialog {
    DisplayGUI* m_displayGUI;  // AreaDialog has a reference to DisplayGUI.
};
```

---

## Planed Architecture
(그림 택 1)
//1.plntuml 로 dependency 정의하고 https://www.plantuml.com/plantuml/uml/SyfFKj2rKt3CoKnELR1Io4ZDoSa70000 에서 그림으로 변환
![image](https://github.com/user-attachments/assets/f33a59d1-fcd3-41a2-b245-8e323af8bcd3)

//2.draw.io 에서 그림
![image](https://github.com/user-attachments/assets/fb08805a-1edb-41e5-b34e-e091b8725491)

### Adopt a 5-Layer Architecture

```
Layer 1: Application Entry (ADS-B-Display)
    ↓
Layer 2: UI & Presentation (DisplayGUI, AreaDialog)
    ↓
Layer 3: Business Logic & Services (Newly Introduced)
    ↓
Layer 4: Data Models & Entities (Aircraft, SBS_Message, AircraftDB)
    ↓
Layer 5: Core Utilities & Infrastructure (Existing Utilities)
```

## Refactoring Steps
### Phase 1: Introduce Service Layer
#### 1.1 Create AircraftService
```cpp
class AircraftService {
public:
    void ProcessSBSMessage(const SBS_Message& message);
    void UpdateAircraft(const Aircraft& aircraft);
    void CalculateCPA();
    std::vector<Aircraft> GetActiveAircraft();

private:
    AircraftDB* m_aircraftDB;
    CPA* m_cpaCalculator;
    TimeFunctions* m_timeFunctions;
};
```
Logic to move:

- Aircraft-related business logic from DisplayGUI
- SBS_Message processing logic
- CPA calculation logic

#### 1.2 Create DataProcessor
```cpp
class DataProcessor {
public:
    bool ProcessRawADSB(const std::string& rawData);
    SBS_Message DecodeMessage(const std::string& data);
    bool ValidateMessage(const SBS_Message& message);

private:
    DecodeRawADS_B* m_decoder;
};
```
Logic to move:
- Raw data processing logic from DisplayGUI
- DecodeRawADS_B invocation

#### 1.3 Create GeometryService
```cpp
class GeometryService {
public:
    bool IsPointInPolygon(double x, double y, const std::vector<Point>& polygon);
    std::vector<Triangle> TriangulatePolygon(const std::vector<Point>& polygon);
    Point ConvertLatLon(double lat, double lon);

private:
    PointInPolygon* m_pointChecker;
    TriangulatPoly* m_triangulator;
    LatLonConv* m_converter;
};
```
Logic to move:
- Geometric calculations from AreaDialog and DisplayGUI


### Phase 2: Apply Dependency Inversion
#### 2.1 Define Interfaces
```cpp
class IAircraftService {
public:
    virtual ~IAircraftService() = default;
    virtual void ProcessSBSMessage(const SBS_Message& message) = 0;
    virtual std::vector<Aircraft> GetActiveAircraft() = 0;
};

class IDataProcessor {
public:
    virtual ~IDataProcessor() = default;
    virtual bool ProcessRawADSB(const std::string& rawData) = 0;
};

class IGeometryService {
public:
    virtual ~IGeometryService() = default;
    virtual bool IsPointInPolygon(double x, double y, const std::vector<Point>& polygon) = 0;
};
```
#### 2.2 Refactor DisplayGUI
```cpp
class DisplayGUI {
private:
    // Remove tight coupling
    IAircraftService* m_aircraftService;
    IDataProcessor* m_dataProcessor;
    IGeometryService* m_geometryService;

public:
    DisplayGUI(IAircraftService* aircraftService,
               IDataProcessor* dataProcessor,
               IGeometryService* geometryService);
};
```
### Phase 3: Introduce Event-Driven Communication
#### 3.1 Implement Observer Pattern
The bidirectional dependency issue between DisplayGUI and AreaDialog.
```cpp
class IEventListener {
public:
    virtual ~IEventListener() = default;
    virtual void OnAircraftUpdated(const Aircraft& aircraft) = 0;
    virtual void OnMessageReceived(const SBS_Message& message) = 0;
};

class EventManager {
public:
    void Subscribe(IEventListener* listener);
    void Unsubscribe(IEventListener* listener);
    void NotifyAircraftUpdated(const Aircraft& aircraft);
    void NotifyMessageReceived(const SBS_Message& message);

private:
    std::vector<IEventListener*> m_listeners;
};
```
#### 3.2 Refactor AreaDialog
```cpp
class AreaDialog : public IEventListener {
private:
    IGeometryService* m_geometryService;
    EventManager* m_eventManager;

public:
    void OnAircraftUpdated(const Aircraft& aircraft) override;
    void OnMessageReceived(const SBS_Message& message) override;
};
```
# Implementation Priorities
## High Priority (Immediate)
- Create AircraftService and migrate aircraft-related logic
- Refactor DisplayGUI to offload business logic

## Medium Priority (Next Step)
- Create DataProcessor and move raw data logic
- Create GeometryService and move geometry logic

## Low Priority (Final Stage)
- Implement the event system
- Fully apply dependency inversion

  
