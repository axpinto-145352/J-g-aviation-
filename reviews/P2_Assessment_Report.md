# Comprehensive Review: P2 — Discrepancy Analytics Engine
## Veteran Vectors LLC → J&G Aviation

**Date:** 2026-02-23
**Proposal:** P2 — Discrepancy Analytics Engine ($2,500 one-time + $200/month retainer)
**Overall Risk Profile: LOW-MEDIUM**

## Executive Summary

P2 is a well-scoped, technically straightforward analytics build that addresses a clearly documented pain point. The proposal demonstrates strong domain knowledge from a completed Phase 1 engagement, and the economics are favorable. However, the proposal has meaningful gaps in data governance, security specifics, schema resilience, and long-term maintainability documentation that -- while not deal-breakers -- need to be addressed before or during the build to protect both parties. The heaviest risks cluster around data integrity (what happens when QMX changes its schema or data format), operational handoff readiness (can J&G actually maintain this without Veteran Vectors), and the absence of explicit contractual protections around data handling and acceptance criteria.

### Top 3 Strengths

1. **Strong problem-solution fit.** The proposal directly references J&G's own failed spreadsheet attempt and the specific analysis Mike already did (trimming low-margin aircraft types). This is not a generic pitch -- it is grounded in observed pain from Phase 1 engagement.
2. **Honest scoping with clear manual/automated boundaries.** The "What Stays Manual" section explicitly carves out pricing judgment and data interpretation as human responsibilities. This sets realistic expectations and avoids overpromising.
3. **Strategic positioning as P3 enabler.** P2 is correctly identified as the data foundation that makes P3 (Smart Estimates) functional. This creates a logical build sequence and a genuine compounding value argument rather than an artificial upsell.

### Top 3 Critical Findings

1. **No data handling, retention, or privacy terms specified.** The proposal involves extracting and storing mechanic performance data, labor hours by individual, and historical cost data in a new PostgreSQL database. There is zero mention of who owns this data, how it is secured, what happens to it if the engagement ends, retention policies, or access controls. For a military-adjacent aviation business, this is a significant omission.
2. **No specification for how QMX data extraction actually works.** The proposal says "pull every discrepancy record from QMX" but does not specify the extraction method (API, direct database query, CSV export, screen scraping). The method chosen has profound implications for reliability, TOS compliance, data freshness, and ongoing maintenance burden. This is the single most important technical detail in the entire proposal and it is absent.
3. **No acceptance criteria or definition of "done."** The proposal moves from "Approve: Sign the SOW" to "Kickoff" with 50/50 payment, but there are no acceptance criteria for when the second 50% is due, no UAT process defined, no definition of what constitutes a working deliverable, and no warranty period.

### Top 5 Priority Actions

| # | Action | Priority | Lens(es) |
|---|--------|----------|----------|
| 1 | Define the QMX extraction method and document it in the SOW | P0 - Critical | Logistical (3), Security (8), Maintainability (12), Data Integrity (13) |
| 2 | Add a data governance addendum covering data ownership, access controls, retention, mechanic performance data handling | P0 - Critical | Legal (1), Security (8) |
| 3 | Establish explicit acceptance criteria with a UAT period and defect resolution process tied to the second payment | P0 - Critical | Guardrails (9), Client UX (11) |
| 4 | Specify the dashboard technology and hosting | P1 - High | Client UX (11), Maintainability (12) |
| 5 | Document a schema change resilience plan | P1 - High | Data Integrity (13), Maintainability (12) |

## Dimensional Analysis

### 1. Legal
- **Current State:** No contractual protections beyond the implicit SOW in the proposal. No data ownership clause, no data handling terms, no IP assignment, no liability limitation. The proposal creates a new database containing sensitive business data (labor hours, costs, mechanic performance) with no governance framework.
- **Risk Rating:** MEDIUM — While the engagement is relatively small ($2,500), the data being collected (mechanic performance, labor costs, discrepancy patterns) has significant business sensitivity. The absence of data governance terms creates ambiguity about ownership and handling.
- **Key Findings:**
  1. No data ownership clause — unclear who owns the PostgreSQL database and its contents
  2. No data handling/privacy terms for mechanic performance data
  3. No IP assignment clause for the ETL workflows and dashboard code
  4. No warranty or liability limitation terms
  5. No mention of QMX TOS compliance for automated data extraction
  6. No terms for data retention or deletion upon engagement termination
- **Recommendations:**
  1. [Quick Win] Add data ownership clause: client owns all data, vendor retains no copies post-engagement
  2. [Quick Win] Add IP ownership clause: workflows, schema, and dashboard code belong to client
  3. [Short-Term] Add a data governance addendum covering retention, access, and deletion policies
  4. [Short-Term] Verify QMX TOS permits automated data extraction before signing

### 2. Ethical
- **Current State:** The proposal includes mechanic performance tracking ("Labor breakdowns by mechanic and aircraft tier. See who is efficient where and where training would help"). This is workforce analytics data with labor relations implications.
- **Risk Rating:** LOW-MEDIUM — While the framing is constructive ("where training would help"), individual mechanic performance data can be misused for punitive purposes. There is no governance around how this data is viewed, shared, or used.
- **Key Findings:**
  1. Mechanic performance data will be stored and displayed without documented access controls
  2. No mention of whether mechanics are informed that their performance is being tracked/analyzed
  3. The framing ("training opportunities") is positive but the data could be used punitively
  4. No usage policy defining appropriate vs. inappropriate uses of mechanic performance data
- **Recommendations:**
  1. [Quick Win] Add a note about appropriate use of mechanic performance data (training-focused, not punitive)
  2. [Short-Term] Define who has access to individual mechanic performance data (management only, not peers)
  3. [Short-Term] Consider whether mechanics should be notified about performance tracking

### 3. Logistical
- **Current State:** The proposal is logistically feasible. It targets a well-defined output (analytics dashboard from QMX data), uses proven technology (PostgreSQL + dashboard tool), and builds on Phase 1 relationships. The 2-week timeline is ambitious but achievable for a straightforward ETL + dashboard build.
- **Risk Rating:** LOW-MEDIUM — The timeline is tight and the QMX extraction method is the key feasibility question. If QMX has a clean API, this is straightforward. If extraction requires workarounds, the timeline and cost could expand.
- **Key Findings:**
  1. The QMX extraction method is not specified — this is the primary logistical risk
  2. The dashboard technology is not specified — different tools have different capability/complexity profiles
  3. The 2-week timeline assumes clean data and no major QMX integration challenges
  4. Infrastructure requirements (hosting, database) are not itemized
- **Recommendations:**
  1. [Quick Win] Specify the QMX extraction method before signing
  2. [Quick Win] Specify the dashboard technology (Metabase, Grafana, custom, etc.)
  3. [Short-Term] Itemize infrastructure costs and hosting requirements in the SOW

### 4. Current State
- **Current State:** The proposal demonstrates excellent current-state understanding. It references J&G's failed spreadsheet attempt, specific analysis Mike performed (trimming low-margin aircraft), and the existing Phase 1 integrations.
- **Risk Rating:** LOW — Strong discovery and domain knowledge. This is a consistent strength across the engagement.
- **Key Findings:**
  1. Direct reference to J&G's own failed analytics attempt validates the pain point
  2. Specific volume metrics and system references demonstrate genuine engagement knowledge
  3. Phase 1 completion provides real institutional knowledge
- **Recommendations:**
  1. Not applicable — this is a strength area

### 5. Future Strategy
- **Current State:** P2 is correctly positioned as the data foundation for P3 (Smart Estimates). The shared data model argument is technically sound. The P4 bundle creates a natural progression path.
- **Risk Rating:** LOW — Well-aligned strategically. P2 standalone has value; P2+P3 has compounding value.
- **Key Findings:**
  1. P2 as data foundation for P3 is architecturally sound
  2. The "one data model, build once, use everywhere" argument is legitimate
  3. Schema extensibility for future use cases is not explicitly addressed
- **Recommendations:**
  1. [Short-Term] Design the PostgreSQL schema with extensibility in mind (new aircraft tiers, new discrepancy types)
  2. [Long-Term] Add data export capability (CSV/API) for future integrations beyond P3

### 6. Cost Effectiveness
- **Current State:** $2,500 one-time + $200/month optional retainer. The proposal claims payback within months through better pricing decisions. The analytics dashboard replaces a failed manual spreadsheet effort, so the alternative cost (continued manual analysis) is real.
- **Risk Rating:** LOW — The pricing is reasonable for an ETL + dashboard build. The $200/month retainer is optional and well-positioned.
- **Key Findings:**
  1. $2,500 for ETL + PostgreSQL + dashboard is competitive for this scope
  2. ROI depends on the quality of insights — "better pricing decisions" is hard to quantify upfront
  3. Infrastructure costs (hosting, DB) are not separated from build costs
  4. The retainer scope ($200/month) is undefined — potential for scope disputes
- **Recommendations:**
  1. [Quick Win] Define retainer scope explicitly (hours, response time, included services)
  2. [Quick Win] Itemize infrastructure costs separately
  3. [Short-Term] Frame retainer as strongly recommended, not truly optional (given ongoing data sync needs)

### 7. Time Effectiveness
- **Current State:** 2-week build timeline. Replaces a manual analysis effort that J&G already attempted and failed. The time-to-insight improvement is significant — from "Mike can't build this spreadsheet" to "automated, always-current dashboard."
- **Risk Rating:** LOW — The time value proposition is clear and well-supported.
- **Key Findings:**
  1. The 2-week timeline is tight but achievable for a standard ETL + dashboard build
  2. No UAT window is included in the timeline — should add 3-5 days
  3. Time-to-value is good — first insights available as soon as data is loaded and dashboard is built
- **Recommendations:**
  1. [Quick Win] Add a 3-5 day UAT window to the timeline

### 8. Security
- **Current State:** A new PostgreSQL database containing sensitive business data (labor costs, mechanic performance, discrepancy patterns) will be created. No security architecture is described — no access controls, no encryption, no backup, no hosting security, no credential management.
- **Risk Rating:** MEDIUM-HIGH — Sensitive business data in a new database with no documented security controls. The data includes individual employee performance metrics, cost data, and operational patterns.
- **Key Findings:**
  1. No authentication or role-based access for the dashboard
  2. No encryption specification (at rest or in transit)
  3. No backup and recovery plan for the PostgreSQL database
  4. No hosting security specification (where is the DB hosted, who has access?)
  5. No credential management for QMX extraction
  6. No breach notification process
- **Recommendations:**
  1. [Quick Win] Add authentication and role-based access to the dashboard
  2. [Short-Term] Specify hosting location and security controls for the PostgreSQL database
  3. [Short-Term] Implement automated daily database backups
  4. [Short-Term] Document credential management for QMX extraction

### 9. Guardrails & Governance
- **Current State:** The proposal has some implicit guardrails (human judgment for pricing decisions, manual data interpretation). However, there are no explicit quality controls, acceptance criteria, monitoring, or change management processes.
- **Risk Rating:** MEDIUM-HIGH — While P2 is primarily read-only (analytics, not automation), data quality issues could lead to incorrect business decisions. No acceptance criteria means no shared definition of "done."
- **Key Findings:**
  1. No acceptance criteria — no shared definition of what constitutes a working deliverable
  2. No data quality validation — how is data completeness and accuracy verified?
  3. No monitoring — how are ETL failures or data staleness detected?
  4. No change management — how are dashboard changes, schema updates, or new metrics handled?
  5. Payment structure (50/50) not tied to specific milestones or acceptance
- **Recommendations:**
  1. [Quick Win] Define acceptance criteria tied to the second payment milestone
  2. [Short-Term] Implement basic monitoring with failure alerts (ETL runs, data freshness)
  3. [Short-Term] Implement a reconciliation report (source record count vs. analytics record count)

### 10. AI Safety & Responsible AI
- **Current State:** No AI/LLM usage disclosed. P2 appears to be a standard ETL + analytics build. No AI components mentioned.
- **Risk Rating:** LOW — Not applicable unless AI components are used for data extraction, classification, or insight generation.
- **Key Findings:**
  1. No AI/LLM usage disclosed — standard ETL + dashboard pattern
- **Recommendations:**
  1. [Quick Win] Clarify whether any AI components are planned for data processing or insight generation

### 11. Client Experience & Usability
- **Current State:** The proposal describes the dashboard's purpose (discrepancy trends, cost breakdowns, mechanic performance) but not its interface, navigation, or user workflow. No wireframes, no user flow, no onboarding plan.
- **Risk Rating:** MEDIUM — The dashboard could be technically correct but difficult to use, leading to low adoption. Mike's failed spreadsheet attempt suggests he values the data but needs it presented accessibly.
- **Key Findings:**
  1. No wireframes or mockups of the dashboard
  2. No description of the user workflow (how does Mike access it? How does he navigate?)
  3. No onboarding plan beyond "Training & Handoff: Included"
  4. No specification of data refresh frequency visible to the user
  5. No feedback mechanism for the client to request changes or report issues
- **Recommendations:**
  1. [Quick Win] Provide wireframes or mockups of the dashboard views before build
  2. [Quick Win] Specify the dashboard technology so the client knows what to expect
  3. [Short-Term] Define training format (live session, recorded walkthrough, written guide)
  4. [Short-Term] Add a data freshness indicator to the dashboard (last refresh timestamp)

### 12. Maintainability & Handoff Readiness
- **Current State:** "Training & Handoff: Included" with no specification. The optional $200/month retainer implies the client may need ongoing support. No documentation deliverables are specified.
- **Risk Rating:** MEDIUM-HIGH — The client receives a database and dashboard but no documentation on how to maintain, troubleshoot, or extend it. The retainer is the only support path.
- **Key Findings:**
  1. No documentation deliverables specified (schema docs, ETL docs, troubleshooting guide)
  2. No handoff checklist (credentials, access, configuration, dependencies)
  3. No workflow version control
  4. No defined path to client self-sufficiency
  5. The retainer framing as "optional" contradicts the likely reality that ongoing support will be needed
- **Recommendations:**
  1. [Quick Win] Define a handoff checklist (credentials, docs, exports, runbook)
  2. [Short-Term] Put workflows and schema in Git (client-owned repository)
  3. [Short-Term] Create a maintainer's guide for future developer handoff
  4. [Short-Term] Frame the retainer honestly — "strongly recommended" vs. "optional"

### 13. Data Integrity & Quality
- **Current State:** The entire value of P2 depends on data quality. The proposal assumes QMX data is complete, consistent, and correctly formatted. No validation, no deduplication, no reconciliation, no schema drift protection.
- **Risk Rating:** HIGH — P2's outputs (analytics, dashboards, insights) are only as good as its inputs. If QMX data is dirty, incomplete, or inconsistently formatted, the dashboard will present misleading information that drives bad business decisions.
- **Key Findings:**
  1. No investigation of QMX data quality before building the analytics layer
  2. No specification of discrepancy taxonomy (free-text vs. coded?) — impacts categorization accuracy
  3. No null/missing data handling rules
  4. No duplicate record handling (idempotent extraction)
  5. No schema drift detection or resilience plan
  6. No reconciliation mechanism (QMX record count vs. analytics record count)
  7. No data freshness specification (how often is data synced?)
- **Recommendations:**
  1. [Quick Win] Investigate QMX data quality during the audit call (completeness, consistency, taxonomy)
  2. [Quick Win] Define data freshness requirements (real-time, daily, weekly?)
  3. [Short-Term] Implement idempotent extraction with deduplication
  4. [Short-Term] Define null/missing data handling rules for each field
  5. [Short-Term] Add reconciliation report comparing source and analytics record counts
  6. [Long-Term] Implement schema drift detection and alerting

## Cross-Cutting Themes

1. **The QMX Black Box:** Everything in P2 depends on QMX data extraction, but the extraction method is completely unspecified. This is the single most important technical decision in the entire proposal.
2. **Data-Driven Decisions Without Data Validation:** P2 will produce dashboards that inform pricing and staffing decisions. If the underlying data is incomplete or incorrect, those decisions will be wrong — with direct financial impact.
3. **Analytics Without Governance:** Performance data about individual employees will be collected, stored, and displayed without any governance framework around access, use, or disclosure.

## Priority Matrix

| # | Recommendation | Lens(es) | Priority | Effort | Impact |
|---|---------------|----------|----------|--------|--------|
| 1 | Specify QMX extraction method in SOW | 1, 3, 8, 12, 13 | Critical | Low | Very High |
| 2 | Define acceptance criteria tied to second payment | 9, 11 | Critical | Low | High |
| 3 | Add data governance addendum | 1, 8 | Critical | Medium | High |
| 4 | Define data freshness requirements | 13, 7 | Critical | Low | Very High |
| 5 | Specify dashboard technology and wireframes | 11, 12 | High | Low | High |
| 6 | Implement reconciliation report | 9, 13 | High | Low | High |
| 7 | Add authentication and role-based access | 8, 2 | High | Medium | High |
| 8 | Itemize infrastructure costs in SOW | 6, 3 | High | Low | Medium |
| 9 | Define handoff checklist | 12, 11 | High | Low | High |
| 10 | Investigate QMX discrepancy taxonomy | 13, 3 | High | Medium | Very High |
| 11 | Verify QMX TOS permits automated extraction | 1 | High | Low | Very High |
| 12 | Define null/missing data handling rules | 13 | Medium | Low | Medium |
| 13 | Implement idempotent extraction | 13 | Medium | Medium | High |
| 14 | Add UAT window to timeline | 7, 9 | Medium | Low | Medium |
| 15 | Implement monitoring with failure alerts | 9, 12 | Medium | Low | High |
| 16 | Put workflows and schema in Git | 12 | Medium | Low | Medium |
| 17 | Frame retainer honestly | 6, 12 | Medium | Low | Medium |
| 18 | Add mechanic context to performance dashboards | 2, 11 | Medium | Medium | Medium |
| 19 | Clarify retainer scope | 6, 11 | Medium | Low | Medium |
| 20 | Define training deliverables | 11, 12 | Medium | Low | Medium |
| 21 | Design schema for extensibility | 5, 13 | Low | Medium | Medium |
| 22 | Build data export capability | 5, 12 | Low | Low | Medium |
| 23 | Assess CMMC/DFARS applicability | 8, 1 | Low | High | Conditional |
| 24 | Create maintainer's guide | 12 | Low | Medium | Medium |
| 25 | Implement schema drift detection | 13 | Low | Medium | High |

## Conclusion & Next Steps

### Overall Assessment

P2 is a **sound proposal with a legitimate value proposition** that addresses a real, documented pain point. The problem is genuine (Mike's failed spreadsheet attempt confirms this), the solution is architecturally appropriate (ETL + PostgreSQL + dashboard is the right pattern), the vendor has relevant experience (Phase 1 relationship + defense analytics case study), and the economics work even on conservative assumptions (payback in 3-4 months).

The proposal's weaknesses are concentrated in **specification, not strategy**. It tells J&G what they will get and why it matters, but not how it will be built, secured, validated, or maintained. For a $2,500 engagement, this level of ambiguity is not unusual — but because P2 produces numbers that drive pricing decisions, data quality and validation deserve more rigor than a typical project at this price point.

The most important pre-contract action is **resolving the QMX extraction method**. Everything else — timeline, feasibility, maintenance burden, data freshness, TOS compliance — flows from that decision.

### Recommended Next Steps

1. **Before signing:** Resolve items 1-5 and 11 from the Priority Matrix
2. **During the audit call:** Resolve items 10 and 12 (QMX taxonomy and data completeness)
3. **During Week 1 of build:** Resolve items 6, 7, 13, 14, 15, 16
4. **At handoff:** Resolve items 9, 17, 18, 19, 20
5. **Post-deployment (Month 1-3):** Resolve items 21-25

### Final Note on Bundle vs. Standalone

P2 standalone is viable but its highest-impact use case — feeding P3's Smart Estimates — requires both systems. The P4 bundle ($5,000 for all three) is the economically rational choice if J&G plans to eventually purchase all three. J&G should decide before signing P2 whether they intend to proceed with the bundle, as building P2 alone then retrofitting it for P3 later could create rework.
