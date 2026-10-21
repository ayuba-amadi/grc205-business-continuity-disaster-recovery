# Task 4 — Business Continuity and Disaster Recovery Plan

**GRC205 | Northbridge Skills Institute | Task 4 of 6**  
**Status:** Coordinated BC/DR plan prepared for academic assessment; **proposed procedures**, not an activated or exercised institutional plan.

## 1. Purpose, scope and command

**Scenario:** Flooding and a power failure disable Northbridge's main campus and local systems at **08:00 WAT, Day 0 (Monday)**. Facilities initially estimates **72 hours** of site closure. **1,800 learners** and **90 staff** may be affected. The **11:00 examination** involves **120 candidates**, of whom **40** need a centre workstation; the alternate venue provides only **25 machines from 10:00**, leaving a **15-device deficit**. Microsoft 365 email/identity work over mobile internet, but local applications rely on **AUTH01**. Two technicians are available for recovery. **No cyberattack is confirmed.**

**Plan scope:** Protect people, coordinate safe alternative delivery of teaching/assessment, fees, admissions, payroll and records (**F1–F5**), restore the network, AUTH01, DB01, LMS01, FIN01, REG01, HR01 and FS01, reconcile temporary records and return safely to the primary site. Integrate [Task 1 impact priorities](../01-business-impact-analysis/), [Task 2 proposed objectives](../02-recovery-objectives-backups/) and [Task 3 provisional warm-site strategy](../03-strategy-and-budget/).

**Authority assignments are proposed for the exercise, not verified named appointments.**

| Role | Authority and operating responsibility | Delegation and backup |
|---|---|---|
| **Executive Sponsor / Institute Director (Incident Commander)** | **Sole plan activation/deactivation authority**, expenditure and residual-risk acceptance, major assessment rescheduling, external escalation, and final return-to-site authorisation. | **Deputy Director** is authorised deputy when the Director is unavailable; the decision log identifies who is acting and when authority transferred. |
| **BC/DR Coordinator (Plan Manager)** | Chairs operational coordination, tracks priorities, assigns business workstreams, logs decisions/objective breaches, convenes situation reports and requests Sponsor decisions. | Nominated Business Continuity Deputy. |
| **Facilities Lead** | Flood/power safety, access restrictions, alternate location inspection, landlord/power/utility contact, documented safe occupancy and return clearance recommendation. | Facilities Deputy. |
| **DR Lead / Technician 1** | Technical restoration sequence and two-technician resource plan; backup checkpoint and change/rollback controls. | Technician 2 serves as operational deputy; cannot be double-booked for simultaneous tasks. |
| **Technician 2** | Restores/validates assigned dependencies and applications under DR Lead direction; records test evidence. | DR Lead when workload and safe coverage permit. |
| **Business owners** | Academic Director/Examinations Lead; Finance Manager; Registrar; HR/Payroll Manager; Records Manager: approve and validate minimum service and reconcile their records. | Each appoints a delegated reviewer with written authority before activation. |
| **Communications Lead** | Drafts consistent staff/learner/provider notices, accessibility formats and timing; obtains Sponsor approval before release. | Named Communications Deputy. |
| **Information Security / IR Lead** | Security triage, identity/log integrity, evidence preservation, containment and security clearance if suspicious activity emerges. | Appointed Security Deputy; coordinates with DR, does not presume the flood is a cyberattack. |

### Activation, escalation and reporting

**Activation thresholds (any):** unsafe/unavailable campus expected beyond **one hour**; critical local systems unavailable such that the **11:00 exam** or financial deadlines are threatened; flood/power conditions prevent safe occupancy; or loss of a shared dependency prevents multiple critical services. Here, activation should be **proposed immediately at 08:00**. The Incident Commander signs time, reason, scope, delegated authority and next review time.

**First 30 minutes:** Facilities prohibits entry and calls relevant emergency/safety contacts as appropriate; BC/DR Coordinator contacts owners and two technicians; Communications Lead confirms accessible contact channels; DR Lead protects logs/backup evidence and identifies restore scope; Sponsor approves the alternate-location and business-continuity approach. **Do not enter a flooded or electrically unsafe site.**

**Escalation:** Any missed F1 10:00 provisional business RTO, infeasible **11:00 examination**, suspected loss of backup integrity, failed independent-access test, privacy concern, or material departure from funded resource limits goes **immediately** to the Sponsor and affected service owner. Critical service exceptions are logged and reassessed at each situation report, not silently accepted.

**Communication fallback:** Primary: approved Microsoft 365 email over mobile networks. Secondary: authorised voice/SMS call tree, with identity verification and minimum necessary personal data; tertiary: face-to-face briefing at a verified safe alternative site. The brief **does not prove** that a particular SMS provider or extra connectivity is available: these routes require pretesting and an approved contact list.

**Situation report cadence (proposed):** at activation, **hourly until the 11:00 examination decision**, every **four hours through Day 0**, then **at least twice daily** while the site remains closed; immediate exceptional reports for deadlines, failed restores or a change to estimated closure. Template fields: timestamp WAT, incident scope, safety, service status and RTO/RPO risk, 25-device availability, decisions/approvals, technicians' workload, backup evidence, supplier status, learner welfare, next action/owner/time, and approved public message. All records are stored in a restricted, access-controlled incident log.

## 2. RACI — exactly one accountable role per activity

**Key:** R = performs work; A = **single** approving/accountable role; C = consulted; I = informed. Multiple responsible roles are permitted, but each row contains **exactly one A**. In this compact matrix, an A role may also execute its responsibility; role abbreviations are **IC** Incident Commander, **BC** BC/DR Coordinator, **FAC** Facilities Lead, **DR** DR Lead/technicians, **ACAD** Academic Director, **FIN** Finance Manager, **REG** Registrar, **HR** HR Manager, **REC** Records Manager, **COM** Communications Lead and **IR** Security/IR Lead.

| Activity | R (responsible) | A (accountable) | C (consulted) | I (informed) |
|---|---|---|---|---|
| Authorise BC/DR activation | BC | **IC** | FAC, DR, ACAD | All owners, COM |
| Approve temporary examination modality / reschedule | ACAD, BC | **IC** | FAC, COM, IR | Learners, DR |
| Validate backup catalog, provenance and recovery point | DR | **DR Lead** | IR, FIN, ACAD | BC, IC |
| Restore network, identity, database and applications | DR | **DR Lead** | IR, affected owners | BC, IC |
| Accept temporary fee confirmations and reconciliation policy | FIN, BC | **FIN** | IR, DR | IC, learners as needed |
| Approve admissions cutoff and temporary intake | REG, BC | **REG** | COM, IR | IC, applicants |
| Authorise payroll bank submission | HR, FIN | **HR** | IR, BC | IC |
| Approve external stakeholder communications | COM, BC | **IC** | ACAD, FAC, IR | Staff, learners, suppliers |
| Validate business service restoration and cutover | DR, affected owner | **Affected business owner** | BC, IR | IC, COM |
| Clear facility for safe re-entry | FAC | **FAC** | Utilities, relevant qualified safety personnel | IC, BC |
| Authorise return to primary site and end alternate operations | BC, FAC, DR, owners | **IC** | IR, COM | All stakeholders |

**Separation-of-duties detail:** DR Lead validates technology; the respective business owner independently **accepts** usable business service. For payroll, HR accountability does not remove Finance's mandatory independent bank-file approval.

## 3. Temporary continuity services for the 72-hour site outage

The goal is a **minimum controlled service**, not unrestricted replication of full local systems. Temporary records are encrypted/restricted, uniquely numbered, timestamped (WAT), verified against independent evidence, and imported to restored systems **only after owner approval**.

| Function | Temporary procedure and staffing/equipment | Approval, privacy and reconciliation |
|---|---|---|
| **F1 Assessment** | Academic Director arranges an alternative invigilated venue from **10:00** with **25 verified devices**; **80 BYOD candidates** require an approved secure exam platform, connectivity, identity and accessibility checks. **40 centre-device candidates − 25 machines = 15 uncovered at once.** Arrange 15 **additional tested, accessible** devices subject to supplier confirmation; or assess controlled staggered sessions *only if timing, examination secrecy, reasonable adjustments and fairness can be assured*; otherwise **formally reschedule**. No method is presumed workable without examination owner sign-off. | Sponsor approves changes/reschedule; Academic Director certifies delivery mode, candidate identity, invigilation, equal opportunity and integrity; keep approved scripts, candidate attendance and results in restricted logs. **Rescheduling after 11:00 triggers the NGN 120,000 model charge.** |
| **F2 Fees** | Finance staff review payment-provider portal/exports using mobile connectivity and maintain a numbered interim ledger with reference, payer, amount, status, time and reviewer. Provide *provisional* fee confirmation as approved; prioritise **16:00 Day 0**. | Finance Manager plus independent reviewer approve exceptions; never infer payments from screenshots alone or duplicate posting; reconcile provider IDs, bank settlements, local DB01/FIN01 and all temporary acknowledgements, documenting discrepancies. |
| **F3 Admissions** | Registrar provides an approved restricted intake channel and time-stamped applications/changes; issue unique case references, confirm receipt and preserve the **18:00 Day 0** cut-off. Accessibility accommodations and alternative support channels require testing. | Registrar sets and documents cutoff/appeal rules; collect minimum data, restrict sharing, check duplicates/eligibility, reconcile case IDs with REG01 on restoration and preserve an import audit trail. |
| **F4 Payroll** | HR/payroll and Finance prepare a draft from last independently verified payroll records, confirmed changes and banking instructions ahead of **12:00 Day 1**. Avoid ad hoc bank-file creation if records cannot be verified. | Dual HR/Finance authorisation, bank acknowledgement, staff confidentiality, no duplicate submission, and exception log are mandatory; only approved changes enter the final ledger. |
| **F5 Records** | Records team establishes an access-controlled request register, issues status updates, and triages time-critical authentic record needs against the **48-hour** service commitment. | Records Manager approves any issue after an independent authoritative source check; otherwise defer rather than produce unsupported certificates. Reconcile request IDs, released versions and audit history with FS01 after restore. |

**Common resource minimum:** Business coordinators and service owner delegates (distinct from the **two dedicated technicians**), trained invigilators, accessible facility, 25 confirmed workstations, approved BYOD controls, secure mobile internet, approved M365 channels, encryption-capable temporary record storage and payment/bank/provider contacts. **Personnel counts beyond the two technicians and workstation inventory are not specified**; staffing adequacy, extra 15 devices, accessible room layout and independent provider portals are **unverified constraints**, not assumed resources.

**Welfare and security:** Issue accessible messages, maintain help contacts, avoid instructing learners to enter flooded buildings or transmit identity/payment information through unofficial links, and preserve statutory privacy controls in all alternative channels.

## 4. Disaster recovery runbook — controlled restore

The **provisional warm site** recommended in [Task 3](../03-strategy-and-budget/) is subject to supplier/geographic validation. The following runbook is procedural. The baseline's **individual durations and two-technician allocation** are modelled separately in Task 5, not invented as accomplished in this plan.

| Order / step | Prerequisite, owner and action | Completion / acceptance evidence | Failure and rollback |
|---|---|---|---|
| **0. Authorise and protect** | IC activates, FAC verifies alternate site safe; DR Lead records inventory, chosen recovery point and change window; IR assesses signs of cyber compromise. | Approval/time, safe site, tech assignments, immutable change/evidence log. | Reject unsafe site, escalate to IC; preserve source logs and evidence. |
| **1. Recovery network (30 min)** | DR technician configures isolated recovery network; check power, routes, approved secure connectivity and admin access. | Measured connectivity and security baseline passed. | Isolate failed network; correct config or switch approved link, log delay. |
| **2. AUTH01 (30 min)** | Network complete. Restore known-good directory/configuration snapshot, examine privileged access and test least-privilege sign-ins. | Authorised sign-ins/group permissions work and snapshot point recorded. | Quarantine inconsistent directory; restore earlier verified state with owner approval and reset exposure calculations. |
| **3. Security and backups (30 min)** | AUTH01 complete. Check catalog, administrator access independence, backup integrity and chain B01 full **23:00 Day −1** plus all necessary B02 incrementals to **07:00 Day 0**; review privileged access. | Signed checklist, selected point/age, valid chain and security disposition. Baseline only **assumes** checkpoints pass. | **Do not** bypass failed integrity checks; isolate affected backup, preserve logs, choose earlier *verified* point, report RPO breach and involve IR when suspicious access is indicated. |
| **4. DB01 (90 min)** | Security/backup checks pass. Restore B01 and ordered verified B02 chain on isolated DB01; run consistency checks. | DB01 schema/table integrity, recovery timestamp and test records validated. | Stop promotion of DB01, restore prior verified checkpoint or offline fallback only after explicit risk acceptance and impact analysis. |
| **5. Applications (LMS01 45; FIN01 30; REG01 30; HR01 45 min)** | Each requires DB01. Assign to **one free technician per indivisible action**; prioritise business urgency while honouring dependencies. | Authentication, representative business records and security checks pass **per application**. | Hold service behind access gate; correct failure or roll back its isolated restoration, notify business owner. |
| **6. FS01 (60 min)** | Requires AUTH01 **and security/backup checks**, but **not DB01**. May run parallel with DB01 if the other technician is free. | Record hashes/permissions, representative certificate/file reads and audit controls pass. | Restore earlier approved copy, keep public issue queue only and flag possible stale/missing versions. |
| **7. Business acceptance** | Owner tests minimal functionality/accessible provision, exception register and reconciliation completeness; BC records actual elapsed time and checkpoint. | **Owner signature**, acceptance time and remaining exceptions. **Technical completion alone is not an accepted business service.** | Continue temporary procedure; declare missed RTO/RPO if applicable and escalate for risk decision. |
| **8. Controlled cutover/rollback** | IC authorises staged traffic after DR and owner recommendations; retain rollback point, monitoring and controlled temporary-record import. | Approved cutover, duplicate/omission checks, monitoring and exception resolution. | Suspend traffic, restore last accepted state, resume temporary services and communicate revised estimate. |

**Boundary:** Current drill data includes the individual action durations as exercise estimates with their **local technical validation** already included. Do not double-count those action checks as extra technical minutes in the baseline schedule; **business-owner acceptance**, exam delivery readiness, manual reconciliation and return to site are separately governed and **not timed** in the brief.

## 5. Stakeholder communication and escalation matrix

| Audience | What they need / trigger | Channel and cadence (proposed) | Drafter / approval |
|---|---|---|---|
| **120 examination candidates and wider learner body** | Safety, location/format, **11:00** assessment confirmation, accessibility support, changes and next update | Approved M365 email and authorised institute channel; initial notice promptly, exam-specific confirmed decision before 11:00, update on changes | COM drafts; **IC approves**, ACAD verifies exam details |
| **90 staff / tutors / invigilators** | Do-not-enter safety order, remote work, required roles and payroll processing status | M365 email, verified voice/SMS backup; at activation, shift change and material decisions | COM and HR draft; IC approves broad notice |
| **Executive Sponsor and service owners** | Risk, RTO/RPO, device gap, payment/admission/payroll deadlines, expenditure and exception decisions | Situation report hourly until exam decision, then every four hours Day 0 and twice daily thereafter | BC compiles; owners verify; IC decides |
| **Alternate-site, backup, utility and internet suppliers** | Capacity, availability, geographic independence, independent backup access, recovery assistance | Approved business contacts; on activation and change/failure, retain case references | FAC/DR/Procurement; IC authorises material commitments |
| **Payment provider and bank** | Transaction exports, disputed payments, fee-confirmation cutoff and controlled payroll instructions | Secure verified provider/bank channels; before **16:00 Day 0** and **12:00 Day 1**, then on mismatches | FIN/HR; respective owner approves submissions |
| **Relevant authorities / emergency responders / regulator (if applicable)** | Safety event, statutory notifications or confirmed privacy/security impact | Through verified official channels when legal thresholds are assessed; do not presume mandatory breach notice solely from a flood | FAC / IR / Legal advise; **IC authorises** |
| **Media and community** | Consistent approved operational status without sensitive details or speculative cause | Only designated spokesperson, on approved major update | COM drafts; IC approves |

### Initial learner notice — 176 words, proposed / NOT issued

> Dear Northbridge learners,
>
> Following flooding and a power failure at our main site at 08:00 WAT today, the campus is temporarily inaccessible. Please do not travel to or enter the affected premises until an official clearance notice is issued.
>
> Teaching and assessment arrangements are being reviewed. Learners scheduled for the 11:00 examination should check their official Microsoft 365 email and approved institute announcement channel for an individual confirmation of the examination arrangements. Do not assume that the examination has moved online or that your scheduled time has changed until you receive an approved instruction.
>
> We are assessing accessible alternative facilities and arrangements for learners who require institution-provided workstations. No learner should be disadvantaged by the current equipment shortfall. Please do not submit examination answers, identity documents or payment details through unofficial links.
>
> Fee payments made through our existing provider remain available; receipt updates may be delayed while records are reconciled. Our learner-support team will provide updates and assistance through established contact channels.
>
> Thank you for your patience and cooperation.
>
> Northbridge Skills Institute — Authorised Communications Office

**Release conditions:** The approved message must include the current verified exam decision and genuine contact channels before distribution; it must not be represented as a real notice already delivered. Because the initial scenario **does not** guarantee 11:00 service readiness, the notice deliberately avoids promising the exam will proceed.

### Incident response (IR) integration

Flooding/power loss requires **BC/DR** first, not automatic declaration of ransomware or a cyberattack. Activate **IR investigation** on credible indicators such as unexpected backup-admin sign-in, failed checks consistent with tampering, unexplained privileges, deletion of backups or suspected data disclosure. Preserve logs with chain of custody, avoid restoring from suspect points, coordinate containment with DR and protect the confidentiality of learner, payroll and finance data. IC maintains unified priorities; IR Lead controls security investigation and advises whether restored systems are safe to release.

## 6. Return to the primary site and closure

**No automatic return at 72 hours.** Facilities' original 72-hour estimate is **not** proof that the buildings are safe, and the Task 5 tabletop will separately consider a five-day extension.

1. **Safety gate:** Qualified Facilities and utility personnel confirm flood-water clearance, electrical isolation/testing, structural/environmental safety, accessibility, power stability and occupancy readiness, recorded with dates and approvals. No entry until clearance.
2. **Technical gate:** DR Lead verifies restored on-site network, identity, servers, patch/security posture, application/data integrity, monitored connectivity and tested fallback; IR Lead confirms no outstanding security condition prevents reuse.
3. **Data-transfer gate:** Business owners freeze and inventory alternate-site/interim changes; compare authoritative source IDs/timestamps, reconcile finance and payroll independently, merge admissions without duplicate entries, validate assessment evidence and records permissions. Maintain a rollback copy and exceptions ledger.
4. **User acceptance gate:** Each F1–F5 owner tests a representative service and confirms accessible operation, records completeness and acceptable outstanding exceptions. Document signed acceptance, **not** just a successful server boot.
5. **Authorised cutback:** IC approves scheduled cutback with communicated downtime and rollback threshold; DR gradually redirects users and monitors correctness; COM notifies stakeholders only on verified completion.
6. **Closure:** BC captures target-versus-actual outcomes, unresolved risks, evidence and corrective-action owners; IC signs off end of alternate operations. A post-incident review updates the plan, training and supplier arrangements.

## 7. Task 4 marking-rubric check (20 marks)

| Required rubric group | Where addressed | Evidence status |
|---|---|---|
| **Activation, roles, RACI (5)** | Sections 1–2: authority and deputy, activation triggers, escalation, alternate communication, reporting cadence and 11-row single-accountability RACI | Proposed and documented |
| **Temporary services (7)** | Section 3: controlled F1–F5 workflows, **25 versus 40 device gap**, staffing, accessibility, privacy, integrity, dual approvals and reconciliation | Resource gaps explicitly unverified |
| **Recovery sequence, validation, communication, return (8)** | Sections 4–6: dependency-based runbook, technical/business acceptance, backup selection, rollback, communication matrix, 176-word learner notice and safe controlled cutback | Documented; no live implementation claimed |

**Assessment position:** This is a coordinated proposed BC/DR plan for a **fictional** scenario. Actual contracts, available staff, third-party technical assurances and approved operational contacts remain to be established. The next assignment stage (Task 5) will calculate the feasible two-technician schedule and report a **modelled baseline** and separate **simulated tabletop**, not observed recovery performance.

## References

- ICDFA (n.d.). *GRC205 Business Continuity and Disaster Recovery Assignment*, Week 21, especially pp. 1–4 and Task 4 requirements on p. 6.
- ICDFA (n.d.). *Business Continuity and Disaster Recovery*, Week 21 teaching slides **3, 10, 12 and 14** (BC versus DR, operational plan elements, governance/RACI and coordinated incident response).
- NIST (2010). *Contingency Planning Guide for Federal Information Systems*, SP 800-34 Rev. 1. https://doi.org/10.6028/NIST.SP.800-34r1.

[Task 3 — Strategy and Budget](../03-strategy-and-budget/) · [Repository overview](../README.md)
