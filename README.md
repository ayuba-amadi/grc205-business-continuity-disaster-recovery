# GRC205 — Business Continuity and Disaster Recovery

**An academic BC/DR planning and recovery simulation | Northbridge Skills Institute**

**International Cybersecurity and Digital Forensics Academy (ICDFA)**  
GRC205 — Incident Management and Business Continuity · Week 21  
**Project documentation:** 21 October 2026

## Project overview

This repository presents an individual academic assessment of **business continuity and disaster recovery (BC/DR)** for **Northbridge Skills Institute**, a fictional training provider. The exercise begins at **08:00 WAT on Day 0**, when flooding and a power failure make the institute's main site and local systems unavailable. The scenario requires decisions about learner safety, critical services, recovery dependencies, data protection, alternate facilities, staffing and affordable resilience.

The project applies a business-led approach: establish which services must continue, quantify disruption impacts, justify restoration and data-loss objectives, select an affordable recovery strategy, coordinate operational response, and evaluate proposed arrangements against a modelled technician schedule and a simulated tabletop exercise.

The repository contains **six documented tasks** and a consolidated **Word/PDF assessment report**. The supporting Markdown documents provide the reasoning, matrices, calculations, decisions and proposed controls behind the report.

## Author and academic details

| Field | Information |
|---|---|
| **Student / author** | **Ayuba Amadi** |
| **Registration number** | **2025/GCR/12684** |
| **Official student email** | **gcr2512684@students.icdfa.edu.ng** |
| **Institution** | International Cybersecurity and Digital Forensics Academy (ICDFA) |
| **Course** | GRC205 — Incident Management and Business Continuity |
| **Assessment** | Business Continuity and Disaster Recovery, Week 21 |
| **Assessment weighting** | 100 marks; contributes 30% of final course grade |
| **Repository owner** | [ayuba-amadi](https://github.com/ayuba-amadi) |

### Brief author biography

**Ayuba Amadi** is a cybersecurity, governance, risk and compliance (GRC), and data protection practitioner and learner with interests in incident response planning, operational resilience, information governance and practical digital systems. This portfolio documents his academic application of BC/DR methods, structured risk analysis, accountable decision-making and evidence-based technical planning. It is presented as **coursework**, not as proof of an implemented continuity programme or a professional certification.

## Assessment scope and constraints

| Scenario parameter | Provided information |
|---|---|
| Organisation | Fictional Northbridge Skills Institute: **1,800 learners, 90 staff** |
| Disruption | Flooding and power failure at **08:00 WAT, Monday (Day 0)** |
| Initial main-site closure estimate | **72 hours** |
| Scheduled examination | **120 candidates at 11:00**; **40** need a centre workstation |
| Alternate premises | **25 workstations available from 10:00** |
| Recovery personnel | **Two technicians**, with business coordinators supporting continuity arrangements |
| Shared technical dependencies | Recovery network, **AUTH01**, **DB01**, and service applications **LMS01, FIN01, REG01, HR01**; **FS01** for records |
| Available communications | Microsoft 365 identity and email via mobile internet; local systems use separate AUTH01 |
| Annual strategy budget | **NGN 3,000,000**, including required independent backup protection and training/testing provisions |

The analysis identifies the **15-workstation shortfall**, the shared identity/database recovery bottlenecks and the need for **business service acceptance**, not simply a successful server restoration.

## Lab navigation — six assessment tasks

| Task | Directory | Key contents | Marks |
|---|---|---|---:|
| **1 — Business Impact Analysis** | [01-business-impact-analysis/](01-business-impact-analysis/) | Five-function BIA, impact calculations, minimum acceptable services, dependency analysis and recovery priority | 20 |
| **2 — Recovery Objectives and Backups** | [02-recovery-objectives-backups/](02-recovery-objectives-backups/) | RTO, RPO and MTD targets; checkpoint ages and gaps; protected backup architecture and validation procedures | 15 |
| **3 — Strategy and Budget** | [03-strategy-and-budget/](03-strategy-and-budget/) | Cold/warm/hot comparison, complete annual costs, provisional warm-site recommendation and residual risks | 15 |
| **4 — Coordinated BC/DR Plan** | [04-continuity-recovery-plan/](04-continuity-recovery-plan/) | Activation, governance, RACI, interim services, DR runbook, stakeholder communications and controlled site return | 20 |
| **5 — Recovery Schedule and Tabletop** | [05-recovery-schedule-exercise/](05-recovery-schedule-exercise/) | Two-technician schedule, objective comparisons, Mermaid Gantt, four tabletop injects and corrective actions | 15 |
| **6 — Governance and KPIs** | [06-governance-and-kpis/](06-governance-and-kpis/) | Plan ownership, testing calendar, NIST/ISO mapping, KPI dashboard and 12-month maturity improvement | 10 |
| **Report presentation and references** | [final-submission/](final-submission/) | Consolidated academic report, references and accompanying PDF | 5 |

## Final assessment documents

| Format | Open document |
|---|---|
| **Microsoft Word — official assessment format** | [GRC205_BCDR_Assignment_2025-GCR-12684.docx](final-submission/GRC205_BCDR_Assignment_2025-GCR-12684.docx) |
| **PDF — reading and repository copy** | [GRC205_BCDR_Assignment_2025-GCR-12684.pdf](final-submission/GRC205_BCDR_Assignment_2025-GCR-12684.pdf) |
| **Submission folder guide** | [Final Submission README](final-submission/README.md) |

The academic brief requires **one Word document** through the ICDFA E-Campus assessment page. **Publication on GitHub does not confirm institutional submission, acceptance or a grade.**

## Selected analytical findings

These figures are **exercise calculations and modelled outcomes**, not observed losses or results from live systems.

| Measure | Outcome |
|---|---|
| Estimated **8-hour disruption impact**, assuming no recovery/continuity | **NGN 1,200,000** |
| Estimated **24-hour disruption impact**, under the same assumption | **NGN 3,360,000** |
| Annual **cold / warm / hot** package costs, including required additions | **NGN 1,200,000 / 2,100,000 / 3,000,000** |
| Provisional strategy | **Warm site**, with business workarounds and explicit recovery-objective exceptions |
| Earliest modelled **LMS01 technical completion** | **11:45 WAT** — after the 11:00 examination |
| Feasible modelled **all-five technical completion** | **12:15 WAT**, with two technicians and baseline-valid backups |
| Tabletop stress scenario | **45-minute simulated discussion**, with four injects and eight proposed corrective actions |

**Critical distinction:** Technical restoration times do not certify safe, accessible, accurate and business-approved service resumption. In the separate minute-30 tabletop inject, a failing DB01 incremental invalidates the baseline recovery-point assumption; resulting delayed finish times are **not invented**.

## Methodology and source basis

The academic work follows the provided **ICDFA GRC205 Week 21 assessment brief and teaching slides**, supported by high-level educational alignment with **[NIST SP 800-34 Revision 1](https://doi.org/10.6028/NIST.SP.800-34r1)** and **[ISO 22301](https://www.iso.org/standard/75106.html)**. The documented workflow connects:

**Business Impact Analysis → recovery objectives → costed strategy → coordinated continuity and DR procedures → schedule/tabletop evaluation → governance and improvement.**

Detailed definitions, assumptions, tables, RACI assignments and supporting citations appear in the task directories and final report. These references demonstrate a **study-based alignment**, not verified standards compliance or ISO certification.

## Evidence, limitations and academic integrity

Northbridge Skills Institute and the disruption are **fictional**. Source-provided facts are distinguished from proposed service targets, planning assumptions, modelled technical outcomes and explicitly **simulated** tabletop decisions.

No live flood response, production restoration, contact with suppliers, real learner communication, completed corrective action or institutional BCMS approval is claimed. Proposed governance roles and recovery controls require actual authorisation and verification before real-world deployment.

The final report includes the academic references and AI-assistance acknowledgement required by the course brief. Student identification is included to identify the coursework author.

---

**Repository maintained by [Ayuba Amadi](https://github.com/ayuba-amadi)** · **21 October 2026**  
[Explore Task 1](01-business-impact-analysis/) · [Browse the final submission](final-submission/)
