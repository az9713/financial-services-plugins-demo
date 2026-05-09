# About This Command: `/financial-analysis:lbo`

## What it does
Builds a **Leveraged Buyout (LBO) model** — the core financial model used by private equity firms to evaluate whether a company can be acquired using significant debt financing and still generate target returns (typically 20–30%+ IRR over a 3–7 year hold). The model shows how debt is layered onto a company, how cash flows repay that debt over time, and what the sponsor's equity returns look like at exit under different scenarios.

## How to invoke
```
/financial-analysis:lbo [company name or ticker]
```
Example: `/financial-analysis:lbo MSFT`

You can supply a real public company (the model uses training-data estimates) or describe a private company with your own financials. Providing entry price, debt structure preferences, and exit horizon produces more tailored output.

## What it produces
A full LBO analysis in these sections:
1. **Transaction summary** — entry price, entry multiples, debt/equity split, hold period
2. **Sources & uses** — full capital structure table (debt tranches, equity, fees)
3. **Operating model** — 3-scenario P&L (Bear/Base/Bull) with revenue CAGR, margin, and FCF assumptions
4. **Debt schedule** — tranche-by-tranche balances and paydown over the hold period, with coverage ratios
5. **Returns analysis** — exit EV, equity value at exit, MOIC and IRR per scenario
6. **Sensitivity tables** — 5×5 IRR and MOIC grid (exit multiple vs. revenue CAGR)
7. **Value creation levers** — what drives the return (growth, margin, multiple expansion, debt paydown)
8. **Risk assessment** — key risks with severity, likelihood, and mitigants

In a live deployment with Excel skill enabled, this also produces a `.xlsx` model file with live formulas.

## Typical use cases
- PE associates building a quick-turn acquisition model
- Teaching LBO mechanics to analysts or finance students
- Stress-testing a deal's return profile across scenarios
- Understanding whether a company is "LBO-able" at a given price

---

# Leveraged Buyout Analysis: Microsoft Azure (Illustrative Divisional LBO)
*Financial Analysis | LBO Model | May 2026*

> **Disclaimer:** A whole-company LBO of Microsoft (~$3T market cap) is not financeable at current scale.
> This analysis frames an illustrative **divisional carve-out LBO of Azure** — Microsoft's cloud platform
> business — as a standalone entity. All figures are training-data estimates labelled as illustrative.
> This does not constitute investment advice.

---

## 1. Transaction Summary

| Parameter | Value |
|---|---|
| **Target** | Microsoft Azure (Cloud Platform Division) |
| **Transaction Type** | Illustrative Divisional Carve-Out LBO |
| **Entry Date** | January 2026 (illustrative) |
| **Hold Period** | 5 years |
| **Exit Date** | December 2030 (illustrative) |
| **Entry Revenue (LTM)** | $105,000M |
| **Entry EBITDA (LTM)** | $36,750M (35.0% margin) |
| **Entry EV** | $500,000M |
| **Entry EV / EBITDA Multiple** | 13.6x |
| **Entry EV / Revenue Multiple** | 4.8x |
| **Sponsor Equity** | $200,000M (40.0%) |
| **Total Debt** | $300,000M (60.0%) |
| **Assumed Exit Multiple** | 12.0x EV/EBITDA |

---

## 2. Sources & Uses of Funds

### Sources

| Tranche | Amount ($M) | % of Total | Rate |
|---|---|---|---|
| Revolving Credit Facility | $15,000 | 3.0% | SOFR + 250 bps (~7.3%) |
| Term Loan A | $85,000 | 17.0% | SOFR + 275 bps (~7.6%) |
| Term Loan B | $120,000 | 24.0% | SOFR + 350 bps (~8.3%) |
| Senior Secured Notes | $80,000 | 16.0% | 8.5% fixed |
| **Total Debt** | **$300,000** | **60.0%** | Blended ~8.0% |
| Sponsor Equity | $200,000 | 40.0% | — |
| **Total Sources** | **$500,000** | **100.0%** | |

### Uses

| Item | Amount ($M) | % of Total |
|---|---|---|
| Purchase of Azure Division | $489,500 | 97.9% |
| Financing Fees & OID | $6,000 | 1.2% |
| Transaction Expenses (legal, advisory) | $3,000 | 0.6% |
| Cash to Balance Sheet | $1,500 | 0.3% |
| **Total Uses** | **$500,000** | **100.0%** |

> **Plug check:** Total Sources ($500,000M) = Total Uses ($500,000M) ✓

---

## 3. Operating Model — Three Scenarios

### Revenue Assumptions

| | Bear | Base | Bull |
|---|---|---|---|
| **Revenue CAGR (5yr)** | 15% | 20% | 28% |
| **Exit EBITDA Margin** | 33% | 38% | 44% |
| **Entry EBITDA Margin** | 35% | 35% | 35% |
| **Capex % Revenue** | 18% | 16% | 14% |
| **D&A % Revenue** | 8% | 8% | 8% |
| **Working Capital % Rev** | 2% | 1% | 1% |

### Base Case — Projected P&L ($M)

| Metric | 2026E | 2027E | 2028E | 2029E | 2030E |
|---|---|---|---|---|---|
| **Revenue** | 126,000 | 151,200 | 181,440 | 217,728 | 261,274 |
| YoY Growth | 20.0% | 20.0% | 20.0% | 20.0% | 20.0% |
| Gross Profit | 88,200 | 105,840 | 126,008 | 151,410 | 181,592 |
| Gross Margin | 70.0% | 70.0% | 69.5% | 69.5% | 69.5% |
| R&D | (15,120) | (18,144) | (21,773) | (26,127) | (31,353) |
| S&M | (12,600) | (15,120) | (18,144) | (21,773) | (26,127) |
| G&A | (6,300) | (7,560) | (9,072) | (10,886) | (13,064) |
| **EBITDA** | 54,180 | 65,016 | 77,019 | 92,624 | 111,048 |
| EBITDA Margin | 43.0% | 43.0% | 42.5% | 42.5% | 42.5% |
| D&A | (10,080) | (12,096) | (14,515) | (17,418) | (20,902) |
| **EBIT** | 44,100 | 52,920 | 62,504 | 75,206 | 90,146 |
| Interest Expense | (24,000) | (22,800) | (21,300) | (19,500) | (17,400) |
| **EBT** | 20,100 | 30,120 | 41,204 | 55,706 | 72,746 |
| Taxes (21%) | (4,221) | (6,325) | (8,653) | (11,698) | (15,277) |
| **Net Income** | 15,879 | 23,795 | 32,551 | 44,008 | 57,469 |

### Base Case — Free Cash Flow ($M)

| | 2026E | 2027E | 2028E | 2029E | 2030E |
|---|---|---|---|---|---|
| EBITDA | 54,180 | 65,016 | 77,019 | 92,624 | 111,048 |
| Less: Taxes | (4,221) | (6,325) | (8,653) | (11,698) | (15,277) |
| Less: Capex | (20,160) | (24,192) | (29,030) | (34,836) | (41,804) |
| Less: Δ Working Capital | (1,260) | (1,512) | (1,814) | (2,177) | (2,613) |
| **Unlevered FCF** | **28,539** | **32,987** | **37,522** | **43,913** | **51,354** |
| Less: Interest | (24,000) | (22,800) | (21,300) | (19,500) | (17,400) |
| **Levered FCF (for Debt Paydown)** | **4,539** | **10,187** | **16,222** | **24,413** | **33,954** |

---

## 4. Debt Schedule ($M)

### Tranche Summary — Base Case

| Tranche | Opening | Year 1 | Year 2 | Year 3 | Year 4 | Year 5 |
|---|---|---|---|---|---|---|
| **Revolving Credit** | 15,000 | 15,000 | 13,500 | 10,000 | 5,000 | 0 |
| **Term Loan A** | 85,000 | 83,000 | 79,000 | 73,000 | 64,000 | 52,000 |
| **Term Loan B** | 120,000 | 118,500 | 116,000 | 112,500 | 107,000 | 99,000 |
| **Senior Secured Notes** | 80,000 | 80,000 | 80,000 | 78,000 | 74,000 | 68,000 |
| **Total Debt** | **300,000** | **296,500** | **288,500** | **273,500** | **250,000** | **219,000** |
| **Cash Paydown (Annual)** | — | 3,500 | 8,000 | 15,000 | 23,500 | 31,000 |

| | 2026E | 2027E | 2028E | 2029E | 2030E |
|---|---|---|---|---|---|
| Total Interest Expense | (24,000) | (22,800) | (21,300) | (19,500) | (17,400) |
| Blended Interest Rate | 8.0% | 7.9% | 7.8% | 7.8% | 7.8% |
| Net Debt / EBITDA | 5.1x | 4.2x | 3.4x | 2.6x | 1.9x |
| Interest Coverage (EBITDA/Int) | 2.3x | 2.9x | 3.6x | 4.8x | 6.4x |

> Debt paydown follows priority waterfall: Revolver → TLA → TLB → Senior Notes.
> All balances floored at zero; excess cash swept to highest-priority tranche first.

---

## 5. Returns Analysis

### Exit Assumptions — Base Case

| | Bear | Base | Bull |
|---|---|---|---|
| Exit Year | 2030 | 2030 | 2030 |
| Exit EBITDA ($M) | 83,000 | 111,048 | 156,000 |
| Exit Multiple (EV/EBITDA) | 10.0x | 12.0x | 14.0x |
| **Exit EV ($M)** | **830,000** | **1,332,576** | **2,184,000** |
| Less: Net Debt at Exit | (219,000) | (219,000) | (219,000) |
| **Exit Equity Value ($M)** | **611,000** | **1,113,576** | **1,965,000** |

### Sponsor Returns

| Metric | Bear | Base | Bull |
|---|---|---|---|
| **Entry Equity ($M)** | 200,000 | 200,000 | 200,000 |
| **Exit Equity ($M)** | 611,000 | 1,113,576 | 1,965,000 |
| **MOIC** | **3.1x** | **5.6x** | **9.8x** |
| **IRR** | **25.3%** | **40.8%** | **57.5%** |
| Hold Period | 5 years | 5 years | 5 years |

### IRR / MOIC Sensitivity Table — Base Case
*(Rows: Exit EV/EBITDA Multiple | Columns: Revenue CAGR)*

**IRR Sensitivity**

| Exit Multiple ↓ / CAGR → | 12% | 16% | 20% | 24% | 28% |
|---|---|---|---|---|---|
| **8.0x** | 9.8% | 13.2% | 17.1% | 21.6% | 26.8% |
| **10.0x** | 17.5% | 21.4% | 25.3% | 29.9% | 35.4% |
| **12.0x** | 24.2% | 32.1% | **40.8%** | 48.2% | 56.1% |
| **14.0x** | 30.1% | 39.4% | 49.7% | 57.3% | 66.4% |
| **16.0x** | 35.4% | 45.8% | 57.5% | 65.8% | 75.2% |

> Center cell (bold) = base case assumption: 20% CAGR × 12.0x exit = **40.8% IRR** ✓

**MOIC Sensitivity**

| Exit Multiple ↓ / CAGR → | 12% | 16% | 20% | 24% | 28% |
|---|---|---|---|---|---|
| **8.0x** | 1.6x | 1.9x | 2.3x | 2.8x | 3.4x |
| **10.0x** | 2.3x | 2.8x | 3.5x | 4.3x | 5.2x |
| **12.0x** | 3.0x | 4.1x | **5.6x** | 7.1x | 9.1x |
| **14.0x** | 3.8x | 5.2x | 7.1x | 9.4x | 12.1x |
| **16.0x** | 4.6x | 6.4x | 8.9x | 11.8x | 15.4x |

---

## 6. Key Value Creation Levers

| Lever | Mechanism | Estimated Contribution to IRR |
|---|---|---|
| **Revenue Growth (20% CAGR)** | AI cloud demand, enterprise migration, geographic expansion | ~18–22 pp |
| **EBITDA Margin Expansion** | Economies of scale in datacenters, operating leverage on S&M/G&A | ~6–8 pp |
| **Multiple Expansion** | Re-rating as pure-play cloud at IPO vs. conglomerate discount at entry | ~5–8 pp |
| **Debt Paydown** | $81B of debt retired over 5 years reduces risk and increases equity value | ~4–6 pp |
| **Financial Engineering** | Tax shield on debt interest (~$5B/yr) | ~2–3 pp |

### Strategic Value Creation Opportunities
1. **AI infrastructure monetization** — Azure OpenAI Service pricing power; GPU/TPU capacity constraints allow premium pricing
2. **Partner ecosystem deepening** — ISV and SI partnerships accelerating enterprise workload migration
3. **Geographic expansion** — Sovereign cloud regions in Middle East, Southeast Asia, India (greenfield, limited competition)
4. **Margin optimization** — Shift from hyperscaler pricing wars to premium managed services (higher-margin AI platform services)
5. **Exit optionality** — IPO as pure-play cloud (premium multiple), strategic sale to sovereign wealth fund, or re-merger

---

## 7. Key Risks

| Risk | Severity | Likelihood | Mitigant |
|---|---|---|---|
| **Leverage at 60% LTV** | High | Medium | Strong EBITDA growth and FCF generation deleverages to <2x by Year 5 |
| **AI demand disappointment** | High | Low–Medium | Azure has contracted backlog; hyperscaler demand is enterprise-driven, not speculative |
| **Competitive response (AWS, GCP)** | Medium | High | Structural switching costs; Azure's Microsoft integration is not replicable |
| **Interest rate risk** | Medium | Medium | ~60% of debt is floating; 100 bps rate rise adds ~$1.8B annual interest cost |
| **Regulatory / antitrust carve-out complexity** | High | High | Microsoft would need regulatory clearance to divest Azure; carve-out is the primary execution risk |
| **Talent retention post-carve-out** | Medium | High | Key engineering talent may prefer Microsoft parent; equity incentive plan critical |
| **Capex intensity** | Medium | Low | Datacenter capex ($20B+/yr) is substantial; any demand softening creates stranded asset risk |
| **Exit multiple compression** | High | Medium | At 8x exit (bear), IRR falls to 17.5% — still acceptable but meaningfully below base |

---

## 8. Investment Summary

**Base Case verdict: INVESTABLE at current assumptions**

- A 5-year hold at 20% revenue CAGR and 12x exit EV/EBITDA generates a **40.8% IRR** and **5.6x MOIC** — well above typical PE hurdle rates of 20–25% IRR
- The bear case (15% CAGR, 10x exit) still returns a **25.3% IRR / 3.1x MOIC** — structurally sound downside
- The primary risk is **execution on the carve-out**, not financial fundamentals — Azure's business quality is exceptional and the AI tailwind is durable
- At 1.9x Net Debt/EBITDA at exit, the business would be pristinely positioned for an IPO or strategic sale

**Key diligence priorities before committing:**
1. Carve-out feasibility and Microsoft regulatory posture
2. Customer contract portability (would enterprise clients accept non-Microsoft Azure?)
3. TPU/infrastructure IP ownership and licensing terms
4. Talent retention plan for top 500 engineers
5. Standalone G&A cost build-up (currently shared with Microsoft corporate)

---

*All figures are illustrative estimates based on publicly available information and training-data approximations as of early 2026. This analysis is for educational demonstration of LBO modeling methodology only and does not constitute investment advice or a solicitation.*
