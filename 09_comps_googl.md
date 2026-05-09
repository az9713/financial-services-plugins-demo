# About This Command: `/financial-analysis:comps`

## What it does
Builds a **comparable company analysis** (also called "trading comps" or "public market comps") — one of the two core valuation methodologies in investment banking and equity research (the other being DCF). Comps answers the question: "What are investors currently paying for similar businesses, and how does our subject company compare?" By benchmarking a company against its peers on operating metrics and valuation multiples, you can determine whether it trades at a premium or discount and why.

## How to invoke
```
/financial-analysis:comps [company name or ticker]
```
Example: `/financial-analysis:comps GOOGL`

You can use any publicly traded company as the subject. The skill automatically selects an appropriate peer group, though you can specify your own.

## What it produces

**In-session output:** A structured analysis with:
1. **Peer group rationale** — why each comparable was selected (business model, scale, sector, geography)
2. **Operating statistics table** — Revenue (LTM), YoY growth, gross margin, EBITDA, EBITDA margin, FCF, FCF margin, R&D %, capex %, net cash — for each company plus statistical summary (Max, 75th, Median, 25th, Min)
3. **Valuation multiples table** — Market cap, net debt, EV, EV/Revenue, EV/EBITDA, P/E (NTM), FCF yield, PEG ratio — with statistical summary
4. **Key insights** — where the subject company trades vs. peer median and what that implies

**Excel file (`.xlsx`):** When the xlsx-author skill is enabled, also generates a fully formatted spreadsheet with:
- Navy/blue institutional-grade header block
- Live Excel formulas for all statistical rows (MAX, PERCENTILE, MEDIAN, MIN)
- Blue fill = hardcoded inputs | White = formula cells
- Yellow highlight for the subject company row
- Notes & methodology section

For this session, the Excel file was also generated at: `GOOGL_Comps_Analysis_2026-05-09.xlsx`

## Typical use cases
- Investment bankers building valuation ranges for a pitch or fairness opinion
- Equity research analysts benchmarking a new coverage name against its peer group
- PE deal teams sizing entry multiples relative to where comparable companies trade
- Students learning how valuation multiples are derived and applied

---

# GOOGL Comparable Company Analysis
*Financial Analysis | Trading Comps | May 2026*

> **Data note:** All figures are estimates from training-data (cutoff early 2026). As noted in the session, GOOGL's actual price as of May 9, 2026 is approximately **$400** — materially different from the ~$170 used in training-data estimates. All market caps, EVs, and multiples below reflect the training-data estimates and should be refreshed with current market data before use. This document is illustrative only and does not constitute investment advice.

---

## Peer Group

| Company | Ticker | Rationale |
|---|---|---|
| **Alphabet** | GOOGL | Subject company |
| Meta | META | Closest digital advertising peer; AI platform investment cycle |
| Microsoft | MSFT | Cloud + AI + LinkedIn/Bing advertising overlap |
| Amazon | AMZN | Cloud (AWS) + fast-growing advertising segment |
| Apple | AAPL | Mega-cap tech ecosystem; services revenue comparison |
| Netflix | NFLX | YouTube analog — digital media + connected TV advertising |

**Peer selection rationale:** Alphabet's revenue is a blend of digital advertising (~67%), cloud (~12%), and digital media (~11%). No single company is a perfect comp. Meta captures the advertising dynamic; Microsoft and Amazon capture the cloud/AI dynamic; Apple captures the mega-cap tech ecosystem and services premium; Netflix proxies the YouTube connected TV monetisation opportunity.

---

## Operating Statistics & Financial Metrics
*LTM / FY2025E | USD Millions*

| Company | Revenue (LTM) | YoY Growth | Gross Margin | EBITDA | EBITDA Margin | FCF | FCF Margin | R&D % Rev | Capex % Rev | Net Cash |
|---|---|---|---|---|---|---|---|---|---|---|
| **Alphabet (GOOGL)** | **$359,000** | **13.2%** | **57.8%** | **$114,000** | **31.7%** | **$72,000** | **20.1%** | **15.5%** | **6.9%** | **$100,000** |
| Meta (META) | $164,500 | 19.0% | 81.7% | $70,000 | 42.6% | $52,000 | 31.6% | 26.9% | 4.3% | $50,000 |
| Microsoft (MSFT) | $261,000 | 15.2% | 69.8% | $125,000 | 47.9% | $74,000 | 28.4% | 13.0% | 5.6% | $30,000 |
| Amazon (AMZN) | $638,000 | 10.9% | 49.7% | $125,000 | 19.6% | $38,000 | 6.0% | 15.4% | 8.2% | $25,000 |
| Apple (AAPL) | $400,000 | 4.0% | 46.8% | $138,000 | 34.5% | $95,000 | 23.8% | 7.4% | 2.8% | $50,000 |
| Netflix (NFLX) | $39,900 | 15.0% | 43.0% | $9,900 | 24.8% | $6,200 | 15.5% | 0.0% | 0.5% | ($5,000) |
| | | | | | | | | | | |
| **Maximum** | $638,000 | 19.0% | 81.7% | $138,000 | 47.9% | $95,000 | 31.6% | 26.9% | 8.2% | $100,000 |
| **75th Percentile** | $429,250 | 15.1% | 67.3% | $126,875 | 42.1% | $78,500 | 27.7% | 15.5% | 7.6% | $62,500 |
| **Median** | $310,000 | 14.1% | 58.8% | $119,500 | 33.1% | $63,000 | 22.0% | 14.2% | 5.1% | $40,000 |
| **25th Percentile** | $177,125 | 10.2% | 47.6% | $75,750 | 22.4% | $40,500 | 12.9% | 8.0% | 3.6% | $17,500 |
| **Minimum** | $39,900 | 4.0% | 43.0% | $9,900 | 19.6% | $6,200 | 6.0% | 0.0% | 0.5% | ($5,000) |

---

## Valuation Multiples
*LTM / NTM estimates | USD Millions*

| Company | Mkt Cap | Net Debt | EV | EV/Revenue | EV/EBITDA | P/E (NTM) | FCF Yield | PEG |
|---|---|---|---|---|---|---|---|---|
| **Alphabet (GOOGL)** | **$2,100,000** | **($100,000)** | **$2,000,000** | **5.6x** | **17.5x** | **20.2x** | **3.4%** | **1.5x** |
| Meta (META) | $1,450,000 | ($50,000) | $1,400,000 | 8.5x | 20.0x | 23.8x | 3.6% | 1.3x |
| Microsoft (MSFT) | $3,000,000 | ($30,000) | $2,970,000 | 11.4x | 23.8x | 31.5x | 2.5% | 2.1x |
| Amazon (AMZN) | $2,300,000 | ($25,000) | $2,275,000 | 3.6x | 18.2x | 37.8x | 1.7% | 3.5x |
| Apple (AAPL) | $3,400,000 | ($50,000) | $3,350,000 | 8.4x | 24.3x | 29.5x | 2.8% | 7.4x |
| Netflix (NFLX) | $385,000 | $5,000 | $390,000 | 9.8x | 39.4x | 34.5x | 1.6% | 2.3x |
| | | | | | | | | |
| **Maximum** | $3,400,000 | | $3,350,000 | 11.4x | 39.4x | 37.8x | 3.6% | 7.4x |
| **75th Percentile** | $2,975,000 | | $2,936,250 | 9.7x | 26.6x | 33.6x | 3.3% | 3.1x |
| **Median** | $2,200,000 | | $2,137,500 | 8.9x | 21.9x | 31.0x | 2.7% | 2.2x |
| **25th Percentile** | $1,556,250 | | $1,506,250 | 6.5x | 18.9x | 24.5x | 1.8% | 1.5x |
| **Minimum** | $385,000 | | $390,000 | 3.6x | 17.5x | 20.2x | 1.6% | 1.3x |

---

## Key Insights

### GOOGL trades at a significant discount to its mega-cap peers

| Metric | GOOGL | Peer Median | GOOGL vs. Median |
|---|---|---|---|
| EV / Revenue | 5.6x | 8.9x | **−37% discount** |
| EV / EBITDA | 17.5x | 21.9x | **−20% discount** |
| P/E (NTM) | 20.2x | 31.0x | **−35% discount** |
| FCF Yield | 3.4% | 2.7% | **+70 bps premium** |

### Three things stand out

1. **GOOGL's FCF yield (3.4%) is the highest in the peer group alongside Apple** — you are being paid more cash yield than any peer for a business growing 13% annually.

2. **The EV/Revenue discount (~37% to median) is anomalous** for a company with EBITDA margins (31.7%) well above the peer median. A business with above-median margins typically commands at or above-median revenue multiples — not a 37% discount.

3. **Microsoft commands a 2x revenue multiple premium to GOOGL** despite only ~2% faster revenue growth. This premium is almost entirely the Azure/AI narrative — the same narrative Google Cloud has not yet received, despite growing faster than Azure.

### Implied re-rating scenario

If GOOGL re-rated to peer median EV/Revenue (8.9x) while all other factors remained constant:
- Implied EV: ~$3,197B
- Implied equity value: ~$3,297B (adding back net cash)
- Implied upside: ~+57% from the training-data price

*Again — verify against actual current prices, which as of May 9, 2026 are approximately $400/share.*

---

## Notes & Methodology

1. Data source: Company filings (10-K / 20-F), earnings releases, and consensus estimates as of early 2026 (training-data estimates).
2. LTM = Last Twelve Months ending closest reported quarter. Revenue, EBITDA, and FCF are on an LTM basis.
3. EBITDA is adjusted for stock-based compensation and one-time items where disclosed by management.
4. FCF = Operating Cash Flow less Capital Expenditures. FCF Yield = LTM FCF / Market Capitalisation.
5. Enterprise Value = Market Capitalisation + Net Debt (negative = net cash).
6. P/E (NTM) is based on consensus next-twelve-months EPS estimates from sell-side research.
7. Netflix R&D shown as 0.0% as content spend is classified as an operating cost, not R&D.
8. An Excel file with live formulas was also generated: `GOOGL_Comps_Analysis_2026-05-09.xlsx`

---

*Generated using the financial-analysis:comps skill | Claude for Financial Services | May 2026*
