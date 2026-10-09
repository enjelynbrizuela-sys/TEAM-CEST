# 10. Provisional Deployment Diagram — Water Watch

```mermaid
flowchart TB
    subgraph client[Client Device]
      browser[Web Browser]
    end
    subgraph hosting[Provisional Hosting Environment]
      webserver[Web Server / Static Web UI]
      appserver[Application Runtime / API]
    end
    subgraph data[Managed Data Environment]
      db[(Relational Database)]
    end
    subgraph external[Optional External Services]
      notify[Email/SMS Provider]
      map[Map / Geocoding Provider]
    end

    browser -->|HTTPS| webserver
    webserver -->|HTTPS API requests| appserver
    appserver -->|TLS database connection| db
    appserver -.->|HTTPS| notify
    appserver -.->|HTTPS| map
```

**Provisional:** hosting provider, runtime, database product, and exact network configuration have not been selected. Confirm these with the team before treating this as a final deployment design.
