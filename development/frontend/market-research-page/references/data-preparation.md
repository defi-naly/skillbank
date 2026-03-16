# Data Preparation

How to structure market research into chartable datasets for each section. Start here before writing any components.

---

## Step 1: Collect Raw Research

Before building the page, gather data in these categories. Each one maps to a specific section and chart type.

| Category | What to collect | Chart it feeds |
|----------|----------------|----------------|
| Market sizing | TAM, SAM, SOM with calculation | TAM/SAM/SOM waterfall bars |
| Market funnel | 5-6 narrowing steps with counts | Market funnel custom bars |
| Growth data | 5-6 years of market growth | Vertical BarChart |
| Pain points | 5-6 pain areas with % severity | Horizontal BarChart |
| Headline metrics | 3 shocking stats about the pain | Metric cards grid |
| Customer persona | Size segments + industry breakdown | Donut + horizontal BarChart |
| Status-quo cost | 4-6 cost components | Vertical BarChart |
| Competitors | 10-16 products with annual price + category | Horizontal BarChart |
| Product features | 10-16 features grouped by tier | Accordion rows |
| Pricing justification | Value components with ranges | Value table |
| Revenue projections | Customer trajectories for 3 scenarios | Stacked AreaChart |
| Unit economics | LTV, CAC, payback, ratio | Metric cards |
| Data sources | Citation for every number | Footnote section |

---

## Step 2: Structure Data as TypeScript Constants

### Market Funnel Data

```ts
const funnelData = [
  { label: "Total addressable entities", value: 624219, barColor: "bg-foreground/30", dotColor: "bg-foreground/30" },
  { label: "Target legal form", value: 200000, barColor: "bg-foreground/50", dotColor: "bg-foreground/50" },
  { label: "Size filter (<10 emp)", value: 170000, barColor: "bg-foreground/70", dotColor: "bg-foreground/70" },
  { label: "On key platform", value: 100000, barColor: "bg-amber-500", dotColor: "bg-amber-500" },
  { label: "Paying incumbent premium", value: 45000, barColor: "bg-teal-600", dotColor: "bg-teal-600" },
  { label: "Year 5 target", value: 1350, barColor: "bg-foreground/40", dotColor: "bg-foreground/40" },
];
```

**Rules**:
- Always sort descending (largest to smallest)
- Include `barColor` and `dotColor` for each row (Tailwind classes)
- 5-6 steps is ideal

### Pain Point Data

```ts
const painData = [
  { task: "Accounting & audit", pctCiting: 50 },
  { task: "VAT returns", pctCiting: 46 },
  { task: "Source tax", pctCiting: 46 },
  { task: "Statistics & reporting", pctCiting: 38 },
  { task: "Health & safety", pctCiting: 30 },
  { task: "Data protection", pctCiting: 25 },
];
```

**Rules**:
- Sort descending by percentage
- Top 3 get accent color in the chart; rest get muted
- Include source and year in the CardFooter

### Competitor Data

```ts
const competitorData = [
  { name: "Free Tool", annual: 0, type: "Software" },
  { name: "Basic SaaS", annual: 120, type: "Software" },
  // ... more competitors ...
  { name: "Your Product", annual: 2090, type: "You" },
  // ... more competitors ...
  { name: "Incumbent (high)", annual: 6000, type: "Traditional" },
];

const typeColors: Record<string, string> = {
  Software: "#A1A1AA",
  "Digital Alternative": "#3B82F6",
  You: "#D42A2A",
  Traditional: "#18181B",
};
```

**Rules**:
- Sort ascending by price
- 4 categories: Software, Digital Alternative, Your Product, Traditional/Incumbent
- Each category gets a distinct color
- Include a `ReferenceLine` at your price point
- 12-16 entries is ideal for visual impact

### Customer Persona Data

```ts
// For the donut chart
const sizeSegments = [
  { segment: "0 employees", count: 18000, pct: 40 },
  { segment: "1 employee", count: 11250, pct: 25 },
  { segment: "2-3 employees", count: 9000, pct: 20 },
  { segment: "4-5 employees", count: 4500, pct: 10 },
  { segment: "6-10 employees", count: 2250, pct: 5 },
];

// For the horizontal bar chart
const industryBreakdown = [
  { industry: "Consulting", pct: 35 },
  { industry: "IT / software", pct: 20 },
  { industry: "Trade / e-commerce", pct: 15 },
  { industry: "Construction", pct: 10 },
  { industry: "Healthcare", pct: 8 },
  { industry: "Other", pct: 12 },
];
```

**Rules**:
- Size segments: sorted by count descending, must sum to 100%
- Industry: sorted by percentage descending, top 2 get accent color

### Revenue Projection Data

```ts
type Scenario = "conservative" | "base" | "optimistic";

const customerTrajectories: Record<Scenario, number[]> = {
  conservative: [112, 338, 675, 900, 1125],   // 5 years
  base:         [225, 675, 1575, 2475, 3375],
  optimistic:   [375, 1250, 2813, 4375, 5625],
};

const scenarios = [
  { key: "conservative", label: "Conservative", penetration: "2.5%" },
  { key: "base",         label: "Base case",    penetration: "7.5%" },
  { key: "optimistic",   label: "Optimistic",   penetration: "12.5%" },
];

const BASE_PRICE = 2090;

// Optional add-on revenue layers
const ADDON_PRICE = 590;
const ADDON_ADOPTION = 0.20;  // 20% of customers
const POST_PMF_PRICE = 2490;  // Year 2+ new customers

// Unit economics
const LTV = 7480;
const LTV_CAC_RATIO = 5;
```

**Rules**:
- 3 scenarios is standard (conservative, base, optimistic)
- Customer numbers must be realistic (derived from penetration % of addressable market)
- Revenue = customers x price (compute dynamically, don't hardcode)
- Add-on layers toggle on/off in the UI

### TAM/SAM/SOM Data

```ts
const waterfallData = [
  { label: "TAM", sublabel: "All compliance spend", value: 900, display: "$900M", barColor: "bg-foreground/15" },
  { label: "SAM", sublabel: "Target segment on key platform", value: 250, display: "$250M", barColor: "bg-foreground/40" },
  { label: "SOM", sublabel: "Reachable, willing to pay", value: 112, display: "$112M", barColor: "bg-foreground/70" },
  { label: "Yr 5", sublabel: "Base case capture", value: 7.05, display: "$7.05M", barColor: "bg-accent" },
];
```

**Rules**:
- Use manual bar widths (not linear scale) because the jump from TAM to Year 5 is too large
- Recommended widths: `[85, 65, 48, 12]` (logarithmic-ish)
- Each row needs a sublabel explaining the calculation

### Cost Breakdown Data

```ts
const costData = [
  { task: "Year-end close", cost: 2000 },
  { task: "Tax return", cost: 1200 },
  { task: "VAT filing", cost: 800 },
  { task: "Receipt reconciliation", cost: 600 },
  { task: "Advisory", cost: 400 },
];

const totalCost = costData.reduce((sum, d) => sum + d.cost, 0);
```

**Rules**:
- Sort descending by cost
- Show total in CardFooter
- 4-6 components is ideal

---

## Step 3: Source Everything

Every number on the page needs a citation. Organize sources by topic:

```ts
const sources = {
  marketSize: "BFS STATENT 2023 (624k SMEs, 141k active GmbHs). Commercial register (~200k total).",
  formationRates: "IFJ Institut für Jungunternehmen 2023-2025. BFS UDEMO 2020-2022.",
  adminBurden: "SECO Bürokratiemonitor 2018 & 2022. BSS/ifo Bürokratiekostenindex 2025.",
  competitorPricing: "Published pricing pages as of [date]. Gryps.ch cost surveys.",
  personaData: "BFS STATENT 2023 employment statistics. BFS NOGA sector classifications.",
  tamSamSom: "TAM: 200k × $4,500 avg. SAM: 50k × $5,000. SOM: 45k × $2,500.",
};
```

Display in the `DataSourcesFootnote` component at the bottom of the page. Use `text-xs text-muted-foreground/60` styling — visible but not distracting.

---

## Checklist Before Building

- [ ] All funnel steps have verified numbers
- [ ] Pain point percentages come from cited surveys
- [ ] Competitor pricing is current (check published pricing pages)
- [ ] Persona segments sum to 100%
- [ ] Revenue trajectories are mathematically consistent (customers x price = ARR)
- [ ] TAM > SAM > SOM > Year 5 target (always narrowing)
- [ ] Every number has a source citation
- [ ] Cost breakdown components sum to a realistic total
- [ ] LTV and CAC metrics are consistent with pricing and churn assumptions
