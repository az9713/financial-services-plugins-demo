# About This Command: `/fund-admin:gl-recon`

## What it does
Runs a **General Ledger (GL) Reconciliation** — the core month-end process in fund administration where the fund's internal accounting records (GL) are compared line-by-line against the prime broker's statement to identify and explain any discrepancies (called "breaks"). Every hedge fund and PE fund must complete this reconciliation before issuing NAV calculations and LP statements. Unexplained breaks can indicate errors, failed trades, or fraud — so resolution is mandatory before close.

## How to invoke
```
/fund-admin:gl-recon
```
No arguments required. The skill prompts you to describe the reconciliation scenario. Useful inputs:
- Fund name and period (month-end date)
- GL balance vs. prime broker balance (and the difference)
- Any known or suspected breaks and their approximate amounts
- Close deadline and LP statement issuance date

The skill works with a simple "here's the gap" description or a detailed line-by-line break list.

## What it produces
A structured GL reconciliation report with:
1. **Reconciliation summary** — GL vs. prime broker totals, gross difference, break count, match rate
2. **Break itemisation** — for each break: root cause analysis, likely cause tag (Timing / FX / Duplicate / Unknown), and recommended resolution with a journal entry where applicable
3. **Full break report** — sortable table of all breaks with break ID, security, type, amounts, and status
4. **Escalation section** — which breaks require CFO or senior ops sign-off, with draft escalation note
5. **NAV impact assessment** — which breaks affect reported NAV and by how much, with recommended adjustments
6. **Sign-off checklist** — owner-assigned action items with deadlines sequenced against the close calendar

## Common break types covered
- **Timing breaks** — accrual-basis (GL) vs. cash-basis (prime broker) cut-off differences (e.g. dividend accruals, unsettled trades)
- **FX rate mismatches** — different rate sources between fund admin and prime broker for foreign-currency positions
- **Duplicate postings** — same trade booked twice in GL
- **Failed trades** — trade booked in GL but rejected at prime broker
- **Corporate action errors** — stock splits, spin-offs, or dividends applied on one side only

## Typical use cases
- Fund administrators preparing month-end close packages
- Controllers reviewing and signing off on NAV before LP statements
- Teaching new fund accountants break investigation methodology
- Demonstrating the operational rigour of fund administration workflows

---

# GL Reconciliation Report
## Apex Capital Partners Fund III LP
**Period:** Month-End April 30, 2026
**Asset Class:** Equity Long Book
**Prepared:** May 2, 2026
**Close Deadline:** May 5, 2026 | **LP Statements:** May 15, 2026
**Status:** ⚠ BREAK — REQUIRES RESOLUTION BEFORE CLOSE

---

## 1. Reconciliation Summary

| | Amount (USD) |
|---|---|
| **GL Balance — Equity Long Book** | $487,200,000 |
| **Prime Broker Statement — Equity Long Book** | $484,900,000 |
| **Gross Difference (GL overstated)** | **$2,300,000** |

| Break Bucket | Count | Amount (USD) | % of Total Break |
|---|---|---|---|
| Timing break — Accrued dividend (AAPL) | 1 | $1,400,000 | 60.9% |
| FX rate mismatch — European positions | 1 | $600,000 | 26.1% |
| Unreconciled residual — Under investigation | 1 | $300,000 | 13.0% |
| **Total** | **3** | **$2,300,000** | **100%** |

**Matched balance:** $484,900,000 (99.53% of GL balance)
**Break as % of NAV:** ~0.47% (below typical 1% materiality threshold but above $500K escalation trigger)

---

## 2. Break Itemization & Root Cause Analysis

---

### Break #1 — Accrued Dividend, Apple Inc. (AAPL)

| Field | GL (Fund Admin) | Prime Broker Statement | Delta |
|---|---|---|---|
| Security | AAPL US Equity | AAPL US Equity | — |
| Break Type | Timing break | | |
| GL Amount | $1,400,000 | $0 | **$1,400,000** |
| Direction | GL overstated | | |
| Posting Date (GL) | April 28, 2026 | — | |
| Expected Settlement | May 5, 2026 | | |

**Root Cause:** Apple Inc. declared a quarterly dividend of $0.25/share with a record date of April 28, 2026 and a pay date of May 5, 2026. The fund admin GL accrued the dividend income on ex-date (April 28) per GAAP accrual accounting. The prime broker statement reflects cash-basis posting — the dividend will only appear on the prime broker statement upon settlement on May 5, 2026.

**Likely Cause Tag:** `Timing` — trade-date vs. settle-date posting / accrual-basis vs. cash-basis cut-off mismatch.

**Expected Resolution:** Self-correcting by May 5, 2026 when the dividend settles. No adjustment required to the GL. Document as a known timing item.

**NAV Impact:** The GL treatment is correct under GAAP. NAV should reflect the accrued dividend receivable. Confirm the $1,400,000 is also reflected as a receivable on the balance sheet (DR Dividend Receivable / CR Dividend Income) to avoid double-counting.

**Recommended Action:**
1. Confirm fund position size in AAPL (implied position: ~5,600,000 shares at $0.25/share)
2. Verify dividend record date and pay date against AAPL IR disclosure
3. Document as a timing item in the sign-off package
4. Expect auto-clearance on the May 5 prime broker statement — schedule a verification check

---

### Break #2 — FX Translation Difference, European Long Positions

| Field | GL (Fund Admin) | Prime Broker Statement | Delta |
|---|---|---|---|
| Scope | European equity long book (EUR-denominated) | Same | — |
| Break Type | Amount break — FX rate mismatch | | |
| GL Base Amount (USD) | *(higher by $600,000)* | | |
| Local Amounts | Agree | Agree | $0 |
| Base Amounts | Differ | | **$600,000** |
| GL FX Rate (EUR/USD) | 1.0842 | 1.0776 | 0.0066 |
| Prime Broker Rate | 1.0776 | | |

**Root Cause:** The fund admin GL translated EUR-denominated European equity positions using the WM/Reuters 4PM London fix rate for April 30, 2026 (EUR/USD 1.0842). The prime broker applied their internal end-of-day rate (EUR/USD 1.0776), which is the NY 4PM close rate. The two rates differ by 0.61% (66 pips), producing a $600,000 base-currency translation difference on the European long book (implied EUR exposure: ~€90.7M).

**Likely Cause Tag:** `FX` — rate-source mismatch (WM/Reuters London 4PM vs. prime broker NY close).

**Expected Resolution:** This is a persistent structural break due to the fund admin and prime broker using different FX rate sources. Resolution options:

| Option | Action | Timeline |
|---|---|---|
| **Option A (Preferred)** | Align to a single rate source — agree with prime broker to use WM/Reuters 4PM London as the standard month-end rate. Requires prime broker system configuration change. | 1–2 months |
| **Option B (Interim)** | GL team manually overrides to match prime broker rate for month-end close. Document override and impact. | Before May 5 close |
| **Option C (Disclosure)** | Accept as a known structural break, document methodology difference in close package, and monitor for growth. | Immediate |

**Recommended Action for April 30 Close:**
1. Apply Option B: Override GL FX rate to 1.0776 (prime broker rate) for month-end reporting
2. Post a reclassification journal entry: DR Unrealized FX Translation Loss $600,000 / CR Equity Long Positions $600,000
3. Open a standing issue ticket with prime broker operations to align on rate source going forward (Option A)
4. Disclose FX methodology in the LP letter footnotes

**NAV Impact:** $600,000 reduction to NAV if GL is adjusted to prime broker rate. Immaterial at fund level (<0.15% of NAV) but must be resolved before LP statement issuance.

---

### Break #3 — Unreconciled Residual

| Field | GL (Fund Admin) | Prime Broker Statement | Delta |
|---|---|---|---|
| Break Type | GL only — no matching subledger entry | | |
| GL Amount | $300,000 | $0 | **$300,000** |
| Identified Cause | **Unknown** | | |
| Age | First observed April 30, 2026 | | |

**Root Cause:** A $300,000 debit balance appears in the GL equity long account with no corresponding position or transaction in the prime broker statement. Preliminary investigation has not identified the source. Possible hypotheses:

| Hypothesis | Probability | Test |
|---|---|---|
| Failed trade — buy-side trade booked in GL, rejected at prime broker | Medium | Pull failed trade report from OMS for April 28–30 |
| Duplicate posting — same trade entered twice in GL | Medium | Search GL for duplicate journal entries on AAPL or other large-cap positions |
| Mapping error — position in a different account mapped incorrectly to equity long | Low | Review GL account mapping table for recent changes |
| Corporate action error — stock split, spin-off, or rights issue applied on one side only | Low | Review corporate action calendar for April |
| Data feed error — stale position from a prior day not cleared | Low | Compare April 29 vs. April 30 GL snapshot |

**Recommended Action:**
1. **IMMEDIATE:** Pull OMS failed trade report for April 28–30
2. Search GL for duplicate journal line IDs on April 28–30 (query: same security, same amount, within 24 hours)
3. Review corporate action calendar for any April activity affecting the fund's positions
4. If not resolved by May 3 (48 hours before close deadline), **ESCALATE** (see Section 4)

**NAV Impact:** $300,000 GL overstatement. If unresolved at close, must be written off or reserved pending investigation. Do not issue LP statements with an unexplained break of this size.

---

## 3. Full Break Report (Sorted by Absolute Delta, Descending)

| # | Break ID | Security / Scope | Break Type | Likely Cause | GL Amount | PB Amount | Delta | Status |
|---|---|---|---|---|---|---|---|---|
| 1 | BRK-2604-001 | AAPL US Equity — Dividend | Timing | Timing / Accrual vs. Cash | $1,400,000 | $0 | $1,400,000 | Known — Self-clearing May 5 |
| 2 | BRK-2604-002 | EUR Equity Long Book | Amount | FX Rate Source Mismatch | Overstated $600K | — | $600,000 | Known — Adjust GL or disclose |
| 3 | BRK-2604-003 | Unknown Position / Entry | GL Only | Under Investigation | $300,000 | $0 | $300,000 | ⚠ Escalation Required |
| | | | | **TOTAL** | | | **$2,300,000** | |

---

## 4. Escalation

### Items Requiring Escalation

| Break | Escalate To | Deadline | Reason |
|---|---|---|---|
| BRK-2604-003 — $300K unreconciled | CFO + Head of Operations | May 3, 2026 EOD | Unexplained break >$100K policy threshold; must resolve before close |
| BRK-2604-002 — FX methodology | Head of Fund Admin + Prime Broker Operations | May 10, 2026 | Structural issue requiring counterparty alignment; not acceptable to recur monthly |

### Escalation Note — BRK-2604-003

> **TO:** [CFO] / [Head of Operations]
> **FROM:** Fund Administration
> **DATE:** May 2, 2026
> **RE:** Unexplained $300,000 GL break — Apex Capital Partners Fund III LP
>
> A $300,000 debit balance appearing in the equity long account of Fund III has no corresponding position or transaction in the April 30 prime broker statement. Root cause investigation is underway. If the break cannot be explained and resolved by May 3 EOD, we recommend either (a) reversing the GL entry pending investigation and posting a suspense liability, or (b) reserving the amount against NAV with full disclosure in the LP package. Please advise on preferred treatment.

---

## 5. NAV Impact Assessment

| Item | GL Treatment | Impact on NAV | Recommended Adjustment |
|---|---|---|---|
| AAPL Dividend Accrual ($1.4M) | Correct per GAAP | No adjustment | None — document as timing |
| FX Rate Mismatch ($600K) | GL overstated | Reduce NAV by $600K | Post reclassification entry |
| Unreconciled Residual ($300K) | GL overstated | Reduce NAV by $300K (if not explained) | Reserve / reverse pending investigation |
| **Net NAV Adjustment** | | **$(900,000)** | |

**Adjusted NAV (post-resolution estimate):** $484,900,000 + $1,400,000 = **$486,300,000**
*(Timing item remains in NAV as receivable; FX and residual adjusted out)*

---

## 6. Sign-Off Checklist

| Item | Owner | Status | Deadline |
|---|---|---|---|
| BRK-2604-001: Document AAPL dividend timing item | Fund Admin Analyst | ☐ Pending | May 3 |
| BRK-2604-001: Verify dividend pay date and position size | Fund Admin Analyst | ☐ Pending | May 3 |
| BRK-2604-002: Post FX reclassification journal entry | Senior Fund Accountant | ☐ Pending | May 4 |
| BRK-2604-002: Open prime broker FX alignment ticket | Head of Fund Admin | ☐ Pending | May 5 |
| BRK-2604-003: Run OMS failed trade report | Operations | ☐ Pending | May 3 EOD |
| BRK-2604-003: Search GL for duplicate entries | Fund Admin Analyst | ☐ Pending | May 3 EOD |
| BRK-2604-003: Escalate to CFO if unresolved | Head of Fund Admin | ☐ Pending | May 3 EOD |
| Final recon sign-off — all breaks resolved or documented | CFO / Controller | ☐ Pending | May 5 |
| LP statements issued | Investor Relations | ☐ Pending | May 15 |

---

## 7. Methodology Notes

- **Data Sources:** Fund admin GL extract (Advent Geneva) vs. prime broker statement (Goldman Sachs Prime Services), April 30, 2026
- **Matching Key:** Security identifier (ISIN) + account + posting date
- **Tolerance:** $0.01 on amounts (zero tolerance on quantity)
- **FX Source (GL):** WM/Reuters 4PM London closing rates
- **FX Source (Prime Broker):** Prime broker internal NY 4PM close rates
- **Matched Balance:** $484,900,000 (99.53% of GL total)
- **Break identification methodology:** Full outer join on security + account key; breaks classified per fund admin reconciliation policy v2.3

---

*This reconciliation report is prepared for internal fund administration purposes only. All figures are subject to final audit and sign-off. This document does not constitute a final NAV determination.*
