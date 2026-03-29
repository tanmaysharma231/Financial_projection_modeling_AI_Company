# Financia - 5-Year Financial Model
NO AI used for building the projection

A full bottom-up financial model built for a SaaS startup that uses AI to generate investor-ready financial projections for early-stage founders.

Built as part of ENTP 5773 (Entrepreneurial Finance) at the University of Utah.

---

## What This Models

Financia is a hybrid SaaS platform targeting startups, accelerators, and venture capital firms. The model covers a 5-year monthly projection from pre-revenue through scale, built from first principles rather than top-down assumptions.

**Key outputs:**
- Reaches operating profitability in Year 4 Q1
- Ends Year 5 with ~$26M cash and ~$3.6M monthly revenue
- Scales from 7 employees (Year 1) to 43 (Year 5)

---

## Model Structure

### Revenue (`Rev`, `Sales Rev`)
- Three customer tiers: Small Cap, Mid Cap, Large Cap
- Two product lines: Basic SaaS subscription and Premium customizable service
- Monthly pricing: $100-$700 (Basic) and $250-$1,400 (Premium) depending on tier and year
- One-time onboarding fees modeled separately
- Monthly new customer acquisition tied to sales headcount with a learning curve - new reps ramp over 1-2 months before reaching full productivity
- Attrition rate baked in; customer count is net not gross

### Headcount (`HeadCount`, `Sales & Marketing`, `R&D`, `G&A`)
- Phased hiring across three functions: G&A, Sales & Marketing, R&D
- Sales roles include VP, Regional Manager, Sales Reps, Senior Reps, Customer Success, and Additional Reps added in later years
- Each role has a defined salary, benefits rate, T&E percentage, and commission structure
- Deferred compensation modeled for early employees - founders take reduced cash salary in Years 1-2 with deferred amounts paid out in Years 3-4

### Cost of Goods Sold (`P&L`)
- Per-user compute costs segmented by tier and tier multiplier
- Fixed cloud hosting cost that scales by year
- Variable compute cost tied to actual customer count monthly

### Operating Expenses
- **R&D**: Salaries, benefits, T&E, training, dev SaaS tools - scales with engineering headcount
- **G&A**: Wages, deferred comp, benefits, T&E, office rent, insurance, legal counsel, office supplies, HR consultant
- **Sales & Marketing**: Advertising, content creation, SEO, marketing wages, sales team wages and commissions

### Capital Expenditure (`CapEx`)
- Developer workstations/laptops per employee
- Office networking gear
- Furniture and fixtures per employee
- Leasehold improvements
- All assets depreciated on a straight-line basis over 5 years
- PPE tracked monthly with net book value carried to balance sheet

### Debt (`Loan`)
- $250,000 loan at 8% annual interest
- 5-year term, monthly amortization schedule
- Principal and interest separated monthly
- Fully paid off by end of Year 5

### Summary Statements (`Summary P&L`, `P&L`, `Balance Sheet`, `Company Summary W Graphs`)
- Monthly P&L flowing through gross profit, operating expenses, EBITDA, depreciation, interest, pre-tax income, taxes at 20%, net income
- Quarterly summary P&L for investor readability
- Balance sheet with cash, accounts receivable, deferred expenses, PPE, loan, deferred compensation payable, and equity
- Company summary tab with graphs for ending cash, operating income, and revenue

---

## Key Assumptions

| Assumption | Value |
|---|---|
| Dev runway before revenue | 6 months |
| First revenue | Month 7 |
| Enterprise customers | Year 1 (late) |
| Sales rep ramp time | 1-2 months before full productivity |
| Attrition rate | Modeled monthly, baked into net customer count |
| Benefits rate | 22% of salary |
| Loan interest rate | 8% annually |
| Tax rate | 20% (applied only when profitable) |
| Depreciation | Straight-line over 5 years |

---

## Design Decisions and Why

These aren't arbitrary assumptions - each one reflects a specific business reasoning decision.

**Compute costs: unit economics vs total spend**
Cost per user decreases as scale increases - this is the standard cloud economy of scale where infrastructure becomes more efficient at volume. But total compute spend still increases as the customer base grows. We modeled both effects separately: per-user cost goes down by tier multiplier over time, while fixed hosting costs step up by year to reflect real infrastructure growth. A model that only shows unit economics improving without showing absolute cost growth would be misleading to an investor.

**Founder deferred compensation instead of zero salary**
Zero founder salary is common advice but it's bad advice. Founders who pay themselves nothing eventually burn out, make desperate decisions, or leave. We modeled founders taking a reduced but real cash salary in Years 1-2 with deferred amounts payable in Years 3-4 when the company has more runway. The logic: investors would rather see a realistic survival plan than a heroic assumption that founders will work for free indefinitely. Zero salary also makes cap table conversations harder later - deferred comp is a cleaner liability than retroactive equity adjustments.

**Stock options vs deferred compensation**
Stock options are better for long-term retention and alignment. Deferred comp was chosen here specifically because it reflects short-term survival reality. For a pre-revenue startup, options are a promise about future value. Deferred comp is a commitment about near-term cash flow. We chose deferred comp to stress-test whether the model could actually support founder survival without equity dilution.

**Loan to preserve cap table**
Rather than issuing equity for all early capital needs, we modeled a $250,000 loan at market rate. The reasoning: early equity is your most expensive equity. Taking on manageable debt to cover initial CAPEX and runway preserves cap table room for future rounds where you can negotiate from a position of traction rather than desperation. The loan is fully amortized by Year 5, so the model shows it as a finite cost not a permanent liability.

**Enterprise customers arriving late Year 1**
Enterprise deals take time - longer sales cycles, procurement processes, legal review, security assessment. We didn't model enterprise revenue in the first months because it would be unrealistic. The secondary logic: some of our early Small Cap and Mid Cap customers grow over time and require enterprise-level features by late Year 1. So enterprise arrival isn't just cold outbound - it includes organic conversion from existing customers scaling up, which is more defensible than assuming you can cold-close enterprise from day one.

**Attrition: higher early, lower later**
Early-stage SaaS products have higher churn because the product is less mature, onboarding is rougher, and customers are still evaluating fit. We modeled attrition higher in Years 1-2 and reduced it progressively through Year 5, reflecting product maturity, better customer success processes, and the natural stickiness that comes with deep workflow integration. This was calibrated against publicly available attrition benchmarks for early-stage and AI-native SaaS companies.

**Sales ramp tied to marketing spend and word of mouth**
New sales reps don't immediately perform at full quota. We modeled a 1-2 month ramp before a new hire reaches full productivity. Beyond individual rep ramp, total sales velocity also scales with marketing investment - as we spend more on advertising, SEO, and content, inbound pipeline grows and reps close faster. The model reflects this compounding effect: sales output is a function of both headcount and marketing spend, not headcount alone.

**One-time fee plus subscription**
The initial financial projection a founder needs is a one-time deliverable - you don't need a new projection every month. We modeled a one-time setup fee for the core projection, with an ongoing subscription for maintenance, updates, and new scenario modeling. We also assumed a percentage of customers only ever buy the one-time product and never convert to subscription - modeling this honestly reduces revenue optimism and makes the recurring revenue projections more credible.

**Customer tiers based on usage and feature needs**
Small Cap, Mid Cap, and Large Cap aren't just pricing segments - they reflect genuinely different product needs. Larger companies need more integrations, more customization, dedicated support, and more complex scenario modeling. The tiered pricing reflects tiered value delivery, not arbitrary price discrimination. Premium tier pricing scales more steeply than Basic because the incremental value to a large enterprise is meaningfully higher.

---

We initially built the model conservatively - a 3-person team, slow sales ramp, modest growth assumptions. The professor pushed back: **work backwards from where you need to be, not forwards from what feels safe.**

The tension between bottom-up and top-down modeling is real. Bottom-up keeps you honest about what's operationally achievable. Top-down keeps you ambitious about what investors need to see. The best models hold both at once.

The deeper lesson: **the assumptions matter more than the spreadsheet.** A model is only as good as the business logic behind it. Sales ramp curves, attrition, deferred comp, compute cost scaling by tier - these aren't accounting details, they're bets about how the business actually works.

---

## Tools Used

- Microsoft Excel
- University of Utah ENTP 5773 framework (Prof. Taft)

---

## About

Built by Tanmay Sharma as part of the Entrepreneurial Finance course at the University of Utah. The course combined financial modeling with startup strategy, patent law, and investor-readiness frameworks.
