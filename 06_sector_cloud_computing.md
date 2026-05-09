# About This Command: `/equity-research:sector`

## What it does
Generates an **industry landscape report** — a structured overview of an entire sector that an equity research analyst would produce to orient institutional investors before initiating coverage on individual names. It answers the macro question: "What is this industry, who are the players, and what are the investment implications?" It is the foundation on which individual stock theses are built.

## How to invoke
```
/equity-research:sector [sector or industry name]
```
Example: `/equity-research:sector cloud computing`

Any sector or sub-sector works: "AI semiconductors", "wealth management", "GLP-1 obesity drugs", "defence primes", "community banking", etc. If no argument is given, the skill asks which industry to cover.

## What it produces
A structured sector report covering:
1. **Market sizing** — TAM, segment breakdown, and 3–5 year CAGR
2. **Key demand drivers** — secular tailwinds powering growth
3. **Competitive dynamics** — market share breakdown, moat analysis, tier-1 vs. tier-2 players
4. **Competitive intensity assessment** — high / medium / low by sub-segment
5. **Investment implications** — bull case drivers, bear case risks, stock-screening framework
6. **Valuation context** — sector median multiples and what the market is pricing in
7. **Summary sector stance** — Overweight / Neutral / Underweight with rationale

## Typical use cases
- Equity research analysts writing sector primers before initiating coverage
- Portfolio managers getting oriented on a new industry
- Associates preparing sector backgrounders for client meetings
- Teaching sector analysis frameworks to junior analysts

---

# Cloud Computing — Industry Landscape Report
*Equity Research | Sector Overview | May 2026*

---

## Market Sizing

**Total Addressable Market**

Global cloud services spending reached approximately **$675–700 billion in 2025**, up ~20% year-over-year, and is on track to surpass **$1 trillion by 2027–2028**. The long-run TAM — encompassing full enterprise IT migration, AI inference workloads, and emerging sovereign cloud — is routinely estimated at **$2.5–3 trillion**.

| Segment | 2025E Market Size | 2025–2028 CAGR |
|---|---|---|
| Infrastructure (IaaS) | ~$290B | ~22% |
| Platform (PaaS) | ~$175B | ~25% |
| Software (SaaS) | ~$215B | ~17% |
| **Total** | **~$680B** | **~21%** |

**Key demand drivers:**
- Generative AI workload migration: GPU clusters, inference APIs, and model hosting are the fastest-growing IaaS subcategory
- Enterprise digital transformation still in early innings — estimated 30–35% of global enterprise workloads have migrated to cloud
- Edge computing and IoT device proliferation extending cloud architecture outward
- Sovereign cloud mandates in the EU, Middle East, and Southeast Asia creating greenfield addressable demand

---

## Competitive Dynamics

### The Big Three — Entrenched Oligopoly

Three hyperscalers control approximately **65–68% of global IaaS/PaaS spend**. Their moats are structural: datacenters require $50–100B+ annual capex, proprietary silicon (TPUs, Trainium, Cobalt) compounds the advantage, and switching costs compound with time as customers integrate managed services.

| Provider | Est. Cloud Revenue (2025) | IaaS Market Share | Key Moat |
|---|---|---|---|
| **Amazon AWS** | ~$115B | ~31% | Breadth (200+ services), SMB/startup flywheel |
| **Microsoft Azure** | ~$105B | ~25% | Enterprise Office 365 integration, OpenAI exclusivity |
| **Google Cloud** | ~$55B | ~12% | AI/ML tooling (Vertex AI, TPUs), data analytics (BigQuery) |

**AWS** leads on breadth and developer mindshare but has ceded ground in AI workloads to Azure's OpenAI partnership. **Azure** is winning enterprise consolidation deals — its ability to bundle Office 365, Copilot, and Azure into a single negotiation is a durable structural advantage. **Google Cloud** is growing fastest (~28% YoY) off a smaller base, with technical credibility in AI but persistent go-to-market challenges.

### Tier 2 — Specialists and Challengers

| Provider | Positioning | Strength |
|---|---|---|
| **Oracle Cloud (OCI)** | Database lift-and-shift; AI GPU clusters | NVIDIA GPU availability, aggressive pricing |
| **Alibaba Cloud** | Asia-Pacific dominance | China + Southeast Asia regulatory positioning |
| **Snowflake / Databricks** | Data cloud layer on top of hyperscalers | Multi-cloud data fabric; not direct IaaS competitors |
| **CoreWeave / Lambda** | GPU-native cloud for AI | Pure-play inference; beneficiary of hyperscaler GPU constraints |

### Competitive Intensity Assessment

**High** at the IaaS commodity layer (compute, storage, networking) — pricing pressure is structural and relentless. Spot instance discounts on AWS/Azure/GCP have compressed gross margins at the infrastructure layer.

**Moderate** at the managed services layer — differentiation through proprietary databases (Aurora, Cosmos DB, Spanner), AI platforms (Bedrock, Azure AI Studio, Vertex), and developer tooling creates stickiness.

**Low** at the AI platform layer — still early, rapidly evolving, and winner-take-most dynamics are unclear. Microsoft/OpenAI have a meaningful first-mover advantage but Google's Gemini integration and AWS's Bedrock multi-model approach are credible responses.

---

## Investment Implications

### Bull Case Drivers

1. **AI as cloud demand multiplier.** Training a frontier model costs $50–500M in compute; inference at scale costs multiples more over time. Every dollar spent on AI models flows through hyperscaler infrastructure at 60–70%+ gross margins. This is structurally additive demand, not a substitution.

2. **Enterprise migration still early.** With only ~33% of enterprise workloads migrated, the secular tailwind has years of runway. Large financial services, healthcare, and government verticals are just beginning meaningful migration.

3. **Pricing discipline improving.** After 2022–2023 discount wars, hyperscalers have pulled back on aggressive committed-use discounting. Net revenue retention across cloud platforms is recovering toward 115–125% for top cohorts.

4. **Sovereign cloud.** Government-mandated local cloud regions in the EU (EUCS), Saudi Arabia, India, and Japan represent incremental, high-margin greenfield with limited competition.

### Bear Case / Key Risks

1. **CapEx overhang.** AWS, Azure, and Google collectively spent ~$200B on capex in 2025, largely data center buildout for AI. If AI demand materializes slower than expected, depreciation drag could pressure margins for 3–5 years.

2. **Commoditization at the infrastructure layer.** OCI and CoreWeave are pricing GPU compute 20–40% below hyperscaler list rates. If GPU availability normalizes, pricing pressure could accelerate.

3. **Multi-cloud fragmentation.** Enterprise adoption of multi-cloud architectures reduces hyperscaler lock-in. Platforms like HashiCorp, Terraform, and Kubernetes reduce migration friction between clouds.

4. **Regulatory risk.** EU DMA, UK CMA, and US FTC scrutiny of hyperscaler bundling (Microsoft in particular) could force unbundling of Azure + Office + Copilot.

5. **On-premise renaissance.** High cloud bills are prompting repatriation of predictable, stable workloads. Dell, HPE, and Pure Storage are beneficiaries of this counter-trend.

### Stock Screening Framework

For equity investors, the most attractive subsets of the cloud value chain are currently:

| Theme | Investable Expression | Why |
|---|---|---|
| AI infrastructure pull-through | **MSFT, GOOGL, AMZN** | Direct beneficiaries of AI capex; pricing power confirmed |
| GPU-native cloud | **CoreWeave** (recently public) | Pure-play; constrained supply → pricing power |
| Data layer | **SNOW, DBX** (private) | Multi-cloud agnostic; sticky enterprise contracts |
| Cloud security | **CRWD, ZS, PANW** | Every migrated workload adds attack surface |
| Optimization / FinOps | **HASHI, DDOG** | Counter-cyclically resilient; needed as bills grow |

### Valuation Context

| Company | Cloud EV/Revenue | Cloud Implied Growth (Consensus) |
|---|---|---|
| AWS (within AMZN) | ~6–8x | ~20–22% |
| Azure (within MSFT) | ~8–10x | ~23–26% |
| Google Cloud (within GOOGL) | ~4–6x | ~27–30% |

---

## Summary View

**Sector stance: Constructive / Overweight**

Cloud computing is not a mature sector — it is in the middle innings of a 10–15 year secular migration with AI acting as an unexpected demand accelerant. The primary risk is valuation: the sector is not cheap, and any evidence that AI capex is misallocated would re-rate multiples quickly. Within the sector, prefer **Azure/Microsoft** (best AI monetization path + enterprise bundling), **Google Cloud** (attractive growth at a relative valuation discount), and **GPU-native specialists** for higher-risk/higher-return positioning.

---

> **Data note:** All figures are estimates based on publicly available information through early 2026. No live data feed was used. Current market data should be verified independently before any investment decision. This does not constitute investment advice.

*Generated using the equity-research:sector skill | Claude for Financial Services | May 2026*
