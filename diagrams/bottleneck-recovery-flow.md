# Bottleneck and Recovery Decision Flow

This decision logic is based on illustrative weekly demand of 138.5 t and effective packaging capacity of 141.25 t before disruption.

```mermaid
flowchart TD
    A[Effective packaging capacity: 141.25 t] --> B[Compare with demand: 138.5 t]
    B --> C{Unplanned downtime?}
    C -- No --> D[Capacity headroom: 2.75 t]
    C -- Yes --> E[Model downtime and lost output]
    E --> F[8-hour stop removes 10 t]
    F --> G[Revised capacity: 131.25 t]
    G --> H[Shortfall: 7.25 t]
    H --> I[Evaluate approved recovery options]
    I --> J[Example: 6 overtime hours recover 7.5 t]
    J --> K[Revised capacity: 138.75 t]
    K --> L{Demand covered with acceptable buffer?}
    L -- No --> M[Escalate: alternate resource, revised promise date or approved demand priority]
    L -- Yes --> N[Planner and operations review before release]
    N --> O[Monitor actual production, quality and shipping]
```

## Interpretation

The example overtime recovery covers modeled demand by just 0.25 t; this is a narrow buffer and should not be described as a robust recovery without checking real operating variability. The recovery capacity also does not support a separate 140 t target. Alternative capacity, split production, or revised delivery commitments should be reviewed where overtime is unavailable or the buffer is too small.
