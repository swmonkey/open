# Mermaid Diagrams

This file shows **common Mermaid diagrams** that render natively in **GitHub Markdown** and can also be rendered on a **web server** using Mermaid.js.

> GitHub automatically renders Mermaid blocks inside fenced code blocks marked as `mermaid`.

## How
1. Choose Diagram - see below
2. Add links e.g.
3. Color
4. Notes

2. Links
```mermaid
flowchart LR
    API[Backend API]:::service
    API --> DB[(Database)]

    click API "https://github.com/org/repo" "View API repo"
    click DB "https://docs.aws.amazon.com/rds/"
```
3. Add colour
```mermaid

flowchart LR
    A[Lambda] --> B[(Database)]

    style A fill:#dbeafe,stroke:#2563eb,stroke-width:2px
    style B fill:#fef3c7,stroke:#f59e0b
```
Class-based styling (recommended)
```mermaid
flowchart LR
    A[Lambda]
    B[(Database)]
    C[External API]

    A --> B
    A --> C

    classDef compute fill:#e0f2fe,stroke:#0284c7
    classDef data fill:#fef3c7,stroke:#f59e0b
    classDef external fill:#fee2e2,stroke:#dc2626

    class A compute
    class B data
    class C external
```

4. Notes
```mermaid
flowchart LR
    A[Lambda]
    B[(Database)]

    A --> B
    A -.-> Note["Reads & writes\nJSON payload"]

    style Note fill:#f9fafb,stroke:#9ca3af,stroke-dasharray: 5 5
```
```mermaid
sequenceDiagram
    Lambda->>DB: Query data
    Note right of DB: Encrypted at rest
```

5. Subgraph
```mermaid
flowchart TB
    subgraph AWS["AWS Account"]
        Lambda
        DB[(RDS)]
    end

    subgraph External["External Systems"]
        API[3rd-party API]
    end

    Lambda --> DB
    Lambda --> API
```
    
---
1. Flowchart  
1ai Flowchart LR (Left Right)
1b Flowchart TB (Top Bottom)
1c flowchart LR (Left Right)
1d Flowchart TD (top Bottom)
3. State

## 1 Flowchart
### 1a Flowchart LR

Best for:
* High-level system logic
* Request flows
* Dev / prod pipelines
  
```mermaid
flowchart LR
    User --> Browser
    Browser --> API
    API --> DB
    DB --> API
    API --> Browser
```
Architectural lens: How things move   
```mermaid
flowchart LR
    User -->|data| WebApp
    WebApp -->|json| API
    API -->|sql| Database
  ```  
Architectural lens: What data moves where
### 1c Flowchart TB
flowchart TB
Mermaid doesn’t have native C4, but flowcharts map perfectly.

System / Container View
```mermaid
flowchart TB
    User --> WebApp
    WebApp --> API
    API --> Database
```
Component View
```mermaid
flowchart TB
    API --> AuthService
    API --> OrderService
    OrderService --> Database
```
### Deployment Diagram — Infrastructure Architecture

Best for:
* Cloud layouts
* Environments
* Nodes & hosting
  
```mermaid
flowchart TB
    subgraph Browser
        User
    end

    subgraph AWS
        ALB --> ECS
        ECS --> RDS
    end

    User --> ALB
```

Architectural lens: Structure at different zoom levels

---
### Flowchart LR
Architectural lens: Separation of concerns  
Best for:
* Internal services
* Modules
* Responsibilities
```mermaid
flowchart LR
    UI --> Auth
    UI --> Orders
    Orders --> Payments
    Payments --> ExternalGateway
```
### 1d Flowchart TD

```mermaid
flowchart TD
    A[Start] --> B{Decision}
    B -- Yes --> C[Do Thing]
    B -- No --> D[Do Other Thing]
    C --> E[End]
    D --> E
```
## 2. Sequence Diagram
### 2A . Sequence Diagram - 
#### API calls

Auth flows

Request/response timing
```mermaid
sequenceDiagram
    participant User
    participant Frontend
    participant Backend
    participant Database

    User->>Frontend: Click save
    Frontend->>Backend: POST /save
    Backend->>Database: Write record
    Database-->>Backend: OK
    Backend-->>Frontend: 200 Success
```
Architectural lens: Who talks to whom, and when

## 3. State Diagram
stateDiagram-v2
```mermaid
stateDiagram-v2
    [*] --> Idle
    Idle --> Processing
    Processing --> Success
    Processing --> Error
    Success --> [*]
```
Architectural lens: How systems change state
#### Client server
```mermaid
sequenceDiagram
    participant User
    participant Browser
    participant Server

    User->>Browser: Click button
    Browser->>Server: HTTP request
    Server-->>Browser: HTML response
    Browser-->>User: Render page
```

---

## Class Diagram

```mermaid
classDiagram
    class User {
        +int id
        +string name
        +login()
    }

    class Order {
        +int id
        +float total
        +place()
    }

    User "1" --> "many" Order
```

---

## State Diagram

```mermaid
stateDiagram-v2
    [*] --> Idle
    Idle --> Processing : start
    Processing --> Success : ok
    Processing --> Error : fail
    Success --> [*]
    Error --> Idle
```

---

## Entity Relationship Diagram (ERD)

```mermaid
erDiagram
    CUSTOMER ||--o{ ORDER : places
    ORDER ||--|{ LINE_ITEM : contains
    CUSTOMER {
        int id
        string name
    }
    ORDER {
        int id
        date created
    }
```

---

## Gantt Chart

```mermaid
gantt
    title Project Timeline
    dateFormat  YYYY-MM-DD

    section Planning
    Requirements     :done,    p1, 2025-01-01, 7d
    Design           :active,  p2, 2025-01-08, 5d

    section Build
    Development      :         p3, 2025-01-15, 10d
    Testing          :         p4, 2025-01-25, 5d
```

---


## GitHub-Friendly Notes

* Must use fenced blocks: ` ```mermaid `
* No external JS needed on GitHub
* Renders in:

  * GitHub repo viewer
  * GitHub PRs
  * GitHub Pages


