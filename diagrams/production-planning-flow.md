# Production Planning Flow

The flow below summarizes the proposed planner workflow for the illustrative case study.

```mermaid
flowchart TD
    A[Review demand and due dates] --> B[Validate product and material master data]
    B --> C[Check raw and packaging material availability]
    C --> D[Validate resource rates and calendars]
    D --> E[Calculate available capacity and changeovers]
    E --> F[Create or review finite production schedule]
    F --> G{Overload or due-date conflict?}
    G -- No --> H[Planner reviews sequence and dates]
    G -- Yes --> I[Evaluate resequencing, split lots, overtime or alternate resource]
    I --> F
    H --> J[Confirm quality, warehouse and shipping constraints]
    J --> K[Approve schedule for release]
    K --> L[Monitor execution KPIs and exceptions]
```

## Planner checkpoints

- Use verified master data and calendars; capacity output is only as reliable as those inputs.
- Do not assume material availability based on lead time alone—check actual or planned receipts.
- Review the finite schedule with production stakeholders before release.
- Record the reason for each manual change and compare actual results with the planned schedule.
