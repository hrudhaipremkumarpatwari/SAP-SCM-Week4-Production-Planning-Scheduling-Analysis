# SAP SCM Week 4 — Production Planning and Scheduling Analysis

**Internship project | SAP Supply Chain Management (SAP SCM)**

## Six-Assessment Portfolio Navigation

This assessment is part of my six-assessment SAP SCM internship portfolio. The series is structured as one connected learning journey from network planning through performance improvement.

| Week | Assessment | Repository |
|---|---|---|
| 1 | Supply Chain Network Planning | [Open Week 1](https://github.com/hrudhaipremkumarpatwari/SAP-SCM-Supply-Chain-Network-Planning) |
| 2 | Master Data & Inventory Optimization | [Open Week 2](https://github.com/hrudhaipremkumarpatwari/SAP-SCM-Master-Data-Inventory-Optimization) |
| 3 | Logistics & Distribution Network Design | [Open Week 3](https://github.com/hrudhaipremkumarpatwari/SAP-SCM-Logistics-Distribution-Network-Design) |
| 4 | Production Planning & Scheduling Analysis | [Open Week 4](https://github.com/hrudhaipremkumarpatwari/SAP-SCM-Week4-Production-Planning-Scheduling-Analysis) |
| 5 | Supply Chain Integration & Collaboration | [Open Week 5](https://github.com/hrudhaipremkumarpatwari/SAP-SCM-Week5-Supply-Chain-Integration-Collaboration) |
| 6 | Performance Evaluation & Continuous Improvement | [Open Week 6](https://github.com/hrudhaipremkumarpatwari/SAP-SCM-Week6-Performance-Evaluation-Continuous-Improvement) |

**Central portfolio hub:** [SAP-SCM-Internship-Portfolio](https://github.com/hrudhaipremkumarpatwari/SAP-SCM-Internship-Portfolio) — the central index for the complete series.



This repository contains a production-planning case study built around an illustrative food-manufacturing scenario. It focuses on capacity-aware scheduling, identifying a bottleneck, evaluating a short equipment-breakdown scenario, and documenting practical validation checks.

## Project objective

Translate a weekly demand plan into a feasible production schedule while checking resource capacity, material readiness, changeovers, and recovery options. SAP APO Production Planning and Detailed Scheduling (PP/DS) concepts are used as the functional framework; the report also discusses the wider planning and integration context.

## Case study

The fictional company **Deccan Harvest Foods Pvt. Ltd.** makes three millet-based ready-to-cook products:

| Product | Illustrative weekly demand |
|---|---:|
| MUM500 | 55.2 t |
| RDM500 | 48.3 t |
| JIM500 | 35.0 t |
| **Total demand** | **138.5 t** |

### Key capacity findings

| Measure | Result |
|---|---:|
| Weekly mixing capacity | 160 t |
| Nominal packaging capacity | 145 t |
| Packaging capacity after two 1.5-hour changeovers at 1.25 t/hour | 141.25 t |
| Utilization against nominal packaging capacity | 95.5% |
| Utilization against effective packaging capacity | 98.1% |
| Effective headroom before a disruption | 2.75 t |
| Capacity lost in an illustrative 8-hour breakdown | 10 t |
| Capacity after breakdown, before recovery | 131.25 t |
| Shortfall against 138.5 t demand | 7.25 t |
| Output recovered by 6 overtime hours | 7.5 t |
| Recovered capacity after overtime | 138.75 t |

The recovery case leaves only **0.25 t** of capacity above demand, so it is a fragile recovery plan rather than a comfortable operating buffer. It meets the modeled demand total, but does not support a 140 t production target in that same breakdown scenario.

## Repository contents

- **docs/** — the full internship report and written supporting analysis.
- **docs/risk-and-validation.md** — risk register, controls, and proposed validation checks.
- **diagrams/** — editable Mermaid flow diagrams for the planning process and bottleneck recovery.
- **README.md** — project overview and key results.

## SAP SCM topics covered

- Demand and supply planning assumptions
- SAP APO PP/DS concepts and finite-capacity scheduling
- Planning master data, resources, calendars, and production data structures
- Material-readiness and integration checks
- Bottleneck analysis and disruption recovery
- KPI monitoring, validation, exception handling, and governance

## How to review this project

1. Read the final report in **docs/** for the end-to-end case study.
2. Review the worked calculations in **docs/production-planning-analysis.md**.
3. Use the files in **diagrams/** to follow the planning and recovery logic.
4. Review **docs/risk-and-validation.md** for the proposed controls and tests.

## Scope and limitations

This is a learning and internship simulation. The company, product codes, capacities, demand, schedule, and scenario results are illustrative assumptions. The report describes SAP planning concepts and a configuration/validation approach; it does **not** claim that the scenario was executed in a live SAP system or that the figures are live system output. Any real implementation would require verification against the organization's SAP version, master data, resource calendars, material availability, and operating rules.
