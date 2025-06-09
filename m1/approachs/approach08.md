# Approach 8: Maintaining user model 
The system shall remember user preferences such as Raspberry Pi IP address, map style, and display settings across sessions to minimize repetitive setup and enhance efficiency.

We have two options.

-  Local Settings Persistence (UI-based)
  - User preferences (e.g., IP address, map view, display options) are saved to a local configuration file (e.g., JSON).
  - When the UI loads, it reads the config file and restores the previous session settings automatically.
  - Updates to settings are written back on user change or on safe-close.
- Approach 2: Cloud-Based User Model (via External Storage)
  - User settings are stored in a cloud storage solution (e.g., Firebase, BigQuery, or a lightweight backend API).
  - On startup, the UI queries the external service for the user’s saved settings.
  - Ideal for multi-device usage or centralized preference management.

## Decision 
After evaluating both architectural approaches against key quality attributes — performance, resiliency, extensibility, and modifiability - the recommended solution for implementing the Maintain User Model functionality is:

Local Settings Persistence (UI-based)

## Rationale 
Tradeoff Analysis

| Quality Attribute | Local Settings Persistence           | Cloud-Based User Model                            |
| ----------------- | ------------------------------------ | ------------------------------------------------- |
| Performance       | Very fast; low latency on read/write | Slight delay due to network access                |
| Resiliency        | Strong offline support               | Dependent on network availability                 |
| Extensibility     | Moderate; localized to UI            | High; supports syncing across devices/users       |
| Modifiability     | Easy to change and debug locally     | Requires external system and authentication logic |

Quality Attribute Deferred Data Rendering Adaptive Data Throttling at Source Performance Fast UI response; data still arrives smoothly May introduce lag due to changing data rates Resiliency High; data always collected locally Moderate; depends on reliable communication Extensibility Moderate; buffering logic localized to UI Limited; requires changes to source data system Modifiability Easier to change within UI component More complex; source and UI must coordinate

- ✅ Choose *Local Settings Persistence* if
  - We need a **lightweight and fast** solution.
  - The system is **used on a single device** (e.g., student laptop).
  - Offline use and simplicity are more important than multi-user sync.
  - We want to **avoid dependency on external services**.
  - **Singleton and Repository pattern Used**
- ⚠️ Choose *Cloud-Based User Model* if
  - We need **settings to sync across devices or users**.
  - The application will eventually be **multi-user or web-based**.
  - The network is reliable, and cloud integration is acceptable.
  - We want to **centralize configuration management**.

## Status
[Proposed | Accepted | ***Deprecated*** | Superseded]

## Consequences
Resulting context will be described.
