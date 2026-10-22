# Risk, Controls, and Validation Plan

This checklist supports the Week 4 illustrative production-planning case study. The checks are proposed validation steps; they are not claimed as completed transactions or test results from a live SAP system.

## Risk and control register

| Risk | Potential impact | Suggested preventive / detective control | Planning response |
|---|---|---|---|
| Packaging line breakdown | Missed demand and late orders | Record downtime and confirm resource availability calendar | Reschedule, evaluate approved overtime or alternate line |
| Packaging material arrives late | Planned orders cannot start or finish | Check material availability dates and lead-time assumptions | Expedite, resequence, or revise the plan |
| Incorrect production rate | Unrealistic schedule and capacity calculations | Validate rates against approved master data and observed output | Correct master data and rerun capacity check |
| Inaccurate resource calendar | False available-capacity result | Review shifts, breaks, maintenance, and shutdowns | Correct calendar and recalculate load |
| Changeover time omitted | Underestimated load | Validate sequence-dependent setup assumptions | Re-sequence and reserve setup time |
| Demand increase | Capacity or material shortfall | Compare revised demand with available capacity | Prioritize critical demand and evaluate extra capacity |
| Raw-material shortage | Order delay or partial production | Reconcile BOM consumption, stock, receipts, and yield | Re-plan dates or seek approved alternate supply |
| Poor integration / stale master data | Planning inconsistency | Reconcile relevant ERP and planning data; review interface exceptions | Correct source data and rerun the planning process |
| Excessive rescheduling | Planner instability and shop-floor confusion | Use planning time fences / frozen horizons where appropriate | Require review before moving near-term operations |
| Overproduction | Excess inventory, shelf-life or storage exposure | Compare proposed output with demand and inventory policy | Reduce quantity or verify approved buffer rules |

## Proposed validation tests

| ID | Test | Expected result / evidence |
|---|---|---|
| VT-01 | Demand reconciliation | 55.2 + 48.3 + 35.0 = 138.5 t |
| VT-02 | Nominal packaging capacity | Weekly capacity basis is explicitly confirmed as 145 t |
| VT-03 | Changeover calculation | Two 1.5-hour changeovers total 3 hours |
| VT-04 | Capacity deduction | At 1.25 t/hour, changeover allowance equals 3.75 t |
| VT-05 | Effective capacity | 145 − 3.75 = 141.25 t, provided these deductions are not already included |
| VT-06 | Utilization calculation | Nominal 95.5%; effective approximately 98.1% |
| VT-07 | Material readiness | Packaging and raw materials are available by planned operation dates |
| VT-08 | Calendar validation | Shifts, breaks, maintenance, and cleaning are consistently represented |
| VT-09 | Breakdown scenario | Eight lost hours at 1.25 t/hour remove 10 t of modeled output |
| VT-10 | Overtime recovery | Six overtime hours recover 7.5 t, giving 138.75 t capacity |
| VT-11 | Demand coverage after recovery | 138.75 t capacity covers 138.5 t demand with 0.25 t headroom |
| VT-12 | Release-control review | Proposed schedule is reviewed for material, quality, shelf-life, warehouse, and shipping constraints |

## Governance checkpoints

- **Before planning:** validate demand version, master data, unit conversions, material availability, production rates, and calendar.
- **Before schedule acceptance:** review overloads, changeovers, due dates, and the effect of any finite-capacity constraints.
- **After an exception:** record the downtime assumption, identify affected orders, compare recovery options, and obtain approval for overtime or alternate-resource use.
- **Before production release:** confirm materials, quality requirements, pack sizes, shelf-life constraints, warehouse space, and shipping dates.
- **After execution:** replace illustrative values with actual output, scrap, downtime, and adherence measures, and explain material deviations.

## Limitations

The case study is a learning simulation. The test cases define expected arithmetic and review evidence; they do not represent a live SAP test log. Actual configuration, interface names, and application behavior depend on the SAP product/version and the organization's implementation.
