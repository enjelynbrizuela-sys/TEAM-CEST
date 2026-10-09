# 7. State Machine Diagram — Group Order

```mermaid
stateDiagram-v2
    [*] --> OPEN: Customer creates group order
    OPEN --> CLOSED: Deadline reached or creator closes group
    OPEN --> CANCELLED: Creator cancels before confirmation
    CLOSED --> CONFIRMED: Station confirms request
    CLOSED --> CANCELLED: Station cannot fulfill request
    CONFIRMED --> FULFILLING: Preparation / delivery begins
    FULFILLING --> COMPLETED: Order fulfilled
    CONFIRMED --> CANCELLED: Exceptional cancellation
    COMPLETED --> [*]
    CANCELLED --> [*]
```

`OrderStatus` values here should match the class diagram. If the team decides that a station cannot cancel after confirmation, remove that transition and document the actual rule.
