# Claude for Financial Services — Complete Onboarding Guide

**For:** New users with no prior financial data background
**Goal:** Professional-grade financial research and analysis from day one
**Time to first output:** < 5 minutes

> **Data disclaimer:** Without a paid subscription to FactSet, S&P Global, Morningstar, or another data connector, all outputs use Claude's training-data knowledge (cutoff ~early 2026). Outputs are illustrative and analytically correct in structure and methodology, but market data (prices, multiples, earnings) must be independently verified before professional use.

---

## Table of Contents

1. [How It Works](#1-how-it-works)
2. [Plugin Map](#2-plugin-map)
3. [Core: Financial Analysis](#3-core-financial-analysis)
4. [Equity Research](#4-equity-research)
5. [Investment Banking](#5-investment-banking)
6. [Private Equity](#6-private-equity)
7. [Wealth Management](#7-wealth-management)
8. [Fund Administration](#8-fund-administration)
9. [Operations & Compliance](#9-operations--compliance)
10. [Partner Plugins: LSEG & S&P Global](#10-partner-plugins-lseg--sp-global)
11. [Named Agents](#11-named-agents)
12. [Power Workflows](#12-power-workflows)
13. [Quick-Reference Command Card](#13-quick-reference-command-card)

---

## 1. How It Works

### Invoking a command
Type a slash command directly in the Claude Code chat prompt:
```
/plugin-name:command-name [optional argument]
```

Examples:
```
/equity-research:sector AI semiconductors
/financial-analysis:comps AAPL
/private-equity:ic-memo
/wealth-management:financial-plan
```

### What happens when you run a command
1. The command loads its skill — a set of detailed instructions that tells Claude exactly how to execute the task at professional quality
2. Claude executes the workflow step by step, asking for any missing inputs
3. Output is delivered as structured text in chat, or as a file (`.xlsx`, `.md`, `.pptx`, `.docx`) saved to your working directory

### Supplying context
Most commands work in two modes:
- **With a company name/ticker:** `/financial-analysis:comps MSFT` — uses training-data knowledge of public companies
- **With your own data:** Paste financial data, paste a company description, or provide a file path — Claude uses your data instead

### Tip: Be generous with context
The richer your description, the better the output. Instead of just a ticker, say:
> *"B2B SaaS company targeting mid-market HR teams, $12M ARR growing 40% YoY, 75% gross margin, 115% NRR, asking $60M"*

---

## 2. Plugin Map

| Plugin | Vertical | Commands | Who Uses It |
|---|---|---|---|
| **financial-analysis** | Core (all verticals) | comps, dcf, lbo, 3-statement-model, competitive-analysis, debug-model, ppt-template | Everyone |
| **equity-research** | Public markets | sector, screen, thesis, earnings-preview, earnings, catalysts, model-update, morning-note, initiate | Research analysts, PMs |
| **investment-banking** | M&A advisory | one-pager, teaser, cim, buyer-list, process-letter, merger-model, deal-tracker | IBD analysts/associates |
| **private-equity** | PE/VC | screen-deal, ic-memo, dd-checklist, dd-prep, returns, source, unit-economics, value-creation, portfolio, ai-readiness | PE investors, deal teams |
| **wealth-management** | Advisory | financial-plan, client-review, client-report, proposal, rebalance, tlh | Financial advisors, RIAs |
| **fund-admin** | Back office | gl-recon, break-trace, nav-tieout, accrual-schedule, roll-forward, variance-commentary | Fund accountants, controllers |
| **operations** | Compliance | kyc-doc-parse, kyc-rules | Compliance, onboarding teams |
| **lseg** *(requires subscription)* | Fixed income / FX / macro | macro-rates, research-equity, analyze-bond-rv, analyze-bond-basis, analyze-swap-curve, analyze-fx-carry, analyze-option-vol, review-fi-portfolio | Fixed income, macro, FX desks |
| **sp-global** *(requires subscription)* | Data + research | tear-sheet, earnings-preview-beta, funding-digest | All research functions |

**Named Agents** (self-contained, bundle their own skills):
`pitch-agent` · `market-researcher` · `earnings-reviewer` · `meeting-prep-agent` · `model-builder` · `gl-reconciler` · `kyc-screener` · `valuation-reviewer` · `month-end-closer` · `statement-auditor`

---

## 3. Core: Financial Analysis

The **financial-analysis** plugin is the foundation. Its tools are used by every other vertical and should be learned first.

---

### `/financial-analysis:comps [company]`
**What:** Builds a comparable company analysis — the benchmark table showing how a company's operating metrics and valuation multiples compare to its peers. Produces a formatted `.xlsx` file with live formulas.

**Output:** Excel file with Operating Statistics table (revenue, growth, margins, FCF) and Valuation Multiples table (EV/Revenue, EV/EBITDA, P/E, FCF yield), each with Max / 75th / Median / 25th / Min statistical summary.

**Examples:**
```
/financial-analysis:comps MSFT
/financial-analysis:comps Salesforce
/financial-analysis:comps
→ (then describe a private company when prompted)
```

**What to tell it for private companies:**
> *"SaaS HR platform, $25M ARR, 30% growth, 75% gross margin, similar to Workday and Rippling"*

---

### `/financial-analysis:dcf [company]`
**What:** Builds a full Discounted Cash Flow (DCF) valuation model, automatically running comps first to anchor the terminal value. Produces two `.xlsx` files: comps and DCF.

**Output:** Bear/Base/Bull revenue projections, WACC calculation, terminal value, implied share price, sensitivity tables (WACC vs terminal growth rate).

**Examples:**
```
/financial-analysis:dcf GOOGL
/financial-analysis:dcf Tesla
/financial-analysis:dcf
→ (describe a company when prompted)
```

**Pro tip:** Run `/financial-analysis:comps` first. Then run `/financial-analysis:dcf` and reference "use the comps we just built" — the DCF will use those peer multiples to anchor exit assumptions.

---

### `/financial-analysis:lbo [company or deal details]`
**What:** Builds a Leveraged Buyout model — the core PE acquisition analysis. Models debt structure, interest schedule, cash flow waterfall, and equity returns under multiple scenarios. Produces a `.xlsx` model.

**Output:** Sources & uses table, 3-scenario P&L, debt schedule, IRR/MOIC returns, 5×5 sensitivity tables (exit multiple vs. revenue CAGR).

**Examples:**
```
/financial-analysis:lbo ServiceNow
/financial-analysis:lbo
→ "Target: HealthcareSaaS Co, $50M EBITDA, $400M entry EV, 60% debt financing, 5-year hold, exit at 12x EBITDA"
```

---

### `/financial-analysis:3-statement-model [file path or company]`
**What:** Builds or populates a 3-statement financial model (Income Statement, Balance Sheet, Cash Flow Statement) with historical data and 5-year projections. The three statements are linked — changes in one flow through to the others.

**Output:** Excel model with 6 tabs: Income Statement, Balance Sheet, Cash Flow, Revenue Detail, Scenarios (Bear/Base/Bull), and Assumptions.

**Examples:**
```
/financial-analysis:3-statement-model AAPL
/financial-analysis:3-statement-model my_template.xlsx
```

---

### `/financial-analysis:competitive-analysis [company or industry]`
**What:** Produces a structured competitive landscape analysis — market map, player positioning, moat assessment, and strategic implications.

**Output:** Market structure overview, competitor profiles, positioning matrix, competitive intensity assessment, strategic implications for the subject company.

**Examples:**
```
/financial-analysis:competitive-analysis cloud computing
/financial-analysis:competitive-analysis Stripe
/financial-analysis:competitive-analysis fintech payments Europe
```

---

### `/financial-analysis:debug-model [file path]`
**What:** Audits an existing Excel financial model for errors — broken formulas, balance sheet imbalances, hardcoded values where formulas should be, circular references, and logic errors.

**Output:** Error report listing each issue by tab and cell, severity rating, and recommended fix.

**Example:**
```
/financial-analysis:debug-model C:/models/MyDCF_v3.xlsx
```

---

### `/financial-analysis:ppt-template [file path]`
**What:** Converts your firm's PowerPoint template into a reusable skill that all other commands can use for output formatting. Run this once with your branded `.pptx` file, and all subsequent deck outputs will use your brand.

**Example:**
```
/financial-analysis:ppt-template C:/templates/FirmBranding.pptx
```

---

## 4. Equity Research

The **equity-research** plugin covers the full research analyst workflow — from morning notes to full initiations.

---

### `/equity-research:sector [sector name]`
**What:** Generates an industry landscape report covering market sizing, competitive dynamics, and investment implications. The starting point for any new coverage area.

**Output:** TAM and segment breakdown, market share analysis, competitive intensity by sub-segment, bull/bear drivers, stock-screening framework, valuation context, sector stance.

**Examples:**
```
/equity-research:sector cloud computing
/equity-research:sector GLP-1 obesity drugs
/equity-research:sector US community banking
/equity-research:sector defence primes UK
/equity-research:sector B2B payments infrastructure
```

---

### `/equity-research:screen [criteria]`
**What:** Runs a quantitative or thematic stock screen to surface investment ideas. Supports value, growth, quality, short, and thematic sweep screens.

**Output:** Shortlist of 5–10 ideas, each with a one-page summary (metrics vs. peers, bull thesis, key risks, next steps), comparison table, and prioritised research agenda.

**Examples:**
```
/equity-research:screen undervalued mid-cap tech
/equity-research:screen profitable SaaS growing above 20%
/equity-research:screen AI infrastructure beneficiaries not yet priced in
/equity-research:screen short ideas — margin compression consumer discretionary
/equity-research:screen high FCF yield industrials
/equity-research:screen small-cap defence CAGR above 15%
```

---

### `/equity-research:thesis [ticker]`
**What:** Creates or updates a structured investment thesis — the full logical chain of why a stock is mispriced, including bull/bear cases, valuation, catalysts, and a monitoring tracker.

**Output:** Thesis statement with conviction/recommendation/price target, bull case (4–5 drivers with evidence), bear case (3–4 risks with mitigants), SOTP or P/E valuation, thesis tracker table, 12-month catalyst list.

**Examples:**
```
/equity-research:thesis NVDA
/equity-research:thesis META
/equity-research:thesis BRKB
→ Update: "Q1 earnings just came out, Cloud beat by 3pp — update the MSFT thesis"
```

---

### `/equity-research:earnings-preview [ticker]`
**What:** Builds a pre-earnings analysis ahead of a company's quarterly results — what consensus expects, key metrics to watch, and scenario analysis for beat/miss/in-line.

**Output:** Consensus estimate snapshot, KPIs to monitor, three scenarios (beat / in-line / miss) with stock reaction expectations, key questions for the earnings call.

**Examples:**
```
/equity-research:earnings-preview AMZN
/equity-research:earnings-preview TSLA Q2 2026
```

---

### `/equity-research:earnings [ticker] [quarter]`
**What:** Analyses actual quarterly earnings results — compares actuals vs. consensus, explains drivers, updates the model, and drafts an earnings reaction note.

**Output:** Actuals vs. estimates table, key beat/miss drivers, guidance analysis, model update summary, revised price target, earnings reaction note for clients.

**Examples:**
```
/equity-research:earnings AAPL Q2 2026
/equity-research:earnings GOOGL
→ (paste the earnings release text when prompted)
```

---

### `/equity-research:catalysts [timeframe]`
**What:** Builds or reviews a catalyst calendar — upcoming events that could move stocks in your coverage universe (earnings dates, FDA decisions, regulatory rulings, product launches, investor days).

**Output:** Catalyst table sorted by date, with event type, company, expected impact (high/medium/low), and suggested position action.

**Examples:**
```
/equity-research:catalysts next 2 weeks
/equity-research:catalysts Q3 2026
```

---

### `/equity-research:model-update [ticker]`
**What:** Updates an existing financial model with new data — fresh earnings, revised guidance, or changed assumptions — without rebuilding from scratch.

**Examples:**
```
/equity-research:model-update MSFT
→ "Q2 revenue was $70.1B vs $69.8B est, Azure grew 33% vs 31% est, guided Q3 revenue to $73-74B"
```

---

### `/equity-research:morning-note`
**What:** Drafts a morning meeting note — the daily briefing analysts send to portfolio managers and clients covering overnight developments, pre-market movers, earnings reactions, and trade ideas.

**Output:** Macro/overnight summary, earnings/news highlights, key trade ideas for the session, what to watch.

**Example:**
```
/equity-research:morning-note
→ (optionally paste pre-market news headlines for richer output)
```

---

### `/equity-research:initiate [ticker]`
**What:** Begins the 5-task workflow to produce an institutional-quality initiating coverage report (30–50 pages). The full pipeline: company research → financial model → valuation → charts → report assembly. Each task is run separately.

**Tasks:**
1. Company research (6–8K word document)
2. Financial model (Excel, 6 tabs)
3. Valuation analysis (DCF + comps + price target)
4. Chart generation (25–35 PNG charts)
5. Report assembly (30–50 page DOCX)

**Example:**
```
/equity-research:initiate NVDA
→ "Start with Task 1"
```

---

## 5. Investment Banking

The **investment-banking** plugin covers the M&A advisory workflow — from first marketing materials through deal close.

---

### `/investment-banking:one-pager [company]`
**What:** Creates a company one-pager / strip profile — the branded, data-rich single-page company overview used in pitch books and deal materials.

**Output:** Company overview, business description, key financial metrics, investment highlights, customer examples, market opportunity, comparable transactions.

**Examples:**
```
/investment-banking:one-pager Stripe
/investment-banking:one-pager
→ "B2B SaaS, $20M ARR, 50% growth, AI-powered legal workflow automation for law firms"
```

---

### `/investment-banking:teaser [company]`
**What:** Drafts a blind/anonymous teaser — the first document sent to potential buyers before they sign an NDA. Describes the company without naming it, generating interest while protecting confidentiality.

**Output:** Sector and business description (anonymised), key metrics, investment highlights, process overview.

**Examples:**
```
/investment-banking:teaser
→ "Mid-market SaaS, verticalised for construction project management, $18M ARR, 40% growth"
```

---

### `/investment-banking:cim [company]`
**What:** Drafts a Confidential Information Memorandum (CIM) — the comprehensive document sent to buyers after NDA execution. The primary diligence document in an M&A process.

**Output:** 30–50 page CIM covering executive summary, company overview, products, market, financials (historical + projected), management team, and investment considerations.

**Examples:**
```
/investment-banking:cim RetailAI Inc
/investment-banking:cim
→ (describe the company and paste any available materials)
```

---

### `/investment-banking:buyer-list [company or sector]`
**What:** Builds a buyer universe for a sell-side process — lists strategic acquirers (by acquisition rationale) and financial sponsors (PE firms by mandate fit), with contact names and deal rationale.

**Output:** Strategic buyer table (company, rationale, deal precedent, contact), financial sponsor table (firm, fund size, relevant portfolio, contact), prioritised outreach list.

**Examples:**
```
/investment-banking:buyer-list healthcare data analytics
/investment-banking:buyer-list RetailAI Inc
```

---

### `/investment-banking:process-letter [IOI or final bid]`
**What:** Drafts process correspondence — the formal letters that govern an M&A auction: IOI instructions, management meeting invitations, and final bid letters.

**Examples:**
```
/investment-banking:process-letter IOI
/investment-banking:process-letter final bid
/investment-banking:process-letter management meeting invite
```

---

### `/investment-banking:merger-model [acquirer] acquiring [target]`
**What:** Builds an accretion/dilution merger model — analyses the EPS, credit, and pro-forma financial impact of an acquisition on the acquirer. Core tool for M&A fairness analysis.

**Output:** Pro-forma income statement, EPS accretion/(dilution) table, synergies bridge, purchase price allocation, pro-forma credit metrics, deal structure sensitivity.

**Examples:**
```
/investment-banking:merger-model MSFT acquiring Salesforce
/investment-banking:merger-model
→ "Acquirer: $5B revenue, 25% EBITDA margin. Target: $1B revenue, 15% EBITDA margin, asking $8B. $200M in synergies."
```

---

### `/investment-banking:deal-tracker`
**What:** Reviews deal pipeline status — tracks live deals by stage, outstanding milestones, and action items. Works as a running process tracker across multiple deals.

**Example:**
```
/investment-banking:deal-tracker
→ (paste your current deal list or describe the pipeline)
```

---

## 6. Private Equity

The **private-equity** plugin covers the full PE lifecycle — sourcing through exit.

---

### `/private-equity:screen-deal`
**What:** Quickly screens an inbound deal (CIM, teaser, or verbal description) against the fund's investment criteria. Go/No-Go in minutes.

**Output:** Deal pass/fail verdict, fit assessment against fund mandate (sector, size, growth, margin, entry multiple), key questions to investigate, preliminary return range.

**Examples:**
```
/private-equity:screen-deal
→ "B2B SaaS, payroll for SMBs, $15M ARR, 35% growth, 72% gross margin, asking $75M (5x ARR)"
→ "Industrial services company, $40M EBITDA, asset-light, asking $280M (7x), Midwest US"
```

---

### `/private-equity:ic-memo [company]`
**What:** Drafts a full Investment Committee Memorandum — the formal document submitted to the IC for approval to acquire a company.

**Output:** Executive summary with recommendation, investment thesis (5 bullets), business overview, market analysis, financial analysis (entry multiples, returns scenarios), due diligence status, risks & mitigants, deal terms, value creation plan.

**Examples:**
```
/private-equity:ic-memo CloudPay Inc
/private-equity:ic-memo
→ (describe the deal)
```

---

### `/private-equity:dd-checklist [company]`
**What:** Generates a comprehensive, sector-tailored due diligence checklist with status tracking fields. Covers all workstreams: commercial, financial, legal, technology, HR, and cybersecurity.

**Examples:**
```
/private-equity:dd-checklist SaaS healthcare company
/private-equity:dd-checklist industrial distribution
```

---

### `/private-equity:dd-prep [company] [meeting type]`
**What:** Prepares for a specific diligence meeting or expert call — generates targeted questions, benchmarks to probe, and red flags to watch for, tailored to the meeting type.

**Examples:**
```
/private-equity:dd-prep CloudPay CEO interview
/private-equity:dd-prep RetailAI customer reference call
/private-equity:dd-prep SaaS company management presentation
```

---

### `/private-equity:returns [deal parameters]`
**What:** Builds IRR/MOIC sensitivity tables across entry multiple, exit multiple, leverage, and growth scenarios. Standalone returns analysis without a full LBO model.

**Examples:**
```
/private-equity:returns
→ "Entry $100M, 50% debt at 8%, 5-year hold, exit 10-14x EBITDA, EBITDA growing 8-15% pa"
```

---

### `/private-equity:source [sector or criteria]`
**What:** Runs the deal sourcing pipeline — discovers target companies matching the fund's criteria, checks for existing relationships, and drafts personalised founder outreach emails.

**Output:** List of 10–20 target companies with brief profile and fit rationale, plus a draft personalised outreach email template.

**Examples:**
```
/private-equity:source B2B SaaS $5-20M ARR healthcare vertical
/private-equity:source industrial services Texas $10-50M EBITDA
/private-equity:source fintech payments Southeast Asia
```

---

### `/private-equity:unit-economics [company]`
**What:** Analyses customer-level economics — ARR cohorts, net dollar retention, CAC/LTV, churn analysis, and payback periods.

**Output:** Cohort table, NRR trend, LTV/CAC by segment, payback period analysis, unit economics benchmarks vs. SaaS peers.

**Examples:**
```
/private-equity:unit-economics CloudPay Inc
→ (paste cohort data or ARR schedule when prompted)
```

---

### `/private-equity:value-creation [company]`
**What:** Builds a post-acquisition value creation plan — structured roadmap from Day 1 through exit, including EBITDA bridge, 100-day plan, and KPI dashboard.

**Output:** EBITDA bridge (entry to exit), 100-day plan by workstream, Year 2–3 initiatives, exit preparation timeline, KPI monitoring dashboard.

**Examples:**
```
/private-equity:value-creation CloudPay Inc
```

---

### `/private-equity:portfolio [company or file path]`
**What:** Analyses a portfolio company's performance against plan — KPIs, budget variances, and early-warning flags.

**Examples:**
```
/private-equity:portfolio CloudPay Inc Q1 2026
→ (paste the quarterly board pack or financial update)
```

---

### `/private-equity:ai-readiness [portfolio companies]`
**What:** Scans portfolio companies for AI leverage opportunities — per-company go/no-go gate, quick wins ranked by EBITDA impact, and cross-portfolio plays.

**Examples:**
```
/private-equity:ai-readiness
→ "Portfolio: CloudPay (HR SaaS), RetailAI (inventory), IndustrialCo (field services)"
```

---

## 7. Wealth Management

The **wealth-management** plugin covers the full financial advisory relationship — from prospect proposal through ongoing reporting.

---

### `/wealth-management:financial-plan`
**What:** Generates a comprehensive personal financial plan — retirement projections, college funding, asset allocation, insurance, tax optimisation, and estate planning — with a prioritised 20-item action plan.

**Output:** Net worth statement, cash flow analysis, retirement scenarios (Bear/Base/Bull + Monte Carlo), college funding gap, asset allocation by account, insurance gaps, tax strategies, estate planning priorities, action plan with deadlines.

**Example:**
```
/wealth-management:financial-plan
→ "Client: 45-year-old couple, $320K household income, $800K in retirement accounts, $200K savings, $600K home equity, $50K in 529s, want to retire at 62, 2 kids in college in 3 and 6 years"
```

---

### `/wealth-management:proposal [prospect name]`
**What:** Creates a personalised investment proposal for a prospective client — tailored to their goals, risk tolerance, and financial situation.

**Output:** Personalised asset allocation proposal, expected return/risk profile, fee structure, why this approach vs alternatives, next steps.

**Examples:**
```
/wealth-management:proposal John and Mary Smith
→ (describe the prospect's situation)
```

---

### `/wealth-management:client-review [client name]`
**What:** Prepares a client annual/quarterly review meeting package — performance summary, allocation drift, rebalancing recommendations, and meeting talking points.

**Output:** Portfolio performance vs benchmark, attribution analysis, current vs target allocation, rebalancing trades, talking points, updated financial plan progress.

**Examples:**
```
/wealth-management:client-review Chen Family Q1 2026
```

---

### `/wealth-management:client-report [client name] [period]`
**What:** Generates a professional client-facing performance report for the period.

**Output:** Portfolio performance summary, holdings breakdown, benchmark comparison, commentary on key moves, outlook.

**Examples:**
```
/wealth-management:client-report Chen Family Q4 2025
/wealth-management:client-report Smith Portfolio 2025 Annual
```

---

### `/wealth-management:rebalance [client or account]`
**What:** Analyses allocation drift and generates specific, tax-aware rebalancing trades to bring the portfolio back to target.

**Output:** Current vs target allocation table, drift analysis, specific buy/sell trades, tax lot optimisation, estimated tax impact.

**Examples:**
```
/wealth-management:rebalance Chen Family
→ (paste current holdings and target allocation)
```

---

### `/wealth-management:tlh [client or account]`
**What:** Scans taxable accounts for tax-loss harvesting opportunities — identifies harvestable losses, suggests replacement securities (avoiding wash sales), and estimates tax savings.

**Output:** Harvesting candidates table (position, unrealised loss, replacement security, wash sale window), estimated tax savings, net-of-fee benefit analysis.

**Examples:**
```
/wealth-management:tlh Chen Family taxable account
→ (paste taxable holdings with cost basis)
```

---

## 8. Fund Administration

The **fund-admin** plugin covers month-end close, reconciliation, and LP reporting for investment funds. Invoked using the skill names directly (no `/fund-admin:` prefix — use `/fund-admin:gl-recon` etc.).

---

### `/fund-admin:gl-recon`
**What:** Runs GL vs prime broker reconciliation — compares the fund's internal accounting records against the prime broker statement, classifies each break, traces root cause, and generates a sign-off package.

**Examples:**
```
/fund-admin:gl-recon
→ "Fund III, April 30 close. GL shows $487.2M equity long book, prime broker shows $484.9M. Known items: $1.4M AAPL dividend accrual (timing), $600K FX rate mismatch on European positions, $300K unexplained."
```

---

### `/fund-admin:break-trace`
**What:** Root-causes a single reconciliation break — follows the audit trail from the break row back to the originating transaction on each side and explains the difference.

**Example:**
```
/fund-admin:break-trace
→ "Break: $300K GL-only debit in equity long account, no matching prime broker entry, first seen April 30"
```

---

### `/fund-admin:accrual-schedule`
**What:** Builds the period-end accrual schedule — for each accrual item (management fees, interest, dividends, expenses), computes the entry, cites the support, and drafts the journal entry for controller approval.

**Example:**
```
/fund-admin:accrual-schedule
→ "Fund III, April 30. Accrue: management fee (1.5% pa on $500M NAV), $2.3M accrued interest on corporate bonds, $400K administrator fee"
```

---

### `/fund-admin:roll-forward`
**What:** Builds a roll-forward schedule for a balance sheet account — beginning balance + additions − reductions = ending balance, with each component tied to the GL.

**Example:**
```
/fund-admin:roll-forward
→ "Unrealised gains account, Fund III, April 30. Opening $12.4M, additions $3.1M, reversals $0.8M"
```

---

### `/fund-admin:variance-commentary`
**What:** Writes flux commentary for every P&L and balance sheet line over threshold — current vs prior period and vs budget, with the driver explained from underlying activity.

**Example:**
```
/fund-admin:variance-commentary
→ (paste current vs prior vs budget financials)
```

---

### `/fund-admin:nav-tieout`
**What:** Ties an LP statement to the fund's NAV pack — independently recomputes the LP's capital account from NAV components and flags any line that doesn't agree.

**Example:**
```
/fund-admin:nav-tieout
→ "LP: Pension Fund X, 4.2% interest in Fund III. April 30 NAV pack shows $500M total NAV. LP statement shows $21.3M capital account."
```

---

## 9. Operations & Compliance

The **operations** plugin handles client onboarding and KYC workflows.

---

### `/operations:kyc-doc-parse`
**What:** Parses an investor or client onboarding packet into structured KYC fields — identity, beneficial ownership, control persons, source of funds, and document inventory. First step of the KYC screening process.

**Output:** Structured KYC record with all parsed fields, document checklist (present/missing), extraction confidence flags, and fields requiring human verification.

**Example:**
```
/operations:kyc-doc-parse
→ (paste the onboarding document text, or describe the client: entity type, ownership structure, jurisdiction, source of funds)
```

---

### `/operations:kyc-rules`
**What:** Applies the firm's KYC/AML rules grid to a parsed onboarding record — assigns a risk rating, lists every rule outcome with the rule cited, and flags what's missing or requires escalation. Does not make final decisions; scores and routes.

**Output:** Risk rating (Low/Medium/High/Escalate), rule-by-rule outcome table, missing document list, escalation flags, recommended next steps.

**Example:**
```
/operations:kyc-rules
→ (paste the structured record from kyc-doc-parse, or describe the client profile)
```

---

## 10. Partner Plugins: LSEG & S&P Global

These plugins require a paid subscription to the respective data provider. Once authenticated, they pull live data into every analysis.

### Authentication
```
Authenticate LSEG:     available via MCP connector — run /lseg:macro-rates and follow auth prompt
Authenticate S&P Global: available via MCP connector — run /sp-global:tear-sheet and follow auth prompt
```

---

### LSEG Commands *(requires LSEG Workspace subscription)*

| Command | What it does | Example |
|---|---|---|
| `/lseg:macro-rates [country]` | Macro & rates dashboard — yield curves, inflation, swap spreads, economic indicators | `/lseg:macro-rates US 5Y` |
| `/lseg:research-equity [ticker]` | Equity research snapshot with consensus estimates, fundamentals, and price performance | `/lseg:research-equity AAPL FY2024-2026` |
| `/lseg:analyze-bond-rv [ISIN]` | Bond relative value analysis — vs yield curve, credit spreads, scenario stress tests | `/lseg:analyze-bond-rv US38141GXZ25` |
| `/lseg:analyze-bond-basis [future RIC]` | Bond futures basis — CTD identification, implied repo rate, basis trade assessment | `/lseg:analyze-bond-basis FGBLc1` |
| `/lseg:analyze-swap-curve [currency]` | Swap curve analysis — government/inflation overlays, curve trade opportunities | `/lseg:analyze-swap-curve EUR ESTR` |
| `/lseg:analyze-fx-carry [currency pair]` | FX carry trade evaluation — spot, forwards, vol surface, historical context | `/lseg:analyze-fx-carry USDJPY 3M` |
| `/lseg:analyze-option-vol [underlying]` | Option volatility analysis — vol surface, Greeks, implied vs realised vol | `/lseg:analyze-option-vol .SPX` |
| `/lseg:review-fi-portfolio [ISINs]` | Fixed income portfolio review — pricing, cashflows, scenario analysis | `/lseg:review-fi-portfolio ISIN1,ISIN2 +100bp` |

---

### S&P Global Commands *(requires S&P Capital IQ subscription)*

| Command | What it does | Example |
|---|---|---|
| `/sp-global:tear-sheet [ticker]` | Professional company tear sheet with live Capital IQ data — for equity research, IB/M&A, corp dev, or sales/BD audience | `/sp-global:tear-sheet MSFT` |
| `/sp-global:earnings-preview-beta [ticker]` | 4–5 page HTML earnings preview with transcript analysis, competitor landscape, and valuation | `/sp-global:earnings-preview-beta NVDA` |
| `/sp-global:funding-digest [sectors]` | Weekly deal flow briefing — recent funding rounds and capital markets activity as a PowerPoint slide | `/sp-global:funding-digest AI infrastructure fintech` |

---

## 11. Named Agents

Named agents are self-contained — they bundle all the skills they need, so you just describe what you want and they handle the workflow end-to-end. Each runs as a full agent session.

| Agent | Invoke as | What it does |
|---|---|---|
| **pitch-agent** | `/pitch-agent` | Full sell-side pitch deck, end to end — runs comps, precedents, LBO, and produces branded deck |
| **market-researcher** | `/market-researcher` | Sector → industry overview + competitive landscape + peer comps + ideas shortlist |
| **earnings-reviewer** | `/earnings-reviewer` | Earnings call + filings → model update → earnings note draft |
| **meeting-prep-agent** | `/meeting-prep-agent` | Upcoming client meeting → briefing pack with performance, news, talking points |
| **model-builder** | `/model-builder` | Describe a model need → DCF / LBO / 3-statement / comps built to spec |
| **gl-reconciler** | `/gl-reconciler` | Describe a break → finds it, traces root cause, routes for sign-off |
| **kyc-screener** | `/kyc-screener` | Paste onboarding docs → parsed KYC record + rules grid + risk rating |
| **valuation-reviewer** | `/valuation-reviewer` | GP valuation package → runs template, stages LP reporting |
| **month-end-closer** | `/month-end-closer` | Month-end inputs → accruals, roll-forwards, variance commentary |
| **statement-auditor** | `/statement-auditor` | LP statement draft → full audit before distribution |

**How to use an agent:**
```
/pitch-agent
→ "Sell-side pitch for CloudPay Inc — B2B payroll SaaS, $15M ARR, exploring strategic sale"

/market-researcher
→ "AI-powered legal workflow automation for law firms — market overview and top 5 pure-play investment ideas"
```

---

## 12. Power Workflows

These multi-command sequences replicate what professionals do in practice. Each workflow chains commands in a logical order — output from one feeds the next.

---

### Workflow 1: Full Equity Research on a New Company
*Time: 30–90 minutes | Output: Sector report + screen + thesis + comps + DCF*

```
Step 1: /equity-research:sector [industry]
        → Understand the landscape before evaluating the company

Step 2: /equity-research:screen [criteria matching your company]
        → Confirm the company surfaces as a screen candidate

Step 3: /equity-research:thesis [ticker]
        → Build the investment case

Step 4: /financial-analysis:comps [ticker]
        → Benchmark valuation and operating metrics vs peers
        → Excel file generated

Step 5: /financial-analysis:dcf [ticker]
        → "Use the comps we just built to anchor the terminal multiple"
        → Full valuation model generated

Step 6: /equity-research:initiate [ticker] — Task 1
        → Start the full 30–50 page initiation report
```

**Example run:**
```
/equity-research:sector AI semiconductors
/equity-research:screen AI infrastructure beneficiaries not yet priced in
/equity-research:thesis NVDA
/financial-analysis:comps NVDA
/financial-analysis:dcf NVDA
/equity-research:initiate NVDA
```

---

### Workflow 2: PE Deal Evaluation — Inbound CIM to IC Vote
*Time: 45–120 minutes | Output: Screen memo + DD checklist + IC memo + LBO model*

```
Step 1: /private-equity:screen-deal
        → Paste or describe the deal — quick go/no-go in 5 minutes

Step 2: /private-equity:dd-checklist [company]
        → Generate the full DD workstream list before the first call

Step 3: /private-equity:dd-prep [company] management presentation
        → Prepare questions and red flags for the management meeting

Step 4: /private-equity:unit-economics [company]
        → Deep-dive customer economics — NRR, cohorts, CAC/LTV

Step 5: /financial-analysis:lbo [company]
        → Build the returns model — confirm the deal can hit fund hurdle

Step 6: /private-equity:ic-memo [company]
        → Draft the IC memo — investment thesis, financials, risks, returns, deal terms

Step 7: /private-equity:value-creation [company]
        → Build the 100-day plan and EBITDA bridge for the IC presentation
```

**Example run:**
```
/private-equity:screen-deal
→ "CloudPay Inc — B2B payroll SaaS, $15M ARR, 35% growth, 72% gross margin, asking $75M"

/private-equity:dd-checklist CloudPay Inc

/private-equity:dd-prep CloudPay CEO interview

/private-equity:unit-economics CloudPay Inc

/financial-analysis:lbo CloudPay Inc

/private-equity:ic-memo CloudPay Inc

/private-equity:value-creation CloudPay Inc
```

---

### Workflow 3: M&A Sell-Side Process — First Marketing to Final Bid
*Time: 60–120 minutes | Output: Teaser + CIM + buyer list + process letters*

```
Step 1: /investment-banking:one-pager [company]
        → Internal reference document; shared with senior bankers

Step 2: /investment-banking:teaser [company]
        → Anonymous version for pre-NDA distribution to buyers

Step 3: /investment-banking:cim [company]
        → Full CIM for post-NDA distribution

Step 4: /investment-banking:buyer-list [company]
        → Build the outreach universe: strategic + financial sponsors

Step 5: /investment-banking:process-letter IOI
        → Draft the IOI instructions letter to distribute with the teaser

Step 6: /financial-analysis:lbo [company]
        → Model the deal from a sponsor's perspective — test their price ceiling

Step 7: /investment-banking:merger-model [likely strategic acquirer] acquiring [company]
        → Test strategic buyer EPS accretion to calibrate strategic pricing

Step 8: /investment-banking:process-letter final bid
        → Draft final bid instructions once IOIs are received
```

**Example run:**
```
/investment-banking:one-pager RetailAI Inc
/investment-banking:teaser RetailAI Inc
/investment-banking:cim RetailAI Inc
/investment-banking:buyer-list retail technology and supply chain
/investment-banking:process-letter IOI
/financial-analysis:lbo RetailAI Inc
/investment-banking:merger-model Shopify acquiring RetailAI Inc
/investment-banking:process-letter final bid
```

---

### Workflow 4: Wealth Management — New Client Onboarding to First Review
*Time: 30–60 minutes | Output: Financial plan + proposal + rebalancing + tax harvest*

```
Step 1: /wealth-management:financial-plan
        → Comprehensive plan: retirement, college, insurance, estate, tax

Step 2: /wealth-management:proposal [client name]
        → Personalised investment proposal based on the plan

Step 3: /wealth-management:rebalance [client]
        → Generate the initial portfolio implementation trades

Step 4: /wealth-management:tlh [client]
        → (At year-end) Identify tax-loss harvesting opportunities

Step 5: /wealth-management:client-report [client] [period]
        → First quarterly performance report

Step 6: /wealth-management:client-review [client]
        → Prepare the annual review meeting package
```

**Example run:**
```
/wealth-management:financial-plan
→ "James Chen, 42, $280K income, $620K in retirement accounts, $155K savings, retiring at 60, 2 kids in college in 6 and 9 years"

/wealth-management:proposal Chen Family

/wealth-management:rebalance Chen Family
→ (paste current holdings vs target allocation)

/wealth-management:tlh Chen Family
→ (paste taxable account with cost basis at year-end)

/wealth-management:client-report Chen Family Q2 2026

/wealth-management:client-review Chen Family
```

---

### Workflow 5: Daily Equity Research Analyst Morning Routine
*Time: 15–20 minutes | Output: Morning note + catalyst update + pre-earnings preview*

```
Step 1: /equity-research:morning-note
        → (paste pre-market headlines)
        → Draft the morning note for distribution

Step 2: /equity-research:catalysts next 2 weeks
        → Update the catalyst calendar for the coverage universe

Step 3: /equity-research:earnings-preview [upcoming earner]
        → Build the pre-earnings scenarios for any name reporting this week

Step 4: /equity-research:model-update [ticker]
        → (post-earnings) Update the model with actual results
```

---

### Workflow 6: Fund Admin Month-End Close
*Time: 30–60 minutes | Output: Full close package ready for LP statements*

```
Step 1: /fund-admin:gl-recon
        → Identify and classify all breaks vs prime broker

Step 2: /fund-admin:break-trace
        → For each unresolved break: trace to source transaction

Step 3: /fund-admin:accrual-schedule
        → Build accrual entries for all period-end items

Step 4: /fund-admin:roll-forward
        → Roll-forward schedules for unrealised gains, fees payable, etc.

Step 5: /fund-admin:variance-commentary
        → Write flux commentary for the close package

Step 6: /fund-admin:nav-tieout
        → Tie each LP statement to the NAV pack before distribution
```

---

### Workflow 7: KYC / New Investor Onboarding
*Time: 10–20 minutes | Output: Structured KYC record + risk rating + escalation flags*

```
Step 1: /operations:kyc-doc-parse
        → Paste or describe the onboarding documents
        → Extracts all structured fields: identity, ownership, source of funds

Step 2: /operations:kyc-rules
        → Apply the rules grid to the parsed record
        → Outputs risk rating, rule outcomes, missing docs, escalation flags
```

---

### Workflow 8: PE Portfolio AI Value Creation Scan
*Identify highest-ROI AI opportunities across all portfolio companies*

```
Step 1: /private-equity:portfolio [company]
        → Review current performance vs plan for each portco

Step 2: /private-equity:ai-readiness
        → Scan all portcos for AI leverage — rank by EBITDA impact

Step 3: /private-equity:value-creation [company]
        → Build the updated value creation plan incorporating AI initiatives

Step 4: /financial-analysis:comps [company]
        → Re-run comps to see if AI-comparable companies trade at a premium
        → Inform exit timing and positioning
```

---

## 13. Quick-Reference Command Card

Copy and keep this near your workspace.

```
━━━ FINANCIAL ANALYSIS (CORE) ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
/financial-analysis:comps [ticker]           Comparable company analysis → .xlsx
/financial-analysis:dcf [ticker]             DCF valuation (runs comps first) → .xlsx
/financial-analysis:lbo [company]            LBO model with scenarios → .xlsx
/financial-analysis:3-statement-model        Full 3-statement model → .xlsx
/financial-analysis:competitive-analysis     Competitive landscape analysis
/financial-analysis:debug-model [file.xlsx]  Audit model for errors
/financial-analysis:ppt-template [file.pptx] Register brand template

━━━ EQUITY RESEARCH ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
/equity-research:sector [industry]           Sector landscape report
/equity-research:screen [criteria]           Stock screen → shortlist of ideas
/equity-research:thesis [ticker]             Investment thesis (Long/Short)
/equity-research:earnings-preview [ticker]   Pre-earnings scenarios
/equity-research:earnings [ticker] [Q]       Post-earnings analysis + note
/equity-research:catalysts [timeframe]       Catalyst calendar
/equity-research:model-update [ticker]       Update model with new data
/equity-research:morning-note                Daily morning briefing note
/equity-research:initiate [ticker]           Full 5-task initiation report

━━━ INVESTMENT BANKING ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
/investment-banking:one-pager [company]      Company strip profile → .pptx
/investment-banking:teaser [company]         Anonymous blind teaser
/investment-banking:cim [company]            Full CIM document
/investment-banking:buyer-list [company]     Strategic + sponsor buyer universe
/investment-banking:process-letter [type]    IOI / final bid / meeting invite
/investment-banking:merger-model [A] [T]     Accretion/dilution model → .xlsx
/investment-banking:deal-tracker             Live deal pipeline tracker

━━━ PRIVATE EQUITY ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
/private-equity:screen-deal                  Quick deal screen vs fund mandate
/private-equity:ic-memo [company]            Investment committee memorandum
/private-equity:dd-checklist [company]       Full DD workstream checklist
/private-equity:dd-prep [company] [meeting]  Meeting prep: questions + red flags
/private-equity:returns [parameters]         IRR/MOIC sensitivity tables
/private-equity:source [sector/criteria]     Deal sourcing + outreach emails
/private-equity:unit-economics [company]     ARR cohorts, LTV/CAC, NRR
/private-equity:value-creation [company]     Post-acquisition value creation plan
/private-equity:portfolio [company]          Portfolio company KPI review
/private-equity:ai-readiness [companies]     AI leverage scan across portfolio

━━━ WEALTH MANAGEMENT ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
/wealth-management:financial-plan            Comprehensive financial plan
/wealth-management:proposal [client]         New client investment proposal
/wealth-management:client-review [client]    Annual/quarterly review package
/wealth-management:client-report [client]    Client performance report
/wealth-management:rebalance [client]        Portfolio drift + rebalancing trades
/wealth-management:tlh [client]              Tax-loss harvesting opportunities

━━━ FUND ADMINISTRATION ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
/fund-admin:gl-recon                         GL vs prime broker reconciliation
/fund-admin:break-trace                      Root-cause a single break
/fund-admin:accrual-schedule                 Period-end accrual entries
/fund-admin:roll-forward                     Balance sheet roll-forward
/fund-admin:variance-commentary              P&L and BS flux commentary
/fund-admin:nav-tieout                       LP statement vs NAV pack tie-out

━━━ OPERATIONS / KYC ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
/operations:kyc-doc-parse                    Parse onboarding docs → KYC record
/operations:kyc-rules                        Apply rules grid → risk rating

━━━ LSEG (requires subscription) ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
/lseg:macro-rates [country]                  Macro & rates dashboard
/lseg:research-equity [ticker]               Equity research snapshot (live data)
/lseg:analyze-bond-rv [ISIN]                 Bond relative value analysis
/lseg:analyze-bond-basis [future RIC]        Bond futures basis analysis
/lseg:analyze-swap-curve [currency]          Swap curve + curve trades
/lseg:analyze-fx-carry [pair]                FX carry trade evaluation
/lseg:analyze-option-vol [underlying]        Option vol surface + Greeks
/lseg:review-fi-portfolio [ISINs]            Fixed income portfolio review

━━━ S&P GLOBAL (requires subscription) ━━━━━━━━━━━━━━━━━━━━━━━━━━
/sp-global:tear-sheet [ticker]               Company tear sheet (live data)
/sp-global:earnings-preview-beta [ticker]    HTML earnings preview (live data)
/sp-global:funding-digest [sectors]          Weekly deal flow briefing → .pptx

━━━ NAMED AGENTS (end-to-end) ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
/pitch-agent                                 Full pitch deck, end to end
/market-researcher                           Sector → market + comps + ideas
/earnings-reviewer                           Earnings → model update → note
/meeting-prep-agent                          Client meeting → briefing pack
/model-builder                               Any model built to your spec
/gl-reconciler                               Break found + traced + routed
/kyc-screener                                Docs → KYC record + risk rating
/valuation-reviewer                          GP package → valuation + LP report
/month-end-closer                            Month-end → accruals + commentary
/statement-auditor                           LP statement → audit before dist.
```

---

## Getting the Most Out of the Plugins

**1. Give context, not just a ticker.**
Instead of `/private-equity:ic-memo ACME`, say:
> *"ACME Corp — HVAC services, $30M EBITDA, 60% residential / 40% commercial, Texas-based, family-owned for 30 years, asking $210M. Fund mandate: US services, $15–50M EBITDA, control buyouts."*

**2. Chain commands intentionally.**
The output of one command feeds the next. When running a DCF, say "use the comps we just built." When writing an IC memo, say "reference the LBO model we ran."

**3. Use fictional companies to learn.**
All commands work with made-up companies. Make up a B2B SaaS company and run every PE command on it — screen-deal → dd-checklist → ic-memo → lbo → value-creation. You'll understand the full workflow without needing real deal access.

**4. The data limitation is real — and manageable.**
Without live data connectors (LSEG, S&P Global), outputs use training-data estimates. The structure, methodology, and analytical framework are always correct. Only the specific numbers need verification. Use it for structure; verify the numbers independently.

**5. Live data changes everything.**
If your firm has a FactSet, S&P Capital IQ, Bloomberg, or Morningstar subscription, authenticate the MCP connector and every analysis becomes current-data accurate. Ask your administrator about API access pricing — it is often lower than desktop licensing.

---

*Claude for Financial Services | Anthropic | Version based on plugin release May 2026*
*This guide and sample outputs: https://github.com/az9713/financial-services-plugins-demo*
*Plugin source: https://github.com/anthropics/financial-services*
