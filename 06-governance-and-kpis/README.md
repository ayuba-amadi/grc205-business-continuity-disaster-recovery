# Task 6 — Governance and Performance Measures

**GRC205 | Northbridge Skills Institute | Task 6 of 6**  
**Status:** Proposed governance and performance framework ready for review. **No actual institutional approval, certification, training or live recovery test is claimed.**

## 1. Plan ownership, approval and accountability

The purpose of the BC/DR programme is to protect learners and staff, maintain approved minimum services during disruption, restore safe information systems, and demonstrate continuous improvement. Northbridge's flood and power incident is **fictional**; its baseline site closure is **72 hours**, with a separate tabletop extension to **five days**. The BIA covers F1–F5 and the technical dependencies network, AUTH01, DB01, LMS01, FIN01, REG01, HR01 and FS01.

| Governance role | Proposed authority and evidence |
|---|---|
| **Executive Sponsor / Institute Director** | Approves BC/DR policy, strategy, budget, proposed RTO/RPO/MTD, risk exceptions and return-to-site; receives quarterly performance reports and chairs an executive review. **Only this role or formally delegated Deputy Director activates the plan.** |
| **BC/DR Coordinator — plan owner** | Owns controlled master plan, version history, BIA refresh, exercise programme, contact list, KPI evidence, corrective-action register and distribution; submits annual reapproval pack. |
| **Business service owners (Academic, Finance, Registrar, HR, Records)** | Approve minimum acceptable service definitions and temporary transaction controls; sign off business recovery; report changing learner, examination, admissions and payroll deadlines. |
| **DR Lead / two technicians** | Owns technical runbook, backup chain evidence, isolated restores, achieved RTO/RPO measurements and supplier technical testing; ensures no technician is scheduled for overlapping actions. |
| **Facilities and Procurement Leads** | Validate safe sites, flood/power hazard controls, geographically separate alternate facility, contracted support, 25-workstation capacity and additional examined requirements. |
| **Information Security / IR Lead and privacy adviser** | Review backup-admin separation, privileged access, encryption, integrity, suspected compromise, evidence preservation and appropriate data-protection escalation. |
| **Communications Lead and HR/training coordinator** | Maintain approved contact channels and accessible learner notices; monitor role-based training and escalation-drill participation. |

**Approval rule:** Policy and material risk decisions require Sponsor sign-off; owner-specific service acceptance cannot be substituted by IT completion. The [Task 4 RACI](../04-continuity-recovery-plan/) retains one accountable role per decision/activity. An approved deputy may act only when documented in the decision log.

## 2. Document lifecycle, distribution and review triggers

**Controlled document:** “Northbridge BC/DR Plan,” proposed **v1.0 draft** for academic exercise; owner BC/DR Coordinator; approver Executive Sponsor; next review **within 12 months of approval**, and immediately after a trigger. No fictional signatories or actual approval dates are entered.

**Version history / change control template**

| Version / state | Change | Prepared / reviewed | Approval evidence |
|---|---|---|---|
| **0.1 — academic proposal** | Tasks 1–6: BIA, objectives, strategy, coordinated plan, modelled schedule, tabletop and governance | BC/DR Coordinator (simulated role) | **Not approved or deployed** |
| **1.0 — proposed future baseline** | Incorporate supplier tests, owner approval, emergency contacts and approved RTO/RPO | Plan owner, affected service owners, Security/Facilities | Sponsor's signature/date required; **not yet issued** |
| **1.x — controlled revision** | After incident, change, exercise or material risk finding | Plan owner records version, reasons, sections and reviewer | Sponsor or delegated authority, according to change significance |

**Distribution:** Approved current master in access-controlled institutional storage; offline encrypted emergency copies for named command, facilities and DR roles (with separate recovery keys); read-only role-appropriate extracts for business coordinators, communications and suppliers. Record recipient, version, access authorisation and confirmation of receipt. Personal contact lists, payroll/banking details and emergency credentials are **not** to be committed to the public coursework repository.

**Mandatory refresh triggers:** material flood hazard or climate exposure changes; primary/alternate site or supplier contract changes; alteration of network, AUTH01, DB01, application or backup architecture; a change to exam timetable or statutory obligations; failed backup/restore, missed recovery objective or suspicious administrator access; new accessibility or staff constraints; exercise findings; or a real incident. Update BIA/dependency inventory, target approvals, security controls and corrective-action closure evidence together.

## 3. Risk-based 12-month testing and training calendar

**Risk rule:** Highest frequency applies to the examination and shared recovery chain (F1/DB01/AUTH01) because they carry strict RTO/RPOs, multiple dependent functions and significant data-integrity risk. Tests use **isolated** environments unless executive change approval explicitly permits production impact. Frequencies are proposals subject to staff availability, scope and the **NGN 200,000** annual training/testing provision in Task 3; actual activity costs require quotations.

| Period / frequency | Planned exercise and minimum evidence | Owner | Risk and approval gate |
|---|---|---|---|
| **Every day; reviewed weekly** | Automated backup success/freshness monitoring; verify alerts, accessible catalog, full-plus-incremental chain and backup-admin audit records. Weekly exception register. | DR Lead / Security Lead | **High:** DB01 15-minute proposed protection and independent restore access. An alert alone does not prove restore capability. |
| **Monthly (M1–M12)** | **Isolated DB01 point-in-time restore**, including randomly chosen increments and a representative LMS/FIN record; record restore duration, achieved point, integrity results and owner check. | DR Lead | **High:** F1/F2 target breaches in the baseline. Two-technician test must not disrupt production. |
| **Quarterly (M3, M6, M9, M12)** | 45-minute cross-functional **tabletop** alternating flood, power, alternate-workstation shortfall and failed backup/admin logon scenarios; test contact tree and learner notice. | BC/DR Coordinator | **High:** examination accessibility and cross-team escalation. Record inject decisions, exercise log and corrective actions. |
| **Quarterly (M3, M6, M9, M12)** | Isolated **AUTH01 and FS01 restore**, including permissions, independent key/credential recovery and alternate-provider export. | DR Lead / Security Lead | **High:** identity concentration and FS01 privacy/integrity. |
| **Semi-annual (M6, M12)** | Structured operational **walkthrough** of recovery network → AUTH01 → checks → DB01 → applications with **two technicians**, business owner acceptance and safe rollback. | DR Lead / service owners | **High:** resource feasibility and real acceptance thresholds. |
| **Annual (M12)** | Extended alternate-site exercise, supplier SLA/geographic/power review, staff/accessibility validation, BIA and objectives refresh, corrective-action review and Sponsor management decision. | Executive Sponsor / Facilities / BC/DR Coordinator | **Strategic:** resilience and funded capability. Do not claim a full-interruption live test unless performed and approved. |
| **At onboarding and after material changes** | Role-specific command, finance reconciliation, temporary admissions, secure evidence and accessible exam notice training; maintain attendance and competency checks. | HR/training coordinator | **High when roles change:** untrained responders are a dependency failure. |

**Exercise evidence standard:** Record date, scope, participants (actual or simulated), action-level start/finish, prerequisite compliance, approved recovery checkpoint, security/data integrity results, independently accepted service point, RTO/RPO outcome, defects, owners and corrective-action due dates. The [Task 5 exercise](../05-recovery-schedule-exercise/) is **hypothetical** and must not be counted as an observed production restore.

## 4. Framework alignment — educational mapping, not certification

### NIST SP 800-34 Revision 1

The NIST contingency planning guide describes **seven planning steps**; the present coursework maps concrete outputs to them. NIST SP 800-34 Rev. 1 is federal-system guidance and is used here as a **transferable planning framework**, not evidence that Northbridge meets federal requirements.

| NIST planning step | GRC205 output / implementation evidence |
|---|---|
| **1. Develop contingency planning policy** | Task 4 activation roles, delegation, escalation and this Task 6 approval/version-control model |
| **2. Conduct BIA** | [Task 1](../01-business-impact-analysis/): five functions, 8-hour/24-hour costs, deadlines, minimum service and priority |
| **3. Identify preventive controls** | [Task 2](../02-recovery-objectives-backups/): isolated/immutable encrypted backups, independent admin roles and tested restore chains; Task 6 flood/power mitigations |
| **4. Create contingency strategies** | [Task 3](../03-strategy-and-budget/): cold/warm/hot, full NGN budget, qualified warm recommendation and residual acceptance |
| **5. Develop information system contingency plan** | [Task 4](../04-continuity-recovery-plan/): ordered prerequisites, runbook, business acceptance, alternative operations and return-to-site |
| **6. Ensure testing, training and exercises** | [Task 5](../05-recovery-schedule-exercise/): non-overlapping two-tech model and simulated injects; Task 6 test calendar |
| **7. Plan maintenance** | Task 6 controlled versions, annual review, change triggers, distribution and corrective-action governance |

### ISO 22301:2019 BCMS themes from Week 21 slide 9

This is a **high-level educational alignment** to the themes summarised in the provided teaching slides and ISO's public standard overview, **not** a clause-by-clause compliance assessment or claim of certification.

| ISO 22301 theme | Corresponding output and responsible evidence |
|---|---|
| **Context (Clause 4)** | Fictional institute's learners, staff, deadlines, flood/power exposure, alternate premises and external dependencies in Task 1 |
| **Leadership (Clause 5)** | Sponsor approval, policy ownership, delegated command and risk acceptance in Task 4 and Task 6 |
| **Planning (Clause 6)** | Prioritised BIA, proposed measurable RTO/RPO/MTD, budget and treatment decisions in Tasks 1–3 |
| **Support (Clause 7)** | Two-technician capacity, communications fallback, competence/training, information protection and controlled documentation |
| **Operation (Clause 8)** | Approved continuity alternatives, backup controls, ordered recovery runbook, technical/business gates and tabletop |
| **Performance evaluation (Clause 9)** | KPI formulas, evidence sources, review frequency, objective breaches and exercise outcomes in this task |
| **Improvement (Clause 10)** | Eight hypothetical Task 5 corrective actions, due dates, re-testing and management closure approvals |

**Climate/flood consideration:** The 2024 amendment to ISO 22301 prompts consideration of climate-related issues in the organisation's management-system context. Northbridge should use site-specific **flood mapping, rainfall/extreme-weather trends, drainage and power reliability** to assess whether primary and alternate facilities face the **same floodplain, substation or telecommunications outage**. Require geographic/power diversity, safe access and climate-informed site-selection evidence. The scenario establishes a flood, **not** a measured future climate trend or evidence of climate-change causation.

## 5. Measurable performance dashboard — proposed programme KPIs

**Measurement principles:** The denominator and evidence source must be defined before reporting. A missing measurement is **“not measured”**, not zero success. A simulated exercise does not prove production recovery effectiveness. Targets are **12-month proposals**, and the reported baseline below is limited to **modelled** observations.

| KPI / formula | Evidence/data source | Proposed target by Month 12 | Frequency / accountable owner | Current evidence status |
|---|---|---|---|---|
| **K1 — On-time technical recoveries (%) = 100 × number of tested F1–F5 functions whose observed technical restore time ≤ approved RTO / number of tested F1–F5 functions with valid time measurements.** Report separate business acceptance success. | Signed restore logs, action timestamps, approved RTO matrix, owner acceptance | **≥90%** of valid tested function outcomes and **100%** of critical F1 objectives, or an explicitly signed exception | After each test; **DR Lead** | **Modelled only:** Task 5 gives **4/5 = 80%** against proposed RTOs; **not** an actual tested KPI. F1 fails. |
| **K2 — RPO compliance (%) = 100 × tested function-data dependency checkpoints meeting approved RPO / all tested in-scope function-data dependency checkpoints.** Count each dependency once per function and publish scope. | Backup checkpoint manifests, hashes, full/incremental chain and isolated restore validation | **100%** of critical F1/F2 data tests; **≥95%** for all valid dependency tests | Monthly/quarterly; **DR Lead / Information Security Lead** | **Checkpoint-age model**, not an observed restore: DB01/AUTH01 for F1–F4 plus FS01/AUTH01 for F5 = **10 comparisons**, of which F3 DB, F4 DB and both F5 dependencies meet target: **4/10 = 40%**. |
| **K3 — Restoration-test coverage (%) = 100 × critical technical assets with a completed, evidence-backed restore test in the reporting period / critical technical assets in approved recovery inventory.** | Test plan, signed logs and asset inventory | **100%** of critical assets at least annually; monthly DB01 checks | Quarterly; **BC/DR Coordinator** | **Not measured.** No evidence of real restores; Task 5 baseline is hypothetical. |
| **K4 — Corrective-action closure on time (%) = 100 × actions closed by approved due date with accepted evidence / all actions due in period.** Report overdue count and aging alongside percent. | Controlled CA01–CA08 tracker, closure test reports, Sponsor/owner acceptance | **≥90%** on time, **zero overdue P1** without signed escalation | Monthly; **BC/DR Coordinator** | **Not measured** in real operations. Task 5's **eight open actions** arise solely from simulation; do not present them as actual failed institutional performance. |
| **K5 — Training and competence completion (%) = 100 × assigned responders completing required training and role check / responders assigned in approved role roster.** | HR attendance register, learning checks and role list | **≥95%** by Month 12, and **100%** of activation decision-makers | Quarterly; **HR / Training Coordinator** | **Not measured**; actual roster and training records are unavailable. |
| **K6 — Plan currency (%) = 100 × approved service plans reviewed within 12 months and after relevant trigger / all approved service plans in scope.** | Version history, change records and sponsor approval | **100%** current, no unreviewed material change | Quarterly; **BC/DR Coordinator** | **Not measured**; current documents are academic proposals, not approved deployed plans. |

**Dashboard computation note:** K2's 4/10 is a *conservative teaching-case dependency comparison* aligned with the proposed Task 2 decision to apply each function's RPO to its AUTH01 dependency. It is not a measured “restore success rate”; institutional approval of a distinct identity-data RPO would change scope/denominator prospectively. K1's **4/5** counts technical application completion only and **does not** certify minimum business service or the 11:00 examination. For real reporting, display each KPI with **numerator, denominator, collection window, evidence status and owner**.

## 6. Maturity assessment and realistic 12-month target

The teaching deck's **slide 13** defines five levels: **1 Initial/ad hoc**, **2 Developing/repeatable**, **3 Defined/standardised**, **4 Managed/measured**, **5 Optimising**.

**Present evidence-based judgement:** The **fictional exercise case supports an indicative Level 2 (Developing) planning posture**, **not a verified institutional rating**. Reasons: some recoverable backups and a warm-site drill model exist, but separate backup administration is not demonstrated; baseline DB01/AUTH01 points miss strict F1/F2 RPOs; alternative devices cannot meet all 40 examination users; supplier access independence and real recovery test records are absent. Newly authored coursework plans **cannot** be credited as an approved, deployed and exercised management system.

**12-month improvement objective:** Advance to **Level 3 (Defined/Standardised)** *subject to independent evidence*, not simply by rewriting procedures.

| Timing | Planned milestone | Acceptance evidence to support Level 3 |
|---|---|---|
| **Months 1–3** | Sponsor approves policy/roles, BIA, RTO/RPO/MTD and warm-site residual risks; baseline external supplier and flood/power reviews. | Signed policy and objectives, approved alternate-site capacity plan, controlled v1.0 issue, initial roster. |
| **Months 4–6** | Establish admin-separated protected backups; test DB01 incremental-chain fallback and AUTH01/FS01 recovery; develop accessible examination alternative for the **15-device baseline deficit** and **25-device stress deficit**. | Privileged-access evidence, full isolated restore results, candidate capacity/fairness test and reconciled business records. |
| **Months 7–9** | Repeat cross-functional exercise, test actual two-technician workload and staff competence, measure RTO/RPO and close overdue P1 actions. | Signed test evidence, actual service-owner acceptance timestamps, training dashboard and verified CA closure. |
| **Months 10–12** | Demonstrate recurrent testing, controlled changes, verified supplier contingency, management review and an independently sampled KPI dashboard. | Audit-ready reports with denominators, corrective-action evidence, owner decisions and formal maturity reassessment. |

**Decision test:** If F1 service remains incapable of meeting its examination business deadline, backups lack independent restore evidence or critical actions remain open without accepted mitigation, **do not declare Level 3 achieved**. Record the remaining Level 2 status and a revised funded corrective programme.

## 7. Task 6 marking-rubric traceability (10 marks)

| Assessment criterion | Evidence presented |
|---|---|
| **Ownership, calendar, framework mapping, maintenance (5)** | Clear sponsor/plan owner/deputy, documented review/distribution/training controls, risk-based 12-month programme, **seven** NIST steps, **seven** ISO BCMS themes and flood/climate issue |
| **Measurable KPIs (3)** | **Six** defined KPIs with formulas, sources, targets, reporting cycles, accountable owners and honest baseline evidence classification |
| **Maturity and improvement (2)** | Slide-13 five-level model; qualified **Level 2** judgement, credible **Level 3 in 12 months** objective and verification milestones |

**Next gate:** Tasks 1–6 now comprise an integrated **academic analysis**. Before submitting, validate the complete marking rubric, resolve any inconsistent assumptions, ensure references cite at least two authoritative sources, and produce **one 3,000–3,500-word DOCX** plus the optional corresponding PDF. The Word file is the formal E-Campus deliverable; the PDF is a supplementary repository artefact.

## References

- ICDFA (n.d.). *Business Continuity and Disaster Recovery*, GRC205 Week 21 teaching deck, **slides 4, 9, 11–14**, especially slide 13's five-level maturity model (provided material).
- ICDFA (n.d.). *GRC205 Business Continuity and Disaster Recovery Assignment*, pp. 7–8 (Task 6 and marking rubric; provided brief).
- NIST (2010). *Contingency Planning Guide for Federal Information Systems*, SP 800-34 Rev. 1. https://doi.org/10.6028/NIST.SP.800-34r1 (official publication).
- ISO (2019). *ISO 22301:2019 — Security and resilience: Business continuity management systems — Requirements*. https://www.iso.org/standard/75106.html (official overview; full standard not reproduced).
- ISO (2024). *ISO 22301:2019/Amd 1:2024 — Climate action changes*. https://www.iso.org/standard/88412.html (official amendment overview).

[Task 5 — Schedule and Tabletop](../05-recovery-schedule-exercise/) · [Repository overview](../README.md)
