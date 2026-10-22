# Production Planning and Scheduling — Supporting Analysis

## 1. Scenario and assumptions

The case study uses a fictional manufacturer, Deccan Harvest Foods Pvt. Ltd., producing three millet-based ready-to-cook products. All quantities and rates below are illustrative and are used to demonstrate planning logic.

| Parameter | Assumption |
|---|---:|
| MUM500 weekly demand | 55.2 t |
| RDM500 weekly demand | 48.3 t |
| JIM500 weekly demand | 35.0 t |
| Mixing capacity | 160 t/week |
| Nominal packaging capacity | 145 t/week |
| Raw millet supply available | 150 t/week |
| Packaging material lead time | 5 days |
| Packaging throughput | 1.25 t/hour |
| Planned changeovers | 2 × 1.5 hours |
| Illustrative weekly cleaning / quality hold | 6 hours |
| Illustrative planned maintenance | 4 hours |

The values are not a live SAP extract. In a real environment, the planner should validate demand, base units of measure, work-center/resource calendars, routing or production-version data, production rates, lot-size rules, and material availability before scheduling.

## 2. Demand reconciliation

Total weekly demand is:

55.2 t + 48.3 t + 35.0 t = **138.5 t**

Raw millet supply of 150 t is 11.5 t above finished-product demand as a simple high-level comparison. This is not a complete material-balance proof: actual consumption depends on each product's bill of material, yield, process loss, quality loss, and unit conversions.

## 3. Effective packaging capacity

Two changeovers require:

2 × 1.5 hours = **3 hours**

At 1.25 t/hour, the modeled capacity consumed by those changeovers is:

3 hours × 1.25 t/hour = **3.75 t**

Effective packaging capacity after this changeover allowance is:

145 t − 3.75 t = **141.25 t**

The effective headroom against demand is:

141.25 t − 138.5 t = **2.75 t**

Nominal utilization is 138.5 ÷ 145 = **95.5%**. Utilization against the reduced effective capacity is 138.5 ÷ 141.25 = **98.1%**. Effective utilization is the more informative warning signal here because the schedule has little spare capacity after the modeled changeovers.

The 6-hour cleaning / quality hold and 4-hour planned-maintenance assumptions must be represented consistently in the resource calendar or available-capacity model. They must not be deducted a second time if already included in the provided 145 t nominal capacity figure. In a real plan, the capacity definition needs to be checked before applying these adjustments.

## 4. Breakdown and recovery analysis

An 8-hour packaging-line breakdown removes modeled output of:

8 hours × 1.25 t/hour = **10 t**

Capacity after that interruption, while retaining the changeover allowance used above:

141.25 t − 10 t = **131.25 t**

The shortfall against demand becomes:

138.5 t − 131.25 t = **7.25 t**

Six hours of overtime would recover:

6 hours × 1.25 t/hour = **7.5 t**

Resulting modeled capacity:

131.25 t + 7.5 t = **138.75 t**

Residual capacity above demand is therefore 138.75 t − 138.5 t = **0.25 t**. The calculation demonstrates that overtime can theoretically recover the modeled demand, but the residual buffer is small. It does not account for unexpected minor stops, speed loss, additional cleaning, quality rejects, or other real-world losses. The overtime must also be checked against labor rules, maintenance status, material supply, and quality controls.

**Important distinction:** a separate baseline illustration may target 140 t output against 138.5 t demand (a 1.5 t buffer) if the 141.25 t effective capacity is available. After the modeled breakdown and 6 hours of overtime, however, 138.75 t is the recovery capacity; it supports 138.5 t demand but not a 140 t output target.

## 5. Scheduling decisions to test in SAP PP/DS

1. Confirm calendar, resource, and production-rate data before creating a finite schedule.
2. Check material availability and packaging-material lead time before releasing orders.
3. Sequence products to balance demand priority, changeover requirements, and customer dates.
4. Compare the optimizer / scheduling proposal with a planner-reviewed schedule; do not accept a mathematically feasible sequence without checking operating rules.
5. Simulate the breakdown as an exception, reschedule affected operations, and compare overtime with alternate-resource or split-lot options.
6. Confirm quality, shelf-life, warehouse, and shipping constraints before proposing output above the demand total.

## 6. KPIs for the planner

- Demand attainment = confirmed feasible output ÷ planned demand.
- Resource utilization = scheduled load ÷ available capacity, using a clearly defined capacity basis.
- Schedule adherence = operations completed on the planned date/time ÷ operations due.
- Changeover hours = total sequence-dependent setup time in the period.
- Downtime loss = planned rate × unplanned downtime, used as an estimate and reconciled with actual production data.
- Exception recovery time = time from disruption to an accepted revised schedule.

KPI definitions should use consistent time windows, units, and source systems. A simulated calculation should remain labeled as simulated until verified against SAP records and actual shop-floor reporting.
