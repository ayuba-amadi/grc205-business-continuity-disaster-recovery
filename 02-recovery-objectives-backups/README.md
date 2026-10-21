# Task 2 — Recovery Objectives and Backup Design

**GRC205 | Northbridge Skills Institute | Task 2 of 6**  
**Status:** Complete draft for review — targets and controls are **proposals**, not demonstrated recovery capability.

## 1. Basis and recovery terminology

The fictional disruption begins **08:00 WAT, Day 0 (Monday)**. Flooding and a power outage make the primary site and local services inaccessible for an **initial estimated 72 hours**. Northbridge has **two DR technicians**, limited alternate-premises capacity and separate local identity **AUTH01**. Microsoft 365 identity/email remain accessible via mobile internet, but **do not replace AUTH01** for local applications. No cyberattack has been confirmed.

- **Recovery Time Objective (RTO):** Maximum target elapsed time **from 08:00** to restoration of a defined *minimum acceptable business service*, including essential functional/security checks and business-owner acceptance. A temporary procedure may satisfy a **business continuity** objective without the corresponding application being restored; distinguish those two results.
- **Recovery Point Objective (RPO):** Maximum tolerable **age of recoverable data**, measured backward from **08:00**. An RPO is not an assertion that all transactions after that point can be recovered.
- **Maximum Tolerable Downtime (MTD):** Longest business interruption that the service owner is prepared to tolerate before harm is unacceptable. MTD exceeds RTO to provide a response/validation/escalation buffer.

All numerical targets below are **proposed exercise decisions** subject to Academic Director, Finance, Registrar, HR and Records owner agreement. The supplied brief does not prescribe individual function RTO/RPO/MTD values. The targets reflect time-critical milestones and integrity concerns in the [Task 1 BIA](../01-business-impact-analysis/).

## 2. Proposed objectives and recovery declaration gates

| Function | Business RTO from 08:00 | RPO | MTD from 08:00 | Buffer (MTD − RTO) | Minimum service / **declaration gate** |
|---|---:|---:|---:|---:|---|
| **F1 Teaching / assessment** | **2 h (10:00 Day 0)** | **15 min** | **3 h (11:00 Day 0)** | **1 h** | Examinations Lead signs off an **accessible, secure and invigilated** 11:00 assessment modality for all 120 candidates, or approves equitable rescheduling with documented learner notification and integrity controls. **Rescheduling is controlled continuity of administration but does not count as an examination delivered on time** or avert the stipulated one-off cost. |
| **F2 Fees / finance** | **4 h (12:00 Day 0)** | **30 min** | **8 h (16:00 Day 0)** | **4 h** | Finance Manager accepts provider-verified provisional acknowledgements, restricted unique-ID transaction register and independent reviewer controls. Final FIN01/DB01 reconciliation remains pending and cannot be claimed complete. |
| **F3 Admissions / registration** | **6 h (14:00 Day 0)** | **1 h** | **10 h (18:00 Day 0)** | **4 h** | Registrar accepts a secure time-stamped intake route, published closing-time rules, unique case IDs and documented later validation/import procedure. |
| **F4 Staff payroll** | **20 h (04:00 Day 1)** | **4 h** | **28 h (12:00 Day 1)** | **8 h** | HR and Finance jointly approve payroll instructions against verified historical records and an authorised changes list; dual review, payment reference checks and bank confirmation are mandatory. |
| **F5 Records / certificates** | **24 h (08:00 Day 1)** | **24 h** | **48 h (08:00 Day 2)** | **24 h** | Records Manager accepts a restricted request queue, authenticated status responses and controlled retrieval/issuance only where authoritative records are verifiable. |

**Planning caveats and gates**

1. The **F1 10:00 RTO is an urgent planning objective for an authorised minimum assessment arrangement**, not a guarantee that all candidates can start at 11:00. The 25 available workstations leave a **15-device simultaneous shortfall** for 40 centre-dependent candidates. A workable exam plan requires confirmed additional devices, properly validated and fair scheduling, or an approved reschedule. *If the RTO gate cannot be certified, record the objective as missed and invoke escalation*. At 11:00, a rescheduled exam still incurs the brief's **NGN 120,000** one-off cost.
2. The F2/F3/F4/F5 **business continuity gates** may be met through controlled offline/alternative processes before production applications return. Their RPOs apply to recoverable authoritative **system data**, not an assumed completeness of interim registers.
3. The current warm-site **technical** times in Task 5 must be compared separately. In particular, the dependency chain to LMS01 alone is **225 minutes**, implying earliest **11:45 Day 0**, so its restoration cannot satisfy the 10:00 minimum-service RTO or 11:00 examination. A future warm-site package's marketed **3–5 hour** estimate does not supersede the current drill data.

## 3. Backup checkpoint age and RPO comparison

Age is calculated from the latest *recoverable* available checkpoint at **08:00 Day 0**, not the backup's upload time or the time of reporting.

| Backup | Checkpoint | Computation at 08:00 Day 0 | Potential loss window | Notes |
|---|---|---|---:|---|
| **B01 — DB01 full** | 23:00 Day −1 | 1 h to midnight + 8 h | **9 h** | Baseline full; alone is 9 hours stale. |
| **B02 — DB01 incremental chain** | **07:00 Day 0** | 08:00 − 07:00 | **1 h** | Latest **recoverable DB01** point **only if B01 plus every required incremental through 07:00 verifies**. |
| **B03 — AUTH01 snapshot** | **00:00 Day 0** | 08:00 − 00:00 | **8 h** | Local account/group/configuration changes since midnight may be absent. |
| **B04 — FS01 full** | **23:00 Day −1** | 1 h to midnight + 8 h | **9 h** | Certificates, files and permissions changed after checkpoint may be absent. |
| **Disconnected fallback full** | 17:00 Day −3 | 7 h to midnight Day −3 + 24 h Day −2 + 24 h Day −1 + 8 h Day 0 | **63 h** | Fallback only; **not** a verified substitute for current checkpoints or ordinary RPO compliance. |

**DB01 dependency chain:** B01 full **23:00 Day −1** → **every chronologically required B02 incremental** after B01, applied in order and verified, **through 07:00 Day 0**. The brief does not enumerate individual incremental filenames, chain count, or hashes. We **cannot** invent their values or assert their integrity outside the **modelled baseline**.

### Function-level gaps

| Function | Authoritative data dependency | Proposed RPO | Available latest point / age | Gap against target | Implication |
|---|---|---:|---|---|---|
| **F1** | DB01 (LMS records), AUTH01 (identity) | **15 min** | DB01 **1 h**; AUTH01 **8 h** | DB **45 min** beyond target; AUTH **7 h 45 min** beyond target | Marks, submissions and identity changes cannot be presumed recovered. Independently verify exam records/identity before release. |
| **F2** | DB01 (FIN records), AUTH01 | **30 min** | DB01 **1 h**; AUTH01 **8 h** | DB **30 min**; AUTH **7 h 30 min** | Payment provider may evidence completed payments absent from FIN01; reconciliation is required before posting. |
| **F3** | DB01 (REG records), AUTH01 | **1 h** | DB01 **1 h**; AUTH01 **8 h** | DB **0** (boundary); AUTH **7 h** | DB01 checkpoint meets **age** target in baseline, but later admissions changes and identity updates need reconciliation. |
| **F4** | DB01 (HR records), AUTH01 | **4 h** | DB01 **1 h**; AUTH01 **8 h** | DB **0**; AUTH **4 h** | Bank file must be checked against separately verified salary instructions and authorised changes. |
| **F5** | FS01 + AUTH01 | **24 h** | FS01 **9 h**; AUTH01 **8 h** | **0** for both checkpoint ages | Age targets pass conditionally; file authenticity, permissions and request records still require post-restore validation. |

**Assumption about shared AUTH01 RPO:** Although AUTH01 contains configuration rather than the transactional DB01 records, identity changes are necessary for secure usable service. This conservative matrix compares **both** dependent data stores with each service's RPO; a separate approved identity-configuration RPO could be adopted after evidence-based BIA review. Application data and identity data **must not** be conflated.

**Interpretation:** The baseline gives **F1 and F2 DB01 RPO failures**, F3 at its DB boundary and F4 inside its DB target. AUTH01 misses the conservative shared objective for F1–F4, while F5's FS01 and AUTH01 backup ages fit its proposed 24-hour window. This is a calculation of **checkpoint age only**. It does not prove the backups are readable, consistent, secure, or capable of delivering a working application.

### What can be reconciled, and what cannot

Finance can compare **payment-provider transaction IDs, settlement records and bank evidence** with the restored DB01 tables and numbered interim ledger; Admissions can inspect independently time-stamped application receipts; HR can compare approved historical pay records, bank acknowledgements and authorised amendment logs. These sources may establish individual events after a backup checkpoint. However, **they do not guarantee complete reconstruction** of missing assessment answers, learner activity, unpublished admissions edits, unsupported payroll amendments, FS01 file versions, AUTH01 identity changes or missing provider-side metadata. Any unsupported or disputed event becomes a documented exception for its business owner; no fabricated record is inserted.

## 4. Proposed backup architecture and schedule

The current offsite catalogue is an **input**, not proof of operational readiness. The design below is a proposed future control set addressing F1/F2 short RPOs, AUTH01 staleness and the risks of shared administrator identity.

| Asset | Backup technique / proposed frequency (WAT) | Planned recovery currency | Proposed retention and location |
|---|---|---|---|
| **DB01** | **Application-consistent weekly full** (Sunday 23:00) + **daily differential** (23:00) + **transaction-log/incremental capture every 15 min**, continuous through operating hours | **≤15 minutes**, if the chain, log sequence and timestamp coverage validate | Encrypted local backup repository for fast restores (7 days), independent provider offsite copies (daily, 35 days), offline/immutable monthly checkpoint (12 months). *Sizing, log compatibility and supplier support unverified.* |
| **AUTH01** | **Configuration/system-state snapshot every 15 min** for high-change periods, daily protected full state, and a separate immediate configuration backup after approved identity changes | **≤15 minutes** proposed, where supported; directory replication **alone is not a backup** | Encrypted independently administered copies offsite (35 days), monthly offline image (12 months), with directory-secret protection and tested restore isolation. |
| **FS01** | Weekly full (Sunday 23:00) plus daily incremental and **daily file-version snapshot**; optional critical change-triggered version capture | **≤24 hours**, with additional revisions protected subject to capacity | Local fast-restore versions (7 days), encrypted offsite daily (35 days), monthly immutable/offline (12 months). |
| **FIN01, REG01, HR01, LMS01** | Daily encrypted application/configuration export plus capture on approved configuration change, **coordinated with DB01** | Application and schema consistency must be validated against DB01 checkpoint | Same segregated local/offsite/offline policy; recover secrets through independently protected vault procedure, not a copied plaintext secret. |

**Schedule/retention figures are proposed targets, not costs, signed supplier SLAs, or confirmed retention requirements.** Institutional records and sensitive learner/staff information may require longer legally determined retention; the Records Manager and privacy lead must approve retention, deletion and the backup exception process before implementation. An **independent protected backup provision of NGN 400,000 annually** is part of the Task 3 price comparison; feasibility of these granular frequencies and the proposed retention must be confirmed against supplier quotations and capacity.

### 3-2-1 plus independence

1. Maintain **at least three copies**: primary live data, operational backup copy and independent protected recovery copy.
2. Use **at least two storage/media domains**, e.g. restricted local disk repository and segregated encrypted offsite object/tape media (the choice must be independently checked; two folders in one cloud account do not provide sufficient fault isolation).
3. Keep **at least one geographically separated offsite copy**, beyond the flood/power-failure exposure of the main campus.
4. Strengthen the conventional 3-2-1 minimum with **one offline or immutable, separately administered copy**, as protection against credential compromise, accidental deletion and propagation of corrupt data. Replicas may improve uptime but **replicate corruption or unauthorised changes** and do not replace known-good point-in-time copies.

### Access restrictions and security controls

- **Eliminate the shared production/network-backup administrator identity.** Create separate role-scoped service principals, distinct backup administrators and emergency access with dual approval, MFA (where supported), independently held credential recovery and audited privileged actions.
- Offsite provider must demonstrate **independent administrative control**, write-once/immutable retention or disconnected copies, supplier audit evidence, export mechanisms and recovery when the main campus and production identity are unavailable. At present these assurances are **undocumented**, hence a material residual risk.
- Encrypt backups **in transit and at rest** using protected keys stored separately from the data, rotate credentials, log access, monitor failed backup jobs/altered retention policies, and segregate sensitive payroll, learner and identity records.
- Treat unexplained privileged logins or failed integrity checks as **security signals**: pause use of suspect media, preserve access and backup logs and coordinate incident response investigation. **Flooding does not by itself prove cyber compromise.**

## 5. Restore method, verification and contingencies

| Phase | Proposed method and validation evidence | Response if unsuccessful |
|---|---|---|
| **1 — Approve recovery** | Incident/BC Lead confirms site safety, recovery scope, target point and authorised recovery location. DR Lead records selected backup identifiers, WAT times and owners. | Pause unsafe access; activate the documented alternate-site route. |
| **2 — Prove access independence** | Authenticate to offsite catalog **without production identity**, verify backup-administrator roles, audit trail, immutability status and available encryption keys. | Escalate missing independent access; invoke segregated emergency recovery controls, not shared administrator credentials. |
| **3 — Select known-good copies** | Verify complete catalog, signed inventory/manifests, consistency metadata, intact incremental chain and hashes. Check for unusual deletion or admin activity before accepting 07:00 B02. | Quarantine failing incremental; select the latest **verified** earlier point, recalculate actual RPO exposure, notify owners and evaluate the 63-hour fallback only with explicit risk acceptance. |
| **4 — Restore dependencies** | Provision network and isolated identity, validate AUTH01 authentication/policy, complete security/backup checks, then restore B01 DB01 full and apply each required incremental in order through verified checkpoint; recover FS01 through its distinct branch. | Stop chain if any link fails, preserve error logs, roll back the isolated restore and repeat from a known-good chain. |
| **5 — Test data and applications** | Verify database integrity, schema/row consistency, transaction markers, representative LMS submissions, payment IDs, admissions timestamps, payroll controls, records permissions and authentication; restrict access until approved. | Flag missing/altered data, reconcile only against independent evidence, contain suspect service and re-restore if material correctness fails. |
| **6 — Business acceptance** | Each service owner signs acceptance of its **minimum service**, accessible operations, security, exception list, and reconciliation status. Record observed recovery point and elapsed time **separately** from declared RTO/RPO targets. | Continue manual procedures; record objective breach, communicate impacts and request management decision. |
| **7 — Resume and monitor** | Introduce production traffic in controlled stages, monitor errors/security events and retain rollback snapshot and change logs. | Suspend cutover, revert to last accepted state and resume continuity workflow; escalate to IR on credible compromise indicators. |

### Test cadence and evidence

- **Every day:** Review scheduled job success, checkpoint freshness, automated consistency/hash alerts, retention status and backup-administrator activity; a successful job status is **not** proof of a successful restore.
- **Monthly:** Isolated sample **DB01 point-in-time restore** including a randomly selected incremental chain; verify a representative application transaction and record actual RPO, total restore duration and any missing log segment.
- **Quarterly:** Restore **AUTH01 and FS01** in an isolated environment; validate sign-in policy, group membership, file permissions, version fidelity and access independence. Include a protected-copy retrieval test.
- **Semi-annually:** Rehearse integrated network → AUTH01 → DB01 → application recovery with both technicians and business owner sign-off; demonstrate failure and fallback handling.
- **Annually and after significant changes:** Perform broader exercise, test geographically separated recovery and review supplier evidence, RTO/RPO results, retention and changes to regulatory obligations.

No validation results are claimed here: the supplied Task 5 **baseline drill assumes B01–B04 integrity checks pass**, whereas the later tabletop's minute-30 inject specifically challenges a DB01 incremental and prompts investigation of a backup-administrator login. Keep these **separate evidence states**.

## 6. Task 2 rubric traceability (15 marks)

| Criterion | Evidence | Status |
|---|---|---|
| Numerical RTO/RPO/MTD and justified buffers **(5)** | Five-row objective matrix, business deadlines, explicit minimum-service gates and **MTD − RTO** buffers | Documented as proposed targets |
| Checkpoint arithmetic and RPO gaps **(6)** | B01=9 h, B02=1 h, B03=8 h, B04=9 h, disconnected backup=63 h; function-specific gaps and reconciliation limits | Calculated; baseline chain integrity conditional |
| Usable backup design and verification **(4)** | Full/differential/incremental schedule; 3-2-1 plus immutable/offline; segregation, encryption, access, restore sequence and measured tests | Proposed pending budget/supplier feasibility |

**Approval limitations:** The business service owners, DR Lead, privacy lead and management have not actually approved these targets or purchased capabilities. Task 3 must assess cost/strategy trade-offs, Task 4 will operationalise the recovery plan and Task 5 must report baseline modelled outcomes and stress-tabletop decisions without suggesting they occurred in production.

## References

- ICDFA (n.d.). *GRC205 Business Continuity and Disaster Recovery Assignment*, Week 21, pp. 1–5: scenario, checkpoints, backup weaknesses and Task 2 marking requirements (provided brief).
- ICDFA (n.d.). *Business Continuity and Disaster Recovery*, GRC205 Week 21 teaching slides **5–8, 10–11 and 14**: BIA, recovery objectives, backup strategy, 3-2-1 and testing (provided course deck).
- NIST (2010). *Contingency Planning Guide for Federal Information Systems*, SP 800-34 Rev. 1. https://doi.org/10.6028/NIST.SP.800-34r1 (official guide; formal mapping appears in Task 6).

[Task 1 — Business Impact Analysis](../01-business-impact-analysis/) · [Repository overview](../README.md)
