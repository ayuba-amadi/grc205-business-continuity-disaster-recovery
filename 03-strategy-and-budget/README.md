# Task 3 — Recovery Strategy and Budget

**GRC205 | Northbridge Skills Institute | Task 3 of 6**  
**Status:** Completed analytical comparison — proposed selection pending management and supplier validation.

## 1. Decision context and assumptions

Northbridge's main site is unavailable from **08:00 WAT on Day 0** following flooding and power loss; Facilities initially estimates **72 hours** before access resumes. The institution serves **1,800 learners and 90 staff**. Its locally dependent services are **F1 LMS01, F2 FIN01, F3 REG01, F4 HR01** (all using DB01), and **F5 FS01**, with recovery network and AUTH01 dependencies. **Two technicians** are available for disaster recovery. An alternate teaching location offers **25 workstations from 10:00**, although **40** examination candidates need a centre workstation at **11:00**. Microsoft 365 email remains available by mobile connectivity; it does not recover the local applications.

The [Task 2 recovery objective matrix](../02-recovery-objectives-backups/) proposes business minimum-service **RTOs** of **2, 4, 6, 20 and 24 hours** for F1–F5 respectively; **RPOs** of **15 minutes, 30 minutes, 1 hour, 4 hours and 24 hours**; and **MTDs** of **3, 8, 10, 28 and 48 hours**. These targets are **proposals**, not measured results. Business continuity arrangements may fulfil a minimum-service RTO without restoring its application. Conversely a server reported “up” does not constitute business acceptance.

**Decision criteria:** cost within the **NGN 3,000,000 annual ceiling**; service and data recovery capability; exam/financial deadlines; two-person technical workforce; site/geographic independence; reliance on suppliers; privacy, integrity and the risk that synchronous copies preserve corruption. The package specifications are **planning estimates only**, with no demonstrated SLA, supplier quotation, contract, test report or probability of an outage.

## 2. Cold, warm and hot site option assessment

The figures below are those supplied in the assignment brief (p. 3). “First critical service” is **not** the point at which all five functions are restored, and none of the quoted timings proves an application-specific RTO.

| Option | First critical service estimate | Estimated data-loss window | Staffing / mobilisation | Geographic and supplier dependencies | Ability to meet proposed objectives |
|---|---|---|---|---|---|
| **Cold site** | **24–48 h** | **Up to 24 h** | Two technicians must install/configure infrastructure and restore data from backup; hardware procurement or setup and transport could add delay. | Verify site is outside same flood/power/telecom risk, accessible to staff, equipped with power/network and supported by suppliers. A low price does not establish readiness. | **Cannot meet** F1 2 h, F2 4 h, F3 6 h or F4 20 h technical recovery on the quoted estimate; could breach F5 24 h. Up-to-24 h loss exceeds F1 15 min, F2 30 min, F3 1 h and F4 4 h RPOs. Only F5 24 h could be met at the estimate's edge, subject to verification. |
| **Warm site** | **3–5 h** | **1–6 h** | Pre-provisioned capacity reduces build time, but **two technicians** must restore/test network, AUTH01, DB01 and applications; coordinate job order and owner sign-off. | Contract for a geographically independent, accessible warm environment; verify bandwidth, provider credentials, power, capacity and the ability to access protected copies during a campus outage. | **Cannot guarantee** F1 2 h technical recovery and may miss F2 4 h depending on which service is first; **1–6 h data-loss range fails** F1 15 min and F2 30 min and may fail F3 1 h/F4 4 h. F5 24 h data RPO appears attainable, pending actual checkpoint tests. Controlled temporary services are necessary. |
| **Hot site** | **About 1 h** | **Up to 15 min** | Preconfigured facilities may reduce technical mobilisation but require **continuous operation, monitoring, secure failover and supplier specialist support** beyond what two local technicians alone can establish. | Ensure independently powered, network-diverse site outside the flood hazard zone; confirm isolation, failover permissions and provider operations coverage. | **Potentially** meets the F1 2 h service RTO and F1 15 min RPO at the stated bounds, if assessment service, users and records can actually be validated; its 15 min advertised data window is within other proposed RPOs. **Does not alone solve the 15-workstation examination shortfall**, and all-service RTOs still require evidence. |

**Corruption/security risk across all options:** A *live replica or hot failover* can immediately propagate corrupted records, accidental deletions or malicious changes. A cold/warm restore can also reintroduce affected data if checkpoints are not verified. **Independent, tested, point-in-time, encrypted and immutable/offline backups** therefore remain required regardless of site choice. Neither offsite location nor replication alone proves recoverability (ICDFA teaching slides 7–8).

### Objectives and supplier claims

The **3–5 h warm estimate** applies to *first service*, not guaranteed LMS01 delivery. The current assignment warm-site baseline (reserved for Task 5) has a dependency chain of **30 + 30 + 30 + 90 + 45 = 225 min**, so the earliest modelled **LMS01 completion is 11:45 WAT** (**3 h 45 min after disruption**) even without any extra business acceptance delay. This **misses the F1 2 h target and the 11:00 exam**. There is no contradiction: “first critical service” and “LMS01 ready” are different metrics.

Furthermore, the actual supplied **DB01 checkpoint is 07:00**, **1 hour before failure**, regardless of the future recovery site's advertised data-loss capability. Installing a hot site cannot retroactively improve the available 08:00 recovery point: the F1 **15 min** and F2 **30 min** DB01 RPOs are breached in the current baseline until backup/replication architecture and data checks are improved.

## 3. Complete annual budget and affordability

Each option covers all five functions and shared infrastructure. The assignment requires the same two annual additions for **each** package:

- Independent protected backups = **NGN 400,000/year**
- Staff training and recovery tests = **NGN 200,000/year**
- **Required additions = NGN 600,000/year**

| Annual cost component (NGN) | Cold | Warm | Hot |
|---|---:|---:|---:|
| Base site package | 600,000 | 1,500,000 | 2,400,000 |
| Protected independent backups | 400,000 | 400,000 | 400,000 |
| Training and tests | 200,000 | 200,000 | 200,000 |
| **Complete annual plan cost** | **1,200,000** | **2,100,000** | **3,000,000** |
| Planning ceiling | 3,000,000 | 3,000,000 | 3,000,000 |
| **Headroom (ceiling − total)** | **1,800,000** | **900,000** | **0** |
| **Within limit?** | **Yes** | **Yes** | **Yes — at ceiling** |

**Worked arithmetic:** Cold **600,000 + 400,000 + 200,000 = NGN 1,200,000**. Warm **1,500,000 + 400,000 + 200,000 = NGN 2,100,000**. Hot **2,400,000 + 400,000 + 200,000 = NGN 3,000,000**. The hot package consumes **100%** of the available budget; warm consumes **70%**, leaving **30%** headroom. Cold consumes **40%**, leaving **60%**.

The provided prices are stipulated teaching-case annual estimates; any equipment for additional exam candidates, connectivity, supplier setup fees, tax, licence changes, specialised labour and operational overheads would need to be **priced and checked** against headroom before procurement. **Do not assume** that an extra NGN 900,000 has been spent or that it guarantees additional coverage.

## 4. Recommended strategy and residual risk

**Recommendation: Choose the WARM site package as the provisional, budget-conscious recovery foundation**, subject to formal management approval and evidence-based supplier acceptance, combined with controlled **business continuity workarounds** and the mandatory **independent protected backups**.

This balances a materially faster recoverable operating platform than a cold site with **NGN 900,000** uncommitted headroom for verified operational gaps. The hot option offers stronger stated technical RTO/RPO performance, but spends the **entire annual ceiling**, still requires independent recovery checks, fails to address the **15 missing exam workstations** and is not established as deliverable with two local technicians and no verified provider contract. A warm site is **not represented as fully compliant** with the aggressive F1/F2 recovery objectives.

The warm site's deficiencies must be stated rather than masked by nominal first-service estimates:

| Residual exposure | Result against proposed objectives | Owner / acceptance and treatment |
|---|---|---|
| **F1 assessment service and 11:00 examination** | **Warm technical restoration cannot meet F1 2 h RTO** on the current drill; the assessed earliest LMS01 time is **11:45**. **25** workstations are insufficient for **40** centre-device users. | **Academic Director / Examinations Lead** must approve a viable examination continuity option, secure accessible verified devices if feasible, or formally reschedule with transparent notification. **Executive Sponsor** accepts resulting residual disruption/cost and fairness risks. |
| **F1/F2 data currency** | Warm advertised loss **1–6 h** breaches **15/30-min** RPOs; current DB01 checkpoint (**1 h**) misses F1 by **45 min**, F2 by **30 min**. | **Information Services Lead/DR Lead** to validate DB01 transaction-log protection, independently recoverable point-in-time copies and representative restored records; **Academic and Finance Owners** accept time-limited exceptions only after impact review. |
| **F3/F4 uncertainty** | Warm data loss can exceed **1 h F3** and **4 h F4** targets; actual achieved point depends on usable backups, not the site label. | Registrar and HR/Finance owners validate reconciled temporary records and payroll bank instructions; BC/DR Coordinator reports any exception to executive governance. |
| **Site and supplier common-cause failure** | Warm provider may share geographic hazard, telecommunications or identity controls with the primary site; no SLA or independent-access evidence supplied. | Facilities Lead and Procurement confirm separation, site inspection, accessibility, contract exits and emergency supplier contacts; **Executive Sponsor** accepts residual supplier risk. |
| **Integrity or credential compromise** | Production and network backup administration currently share an admin identity; offsite provider's access-independence is undocumented. | Security Lead and DR Lead separate identities, confirm immutable/offline copy and test restore access; investigate suspicious admin activity through incident response, without asserting a cyberattack occurred. |
| **Staffing and recovery duration** | Only two technicians are specified; competing restores, security checks and owner acceptance could delay completion. | DR Lead to prove non-overlapping two-technician schedule in Task 5; business coordinators operate authorised interim services separately. Executive Sponsor accepts any unresolved timing exposure. |

**Acceptance gate:** Do **not** authorise a contract or claim that the warm site meets every target without written residual-risk acceptance by the **Executive Sponsor**, endorsed by Academic, Finance, Registrar, HR and Records owners, with evidence and decision dates. If management **will not accept** the F1/F2 shortfall, reconsider a hot-site approach or revise service objectives **only through documented BIA/business-owner approval**; targets must not be quietly relaxed to fit a preferred package.

## 5. Investment comparison: financial exposure is not annual ROI

Task 1's *no-recovery/no-continuity* exercise calculations are:

| Comparative measure | NGN |
|---|---:|
| 8 h theoretical interruption cost | **1,200,000** |
| 24 h theoretical interruption cost | **3,360,000** |
| Proposed warm-site complete **annual cost** | **2,100,000** |
| Difference: 24 h hypothetical loss less annual warm cost | **1,260,000** |
| Difference: annual warm cost less 8 h hypothetical loss | **900,000** |

The **NGN 3,360,000** scenario exceeds the **NGN 2,100,000** annual warm budget, but this **does not prove** a positive annual return on investment: recovery would not necessarily eliminate the entire outage cost; the 11:00 exam charge may still occur; real avoided loss depends on the time and quality of business resumption, actual outage probability, downtime distribution, event severity, testing success and extra operating expenses. Conversely the short 8-hour comparison does not demonstrate the site is uneconomic.

For an investment case, collect or estimate:

- A defensible **annual likelihood and frequency** of flood, power, facility, supplier and technology outages, plus plausible durations (supported by incident histories and hazard analysis).
- Verified **actual loss drivers** and whether temporary services reduce each function's losses, including peak assessment and admissions periods.
- **Measured**, function-specific restore/acceptance times and recoverable DB01/AUTH01/FS01 points for each site option; failures, rollback needs and dependencies.
- Supplier contracts/SLAs, tested alternate geographic/power/connectivity independence, resilience of privileged backup access and realistic staffed support.
- Total lifecycle expenditure including facility readiness, 15-device gap treatment, network, licensing, training, supplier support and any additional secure backup frequency/retention.

Only after these inputs are obtained should management estimate **expected annual loss reduction net of full strategy costs** or calculate financial ROI; the exercise does **not** provide enough evidence for a numerical annual ROI.

## 6. Decision record and rubric traceability

| Assessment requirement (15 marks) | Evidence in this README |
|---|---|
| **Option comparison (4)** | Cold/warm/hot site recovery and data windows; RTO/RPO weaknesses; technicians, geography, supplier and corruption exposure |
| **Budget arithmetic (5)** | Each base price plus **NGN 400,000** and **NGN 200,000**; full totals, remaining budget and affordability |
| **Defensible choice, residual risks and investment reasoning (6)** | Qualified warm recommendation; owners and executive risk acceptance; F1/F2 breaches; comparison to 8 h/24 h loss; why annual ROI cannot be established; required approval evidence |

**Next task linkage:** Task 4 operationalises alternate minimum services and formal decision authority; Task 5 separately models the supplied warm-site technician schedule. Any findings affecting affordability or objectives trigger an approved revision of the recommendation, not retrospective alteration of the source data.

## References

- ICDFA (n.d.). *GRC205 Business Continuity and Disaster Recovery Assignment*, Week 21, pp. 1–5 (scenario, annual limit, package timings/costs and Task 3 rubric).
- ICDFA (n.d.). *Business Continuity and Disaster Recovery*, GRC205 Week 21 slides **5–8, 10–11 and 13** (business-based recovery priorities, alternate sites, 3-2-1 backups, exercise validation and measurement).
- NIST (2010). *Contingency Planning Guide for Federal Information Systems*, NIST SP 800-34 Rev. 1. https://doi.org/10.6028/NIST.SP.800-34r1 (planning-strategy and validation guidance).

[Task 2 — Recovery Objectives](../02-recovery-objectives-backups/) · [Repository overview](../README.md)
