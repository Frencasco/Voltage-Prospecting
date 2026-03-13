# Voltaage Lead Discovery

Find new prospects matching Voltaage's Ideal Customer Profile in a specified industry vertical.

## Usage

```
/sales discover <industry>
```

**Accepted industries:** `cpo`, `energy`, `telecom`, `retail`, `logistics`, `renewable`, `real-estate`, `utilities`, or `all`

---

## Process

### Step 1: Load Voltaage Context

Read `voltaage-context.md` from the project root. Understand Voltaage's target industries (Tier 1/2/3), pain points, and ICP criteria.

If `IDEAL-CUSTOMER-PROFILE.md` exists, load it for additional screening criteria.

### Step 2: Run Targeted Web Searches

Based on the specified industry, run multiple WebSearch queries to find prospect companies. Use these search templates:

#### CPO (Charge Point Operators)
```
"charge point operator" Europe
"EV charging network" company Europe
"expanding charging network" OR "new stations" 2025 OR 2026
"CPO" "electric vehicle" charging company
AFIR compliance "charging network" company
```

#### Energy / Utilities
```
"energy syndicate" OR "utility company" "infrastructure planning" Europe
"grid planning" OR "grid expansion" company Europe
"smart grid" company Europe France OR Italy
"energy transition" "infrastructure" company
```

#### Telecom
```
"5G deployment" OR "tower company" OR "cell tower" Europe
"network expansion" telecom operator Europe
"tower placement" OR "coverage planning" company
```

#### Retail Networks
```
"retail expansion" OR "store network" "location planning" Europe
"franchise network" expansion Europe
"retail chain" "new locations" Europe
```

#### Logistics
```
"logistics network" "depot" OR "warehouse" "expansion" Europe
"last mile delivery" "hub" company Europe
"distribution network" "optimization" company
```

#### Renewable Energy
```
"solar farm" OR "wind farm" "site selection" Europe
"renewable energy developer" Europe
"energy storage" "project development" company
```

#### Real Estate
```
"real estate developer" "infrastructure" Europe
"mixed-use development" company Europe France OR Italy
"property development" "location intelligence" company
```

#### Utilities
```
"utility company" "grid planning" OR "demand forecasting" Europe
"electricity distribution" "network planning" company
"electrification" "infrastructure upgrade" utility
```

For `all`, run the top 2 queries from each industry category.

### Step 3: Screen Results Against Voltaage ICP

For each company found, quickly assess:

1. **Industry Tier** — Is this a Tier 1, 2, or 3 industry for Voltaage?
2. **Geographic Presence** — Do they operate in France/Italy (A), broader EU (B), or globally (C)?
3. **Infrastructure Footprint** — Do they operate physical infrastructure networks? How large?
4. **Growth Signals** — Are they expanding, deploying new infrastructure, or recently funded?
5. **Pain Signal** — Any evidence of infrastructure planning challenges, utilization issues, or manual processes?

Rate each prospect: **A** (strong fit), **B** (good fit), **C** (possible fit), **D** (poor fit)

### Step 4: Enrich Top Prospects

For the top 10 prospects (rated A or B), use WebFetch to visit their homepage and extract:
- Company description and positioning
- Geographic presence
- Infrastructure scale signals
- Technology signals (GIS tools, OCPP, fleet management)
- Recent news (expansion, funding, regulatory)

### Step 5: Generate Prospect List

Output a scored, prioritized prospect list.

---

## Output

Save to `PROSPECT-LIST.md` in the current directory:

```markdown
# Voltaage Prospect Discovery — [Industry]

**Generated:** [date]
**Search Scope:** [industry vertical]
**Total Prospects Found:** [count]
**A-Rated:** [count] | **B-Rated:** [count] | **C-Rated:** [count]

---

## Priority Prospects (A-Rated)

### 1. [Company Name]
- **Website:** [url]
- **Industry:** [industry] (Tier [X])
- **Location:** [country/region]
- **Infrastructure:** [description of their infrastructure network]
- **Why They Fit Voltaage:** [2-3 sentences on specific fit signals]
- **Pain Signals Detected:** [specific evidence]
- **Suggested Action:** `/sales prospect [url]` for full analysis

### 2. [Company Name]
[same structure]

---

## Strong Prospects (B-Rated)

### [number]. [Company Name]
- **Website:** [url]
- **Industry:** [industry] (Tier [X])
- **Location:** [country/region]
- **Infrastructure:** [description]
- **Why They Fit:** [brief]
- **Suggested Action:** `/sales research [url]` for deeper look

---

## Possible Prospects (C-Rated)

| Company | Website | Industry | Location | Quick Assessment |
|---------|---------|----------|----------|-----------------|
| [name] | [url] | [industry] | [location] | [one-line assessment] |

---

## Search Queries Used
[List all search queries run for reproducibility]

## Next Steps
1. Run `/sales prospect <url>` on top A-rated prospects
2. Run `/sales research <url>` on B-rated prospects to validate fit
3. Re-run `/sales discover <industry>` monthly to find new entrants
```

---

## Important Rules

1. **Only include real companies.** Every company listed must be a real entity found through web search. Never fabricate company names or details.
2. **Prioritize quality over quantity.** 5 well-researched A-rated prospects are more valuable than 50 poorly screened names.
3. **Focus on Voltaage fit.** Every prospect must be evaluated through the lens of Voltaage's specific products and capabilities, not generic B2B fit.
4. **Include actionable next steps.** Each prospect entry should tell the user exactly what to do next.
5. **Geographic focus.** Prioritize France and Italy, then broader EU, then global. Voltaage's data and operations are strongest in France/Italy.
6. **Note data freshness.** Flag when information may be outdated. Infrastructure companies evolve quickly.
