# Cross-Proposal Synthesis: J&G Aviation Automation Engagement
## Veteran Vectors LLC → J&G Aviation | All Four Proposals Reviewed

**Date:** 2026-02-23
**Proposals Reviewed:**
- **P1** — Work Order Automation ($2,000 + $100/mo)
- **P2** — Discrepancy Analytics Engine ($2,500 + $200/mo)
- **P3** — Smart Estimates ($2,000 + $100/mo)
- **P4** — Combined Bundle ($5,000 + $300/mo)

**Overall Risk Profiles:**
- P1: NEEDS ATTENTION
- P2: LOW-MEDIUM
- P3: NEEDS ATTENTION
- P4: HEALTHY — Needs Attention in Targeted Areas

---

## 1. Unified Risk Heatmap

| # | Lens | P1 | P2 | P3 | P4 | Cross-Proposal Pattern |
|---|------|----|----|----|----|------------------------|
| 1 | Legal | **HIGH** | MEDIUM | MEDIUM | MEDIUM | Systemic gap — no proposal addresses FAA Part 145/Part 43, ITAR/CUI, or liability |
| 2 | Ethical | LOW | LOW-MEDIUM | LOW | MEDIUM | P2/P4 mechanic performance tracking is the concern; others are clean |
| 3 | Logistical | MEDIUM | LOW-MEDIUM | MEDIUM | MEDIUM | Feasible but underspecified testing/validation across the board |
| 4 | Current State | LOW | LOW | LOW | LOW | All proposals show strong domain knowledge; consistent strength |
| 5 | Future Strategy | LOW | LOW | LOW | LOW | Well-aligned strategically; phased model is sound |
| 6 | Cost Effectiveness | MEDIUM | LOW | LOW | LOW | P1 Year-1 ROI thinner than presented; bundle (P4) is the rational choice |
| 7 | Time Effectiveness | LOW | LOW | LOW | LOW | Time savings well-quantified everywhere; consistent strength |
| 8 | Security | **HIGH** | MEDIUM-HIGH | MEDIUM | MEDIUM | P1 worst (6 APIs, no controls); all proposals omit security architecture |
| 9 | Guardrails & Governance | **CRITICAL** | MEDIUM-HIGH | **HIGH** | **HIGH** | Systemic crisis — no error handling, rollback, monitoring, or acceptance criteria anywhere |
| 10 | AI Safety | LOW* | LOW | LOW | LOW | Low risk assuming no undisclosed AI/ML; P1 flagged conditional risk |
| 11 | Client Experience/UX | MEDIUM | MEDIUM | MEDIUM | MEDIUM | Every proposal sells outcomes but never shows the user journey |
| 12 | Maintainability/Handoff | **HIGH** | MEDIUM-HIGH | **HIGH** | **HIGH** | Systemic gap — "Training & Handoff: Included" is a single line with no specification |
| 13 | Data Integrity | **HIGH** | **HIGH** | **HIGH** | **HIGH** | Universal HIGHEST risk — no validation, no dedup, no reconciliation in any proposal |

**Legend:** CRITICAL = immediate blocker | HIGH = must fix before delivery | MEDIUM = should address | LOW = acceptable

**Heat Summary:**
- **Red zone (HIGH/CRITICAL across 3+ proposals):** Lenses 9, 12, 13
- **Orange zone (HIGH in 1-2 proposals):** Lenses 1, 8
- **Green zone (LOW across all):** Lenses 4, 5, 7, 10

---

## 2. Common Themes

### Theme A: "Governance Vacuum" (Lenses 9, 12, 13 — all proposals)
Every proposal describes WHAT the automation does but none specify what happens when it fails, how errors are detected, how records are validated, or how the client takes ownership. This is the single most pervasive issue across the engagement. For aviation maintenance — where work orders and estimates are adjacent to safety-critical processes — this is not a cosmetic gap.

### Theme B: "Data Integrity by Assumption" (Lens 13 — all proposals)
All four proposals assume clean upstream data. P1 assumes input data is valid when creating records in 6 systems. P2 assumes QMX discrepancy records are complete and consistently formatted. P3 assumes P2 data (or QMX historical data) is accurate enough to auto-populate customer-facing estimates. P4 inherits all three assumptions. None define validation rules, anomaly detection, or "garbage in" protections.

### Theme C: "Handoff as Afterthought" (Lens 12 — all proposals)
Every proposal includes some variant of "Training & Handoff: Included" as a single line item. None define what documentation is delivered, what training format is used (live? recorded? written?), what self-sufficiency looks like, or what happens if the retainer is declined and something breaks. This creates vendor dependency by default, even though the proposals claim "You Own Everything."

### Theme D: "Security by Omission" (Lens 8 — all proposals)
No proposal contains a security architecture section. P1 involves 6 sets of API credentials with write access to production systems. P2 involves extracting and storing sensitive business data in a new database. P3 involves auto-generating customer-facing pricing. P4 combines all three. Zero proposals discuss: credential management, access controls, encryption, audit logging, API permission scoping, or breach notification.

### Theme E: "Regulation-Blind" (Lens 1 — all proposals)
J&G Aviation is a military-adjacent FAA Part 145 repair station. All four proposals treat it as a generic small business. No proposal mentions FAA Part 43/145 record-keeping requirements, ITAR/EAR for military aircraft data, DFARS/CMMC for potential DoD contracts, or state labor laws for the mechanic performance tracking data.

### Theme F: "Strong Discovery, Weak Specification" (Lenses 3, 4, 11)
Every proposal demonstrates deep client knowledge — specific systems, specific SOPs, specific volume metrics, specific prior conversations. The discovery is excellent. But the proposals consistently convert this discovery into outcome descriptions rather than implementation specifications. They say what the automation will achieve, not how it will be built, tested, validated, or maintained.

### Theme G: "The QMX Black Box" (Lenses 3, 8, 12, 13)
QMX is the foundational system for all four proposals. P1 creates work orders in QMX. P2 extracts discrepancy data from QMX. P3 depends on QMX data (directly or via P2). P4 combines all three. Yet no proposal specifies the QMX integration method (API? direct DB? CSV export? screen scraping?), QMX TOS compliance, QMX schema change resilience, or QMX rate limits. This is the single most important technical detail across the entire engagement and it is absent everywhere.

---

## 3. Critical Findings Summary (Ranked by Severity)

| Rank | Finding | Affected Proposals | Severity | Domain Impact |
|------|---------|-------------------|----------|---------------|
| **1** | No error handling, rollback, or partial-failure behavior specified for multi-system automations | P1, P3, P4 | CRITICAL | Orphaned/incomplete work orders in aviation maintenance systems |
| **2** | No data validation, duplicate prevention, or reconciliation logic anywhere | P1, P2, P3, P4 | CRITICAL | Incorrect records propagated across 6 production systems; bad data feeding customer-facing estimates |
| **3** | QMX extraction/integration method completely unspecified | P1, P2, P3, P4 | HIGH | Entire engagement feasibility depends on this; TOS violation risk |
| **4** | No acceptance criteria or definition of "done" for any proposal | P1, P2, P3, P4 | HIGH | Scope disputes, payment conflicts, no shared quality standard |
| **5** | Handoff documentation unspecified despite "You Own Everything" claim | P1, P2, P3, P4 | HIGH | Vendor dependency contradicts the stated ownership model |
| **6** | No FAA/regulatory compliance acknowledgment for aviation maintenance automation | P1, P2, P3, P4 | HIGH | Regulatory audit exposure; automated records may not satisfy Part 145 requirements |
| **7** | 6+ sets of API credentials with write access; no security controls documented | P1, P4 | HIGH | Attack surface for production systems in military-adjacent context |
| **8** | Mechanic performance tracking has undisclosed labor relations/ethical implications | P2, P4 | HIGH | Workforce surveillance data without transparency, notification, or governance |
| **9** | P3 dependency on P2 data quality underspecified; degraded-mode UX undefined | P3, P4 | MEDIUM-HIGH | Standalone P3 delivers significantly less value than claimed |
| **10** | No monitoring, alerting, or health-check mechanism for any automation | P1, P2, P3, P4 | MEDIUM-HIGH | Silent failures; client discovers issues only when downstream processes break |
| **11** | Monthly retainer scope undefined across all proposals | P1, P2, P3, P4 | MEDIUM | Scope creep risk; client expectation mismatch |
| **12** | User experience described only as outcomes; no user journey or interface specification | P1, P2, P3, P4 | MEDIUM | Mismatch between what client expects to see/do and what is delivered |

---

## 4. Consolidated Priority Actions (Top 15, Deduplicated)

| # | Action | Urgency | Applies To | Source Lenses | Phase |
|---|--------|---------|------------|---------------|-------|
| **1** | **Define error handling and partial-failure protocol** — specify behavior when step N of M fails across multi-system chains; include rollback, retry, user notification, and orphan cleanup | P0 - BLOCKER | P1, P3, P4 | 9, 13 | Pre-contract |
| **2** | **Specify data validation rules and duplicate prevention** — idempotency keys, input field validation, reasonableness checks, cross-system record reconciliation | P0 - BLOCKER | All | 9, 13 | Pre-contract |
| **3** | **Define and document the QMX integration method** — API, direct DB, CSV, or scraping? Verify TOS compliance. Document schema dependencies. Plan for schema change resilience | P0 - BLOCKER | All | 3, 8, 12, 13 | Pre-contract |
| **4** | **Establish acceptance criteria and UAT process** — define what "done" looks like for each deliverable, with test cases, a UAT period, and defect resolution process tied to payment milestones | P1 - HIGH | All | 9, 11 | Pre-contract |
| **5** | **Add FAA/regulatory compliance statement** — address how automated record creation satisfies (or explicitly does not interact with) Part 145/Part 43 record-keeping requirements | P1 - HIGH | All | 1 | Pre-contract |
| **6** | **Create a security architecture section** — credential management, API permission scoping (least privilege), encryption at rest/in transit, audit logging, access controls, breach notification | P1 - HIGH | All | 8 | Pre-contract |
| **7** | **Enumerate handoff deliverables** — system architecture diagram, runbook, troubleshooting guide, credential inventory, recorded training, business rules reference, self-sufficiency roadmap | P1 - HIGH | All | 12, 11 | Pre-contract |
| **8** | **Add a Data Processing/Governance Addendum** — data ownership, retention, access controls, mechanic performance data handling policy, what happens to data if engagement ends | P1 - HIGH | All (especially P2, P4) | 1, 2, 8 | Pre-contract |
| **9** | **Define mechanic performance data governance** — who sees it, how it is used, whether mechanics are notified, usage restrictions, retention/deletion policies | P1 - HIGH | P2, P4 | 2, 1 | Pre-contract |
| **10** | **Add human-in-the-loop checkpoints** — at minimum, a confirmation step before records are committed to QMX and HubSpot (P1); before estimates are finalized (P3) | P1 - HIGH | P1, P3, P4 | 9, 10 | Build phase |
| **11** | **Implement monitoring and alerting** — health checks, failure notifications (Slack channel), silent failure detection, monthly reconciliation audits | P2 - MEDIUM | All | 9, 12 | Build phase |
| **12** | **Define retainer scope explicitly** — SLA, response time, included hours, what constitutes in-scope vs. out-of-scope, escalation path | P2 - MEDIUM | All | 6, 11 | Pre-contract |
| **13** | **Specify the P3-without-P2 experience** — quantify standalone ROI, define degraded-mode UX, explain what manual input means operationally when P2 data is absent | P2 - MEDIUM | P3 | 3, 6, 11 | Pre-contract |
| **14** | **Add user journey descriptions** — show the actual screens/steps/notifications the user will experience, not just outcomes; include "What It Looks Like" section | P2 - MEDIUM | All | 11 | Pre-contract |
| **15** | **Implement workflow version control and credential rotation schedule** — n8n workflow exports to Git, quarterly credential rotation, configuration change management | P3 - STANDARD | All | 8, 12 | Post-deployment |

---

## 5. Implementation Dependencies

### Critical Path Diagram

```
                    QMX Integration Method
                    (MUST resolve first)
                           |
                    +------+------+
                    |             |
                    v             v
              P2: Analytics    P1: Work Order
              Engine           Automation
              (Weeks 1-2)     (Weeks 3-4 in
                    |          bundle, or
                    |          standalone)
                    v
              P3: Smart Estimates
              (Weeks 3-4 in bundle,
               or after P2)
```

### Dependency Map

| Dependency | Upstream | Downstream | Risk if Unresolved |
|------------|----------|------------|-------------------|
| **QMX API/integration method** | External (QMX vendor) | ALL proposals | Entire engagement may be infeasible |
| **P2 data quality** | P2 build | P3 auto-population accuracy | P3 value proposition degrades to manual-entry assist |
| **Phase 1 integrations** | Already complete | P1, P2, P3, P4 | Low risk — already validated |
| **n8n platform stability** | External (n8n) | ALL proposals | Single platform dependency for all automation |
| **Security/credential architecture** | Must be designed first | All build phases | Retrofitting security is harder and riskier |
| **Data governance framework** | Must be agreed pre-contract | P2 mechanic data, all data handling | Legal exposure if built without agreement |
| **Acceptance criteria** | Must be defined pre-contract | All payment milestones | Scope disputes at handoff |

### Build Sequence (If Bundled via P4)

1. **Pre-build (Week 0):** Resolve QMX integration method, define acceptance criteria, agree data governance, document security architecture
2. **Week 1-2:** Build P2 Analytics Engine (data foundation) — extract, transform, load QMX data; build PostgreSQL schema; validate data quality
3. **Week 2 (overlap):** Data quality assessment checkpoint — is QMX data clean enough to feed P3?
4. **Week 3:** Build P1 Work Order Automation — multi-system orchestration with error handling
5. **Week 3-4:** Build P3 Smart Estimates — leveraging P2 data for auto-population
6. **Week 4-5:** Integration testing, UAT, parallel processing validation
7. **Week 5:** Handoff, documentation delivery, training

---

## 6. Gap Analysis: What Is Missing Collectively

### A. Missing from ALL proposals

| Gap | Impact | Recommendation |
|-----|--------|----------------|
| **Disaster recovery / business continuity plan** | If n8n goes down, all automations stop. No fallback documented. | Define manual fallback procedures for each automation; document "break glass" runbook |
| **Change management process** | When business rules change (tier pricing, standard costs, new aircraft types), no process for updating the automation | Define configuration change workflow: who requests, who implements, how tested, how deployed |
| **Monitoring and observability** | No health checks, no dashboards for automation performance, no alerting | Build a meta-dashboard showing automation health, execution counts, error rates |
| **Testing strategy** | No mention of unit tests, integration tests, regression tests, or test environments | Define test environment (staging n8n instance?) and test protocol before production deployment |
| **Rollback/version control** | No way to revert to a previous version of any automation if an update breaks it | Implement n8n workflow version control (Git export); database backup schedule |
| **Incident response playbook** | When something goes wrong in production, no documented response process | Create runbook: who to contact, what to check, how to escalate, how to revert |
| **Compliance documentation** | No regulatory compliance mapping for aviation maintenance context | Produce a one-page compliance matrix mapping each automation to relevant regulatory requirements |
| **Performance benchmarks** | Time savings are projected but no measurement plan to validate post-deployment | Define KPIs and measurement method for first 90 days (actual time per WO, estimate accuracy, etc.) |

### B. Missing from the engagement model

| Gap | Impact | Recommendation |
|-----|--------|----------------|
| **No SLA for the retainers** | Client pays $100-300/month but guaranteed response time/availability is undefined | Define SLA tiers: response time, resolution time, availability hours |
| **No escalation path** | If the vendor is unavailable (illness, vacation, business closure), there is no plan | Define backup contact, documentation sufficient for another developer to take over |
| **No exit strategy** | "You Own Everything" but no transition plan if client switches vendors | Deliver a transition package: all credentials, architecture docs, code comments, dependency list |
| **No scope control mechanism** | No change request process for scope additions during build | Define change request process with cost/timeline impact assessment |

### C. Missing from the technical architecture

| Gap | Impact | Recommendation |
|-----|--------|----------------|
| **No API rate limit analysis** | HubSpot, Slack, QMX all have API rate limits; high-volume periods could trigger throttling | Document rate limits for each platform; implement backoff/retry logic |
| **No data freshness specification** | How current is the P2 data? Real-time? Daily batch? Weekly? | Define refresh intervals and timestamp all derived data |
| **No schema migration plan** | When QMX, HubSpot, or any platform updates their API/schema, no detection or adaptation plan | Implement schema drift detection; document API version pinning strategy |
| **No audit trail architecture** | No logging of what the automation did, when, with what inputs, producing what outputs | Implement structured logging for every automation run; retain logs per regulatory requirements |

### D. Missing from the client relationship

| Gap | Impact | Recommendation |
|-----|--------|----------------|
| **No post-deployment review cadence** | No planned check-in after go-live to assess whether the automation is performing as expected | Schedule 30/60/90-day reviews with defined metrics |
| **No feedback mechanism** | No way for the end user (Mike) to report issues, request changes, or provide improvement ideas | Create a dedicated feedback channel (Slack channel, form, or email alias) |
| **No success metrics agreement** | "45-57 hours saved" is projected but never measured; no shared definition of success | Agree on 3-5 KPIs before build; measure at 30/60/90 days |

---

## Final Assessment

**The proposals collectively represent a well-conceived, strategically sound automation engagement built on genuine domain expertise and strong client discovery.** The phased model is intelligent. The human-in-the-loop design is appropriate for the aviation maintenance context. The pricing is competitive. The vendor demonstrates real knowledge of the client's operations.

**The proposals collectively fail in one critical dimension: operational governance.** They describe what the automations will do but not how they will fail gracefully, how they will be validated, how they will be secured, how they will be handed off, or how data integrity will be maintained. For a generic small business, this might be acceptable at this price point. For a military-adjacent FAA Part 145 repair station, it is a gap that must be closed before delivery.

**The three P0 actions that must be resolved before any contract is signed:**
1. Define the QMX integration method (determines feasibility of everything)
2. Specify error handling and data validation for all multi-system workflows
3. Establish acceptance criteria with a UAT process

**The recommended purchase path:** P4 (bundle) is the economically rational and architecturally correct choice, with P2 built first as the data foundation. However, J&G should not sign until the pre-contract items in the Priority Actions table (items 1-9) are addressed either in the proposal or the SOW.

**Estimated effort to address all pre-contract gaps:** 1-2 days of focused work by Veteran Vectors, producing addenda or revised proposal sections. This is a small investment that materially reduces delivery risk and strengthens the client relationship.
