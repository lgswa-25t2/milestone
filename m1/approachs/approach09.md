# **Approach 9: Notifying Users of System Errors in Real Time**

There are general tactics for usability and failure awareness.

* **Fault Detection**

  * Monitor internal and external system components for failure events.

* **Fault Notification**

  * **User Feedback Mechanism**: Display a popup in the Remote User Interface (RUI) when an error occurs.
  * **Non-technical Messaging**: Ensure all error messages are clear, concise, and free from technical jargon to support end-user understanding.

* **Response Time Optimization**

  * Ensure notifications are displayed to the user within **1 second** of error detection to maintain user awareness and trust.

## **Decision**

We will implement a user feedback mechanism in the Remote User Interface (RUI) that detects system or external service failures and notifies users immediately using friendly and informative messages.

## **Rationale**

Users must be informed of system problems in real time to understand system status and prevent confusion or incorrect assumptions. Clear, timely, and non-technical error messages improve user trust and overall usability, particularly in mission-critical systems such as aircraft tracking or control environments. This aligns with usability quality attributes like **user awareness**, **error recovery**.

## **Status**

[***Proposed*** | Accepted | Deprecated | Superseded]

## **Consequences**

### **Positive**

* **Improved Usability**: Users can quickly recognize system issues and avoid misinterpretation.


### **Negative**

* **UI Complexity**: Requires designing and testing multiple UI states and messages.

## Related scenario

[IFTA_QA_006](../2-ArchitecturalDrivers.md#ifta_qa_006)
