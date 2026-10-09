# 8. Package Diagram — Water Watch

```mermaid
flowchart TB
    subgraph presentation[Presentation Package]
      pages[Pages / UI Components]
    end
    subgraph application[Application Package]
      controllers[Controllers / API Routes]
      services[Application Services]
    end
    subgraph domain[Domain Package]
      models[Domain Models and Enums]
      rules[Validation and Business Rules]
    end
    subgraph infrastructure[Infrastructure Package]
      repos[Repository Implementations]
      integrations[Notification / Map Adapters]
      database[(Database)]
    end

    pages --> controllers
    controllers --> services
    services --> models
    services --> rules
    services --> repos
    services -.-> integrations
    repos --> database
```

**Layering rule:** Presentation code must call application services; it must not access the database directly. Domain rules should not depend on UI or database implementation details.
