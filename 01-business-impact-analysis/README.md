# Task 1 — Business Impact Analysis

**GRC205 | Northbridge Skills Institute | Stage 1 of 2**  
**Status:** Stage 1 documented; awaiting review. Stage 2 will complete business prioritisation, dependency risks and the visual dependency map.

## 1. Scope, evidence and assumptions

At **08:00 WAT on Day 0 (Monday)**, flooding and a power failure render Northbridge's main site and local systems unavailable. Facilities estimates **72 hours** of site inaccessibility. The institute has **1,800 learners and 90 staff**. Microsoft 365 identity and email remain accessible through mobile internet, but locally hosted systems use a distinct directory, **AUTH01**. No cyberattack has been confirmed.

An alternative facility opens at **10:00 WAT** with **25 workstations**. At **11:00 WAT**, **120 learners** are due to sit an examination: **80** can use their own devices, while **40** require centre workstations. Thus, simultaneous on-site workstation demand exceeds the supplied capacity by **15**. The institute has **two recovery technicians**; business coordinators can arrange alternative services and learner support.

**Evidence basis:** ICDFA, *GRC205 BC/DR Assignment*, pp. 1–4 (scenario, function rates and constraints), and ICDFA, *Business Continuity and Disaster Recovery*, Week 21, slides 3 and 5 (BC versus DR and BIA methodology). The service arrangements, role assignments and controls proposed below are **planning assumptions**, not verified existing capabilities.

**Interpretation:** The hourly amounts are independent, non-overlapping incremental loss estimates. All functions remain disrupted in the requested 8-hour and 24-hour **no-recovery/no-continuity** calculations. Rates apply for the first 24 hours only; the examination's NGN 120,000 rescheduling charge is added once because an acceptable assessment service is unavailable at 11:00. Do not extrapolate these hourly rates beyond 24 hours.

## 2. Five-function BIA

The owners are **proposed accountable business roles**; actual appointments and delegations require management approval. “Users” describes the people or groups primarily affected, **not invented counts of active users**.

| Function / proposed owner | Users and time-sensitive impact | Critical resources, dependencies and information | Minimum acceptable continuity service and controls |
|---|---|---|---|
| **F1 — Teaching and assessment**; Academic Director / Examinations Lead | Scheduled examination: **120 learners at 11:00**; wider teaching services affect the learner body and tutors. **NGN 60,000/hour** plus **NGN 120,000 once** if the exam cannot proceed acceptably by 11:00. Welfare, reasonable adjustments, access equality and assessment validity are major non-financial impacts. | **LMS01 + DB01**, recovery network, **AUTH01**, tutors/invigilators, accessible premises, device capacity, connectivity, verified candidate roster, exam rules and protected question/answer materials. | Authorised examination continuity arrangement with verified identity, accessible delivery, controlled invigilation, time-stamped attendance and secure evidence capture. Examinations Lead must approve any changed modality, staggered session or rescheduling; maintain version-controlled candidate lists and a signed reconciliation/incident log. **25 devices cannot accommodate 40 concurrent centre-dependent candidates**; do not claim that merely using the alternate facility satisfies the deadline. |
| **F2 — Fees and finance**; Finance Manager | Payments still reach the external provider, but local receipt and wallet updates fail. **NGN 40,000/hour**; fee-confirmation deadline **16:00 Day 0**. Missed confirmation may disrupt learner access and financial assurance. | **FIN01 + DB01**, network, AUTH01, Finance staff, provider portal and statements, transaction IDs, controlled reconciliation ledger, dual-review access. | Provider-confirmed transactions logged in a restricted, numbered temporary register; clearly issue *provisional* acknowledgements rather than claiming a FIN01 receipt. Finance Manager approves exception handling; a second reviewer checks amounts and references. Reconcile every entry with provider evidence and restored DB01 before posting final receipts or balances. |
| **F3 — Admissions and registration**; Registrar / Admissions Lead | New applications and enrolment changes cannot be recorded locally; **NGN 20,000/hour**. Admissions close **18:00 Day 0**. Applicants may lose fair access if timestamps are not preserved. | **REG01 + DB01**, network, AUTH01, trained admissions staff, approved intake forms, submission timestamps, privacy notices and eligibility rules. | Restricted, timestamped temporary intake with unique reference numbers, applicant consent/notice, authorised access and a documented cutoff rule. Registrar approves exceptions; on restoration, double-check identity, duplicates, eligibility and order of submission before importing or accepting entries. |
| **F4 — Staff payroll**; HR/Payroll Manager | All **90 staff** are potentially affected; **NGN 10,000/hour**. Bank submission is due **12:00 Day 1**; inaccurate or duplicated instructions could cause material harm. | **HR01 + DB01**, network, AUTH01, payroll officers, verified change register, bank instructions, payment approval mandates and restricted salary records. | Prepare a controlled draft from the **last verified payroll** and documented authorised changes. HR Manager and Finance Manager provide separate approval before bank submission; prohibit unverified amendments and duplicate uploads. Retain authorisation, bank acknowledgement and a subsequent reconciliation trail. |
| **F5 — Records and certificates**; Records Manager | Requests from learners, alumni and staff risk delay; **NGN 5,000/hour**. Internal service commitment is **48 hours**. Document integrity, confidentiality and authenticity matter. | **FS01**, recovery network, AUTH01, records staff, approved retention rules, certificate templates, source registers, controlled access and chain of custody. | Provide verified status enquiries and log urgent requests in a restricted, uniquely numbered queue. Release a certificate or amended record **only where its source can be independently authenticated** and the Records Manager authorises release. Otherwise issue a transparent delay notice and reconcile queued requests after restoration. |

### Cross-cutting people, premises and supplier requirements

| Resource class | Minimum arrangements and unresolved assumptions |
|---|---|
| **People** | Business service owners, continuity coordinator, examination invigilators, learner-support/accessibility staff, Finance and HR dual approvers, registrar and records custodians; two technicians remain dedicated to the technical recovery schedule. **Staff availability and precise shift coverage are unverified.** |
| **Premises and equipment** | Secure alternate teaching/assessment space from 10:00; 25 supplied workstations, power, internet, accessibility measures, privacy for payroll and records, physical security, supervised devices and secure storage. Capacity shortfall: **40 − 25 = 15 workstations** for a simultaneous centre-based sitting. |
| **Suppliers** | Alternate-facility provider, external payment processor, offsite backup provider, network/mobile connectivity suppliers and bank. Confirm service-level commitments, business contacts, emergency access and evidence exports; these are **not established by the brief**. |
| **Information and controls** | Authoritative identity/candidate/payroll records, backup catalogue, assessment approvals, audit trails, receipt references, timestamped interim transaction logs, encryption, least-privilege access, dual review where financially material, retention and reconciliation on restoration. M365 mobile email supports coordination **but does not restore locally dependent applications**. |

## 3. Worked disruption impact calculations

**Model:** For function \(i\), cost \(C_i(t)=r_i\times t\) for \(t=8\) or \(24\) hours with no mitigation. For F1, add the examination rescheduling charge \(E=\text{NGN }120{,}000\) once when the **11:00** trigger is met. The 8-hour window runs **08:00–16:00 Day 0**; the 24-hour window runs **08:00 Day 0–08:00 Day 1**.

| Function | Hourly rate (NGN) | 8-hour working | 8-hour impact (NGN) | 24-hour working | 24-hour impact (NGN) |
|---|---:|---|---:|---|---:|
| **F1 Teaching/assessment** | 60,000 | 60,000 × 8 + 120,000 | **600,000** | 60,000 × 24 + 120,000 | **1,560,000** |
| **F2 Fees/finance** | 40,000 | 40,000 × 8 | 320,000 | 40,000 × 24 | 960,000 |
| **F3 Admissions/registration** | 20,000 | 20,000 × 8 | 160,000 | 20,000 × 24 | 480,000 |
| **F4 Payroll** | 10,000 | 10,000 × 8 | 80,000 | 10,000 × 24 | 240,000 |
| **F5 Records/certificates** | 5,000 | 5,000 × 8 | 40,000 | 5,000 × 24 | 120,000 |
| **Combined** | **135,000** | **(135,000 × 8) + 120,000** | **1,200,000** | **(135,000 × 24) + 120,000** | **3,360,000** |

**Checks:** Sum of base hourly rates = \(60{,}000+40{,}000+20{,}000+10{,}000+5{,}000=\text{NGN }135{,}000\). Eight-hour baseline = NGN **1,080,000**, plus NGN **120,000** once = NGN **1,200,000**. Twenty-four-hour baseline = NGN **3,240,000**, plus NGN **120,000** once = NGN **3,360,000**. The extra examination cost **must not** be added a second time at 24 hours.

### Interpretation and limitations

1. **Simplified financial model:** Rates are stipulated teaching-case estimates and deliberately independent; they do not reflect real transaction volumes, changing demand, effective workarounds, insurance recoveries, avoided expenses or any escalation after 24 hours. Neither sum is an observed loss or a forecast of a 72-hour or five-day outage.
2. **Incomplete total impact:** The model excludes learner welfare and accessibility, potential unfair treatment at the 11:00 examination, loss of academic confidence, institutional reputation, confidentiality and integrity consequences, regulatory exposures and the risk of incorrect payroll or duplicate finance entries. These effects cannot responsibly be inferred from the supplied hourly rates.

## 4. Decision points for subsequent prioritisation

- **11:00 Day 0 — Examination:** An acceptable service must be confirmed before the examination; 25 alternate devices from 10:00 leave a 15-device shortfall for 40 centre-dependent candidates. The Academic Director must approve a verified workaround or fair rescheduling, rather than assume a technical restoration or an untested device-sharing arrangement.
- **16:00 Day 0 — Fees:** Finance must establish provider-confirmed temporary recording and two-person reconciliation in time for the confirmation deadline.
- **18:00 Day 0 — Admissions:** Registrar must authorise timestamped intake and a defensible closing-time/exception policy.
- **12:00 Day 1 — Payroll:** Secure, dual-authorised bank instructions must be prepared without duplicating payments.
- **48-hour service commitment — Records:** Maintain an auditable request queue, with no unverified certificate issuance.

**Technical dependency observation:** F1–F4 rely on recovery network → AUTH01 → security/backup checks → DB01 → application; F5 relies on network → AUTH01 → security/backup checks → FS01. **Business urgency does not eliminate prerequisite restoration steps.** The complete ranked priority sequence, risk analysis and dependency diagram will be developed and reviewed in **Stage 2**.

## 5. Stage 1 review gate

**Prepared for review:** Scenario assumptions; five-function BIA with proposed owners, affected users, resources and minimum service controls; people/premises/supplier/information requirements; accurate 8-hour and 24-hour impacts; financial-model limitations and deadline decisions.

**Still to complete before Task 1 is accepted:** Final business priority ranking against deadline and impact, explicit differentiation from the technically feasible restoration order, at least three dependency risk assessments, and a concise dependency visual (Stage 2).

## References

- ICDFA (n.d.). *GRC205 Incident Management and Business Continuity: Business Continuity and Disaster Recovery Assignment*, pp. 1–5, Task 1 and business context (provided assessment brief).
- ICDFA (n.d.). *Business Continuity and Disaster Recovery*, GRC205 Week 21 teaching slides, especially slides 3, 5, 6 and 8 (provided teaching deck).

[Back to repository overview](../README.md)
