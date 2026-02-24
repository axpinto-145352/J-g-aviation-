# P2 — Discrepancy Analytics Engine (Enhanced Original)
## Veteran Vectors LLC → J&G Aviation
### Original proposal content preserved with inline review recommendations

---

## The Problem

You've got years of discrepancy data sitting in QMX — types, labor hours, parts costs, mechanic assignments — but no way to see patterns. Mike tried building a spreadsheet. It didn't work. Without analytics, you're pricing by memory and gut feel, which means you're leaving money on the table or undercharging on complex jobs.

> **[STRENGTH]** Directly references J&G's own failed attempt (Mike's spreadsheet), grounding the problem in observed pain rather than hypothetical need. This is excellent discovery work.

## What This Builds

A dedicated analytics engine that:

- Pulls every discrepancy record from QMX
- Normalizes and structures the data in a PostgreSQL database
- Generates dashboards showing:
  - Discrepancy frequency by type and aircraft tier
  - Average labor hours per discrepancy type
  - Parts cost trends over time
  - Labor breakdowns by mechanic and aircraft tier
  - Seasonal patterns and volume forecasting

> **[CRITICAL — Logistical (Lens 3), Data Integrity (Lens 13)]** "Pulls every discrepancy record from QMX" — how? The extraction method (API, direct database query, CSV export, screen scraping) is the single most important technical detail in this proposal and it is absent. This determines feasibility, TOS compliance, data freshness, and ongoing maintenance burden. **Must be specified before signing.**
> Priority: P0 - Critical | Effort: Low (research + document) | Timeline: Pre-contract

> **[CRITICAL — Data Integrity (Lens 13)]** No data quality assessment is planned before building the analytics layer. QMX data may have inconsistent formatting, missing fields, free-text vs. coded discrepancy types, or historical data gaps. A data quality assessment should be the first milestone. **Add a Week 0.5 data quality audit as a go/no-go gate.**
> Priority: P0 - Critical | Effort: Medium (4-8 hrs) | Timeline: Week 1 of engagement

> **[RECOMMENDATION — Data Integrity (Lens 13)]** "Normalizes and structures the data" — what normalization rules? How are free-text discrepancy descriptions categorized? How are duplicate records handled? How are null/missing values treated? Document the transformation rules as a deliverable.
> Priority: P1 - High | Effort: Medium (3-5 hrs) | Timeline: During build

> **[RECOMMENDATION — Ethical (Lens 2)]** "Labor breakdowns by mechanic and aircraft tier. See who is efficient where and where training would help." This is individual workforce performance data. Add governance: who can see individual mechanic data, usage policy (training-focused, not punitive), whether mechanics are notified about tracking, and retention/deletion policies.
> Priority: P1 - High | Effort: Low (1-2 hrs) | Timeline: Pre-contract

> **[RECOMMENDATION — Client UX (Lens 11)]** No dashboard technology specified. Is this Metabase, Grafana, a custom web app, or something else? The choice affects usability, hosting, cost, and maintainability. Provide wireframes or mockups before the build begins.
> Priority: P1 - High | Effort: Low (2-3 hrs) | Timeline: Pre-contract

## What Stays Manual

- Pricing decisions based on the analytics
- Data interpretation and strategic conclusions
- Customer relationship management
- Deciding which aircraft types to pursue or avoid

> **[STRENGTH]** Explicit carve-out of human judgment areas. This sets realistic expectations and avoids overpromising. The reference to "which aircraft types to pursue or avoid" directly connects to Mike's prior analysis (trimming low-margin types).

## The Value

- Stop pricing by memory — see actual historical costs
- Identify which discrepancy types eat margin
- See which mechanics are fastest on which aircraft types
- Spot seasonal patterns to plan staffing
- Build the data foundation for P3 Smart Estimates

> **[STRENGTH]** Strategic positioning as P3 enabler. The "data foundation" framing is technically accurate and creates a genuine compounding value argument.

> **[RECOMMENDATION — Cost Effectiveness (Lens 6)]** The value claims are qualitative. Consider adding one concrete example: "In your Phase 1 review, Mike identified [aircraft type] as low-margin and trimmed it. This dashboard would have surfaced that insight in minutes instead of weeks of manual analysis." Quantify where possible.
> Priority: P3 - Low | Effort: Low (30 min) | Timeline: Before sending proposal

## Pricing

| Item | Cost |
|------|------|
| One-time build | $2,500 |
| Monthly retainer (optional) | $200/mo |

Payment: 50% on approval, 50% on completion.

> **[CRITICAL — Guardrails (Lens 9)]** "50% on completion" — but there are no acceptance criteria defining what "completion" means. Add specific, testable acceptance criteria tied to the second payment: dashboard loads without errors, all specified views are functional, data reconciliation report shows >95% match between QMX source and analytics database, client UAT sign-off within 5 business days.
> Priority: P0 - Critical | Effort: Low (1-2 hrs) | Timeline: Pre-contract

> **[RECOMMENDATION — Cost Effectiveness (Lens 6)]** Infrastructure costs (PostgreSQL hosting, dashboard hosting, any compute for ETL) are not itemized. These become ongoing costs for the client. Itemize them separately so J&G can budget accurately.
> Priority: P1 - High | Effort: Low (30 min) | Timeline: Pre-contract

> **[RECOMMENDATION — Maintainability (Lens 12)]** "Monthly retainer (optional)" — be honest about whether it's truly optional. If the QMX extraction method requires monitoring, data syncing, and schema updates, the retainer isn't optional — it's necessary. Frame it as "strongly recommended" with a clear scope definition.
> Priority: P2 - Medium | Effort: Low (30 min) | Timeline: Before sending proposal

## Timeline

2 weeks from kickoff to dashboard delivery.

> **[RECOMMENDATION — Time (Lens 7)]** Add a 3-5 day UAT window after delivery. The client needs time to validate that the dashboards show data they recognize and trust. Without UAT, the "completion" milestone is vendor-defined, not client-validated.
> Priority: P2 - Medium | Effort: Low (add to timeline) | Timeline: Pre-contract

## Training & Handoff: Included

> **[CRITICAL — Maintainability (Lens 12)]** Same issue as P1 — this single line needs to become an enumerated deliverable list:
> - Database schema documentation (tables, relationships, field definitions)
> - ETL pipeline documentation (extraction method, transformation rules, load process)
> - Dashboard user guide (how to read each view, filter, export)
> - Troubleshooting guide (what to check when data looks wrong, ETL fails, or dashboard is stale)
> - Credential inventory (QMX extraction credentials, database credentials, dashboard access)
> - Recorded training session (walkthrough of all dashboard views and common queries)
> Priority: P1 - High | Effort: Medium (6-10 hrs) | Timeline: Specify in proposal; deliver at handoff

## You Own Everything

All data, dashboards, queries, and configurations belong to J&G.

> **[RECOMMENDATION — Legal (Lens 1)]** Formalize this as an IP ownership clause in the SOW. Also add: data ownership (J&G owns all extracted and derived data), what happens to data if the engagement ends (vendor deletes all copies within 30 days), and whether the client receives database export capabilities.
> Priority: P2 - Medium | Effort: Low (30 min) | Timeline: Pre-contract

---

## Missing Sections (Recommended Additions)

### QMX Integration Specification (NEW SECTION — P0 Critical)

*This section does not exist in the original proposal and must be added.*

- **Extraction method:** [API / Direct DB query / CSV export / Screen scraping] — specify which
- **TOS compliance:** Verify that QMX permits automated data extraction via the chosen method
- **Data freshness:** How often is data synced? Real-time, daily, weekly?
- **Schema dependencies:** Which QMX fields/tables does this depend on? What happens when QMX updates its schema?
- **Error handling:** What happens when extraction fails? Alerting, retry, manual fallback?

### Data Governance (NEW SECTION — P1 High)

*This section does not exist in the original proposal and should be added.*

- **Data ownership:** J&G Aviation owns all extracted and derived data
- **Mechanic performance data:** Access restricted to [specified roles]. Used for training and optimization purposes only. Mechanics to be notified that performance analytics are being tracked.
- **Retention policy:** Data retained for [X months/years]. Client can request full deletion at any time.
- **Access controls:** Dashboard access requires authentication. Role-based access for different data views.
- **Breach notification:** Vendor will notify client within 48 hours of any data security incident.

### Acceptance Criteria (NEW SECTION — P0 Critical)

*This section does not exist in the original proposal and must be added.*

The second payment milestone (50%) is due upon meeting these criteria:
1. All 5 dashboard views are functional and loading data
2. Data reconciliation: analytics record count matches QMX source within 2%
3. Date range filters work correctly across all views
4. Data refresh is running on the specified schedule without errors for 5 consecutive days
5. Client completes UAT walkthrough and signs off within 5 business days

### Security & Access (NEW SECTION — P1 High)

*This section does not exist in the original proposal and should be added.*

- **Dashboard authentication:** Username/password or SSO integration
- **Role-based access:** Admin (full access), Manager (all views), Viewer (limited views)
- **Database security:** Encryption at rest, TLS for connections, IP whitelisting
- **Backup schedule:** Automated daily backups with 30-day retention
- **Credential management:** All API keys stored in n8n credential vault, rotated quarterly
