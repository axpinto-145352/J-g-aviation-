# P3 — Smart Estimates (Enhanced Original)
## Veteran Vectors LLC → J&G Aviation
### Original proposal content preserved with inline review recommendations

---

## The Problem

Every estimate takes 30-45 minutes. You're pulling labor hours from memory, looking up parts costs manually, applying tier pricing by hand, and rebuilding the same structure for similar jobs. At 50+ estimates per year, that's 25-37 hours spent on repetitive data entry that could be pre-filled.

> **[STRENGTH]** Specific, quantified pain point grounded in observed workflow. The 30-45 min/estimate figure and 50+/year volume create a credible savings projection.

## What This Builds

A smart estimate system that:

- Auto-populates labor hours based on historical discrepancy data
- Applies tier-based pricing automatically (Tier 1, 2, 3 aircraft rates)
- Pre-fills standard cost items (consumables, shop supplies, inspection kits)
- Pulls parts costs from recent purchase history
- Generates a draft estimate in QMX Portal format for Mike's review

> **[CRITICAL — Logistical (Lens 3), Cost (Lens 6)]** "Auto-populates labor hours based on historical discrepancy data" — this is the headline deliverable and it requires P2 data. The proposal states P3 "works best paired with P2" and without it, "labor hours default to your manual input." This means standalone P3 is a fundamentally different (and less valuable) product. **Quantify P3 standalone ROI separately from P3+P2 ROI. Define what the user experiences when P2 data is absent.**
> Priority: P0 - Critical | Effort: Low (1-2 hrs) | Timeline: Pre-contract

> **[RECOMMENDATION — Data Integrity (Lens 13)]** "Auto-populates labor hours based on historical discrepancy data" — what averaging method? Mean or median? What's the minimum sample size required? If a discrepancy type has only 2 historical data points, is that enough to auto-populate? Display the sample size (n) alongside auto-populated values so Mike can judge confidence.
> Priority: P1 - High | Effort: Low (1-2 hrs) | Timeline: During build

> **[RECOMMENDATION — Data Integrity (Lens 13)]** "Pulls parts costs from recent purchase history" — how recent? What if the last purchase was 2 years ago and prices have changed 30%? Add a parts cost freshness indicator showing the date of the last purchase.
> Priority: P2 - Medium | Effort: Low (1-2 hrs) | Timeline: During build

> **[RECOMMENDATION — Guardrails (Lens 9)]** Add validation rules for auto-populated values: flag labor hours that fall outside 2 standard deviations of the historical mean, require confirmation for estimates exceeding $X threshold, reject line items with zero labor hours. These are safety nets for the human reviewer.
> Priority: P1 - High | Effort: Medium (3-5 hrs) | Timeline: During build

> **[RECOMMENDATION — Data Integrity (Lens 13)]** Define cold-start behavior: what happens when an aircraft type or discrepancy type has no historical data? Options: leave field blank (user fills manually), use fleet-wide average with a "low confidence" flag, or use tier default values. Document the chosen approach.
> Priority: P1 - High | Effort: Low (1 hr) | Timeline: During build

## What Stays Manual

- Final estimate review and approval (Mike)
- Custom line items and special pricing
- Customer communication and negotiation
- First-time-seen discrepancy pricing

> **[STRENGTH]** Human-in-the-loop by design. Keeping estimate review, approval, and custom overrides with Mike is the right architecture for pricing automation in aviation maintenance. This is the proposal's strongest design decision.

> **[RECOMMENDATION — Client UX (Lens 11)]** Define the override mechanism: when Mike disagrees with an auto-populated value, how does he change it? Is it inline editing? A separate review screen? Is the original auto-populated value preserved for audit purposes?
> Priority: P1 - High | Effort: Low (1 hr) | Timeline: Pre-contract

## Hours Saved

| Task | Manual Time | Automated | Savings |
|------|------------|-----------|---------|
| Labor hour lookup | 10-15 min | Auto-filled | 10-15 min |
| Tier pricing application | 5-8 min | Auto-applied | 5-8 min |
| Standard cost items | 5-10 min | Pre-filled | 5-10 min |
| Parts cost research | 10-12 min | Pre-populated | 10-12 min |

At 50+ estimates per year: **25-37 hours saved annually**

> **[RECOMMENDATION — Time Effectiveness (Lens 7)]** These savings assume P2 data is available for labor hour auto-fill. Without P2, the first row ("Labor hour lookup: 10-15 min saved") drops out entirely, reducing annual savings to 15-25 hours. Present both scenarios clearly.
> Priority: P1 - High | Effort: Low (30 min) | Timeline: Pre-contract

> **[RECOMMENDATION — Cost Effectiveness (Lens 6)]** Add a "margin improvement" line item. If auto-populated historical data prevents Mike from underpricing even 5% of estimates by even 5%, the margin impact could exceed the time savings value. This is the stronger ROI argument.
> Priority: P3 - Low | Effort: Low (30 min) | Timeline: Before sending proposal

## Works Best Paired With P2

P3 uses P2's discrepancy data to auto-populate labor hours. Without P2, labor hours default to your manual input — the rest of the system still works.

> **[CRITICAL — Client UX (Lens 11)]** "The rest of the system still works" — but what does it look like? When P2 data is absent, does the labor hours field show blank? A placeholder? A message saying "Connect P2 for auto-fill"? Define the degraded-mode UX explicitly so the client makes an informed purchase decision.
> Priority: P0 - Critical | Effort: Low (1 hr) | Timeline: Pre-contract

## Pricing

| Item | Cost |
|------|------|
| One-time build | $2,000 |
| Monthly retainer (optional) | $100/mo |

> **[RECOMMENDATION — Cost Effectiveness (Lens 6)]** Define retainer scope: hours per month, response time, what's included (bug fixes, tier table updates, QMX schema changes) vs. out of scope (new features, additional dashboard views).
> Priority: P1 - High | Effort: Low (30 min) | Timeline: Pre-contract

## Timeline

2 weeks from kickoff to live.

> **[RECOMMENDATION — Guardrails (Lens 9)]** Add acceptance criteria: what constitutes a working P3 delivery? Suggested criteria: (1) All 4 auto-fill functions work for the top 10 most common discrepancy types, (2) Tier pricing calculates correctly for all 3 tiers, (3) Standard cost items pre-fill with current values, (4) Mike completes 3 test estimates and confirms accuracy, (5) 3-day UAT window with defect resolution before final payment.
> Priority: P0 - Critical | Effort: Low (1-2 hrs) | Timeline: Pre-contract

## Training & Handoff: Included

> **[CRITICAL — Maintainability (Lens 12)]** Enumerate the handoff deliverables:
> - Business rules reference (all tier formulas, standard cost logic, averaging methods, first-time annual adjustments)
> - Operations manual (how to trigger an estimate, review auto-populated values, override, finalize, send)
> - Technical reference (n8n workflow documentation, data sources, API connections)
> - Tier table update guide (how to change tier pricing when rates change)
> - Troubleshooting guide (top 10 failure scenarios and fixes)
> - Recorded training session (Mike walkthrough with screen recording)
> Priority: P1 - High | Effort: Medium (6-8 hrs) | Timeline: Specify in proposal; deliver at handoff

## You Own Everything

> **[RECOMMENDATION — Legal (Lens 1)]** Formalize as IP ownership clause. Add liability/warranty language: "Veteran Vectors is not liable for pricing decisions made using auto-populated data. The system is a tool that assists human judgment; it does not replace it."
> Priority: P2 - Medium | Effort: Low (30 min) | Timeline: Pre-contract

---

## Missing Sections (Recommended Additions)

### User Flow (NEW SECTION — P1 High)

*This section does not exist in the original proposal and should be added.*

**How It Works (5 Steps):**
1. **Trigger:** Mike opens the estimate form and enters aircraft tail number, customer, and estimate type
2. **Auto-Fill:** System populates labor hours (from P2 data or manual entry), tier pricing, standard costs, and parts costs
3. **Review:** Mike sees the draft estimate with auto-populated values highlighted. Sample size (n) shown for labor hour averages. Freshness dates shown for parts costs.
4. **Override:** Mike adjusts any values that need customization. Original auto-populated values preserved in audit log.
5. **Finalize:** Mike approves → estimate is generated in QMX Portal format → confirmation sent via Slack

### Error Handling (NEW SECTION — P0 Critical)

*This section does not exist in the original proposal and must be added.*

Top 5 failure modes and their handling:
1. **No historical data for discrepancy type:** Field shows blank with "No data — enter manually" indicator
2. **QMX API unavailable:** System displays cached data with "Last updated [date]" warning; estimate can proceed with manual values
3. **New/unknown aircraft type:** Tier defaults to "unclassified" with manual tier selection prompt
4. **Duplicate estimate submission:** System detects and blocks duplicate within 5-minute window; displays "Estimate already created" with link to existing
5. **Parts cost data stale (>12 months):** Field shows value with amber "Stale — verify pricing" flag

### Data Validation Rules (NEW SECTION — P1 High)

*This section does not exist in the original proposal and should be added.*

Auto-populated values are checked before display:
- Labor hours: flagged if >2 standard deviations from mean (amber warning)
- Parts costs: flagged if >30% change from previous estimate for same discrepancy type
- Line item total: reconciliation check ensures line items sum to estimate total
- Required fields: aircraft, customer, estimate type, at least one discrepancy line item
- Zero-value check: reject line items with zero labor hours (requires explicit override)

### Security & Access (NEW SECTION — P2 Medium)

*This section does not exist in the original proposal and should be added.*

- **Access control:** Estimate generation restricted to authorized users (Mike + designated backups)
- **Audit trail:** Every estimate logged: who generated it, when, what was auto-populated, what was manually changed
- **Pricing data security:** Tier tables and standard cost data are competitive business information — stored with appropriate access controls
- **QMX credentials:** Stored in n8n credential vault, scoped to minimum required permissions
