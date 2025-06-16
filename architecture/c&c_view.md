# C&C View for Data Processing
## **Legacy Data Processing C&C View**
![image](https://github.com/user-attachments/assets/ec353a89-6427-44c5-9a95-bd74251aa911)
//Legend update 필요

## **Planned Data Processing C&C View**
![image](https://github.com/user-attachments/assets/7cd88c15-0e59-420f-9a7f-e234ff846421)
//Legend update 필요

### **Summary: Before vs. After Comparison**

| Component         | Legacy Structure                 | Improved Structure                      | Benefits                          |
|------------------|----------------------------------|------------------------------------------|-----------------------------------|
| **Data Input**    | Direct input into DisplayGUI     | Message Receiver + Queue                 | Buffering, asynchronous handling  |
| **Message Handling** | Immediate synchronous processing | Pipeline-based staged processing         | Throughput, reliability           |
| **Data Storage**  | Global HashTable                 | Aircraft Repository                      | Thread safety, memory safety      |
| **Error Handling**| Distributed & inconsistent       | Centralized Message Validator            | Consistency, recoverability       |

---

## **1. Improved Data Input Layer**

### **Before: All inputs directly handled by DisplayGUI**

```cpp
// Legacy issues
ADSB_HW → DisplayGUI (directly connected)
NET_FEED → DisplayGUI (directly connected)
FILE_IN → DisplayGUI (directly connected)

// DisplayGUI handles all inputs
void __fastcall TTCPClientRawHandleThread::HandleInput(void) {
  // No buffering, processed immediately
  Status = decode_RAW_message(StringMsgBuffer, &mm);
}
````

### **After: Dedicated Message Receiver + Queue**

```puml
// Improved structure
ADSB_HW → Message Receiver → Message Queue  
NET_FEED → Message Receiver → Message Queue  
FILE_IN → Message Receiver → Message Queue  
```

**Benefits:**

*  **Burst traffic handling**
*  **Input source abstraction**

---

## **2. Improved Message Processing Pipeline**

### **Before: Immediate synchronous processing**

```cpp
// Legacy problem - sequential, blocking
Raw Message → decode_RAW_message() → direct HashTable insertion  
// Any failure blocks the entire pipeline  
```

### **After: Staged processing pipeline**

```puml
Message Queue → Message Validator → Raw Message Decoder →  
SBS Message Handler → Aircraft State Manager  
```

**Benefits:**

*  **Separation of concerns**: Each stage handles its own task
*  **Performance**: Enables parallel and staged processing

---

## **3. Improved Data Storage Layer**

### **Before: Direct access to global HashTable**

```cpp
// Global access from multiple modules
Form1->HashTable  // From DisplayGUI  
ght_get(Form1->HashTable, ...)  // From RAW_DECODER  
ght_insert(Form1->HashTable, ...)  // From SBS_Message  

// Thread-unsafe
ADS_B_Aircraft = (TADS_B_Aircraft *) ght_get(Form1->HashTable, ...);
if (ADS_B_Aircraft) {
  // Race conditions possible
}
```

### **After: Abstracted Aircraft Repository**

```puml
Aircraft State Manager → Aircraft Repository → Aircraft Database  
Aircraft Repository ↔ Message History  
```

**Benefits:**

* **Thread safety**: Internal synchronization
* **Memory safety**: Use of smart pointers
* **Data consistency**: Single point for read/write



## **4. Improved Architectural Patterns**

### **Before**

```cpp
// God Object Pattern
DisplayGUI manages everything  

// Tight Coupling  
All modules directly depend on Form1  

// Synchronous Processing  
Everything runs in blocking sequence  
```

### **After: Better architectural patterns**

```puml
// Producer-Consumer Pattern  
Message Receiver → Message Queue → Message Processor  

// Repository Pattern  
Aircraft State Manager → Aircraft Repository  

// Pipeline Pattern  
Validator → Decoder → Handler → Manager  
```

**Benefits:**

* **Single Responsibility Principle** across components
* **Loose coupling** through interfaces
* **High testability** with modular structure

---


