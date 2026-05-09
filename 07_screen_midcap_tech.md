# About This Command: `/equity-research:screen`

## What it does
Runs a **stock screen** — a systematic sweep across the equity universe to surface investment ideas that match a specified set of criteria. Screens can be quantitative (e.g. "FCF yield >5%, EV/EBITDA <12x") or thematic (e.g. "AI infrastructure beneficiaries the market hasn't priced"). The output is a ranked shortlist of ideas, each with a one-page summary, key metrics vs. peers, bull thesis, and key risks.

## How to invoke
```
/equity-research:screen [screen criteria]
```
Examples:
- `/equity-research:screen undervalued mid-cap tech`
- `/equity-research:screen profitable SaaS growing >20%`
- `/equity-research:screen defence spending tailwind small-cap`
- `/equity-research:screen short ideas — margin compression consumer discretionary`

If no criteria are given, the skill asks for direction (long/short), market cap, sector, style, and theme.

## What it produces
For each idea that passes the screen:
1. **Company name, ticker, direction** (Long/Short), and one-line thesis
2. **Metrics table** — Market cap, EV/Revenue, EV/EBITDA, P/E, revenue growth, EBITDA margin, FCF yield — with peer comparison
3. **Bull thesis** — 3–5 bullets on why the stock is mispriced and what the market is missing
4. **Key risks** — what would make the thesis wrong
5. **Suggested next steps** — model build, channel check, expert call

Plus a **comparison table** across all ideas and a **prioritised research agenda** — which ideas to pursue first and why.

## Screen types supported
- **Value screen** — P/E below sector median, FCF yield >5%, EV/EBITDA below historical average
- **Growth screen** — Revenue growth >15%, margin expansion, high NRR
- **Quality screen** — Consistent growth, high ROIC, insider ownership
- **Short screen** — Decelerating revenue, margin compression, accounting red flags
- **Thematic sweep** — Identify beneficiaries of a macro trend regardless of style

## Typical use cases
- Analysts scanning for new long/short ideas at the start of a coverage review
- Portfolio managers looking for underexplored names in a specific sector
- Teaching students how to apply a valuation framework across a peer group
- Generating a pipeline of ideas for deeper fundamental research

---

# Stock Screen: Undervalued Mid-Cap Tech
*Idea Generation | Equity Research | May 2026*

**Screening criteria:** Long ideas | Mid-cap ($2B–$15B market cap) | Technology sector | Value style

**Methodology:** Value screen (P/E below sector median, EV/EBITDA below historical average, FCF yield >4%, revenue growth >10%) applied to US-listed technology companies with market cap $2B–$15B.

---

## Shortlist — 7 Ideas

---

### 1. Elastic NV (ESTC) — Long — "Datadog at half the price"

| Metric | Value | vs. Peers |
|---|---|---|
| Market cap | ~$8B | — |
| EV/Revenue (NTM) | ~7x | DDOG: 18x, SPLK: acquired at 10x |
| Revenue growth | ~18% YoY | Sector median: 14% |
| Gross margin | ~76% | Best-in-class |
| FCF margin | ~12% | Improving |
| FCF yield | ~4.5% | vs. DDOG <1% |

**Thesis:**
- Elastic's search platform underpins observability, security (SIEM), and vector search for AI applications — three of the fastest-growing enterprise IT spend categories
- Market mis-prices it as a legacy search vendor; AI-driven vector search use case is an underappreciated growth driver (embedding search is a core RAG pipeline component)
- Gross margins (76%) and FCF trajectory are converging toward DDOG-quality fundamentals at a 60% valuation discount
- New Elastic Cloud attach rates and ESQL query language gaining enterprise traction

**Key risks:** Opensearch (AWS free alternative) competes at the low end; DDOG expanding into search; customer concentration in SMB creates churn risk in a slowdown

**Next step:** Model the AI/vector search TAM contribution; expert call on AWS Opensearch competitive dynamics

---

### 2. Commvault Systems (CVLT) — Long — "Boring data protection with a cloud second act"

| Metric | Value | vs. Peers |
|---|---|---|
| Market cap | ~$4B | — |
| EV/EBITDA (NTM) | ~16x | Veeam/Rubrik: 25–30x |
| Revenue growth | ~10% YoY | Stabilizing post-transition |
| Gross margin | ~83% | Software-quality |
| FCF margin | ~22% | Best-in-class conversion |
| FCF yield | ~6% | High vs. peer group |

**Thesis:**
- Commvault's transition from on-premise license to SaaS (Metallic) is underway and accelerating — ARR growth outpacing total revenue growth
- FCF yield of ~6% is anomalous for a software business with 83% gross margins and improving growth
- Data protection is non-discretionary spend; cyber insurance mandates are forcing enterprises to modernize backup infrastructure
- Insider ownership elevated; management buyback active

**Key risks:** Rubrik (recently IPO'd) and Veeam are well-capitalized competitors; legacy on-prem installed base churns slower than hoped

**Next step:** Track Metallic ARR disclosure cadence; model SaaS mix shift timeline

---

### 3. Calix (CALX) — Long — "Platform vendor to broadband ISPs, trading at 2020 multiples"

| Metric | Value | vs. Peers |
|---|---|---|
| Market cap | ~$2.5B | — |
| EV/Revenue (NTM) | ~4x | Was 12x+ at peak |
| Revenue growth | ~5–8% YoY | Decelerating, but normalizing |
| Gross margin | ~55% | Hardware-mixed |
| FCF margin | ~8% | Improving |
| Short interest | ~18% | High — potential squeeze |

**Thesis:**
- Calix is a cloud software platform for broadband service providers (ISPs), not a hardware company — but the market still values it on hardware multiples after the post-pandemic ISP capex hangover
- BEAD program ($42B federal broadband subsidy) will drive multi-year equipment refresh cycle for Calix's core customer base
- Revenue growth should re-accelerate to 15%+ as BEAD deployments commence; consensus is anchored to trough numbers
- High short interest creates asymmetric upside if revenue inflects

**Key risks:** BEAD program deployment delays; customer concentration in small/mid-size ISPs; hardware margin mix dampens FCF

**Next step:** Track BEAD state-level deployment timelines; channel checks with regional ISP CIOs

---

### 4. Viavi Solutions (VIAV) — Long — "Network test cash machine, ignored by the market"

| Metric | Value | vs. Peers |
|---|---|---|
| Market cap | ~$2B | — |
| EV/EBITDA (NTM) | ~9x | Spirent/EXFO: 12–15x |
| Revenue growth | ~3–5% YoY | Low but stable |
| Gross margin | ~53% | Mixed hardware/software |
| FCF margin | ~14% | Consistent |
| FCF yield | ~7.5% | Very high |

**Thesis:**
- Viavi makes network test and measurement equipment essential for every 5G buildout, datacenter fiber upgrade, and optical network expansion
- FCF yield of ~7.5% is anomalous; FCF is real, recurring, and growing as hyperscaler fiber capex (Microsoft, Google, Meta) drives optical test demand
- Network test is a recurring revenue model — every new network node requires continuous test cycles
- Potential M&A target; Keysight and Spirent have both made acquisitions in this space

**Key risks:** Telecom capex cycles are lumpy; 5G spending peaked in some geographies; small-cap liquidity limits institutional ownership

**Next step:** Map hyperscaler fiber capex plans to Viavi product exposure; check M&A precedents

---

### 5. Appian (APPN) — Long — "Low-code for regulated industries, undervalued on government traction"

| Metric | Value | vs. Peers |
|---|---|---|
| Market cap | ~$2.5B | — |
| EV/Revenue (NTM) | ~5x | ServiceNow: 16x |
| Revenue growth | ~14% YoY | Subscription growth: ~20% |
| Gross margin | ~70% | Strong software margins |
| FCF margin | ~5% | Turning FCF positive |
| Subscription ARR growth | ~20% | Accelerating |

**Thesis:**
- Appian's low-code BPM platform has deep penetration in US federal government and regulated financial services — long contract cycles, high switching costs, mission-critical workloads
- AI Process Automation integrates AI agents directly into BPM workflows; data fabric architecture is a compliance advantage for regulated customers
- Subscription ARR growing 20% while the market prices the stock on blended revenue multiples — a valuation illusion that should close as mix shifts
- Founder-led, low debt, no acquisition overhang

**Key risks:** Federal government IT budget uncertainty; professional services revenue obscures software quality; ServiceNow expanding downmarket

**Next step:** Model subscription revenue mix shift; expert calls on federal procurement pipeline

---

### 6. Rapid7 (RPD) — Long — "Cybersecurity platform at a deep discount, potential take-private"

| Metric | Value | vs. Peers |
|---|---|---|
| Market cap | ~$2.5B | — |
| EV/Revenue (NTM) | ~3x | CrowdStrike: 22x, Palo Alto: 12x |
| Revenue growth | ~8–10% YoY | Slowing but profitable |
| Gross margin | ~69% | Solid |
| FCF margin | ~10% | Positive and growing |
| FCF yield | ~8% | Very high for cybersecurity |

**Thesis:**
- Rapid7's vulnerability management and SIEM platform serves mid-market enterprises at a price point that CrowdStrike/Palo Alto don't effectively address
- At ~3x EV/Revenue, this is the cheapest publicly traded pure-play cybersecurity platform; cyber spend is non-discretionary
- FCF yield of ~8% at <10% growth is priced as a no-growth business — not warranted for a company with improving margins
- Credible take-private target; PE sponsors have examined this multiple times

**Key risks:** Growth deceleration from 20%+ to ~8–10% reflects competitive pressure from MSFT Sentinel (free bundled SIEM); customer consolidation to larger platforms is a secular headwind

**Next step:** Stress-test the MSFT Sentinel cannibalization thesis; estimate take-private LBO math

---

### 7. GitLab (GTLB) — Long — "Best-of-breed DevSecOps at a discount to the platform story"

| Metric | Value | vs. Peers |
|---|---|---|
| Market cap | ~$9B | — |
| EV/Revenue (NTM) | ~9x | GitHub (implied): 15–20x+ |
| Revenue growth | ~25% YoY | Decelerating from 35%+ |
| Gross margin | ~87% | Best-in-class SaaS |
| FCF margin | ~8% | Turned FCF positive |
| Net Revenue Retention | ~120% | Strong upsell |

**Thesis:**
- GitLab is the only credible enterprise alternative to GitHub (Microsoft-owned) — enterprises choosing to avoid Microsoft vendor concentration are a structural, growing customer base
- GitLab Duo (AI coding) is more deeply embedded in the CI/CD pipeline than GitHub Copilot for teams already on GitLab — creates upsell on every seat
- Path to 20%+ FCF margins as headcount growth moderates; 87% gross margins + 120% NRR + 25% growth at 9x revenue is genuinely cheap
- Founder-led, no acquisition overhang

**Key risks:** Microsoft can bundle GitHub Copilot into E5 enterprise agreements at zero incremental cost; AI-assisted coding commoditises the SCM layer

**Next step:** Track Duo AI seat attach rates; model FCF margin expansion to 20%

---

## Comparison Table

| Ticker | Market Cap | EV/Revenue | Growth | FCF Yield | Priority |
|---|---|---|---|---|---|
| ESTC | ~$8B | ~7x | ~18% | ~4.5% | ⭐⭐⭐ High |
| CVLT | ~$4B | — / ~16x EBITDA | ~10% | ~6% | ⭐⭐⭐ High |
| CALX | ~$2.5B | ~4x | ~5–8% | ~3% | ⭐⭐ Medium (catalyst-dependent) |
| VIAV | ~$2B | — / ~9x EBITDA | ~4% | ~7.5% | ⭐⭐ Medium |
| APPN | ~$2.5B | ~5x | ~14% | ~2% | ⭐⭐⭐ High |
| RPD | ~$2.5B | ~3x | ~9% | ~8% | ⭐⭐⭐ High (take-private optionality) |
| GTLB | ~$9B | ~9x | ~25% | ~2% | ⭐⭐ Medium |

---

## Prioritised Research Agenda

1. **RPD** — highest FCF yield in cybersecurity; take-private math compelling; highest-conviction starting point
2. **CVLT** — FCF generative, non-discretionary workload, SaaS transition underway; lowest risk on this list
3. **ESTC** — AI/vector search angle underappreciated; build model on Elastic Cloud ARR trajectory
4. **APPN** — government + AI process automation intersection; do federal pipeline channel check first

---

> **Data note:** All figures are estimates based on publicly available training-data information through early 2026. No live data feed was used. Verify current prices, market caps, and multiples before acting. This does not constitute investment advice.

*Generated using the equity-research:screen skill | Claude for Financial Services | May 2026*
