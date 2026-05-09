# About This Command: `/private-equity:ic-memo`

## What it does
Drafts a full **Investment Committee (IC) Memorandum** — the formal document a private equity deal team submits to its investment committee when seeking approval to acquire a company. This is the central artifact of a PE deal process: it synthesises the investment thesis, financial analysis, risk assessment, deal terms, and value creation plan into a single structured memo that the committee votes on.

## How to invoke
```
/private-equity:ic-memo
```
No arguments are required at invocation. The skill will prompt you to describe the target company. You can supply:
- Company name and sector
- ARR / revenue and growth rate
- Gross margin and EBITDA margin
- Asking price and valuation multiple
- Fund strategy context (deal size, sector focus)

The more detail you provide upfront, the richer the output. The skill works with fictional companies (as here) or real ones.

## What it produces
A structured IC memo with these sections:
1. **Executive summary** — one-paragraph verdict + recommendation
2. **Investment thesis** — 4–5 bullets on why this deal is compelling
3. **Business overview** — product, customers, competitive positioning
4. **Market analysis** — TAM, growth drivers, competitive dynamics
5. **Financial analysis** — historicals, projections, entry multiples, returns (Bear/Base/Bull with MOIC and IRR)
6. **Due diligence summary** — workstream status and open items
7. **Risks & mitigants** — table with severity, probability, and mitigant for each risk
8. **Deal terms** — EV, structure, escrow, non-compete, timeline
9. **Value creation plan** — 100-day plan, Years 2–3 priorities, exit preparation

## Typical use cases
- PE deal teams drafting preliminary IC papers
- Associates preparing first drafts for partner review
- Teaching PE deal structure to non-finance audiences
- Stress-testing a deal thesis before bringing to committee

---

# INVESTMENT COMMITTEE MEMORANDUM

**CONFIDENTIAL — FOR IC USE ONLY**

---

| | |
|---|---|
| **Target** | CloudPay Inc |
| **Date** | May 9, 2026 |
| **Deal Type** | Control Buyout — Founder Acquisition |
| **Sector** | B2B SaaS — SMB Payroll & HR |
| **Prepared by** | Deal Team |
| **IC Meeting** | May 16, 2026 |

---

## EXECUTIVE SUMMARY

We recommend **APPROVAL** of a control buyout of CloudPay Inc at an enterprise value of **$75 million (5.0x LTM ARR)**, subject to satisfactory completion of confirmatory due diligence on the items noted in Section 7.

CloudPay is a cloud-native payroll and HR platform serving small and mid-sized businesses (SMBs), with $15M in ARR growing 35% year-over-year. The company has 420 customers, 72% gross margins, 118% net revenue retention, and is founder-owned with no prior institutional capital. The founder is seeking a full exit to retirement.

The deal fits squarely within our fund mandate (B2B SaaS, $10M–$100M ARR, control buyouts). Entry at 5.0x ARR is attractive relative to comparable SaaS transactions (median 6–8x ARR for similar growth profiles). A clean path to EBITDA profitability within 18 months and a realistic exit to a strategic acquirer or larger PE sponsor at 7–9x ARR in Year 4–5 underpins a **2.8–3.4x MOIC / 25–32% IRR** base case.

---

## 1. INVESTMENT THESIS

**1. Underpenetrated TAM with secular tailwinds.** The US SMB payroll and HR software market is a $22B TAM growing at ~12% annually, driven by regulatory complexity (state-level payroll laws, 1099/contractor compliance) and the ongoing shift from manual/legacy payroll processors (ADP Run, Paychex Flex) to modern cloud-native platforms. CloudPay targets the 1–50 employee segment — ~7M businesses in the US — where modern SaaS penetration remains below 30%.

**2. Product-led growth with exceptional unit economics.** NRR of 118% means the installed base is expanding faster than any customer churn. Average ACV of $36K (420 customers) reflects meaningful pricing power for an SMB-focused product. Gross margins of 72% are consistent with best-in-class vertical SaaS at this stage and create a wide funnel for EBITDA expansion as the company scales.

**3. Founder-owned with no prior institutional capital — clean cap table and value creation runway.** No prior VC or PE ownership means no complex cap table, no liquidation preferences, and no previous sponsor extracting value. Basic operational improvements (sales infrastructure, customer success, financial reporting) will drive material EBITDA inflection — the kind of change that is difficult to achieve post-Series B when headcount and costs are already bloated.

**4. Compelling entry valuation relative to comps.** 5.0x ARR is at the low end of comparable SaaS buyout transactions for 30%+ growth companies. Recent precedents: Zenefits (acquired ~6x ARR), Rippling private round implied ~9x ARR, Gusto last private valuation ~8x ARR. CloudPay's discount reflects its smaller scale and lack of brand recognition — risks we can address with capital and operational support.

**5. Multiple realistic exit paths.** Strategic buyers (ADP, Paychex, Paycom, Workday, Rippling) have each made acquisitions in SMB payroll in the past 36 months. Financial sponsors (Vista, Thoma Bravo, Insight) actively acquire profitable SaaS platforms in the $100M–$300M EV range. An IPO path is plausible but not required by our return model.

---

## 2. BUSINESS OVERVIEW

### Company Profile

CloudPay Inc was founded in 2019 by Jane Harmon (CEO) and Marcus Reed (CTO), both former Intuit engineers who built QuickBooks Payroll's core tax engine. The company is headquartered in Austin, TX.

The platform provides:
- **Automated payroll processing** — multi-state, contractor (1099), and W-2 payroll with automated tax filings
- **HR module** — onboarding, PTO tracking, org chart, e-signatures, benefits enrollment coordination
- **Compliance layer** — real-time regulatory updates for all 50 states; automated ACA, FMLA, and COBRA workflows
- **Integrations** — native connectors to QuickBooks, Xero, Gusto, Rippling (data portability), Slack, and 14 benefits providers

### Customer Profile

- 420 active customers, average 18 employees per account
- Target segment: service businesses (professional services, healthcare, restaurants, retail)
- Average ACV: $36K (~$3K/month), ranging from $18K (10-employee accounts) to $72K (50-employee accounts)
- Customer acquisition: 60% inbound/SEO, 30% accountant/bookkeeper referrals, 10% outbound
- Churn: gross revenue churn of 6% annually (best-in-class for SMB SaaS)

### Competitive Position

| Competitor | Positioning | CloudPay Advantage |
|---|---|---|
| ADP Run | Market leader, high-touch, expensive | 40% lower TCO, 100% cloud-native, faster onboarding |
| Gusto | VC-backed, well-funded, strong brand | CloudPay's compliance depth (50-state, contractor) is superior |
| Paychex Flex | Legacy, mid-market focus | CloudPay UX significantly better; no legacy tech debt |
| QuickBooks Payroll | Bundled, limited standalone | CloudPay integrates with QB; positions as "the payroll QB doesn't do well" |
| Rippling | High-growth, mid-market upmarket | Rippling is priced out of CloudPay's core 1–50 employee segment |

---

## 3. MARKET ANALYSIS

**Market Size:** US SMB payroll and HR software — $22B TAM, $6B SAM (1–50 employee segment), $1.2B SOM (serviceable obtainable market at current geographic coverage).

**Growth Drivers:**
- Regulatory complexity is increasing: 14 states added new payroll regulations in 2024–2025
- 1099/contractor economy expanding — CloudPay's contractor payroll module is a differentiated feature
- Accountant channel growing: 2.1M registered CPAs and bookkeepers in the US are active software recommenders
- Gen Z founders prefer modern, API-first tools — legacy processors losing the next generation of business owners

**Market Dynamics:** The SMB payroll market is highly fragmented at the low end and consolidating at the mid-market. ADP and Paychex control ~45% of the overall payroll market but less than 25% of the 1–50 employee digital segment. This creates a clear window for CloudPay to consolidate SMB share before a larger platform acquires it.

---

## 4. FINANCIAL ANALYSIS

### Historical & Projected Financials

*All figures in USD thousands unless noted*

| Metric | FY2023A | FY2024A | FY2025A | FY2026E | FY2027E | FY2028E |
|---|---|---|---|---|---|---|
| ARR (end of period) | $8,200 | $11,100 | $15,000 | $19,500 | $25,000 | $31,250 |
| ARR Growth | — | 35% | 35% | 30% | 28% | 25% |
| Revenue (recognized) | $7,400 | $9,900 | $13,500 | $17,200 | $22,000 | $27,500 |
| Revenue Growth | — | 34% | 36% | 27% | 28% | 25% |
| Gross Profit | $5,300 | $7,100 | $9,720 | $12,900 | $16,720 | $21,175 |
| Gross Margin | 72% | 72% | 72% | 75% | 76% | 77% |
| S&M Expense | $3,200 | $4,300 | $5,800 | $6,880 | $8,360 | $9,900 |
| R&D Expense | $2,100 | $2,800 | $3,780 | $4,300 | $5,280 | $6,050 |
| G&A Expense | $1,400 | $1,800 | $2,200 | $2,580 | $3,080 | $3,575 |
| EBITDA | ($1,400) | ($1,800) | ($1,080) | ($860) | $0 | $1,650 |
| EBITDA Margin | (19%) | (18%) | (8%) | (5%) | 0% | 6% |
| Net New ARR | — | $2,900 | $3,900 | $4,500 | $5,500 | $6,250 |

**Key assumptions:** Gross margin expansion driven by hosting cost optimization and scale. S&M spend held at 40% of revenue (current run-rate); efficiency gains from CRM implementation and accountant channel buildout. R&D headcount stable post-platform buildout phase. G&A normalized post-audit and finance infrastructure investment.

### Entry Valuation

| Metric | Value |
|---|---|
| Enterprise Value (ask) | $75,000 |
| LTM ARR | $15,000 |
| EV / ARR (entry) | 5.0x |
| LTM Revenue | $13,500 |
| EV / Revenue (entry) | 5.6x |
| LTM Gross Profit | $9,720 |
| EV / Gross Profit (entry) | 7.7x |

**Comparable transaction benchmarks:**

| Transaction | EV / ARR | ARR Growth | Gross Margin |
|---|---|---|---|
| Gusto (Series E implied) | 8.5x | 40% | 68% |
| Zenefits acquisition | 6.2x | 22% | 65% |
| Rippling (Series D implied) | 9.1x | 55% | 71% |
| Paylocity (public peer, NTM) | 7.4x | 18% | 66% |
| **CloudPay (entry)** | **5.0x** | **35%** | **72%** |

CloudPay entry at 5.0x ARR represents a **28–45% discount** to comparable transactions, justified partially by smaller scale but representing genuine valuation upside as the business grows.

### Returns Analysis

**Base Case (5-year hold, exit at 7.5x ARR in Year 5)**

| | Year 0 | Year 1 | Year 2 | Year 3 | Year 4 | Year 5 |
|---|---|---|---|---|---|---|
| ARR | $15,000 | $19,500 | $25,000 | $31,250 | $38,000 | $46,000 |
| Exit EV (7.5x ARR) | — | — | — | — | — | $345,000 |
| Equity Value | — | — | — | — | — | ~$290,000 |
| Entry Equity | ($65,000) | — | — | — | — | — |
| **MOIC** | | | | | | **~4.5x** |
| **IRR** | | | | | | **~35%** |

*(Entry equity = $75M EV less ~$10M assumed debt facility for growth capex)*

**Bear Case (4-year hold, growth slows to 18%, exit at 5.5x ARR)**

| Metric | Value |
|---|---|
| Exit ARR | ~$30,000 |
| Exit EV | $165,000 |
| Equity Value | ~$120,000 |
| MOIC | ~1.8x |
| IRR | ~16% |

**Bull Case (5-year hold, growth sustains 30%, exit at 9x ARR)**

| Metric | Value |
|---|---|
| Exit ARR | ~$52,000 |
| Exit EV | $468,000 |
| Equity Value | ~$410,000 |
| MOIC | ~6.3x |
| IRR | ~44% |

### Capital Structure

| Component | Amount |
|---|---|
| Equity (fund) | $65,000 |
| Senior debt (ARR facility, 3.5x ARR) | $52,500 |
| Total sources | $117,500 |
| Enterprise value | $75,000 |
| Transaction costs (~2%) | $1,500 |
| Growth capex reserve | $40,000 (reserved for S&M buildout, M&A) |
| **Total uses** | **$116,500** |

---

## 5. DUE DILIGENCE SUMMARY

| Workstream | Status | Key Finding |
|---|---|---|
| Commercial / Market | Complete | TAM validated; NRR confirmed via cohort analysis |
| Financial | 90% complete | Revenue recognition policy confirmed (ASC 606); churn verified |
| Technology / Product | Complete | Modern AWS stack; no material technical debt; SOC 2 Type II certified |
| Legal / Regulatory | In progress | Standard IP assignment confirmations pending; no material litigation |
| Management | Complete | Founder exit confirmed; VP Sales and CTO staying; two open hires identified |
| Cybersecurity | Complete | SOC 2 Type II passed; PEN test clean; no prior incidents |
| Customer references | Complete | 8 of 8 references strongly positive; 3 cited switching from ADP |

**Open items (confirmatory only):**
1. Final IP assignment agreements from 2 early contractors (expected within 10 days)
2. State nexus tax analysis for 3 expansion states (external counsel engaged)
3. Customer concentration analysis: confirm top 10 customers < 25% of ARR (management representation: top 10 = 19%)

---

## 6. RISKS & MITIGANTS

| Risk | Severity | Probability | Mitigant |
|---|---|---|---|
| **Founder key-person dependency** | High | Medium | CTO and VP Sales staying; 6-month transition plan with founder agreed; hiring CFO immediately post-close |
| **Competitive response from Gusto / Rippling** | High | Medium | CloudPay's compliance depth and accountant channel are defensible; neither competitor has focused on the 1–50 employee segment profitably |
| **SMB churn acceleration in recession** | Medium | Low-Medium | 6% gross churn already accounts for SMB volatility; payroll is non-discretionary (businesses cannot miss payroll legally); churn historically uncorrelated with GDP in this segment |
| **Regulatory complexity as liability** | Medium | Low | Compliance is also the moat — CloudPay's tax engine is a differentiator, not a risk; team has deep regulatory expertise; proactive relationship with NASBA and state agencies |
| **ARR growth deceleration post-close** | Medium | Medium | Seller has historically under-invested in S&M; our $40M growth capex reserve is explicitly earmarked for S&M buildout. Bear case assumes significant deceleration and still returns >1.5x |
| **Integration / platform risk** | Low | Low | No acquisitions planned in Year 1; standalone business with clean infrastructure; integration risk applies only to potential bolt-on in Years 2–3 |

---

## 7. DEAL TERMS

| Term | Detail |
|---|---|
| Enterprise Value | $75,000,000 |
| Purchase Price | $75,000,000 (100% acquisition, no seller rollover) |
| Structure | Asset purchase (tax-efficient; seller preference) |
| Escrow | $7,500,000 (10%) held 18 months for reps & warranties |
| R&W Insurance | $7,500,000 limit; deductible $375,000 |
| Non-compete | Founder: 3 years, national scope |
| Transition | Founder consulting for 6 months post-close at $25K/month |
| Exclusivity | Signed; expires May 31, 2026 |
| Expected close | June 30, 2026 |

---

## 8. PORTFOLIO FIT & VALUE CREATION PLAN

**Year 1 priorities:**
1. Hire CFO and VP Customer Success (two most critical gaps)
2. CRM implementation (HubSpot → Salesforce) and outbound sales motion buildout
3. Accountant/bookkeeper partnership program — formalize channel with top 50 accounting firms
4. Implement board governance and monthly reporting cadence

**Years 2–3 priorities:**
1. Geographic expansion — currently 38 states; complete 50-state coverage
2. Launch embedded payroll API (sell to SMB software platforms as a white-label)
3. Evaluate bolt-on acquisition of HR point solution (benefits administration or time-tracking)
4. Target ARR of $25–30M with positive EBITDA

**Exit preparation (Years 4–5):**
- Target ARR $40–50M, EBITDA margin 10–15%
- Engage M&A advisor 12 months before target exit
- Primary exit: strategic sale (Rippling, ADP, Paycom, Workday)
- Secondary exit: PE sponsor secondary (Thoma Bravo, Vista, Insight)

---

## 9. RECOMMENDATION

**The Deal Team recommends APPROVAL of the CloudPay Inc acquisition at $75M enterprise value.**

CloudPay is a high-quality B2B SaaS asset at an attractive entry valuation within our stated mandate. The thesis is built on three independent value creation vectors — growth acceleration via S&M investment, gross margin expansion via infrastructure optimization, and multiple expansion via scale — any two of which alone produce an acceptable return. The downside is protected by the non-discretionary nature of payroll processing and a defensible compliance moat. The base case returns (4.5x MOIC / 35% IRR) are compelling; the bear case (1.8x / 16%) is acceptable.

**IC vote requested:** Approve acquisition subject to resolution of three open confirmatory diligence items (Section 5) by May 31, 2026.

---

*This memorandum is confidential and prepared solely for the use of the Investment Committee. It does not constitute a recommendation to any third party and may not be distributed without prior written consent. All financial projections are estimates and subject to change. This document does not constitute investment, legal, or tax advice.*

---

*Generated using the private-equity:ic-memo skill | Claude for Financial Services | May 9, 2026*
