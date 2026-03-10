# AI Sales Team for Claude Code

**14 Skills · 5 Agents · 4 Scripts · PDF Reports**

A comprehensive AI-powered sales toolkit that transforms Claude Code into a full sales team. Analyze prospects, qualify leads, find decision makers, generate outreach sequences, prepare for meetings, write proposals, handle objections, and produce professional PDF pipeline reports — all from the command line.

---

## What It Does

The AI Sales Team gives Claude Code a complete sales workflow:

- **Prospect Analysis** — Scrape and analyze any company website for sales intelligence
- **Lead Qualification** — Score leads using BANT + MEDDIC frameworks with confidence levels
- **Contact Discovery** — Find decision makers, classify seniority, and predict buying roles
- **Outreach Generation** — Create cold, warm, and referral-based email sequences
- **Meeting Preparation** — Generate comprehensive briefs with talking points and objection responses
- **Proposal Writing** — Build client proposals with 3-tier pricing and ROI projections
- **Pipeline Reporting** — Produce Markdown and PDF reports with score gauges and action plans
- **Competitive Intelligence** — Analyze competitors and build battle cards
- **ICP Development** — Define and refine your Ideal Customer Profile

---

## Quick Start

### One-Line Install

```bash
curl -fsSL https://raw.githubusercontent.com/zubair-trabzada/ai-sales-claude/main/install.sh | bash
```

### Manual Install

```bash
git clone https://github.com/zubair-trabzada/ai-sales-claude.git
cd ai-sales-claude
./install.sh
```

### Install Python Dependencies

```bash
pip3 install -r requirements.txt
```

---

## Command Reference

| Command | Description | Output |
| ------- | ----------- | ------ |
| `/sales prospect <url>` | Full prospect audit (5 parallel agents) | `PROSPECT-ANALYSIS.md` |
| `/sales quick <url>` | 60-second prospect snapshot | Terminal output |
| `/sales research <url>` | Company research & firmographics | `COMPANY-RESEARCH.md` |
| `/sales qualify <url>` | BANT + MEDDIC lead scoring | `LEAD-QUALIFICATION.md` |
| `/sales contacts <url>` | Decision maker identification | `DECISION-MAKERS.md` |
| `/sales outreach <prospect>` | Cold outreach email sequence | `OUTREACH-SEQUENCE.md` |
| `/sales followup <prospect>` | Follow-up email sequence | `FOLLOWUP-SEQUENCE.md` |
| `/sales prep <url>` | Meeting preparation brief | `MEETING-PREP.md` |
| `/sales proposal <client>` | Client proposal generator | `CLIENT-PROPOSAL.md` |
| `/sales objections <topic>` | Objection handling playbook | `OBJECTION-PLAYBOOK.md` |
| `/sales icp <description>` | Ideal Customer Profile builder | `IDEAL-CUSTOMER-PROFILE.md` |
| `/sales competitors <url>` | Competitive intelligence | `COMPETITIVE-INTEL.md` |
| `/sales report` | Sales pipeline report (Markdown) | `SALES-REPORT.md` |
| `/sales report-pdf` | Sales pipeline report (PDF) | `SALES-REPORT-*.pdf` |

---

## How It Works

### Architecture: Orchestrator, Sub-Skills, and Parallel Subagents

The system uses a three-layer architecture:

```
/sales <url>  (Orchestrator Skill)
    |
    ├── Phase 1: Discovery
    |   └── /sales-prospect <url>  (analyze website)
    |
    ├── Phase 2: Parallel Analysis (5 Subagents)
    |   ├── sales-company     → Deep company research
    |   ├── sales-contacts    → Decision maker mapping
    |   ├── sales-opportunity → BANT/MEDDIC scoring
    |   ├── sales-competitive → Competitive analysis
    |   └── sales-strategy    → Outreach strategy
    |
    └── Phase 3: Synthesis
        └── Combined report with scores, contacts, strategy
```

The orchestrator (`/sales`) coordinates the full workflow. Each sub-skill can also be invoked independently for targeted tasks.

---

## Full Prospect Analysis

When you run `/sales <url>`, the system executes a three-phase analysis:

### Phase 1: Discovery

The `analyze_prospect.py` script fetches the company website and subpages (/about, /team, /pricing, /careers, /contact) to extract:

- Company name, description, and industry signals
- Tech stack detection (WordPress, Shopify, Next.js, HubSpot, etc.)
- Social media links
- Team member information
- Pricing tiers
- Job posting indicators
- Contact information
- Company size signals

### Phase 2: Parallel Analysis

Five subagents run in parallel, each with a specialized focus:

1. **Company Agent** — Deep-dives into company background, business model, and growth trajectory
2. **Contacts Agent** — Maps the buying committee with seniority, department, and buying role classification
3. **Opportunity Agent** — Runs BANT + MEDDIC scoring to produce a qualified lead score
4. **Competitive Agent** — Identifies competitors and builds differentiation analysis
5. **Strategy Agent** — Develops personalized outreach strategy and messaging

### Phase 3: Synthesis

Results from all agents are combined into a comprehensive prospect analysis with:

- Overall prospect score and grade
- Decision maker map with recommended approach for each contact
- Competitive positioning strategy
- Personalized outreach sequence
- Recommended next steps with timeline

---

## Prospect Scoring

### BANT Scoring (0-100)

Each BANT dimension is scored 0-25 based on available signals:

| Dimension | Max Score | Signals |
| --------- | --------- | ------- |
| **Budget** | 25 | Funding amount, employee count, pricing visibility, tech spend indicators |
| **Authority** | 25 | Decision makers found, C-suite identified, org chart mapped |
| **Need** | 25 | Pain points detected, relevant job posts, review complaints, competitor dissatisfaction |
| **Timeline** | 25 | Hiring for relevant roles, recent funding, contract renewal, urgency mentions |

### MEDDIC Assessment

Each MEDDIC dimension is assessed for completeness (0-100%):

- **Metrics** — Can we quantify the business impact?
- **Economic Buyer** — Have we identified who controls the budget?
- **Decision Criteria** — Do we know how they will evaluate solutions?
- **Decision Process** — Do we understand their buying process?
- **Identify Pain** — Have we confirmed their pain points?
- **Champion** — Have we found an internal advocate?

### Grade Interpretation

| Score | Grade | Meaning | Action |
| ----- | ----- | ------- | ------ |
| 75-100 | A | High-value prospect | Schedule discovery call immediately |
| 50-74 | B | Promising prospect | Nurture with targeted content |
| 25-49 | C | Needs development | Research more, multi-thread outreach |
| 0-24 | D | Low priority | Add to long-term nurture sequence |

---

## Individual Skills

### /sales-prospect
Analyzes a company website to extract structured intelligence: company info, tech stack, social links, team data, pricing, and hiring signals.

### /sales-research
Performs deep company research beyond the website — industry analysis, business model assessment, growth trajectory, and market position.

### /sales-qualify
Runs the full BANT + MEDDIC scoring algorithm on a prospect. Produces a lead score, grade, confidence level, and recommended next action.

### /sales-contacts
Maps the buying committee by finding leadership and team members. Classifies each contact by seniority (C-Suite to IC), department, and predicted buying role (Economic Buyer, Champion, Evaluator, End User, Blocker).

### /sales-outreach
Generates personalized outreach sequences using cold, warm, or referral templates. Each sequence includes subject lines, email bodies, CTAs, timing, and LinkedIn touchpoints.

### /sales-followup
Creates follow-up sequences for prospects who have engaged but not converted. Adapts tone and content based on previous interactions.

### /sales-prep
Generates a comprehensive meeting preparation brief including company snapshot, attendee profiles, talking points, discovery questions, expected objections, and a quick-reference cheat sheet.

### /sales-proposal
Builds a full client proposal with executive summary, situation analysis, proposed solution, scope of work, timeline, 3-tier pricing, ROI projection, team bios, case studies, and next steps.

### /sales-objections
Creates a customized objection handling playbook with responses for universal, industry-specific, competitive, and pricing objections using the LAER framework.

### /sales-icp
Develops or refines an Ideal Customer Profile based on your best customers, defining firmographic, technographic, and behavioral characteristics.

### /sales-competitors
Performs competitive intelligence gathering — identifies competitors, analyzes their positioning, pricing, and strengths/weaknesses relative to your offering.

### /sales-report
Generates a Markdown sales pipeline report summarizing all active prospects, scores, stages, and recommended actions.

### /sales-report-pdf
Produces a professional PDF pipeline report with score gauges, bar charts, prospect cards, pipeline summary tables, and prioritized action plans.

---

## Python Scripts

### analyze_prospect.py
Fetches a company website and extracts structured data for sales intelligence. Uses `urllib` with no external dependencies required.

```bash
python3 scripts/analyze_prospect.py --url https://example.com --output json
```

### lead_scorer.py
Implements the BANT + MEDDIC scoring algorithm. Accepts JSON input via file or stdin.

```bash
python3 scripts/lead_scorer.py prospect_data.json
```

### contact_finder.py
Extracts leadership and team information from company web pages. Finds names, titles, seniority, departments, and LinkedIn profiles.

```bash
python3 scripts/contact_finder.py --url https://example.com --output json
```

### generate_pdf_report.py
Generates professional PDF pipeline reports with ReportLab. Run with no arguments for a demo report.

```bash
python3 scripts/generate_pdf_report.py                    # demo mode
python3 scripts/generate_pdf_report.py data.json out.pdf  # from data
```

---

## Templates

The following templates are included and used by the skills:

| Template | Description |
| -------- | ----------- |
| `outreach-cold.md` | 5-email cold outreach sequence with LinkedIn touchpoints |
| `outreach-warm.md` | 3-email warm introduction sequence |
| `outreach-referral.md` | 3-email referral-based outreach sequence |
| `meeting-prep.md` | Comprehensive meeting preparation brief |
| `proposal-template.md` | Full client proposal with 11 sections |
| `objection-playbook.md` | Objection handling playbook with 15 universal objections |

---

## Examples

### Full Prospect Analysis

```
> /sales prospect https://stripe.com

Running full prospect analysis on stripe.com...
Phase 1: Discovering company information...
Phase 2: Running parallel analysis (5 agents)...
Phase 3: Synthesizing results...

Output: PROSPECT-ANALYSIS.md
```

### Quick Lead Qualification

```
> /sales qualify https://notion.so

Analyzing notion.so for lead qualification...
BANT Score: 78/100 (Grade A)
Budget: 22/25 | Authority: 18/25 | Need: 20/25 | Timeline: 18/25
MEDDIC Completeness: 72%
Action: Schedule discovery call — high-priority prospect.

Output: LEAD-QUALIFICATION.md
```

### Generate Outreach Sequence

```
> /sales outreach https://linear.app

Generating outreach sequence for linear.app...
Type: Cold outreach (5-email sequence)
Personalized for: Engineering-focused B2B SaaS

Output: OUTREACH-SEQUENCE.md
```

### Meeting Prep

```
> /sales prep https://datadog.com

Generating meeting brief for datadog.com...
Attendees profiled: 3
Talking points: 7
Discovery questions: 10
Objection responses: 5

Output: MEETING-PREP.md
```

---

## Requirements

- **Claude Code** — Required for skills and agents
- **Python 3.8+** — Required for scripts
- **reportlab** — Required for PDF report generation (`pip3 install reportlab`)
- **beautifulsoup4** — Optional, enhances HTML parsing (`pip3 install beautifulsoup4`)
- **requests** — Optional fallback for URL fetching (`pip3 install requests`)

---

## Uninstall

```bash
# From the repository directory
./uninstall.sh

# Or manually
curl -fsSL https://raw.githubusercontent.com/zubair-trabzada/ai-sales-claude/main/uninstall.sh | bash
```

This removes all skills, agents, scripts, and templates. Python packages are not removed.

---

## License

MIT License. Copyright (c) 2026 Zubair Trabzada. See [LICENSE](LICENSE) for details.
