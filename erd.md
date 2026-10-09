# 11. Entity Relationship Diagram — Water Watch

```mermaid
erDiagram
    USERS {
      uuid user_id PK
      string full_name
      string email UK
      string password_hash
      string role
      datetime created_at
    }
    STATIONS {
      uuid station_id PK
      uuid operator_user_id FK
      string name
      string address
      decimal latitude
      decimal longitude
      boolean is_active
    }
    WATER_PRODUCTS {
      uuid product_id PK
      string name
      string container_size
      boolean is_active
    }
    STATION_PRICES {
      uuid station_price_id PK
      uuid station_id FK
      uuid product_id FK
      decimal price
      boolean is_available
      datetime updated_at
    }
    GROUP_ORDERS {
      uuid group_order_id PK
      uuid creator_user_id FK
      uuid station_id FK
      uuid product_id FK
      datetime created_at
      datetime deadline
      string delivery_preference
      string status
      string notes
    }
    ORDER_PARTICIPANTS {
      uuid participant_id PK
      uuid group_order_id FK
      uuid user_id FK
      int quantity
      datetime joined_at
      string status
    }

    USERS ||--o{ STATIONS : operates
    STATIONS ||--o{ STATION_PRICES : offers
    WATER_PRODUCTS ||--o{ STATION_PRICES : has_price
    USERS ||--o{ GROUP_ORDERS : creates
    STATIONS ||--o{ GROUP_ORDERS : receives
    WATER_PRODUCTS ||--o{ GROUP_ORDERS : requested
    GROUP_ORDERS ||--|{ ORDER_PARTICIPANTS : includes
    USERS ||--o{ ORDER_PARTICIPANTS : joins
```

**PII note:** `USERS.full_name` and `USERS.email` are personally identifiable information. `password_hash` is sensitive security data and must never be displayed in ordinary UI or logs. Apply suitable access controls and retention rules.
