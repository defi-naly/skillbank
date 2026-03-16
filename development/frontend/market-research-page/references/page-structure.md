# Page Structure — The 4-Act Market Narrative

Complete section-by-section blueprint for building a market research page. Each section describes what to show, what chart type to use, and what data is needed.

---

## Main Page Layout

```tsx
export default function MarketPage() {
  return (
    <>
      <Header />
      <main>
        {/* Act 1: THE MARKET */}
        <div className="bg-background">
          <MarketHero />
          <MarketFunnel />
          <GrowthContext />
          <GrowthTrends />
        </div>

        <div className="h-px bg-border/40" />

        {/* Act 2: THE PAIN */}
        <div className="bg-[#FAFAFA]">
          <CoreInsight />
          <PainPoints />
          <CustomerPersona />
          <CostBreakdown />
        </div>

        <div className="h-px bg-border/40" />

        {/* Act 3: THE SOLUTION */}
        <div className="bg-background">
          <ProductTiers />
          <ScopeAndArchitecture />
        </div>

        <div className="h-px bg-border/40" />

        {/* Act 4: THE OPPORTUNITY */}
        <div className="bg-[#FAFAFA]">
          <CompetitorLandscape />
          <MarketSizing />
          <PricingStrategy />
          <RevenueProjections />
        </div>

        <div className="h-px bg-border/40" />

        {/* Appendix */}
        <div className="bg-background">
          <DataSourcesFootnote />
        </div>
      </main>
      <Footer />
    </>
  );
}
```

---

## Act 1: THE MARKET

### Section 1.1 — Hero

**Purpose**: Set the stage. Title + subtitle + optional key metrics.

**Content**:
- Section label (small caps, accent color): "Market Opportunity"
- H1: The bold thesis statement (e.g., "The market opportunity")
- Subtitle: One-line framing (e.g., "Why [market] is ready for [solution]")
- Optional: 4 key metrics displayed prominently

**Chart**: None (pure narrative)

**Data needed**: The thesis statement and 3-4 headline numbers

### Section 1.2 — Market Funnel

**Purpose**: Show how the total market narrows to your target segment.

**Content**:
- Narrative paragraph explaining the funnel logic
- Custom horizontal bar chart (CSS-animated, not Recharts) showing 5-6 stages
- Side legend with exact numbers
- CardFooter with addressable market callout

**Chart type**: Custom CSS horizontal bars (animated width on scroll-reveal)

**Data needed**: 5-6 rows of `{ label, value, barColor }` narrowing from total market to target

**Why CSS bars, not Recharts**: The funnel needs labels inside bars, animated widths on scroll, and a side legend — easier with custom divs than Recharts.

### Section 1.3 — Growth Context

**Purpose**: Explain the structural/regulatory/market forces that create the opportunity.

**Content**:
- Narrative explaining why this market exists (regulations, structural gaps, trends)
- A "key fact" Card with a big number, progress bar, and blockquote (e.g., a regulatory threshold)
- Source footnotes

**Chart type**: Progress bar or simple visual inside a Card

**Data needed**: The structural insight, key regulation/threshold, authoritative quote

### Section 1.4 — Growth Trends

**Purpose**: Show the market is growing, not static.

**Content**:
- Narrative with growth headline
- Vertical BarChart showing 5-6 years of growth data
- Highlight the latest year in accent color

**Chart type**: Vertical BarChart (Recharts)

**Data needed**: 5-6 years of `{ year, value }` showing growth trend

---

## Act 2: THE PAIN

### Section 2.1 — Core Insight

**Purpose**: Reframe the problem. Not the obvious pain — the deeper insight.

**Content**:
- Narrative paragraph explaining the reframe
- Large blockquote with the one-sentence thesis (left border accent)

**Chart**: None (pure narrative + blockquote)

**Data needed**: The insight statement and supporting narrative

### Section 2.2 — Pain Points

**Purpose**: Quantify the pain with data.

**Content**:
- 3 metric cards (grid-cols-3) with headline stats
- Horizontal BarChart showing top pain points ranked by severity
- Highlight top 3 in accent color, rest in muted

**Chart type**: Horizontal BarChart (Recharts) with `Cell` color per bar

**Data needed**: 3 headline metrics + 5-6 rows of `{ task, percentage }` pain-point data

### Section 2.3 — Customer Persona

**Purpose**: Show who the target customer is.

**Content**:
- Two charts side by side (lg:grid-cols-2):
  - Donut chart: segmentation by size/type (PieChart with innerRadius)
  - Horizontal BarChart: segmentation by industry/category
- Callout card with key persona insight

**Chart type**: Donut (PieChart) + Horizontal BarChart

**Data needed**: Size segments with `{ segment, count, pct }` + industry breakdown with `{ industry, pct }`

### Section 2.4 — Cost Breakdown

**Purpose**: Show what the customer pays today for the status quo.

**Content**:
- Vertical BarChart breaking down cost by component
- CardFooter with total cost callout

**Chart type**: Vertical BarChart (Recharts)

**Data needed**: 4-6 cost components with `{ task, cost }` that sum to a total

---

## Act 3: THE SOLUTION

### Section 3.1 — Product Tiers

**Purpose**: Show what your product offers, grouped by value tier.

**Content**:
- 3 tiers of features, each as a group of accordion rows:
  - **Tier 1**: "Must-have" — features that drive the purchase
  - **Tier 2**: "Nice-to-have" — features that justify the subscription
  - **Tier 3**: "Tracked, not built" — obligations tracked in calendar only
- Each feature row: icon + name + summary + metric + expandable detail
- Optional premium add-on callout card at bottom

**Chart**: None (accordion UI)

**Data needed**: Features with `{ icon, name, metric, metricLabel, summary, description }` grouped by tier

### Section 3.2 — Scope & Architecture

**Purpose**: Set expectations about what the product is and isn't.

**Content**:
- Architecture table: 4-5 rows of `{ layer, description }` (e.g., data source, intelligence, output, interface, data residency)
- 4 "What it's NOT" cards in a 2-col grid

**Chart**: None (Table + cards)

**Data needed**: Architecture layers + scope boundary cards

---

## Act 4: THE OPPORTUNITY

### Section 4.1 — Competitor Landscape

**Purpose**: Show the pricing gap your product fills.

**Content**:
- Horizontal BarChart with 12-16 competitors sorted by price
- Color-coded by category (Software, Digital alternative, Your product, Traditional/incumbent)
- ReferenceLine at your price point
- Manual legend above chart

**Chart type**: Horizontal BarChart with `Cell` colors + `ReferenceLine`

**Data needed**: 12-16 rows of `{ name, annual, type }` competitors

### Section 4.2 — TAM/SAM/SOM Market Sizing

**Purpose**: Show investor-grade market sizing.

**Content**:
- Custom horizontal bars (same pattern as Market Funnel) showing TAM → SAM → SOM → Your target
- Legend with calculation breakdown
- 4 metric cards below with detailed math

**Chart type**: Custom CSS horizontal bars (log-ish scale)

**Data needed**: 4 rows with `{ label, sublabel, value, display }` + calculation breakdowns

### Section 4.3 — Pricing Strategy

**Purpose**: Justify the price point with value math.

**Content**:
- Value delivered table: 4-5 components with cost ranges, summing to total value
- "You capture X%" callout with price
- 3 cards explaining "why this pricing model" (e.g., why one plan, why flat rate)
- Optional "dead zone" callout explaining how you survive mid-market pricing

**Chart**: None (structured cards and tables)

**Data needed**: Value components, capture percentage, pricing philosophy

### Section 4.4 — Revenue Projections

**Purpose**: Show the financial trajectory. The most interactive section.

**Content**:
- **Hero metric card**: Big ARR number + MRR + YoY growth badge
- **Scenario toggles**: 3 buttons (Conservative/Base/Optimistic) with penetration %
- **Feature toggles**: 1-2 optional revenue add-ons (toggle on/off)
- **Composition bar**: Stacked bar showing revenue mix (base + add-ons)
- **Stacked AreaChart**: 5-year projection with ghost lines for non-selected scenarios
- **6 metric cards**: ARR, Customers, ARPU, YoY Growth, MRR, LTV:CAC
- **4 unit economics cards**: LTV, Max CAC, LTV:CAC ratio, Payback period
- **Price trajectory**: Timeline showing launch → post-PMF pricing

**Chart type**: Stacked AreaChart + Line (ghost scenarios) — all interactive

**Data needed**: Customer trajectories per scenario, base price, add-on prices, LTV/CAC metrics

---

## Appendix — Data Sources Footnote

**Purpose**: Academic-grade citations for every number used.

**Content**:
- Organized by topic (Market size, Formation rates, Admin burden, Competitor pricing, etc.)
- Each paragraph cites specific sources with years
- Very small text: `text-xs text-muted-foreground/60`

**Data needed**: All source citations organized by topic
