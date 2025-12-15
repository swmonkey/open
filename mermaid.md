# Mermaid Diagrams

This file shows **common Mermaid diagrams** that render natively in **GitHub Markdown** and can also be rendered on a **web server** using Mermaid.js.

> GitHub automatically renders Mermaid blocks inside fenced code blocks marked as `mermaid`.

---

## Flowchart

```mermaid
flowchart TD
    A[Start] --> B{Decision}
    B -- Yes --> C[Do Thing]
    B -- No --> D[Do Other Thing]
    C --> E[End]
    D --> E
```

---

## Sequence Diagram

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

## Shapes ##
((Circle)) - Used for start/end  
Often means initialisation, entry point, or setup phase  
{{Hexagon}} - Represents a preparation step  

Syntax	Shape	Typical meaning  
( )	Rounded	Process  
(( ))	Circle	Start / End  
[ ]	Rectangle	Action  
{ }	Diamond	Decision  
{{ }}	Hexagon	Preparation / Build  
[/ /]	Parallelogram	Input / Output  

## GitHub-Friendly Notes

* Must use fenced blocks: ` ```mermaid `
* No external JS needed on GitHub
* Renders in:

  * GitHub repo viewer
  * GitHub PRs
  * GitHub Pages


