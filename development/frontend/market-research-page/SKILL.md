---
name: market-research-page
description: Build a production-ready, data-rich market research page for presenting a business opportunity. Creates a scrollable narrative site with interactive charts, market sizing, competitive landscape, founder personas, pain-point analysis, product tiers, pricing strategy, and revenue projections — all using shadcn/ui + Recharts. Use when user asks to "build a market page," "create a pitch site," "market research visualization," "investor page," "business case site," or "data-driven market analysis."
---

You are an expert at building investor-grade market research pages — long-form, narrative-driven sites that present a business opportunity through data, charts, and clear storytelling. You produce pages that feel like a polished pitch deck rendered as a live, interactive website.

The output is a single scrollable page with 4 narrative acts, each containing multiple sections. Every section pairs explanatory prose with data visualization. The page uses shadcn/ui components (Card, Badge, Table) and Recharts for charts, with scroll-reveal animations and responsive layouts.

## Before You Start

### 1. Gather the research data

Before writing any code, you need structured data for every section. Ask the user for (or help them research):

- **Market sizing**: Total addressable market (TAM), serviceable (SAM), obtainable (SOM) — with the math behind each
- **Market funnel**: The narrowing from total market to target segment (5-6 steps)
- **Pain points**: Top 3-6 problems the target market faces, ideally with survey/study data
- **Customer persona**: Segmentation by size, industry, or behavior — with percentages
- **Cost breakdown**: What the customer pays today for the status quo
- **Competitor landscape**: 10-16 products/services with annual pricing and category
- **Product offering**: Features grouped by importance tier (must-have, nice-to-have, tracked)
- **Pricing strategy**: The price point with value justification math
- **Revenue projections**: 3-5 year ARR under conservative/base/optimistic scenarios
- **Data sources**: Citations for every number (studies, government data, published pricing)

If the user provides a brief or research document, extract all chartable datasets from it first.

### 2. Verify the tech stack

- Next.js with App Router (`"use client"` for interactive components)
- shadcn/ui initialized (`components.json` exists) — need Card, Badge, Table, and Chart components
- Recharts installed (comes with `shadcn add chart`)
- A scroll-reveal hook (create one if it doesn't exist)
- lucide-react for icons

Install any missing pieces before building sections.

## Page Architecture — The 4-Act Structure

The page is a scrollable narrative divided into 4 acts separated by thin divider lines (`h-px bg-border/40`), with alternating background colors for visual rhythm:

```
Act 1: THE MARKET        (bg-background)
  → Hero, Market Funnel, Regulatory/Structural context, Growth trends

Act 2: THE PAIN           (bg-[#FAFAFA])
  → Core insight, Pain-point data, Customer persona, Cost breakdown

Act 3: THE SOLUTION        (bg-background)
  → Product tiers (accordion), Scope & architecture

Act 4: THE OPPORTUNITY     (bg-[#FAFAFA])
  → Competitor landscape, TAM/SAM/SOM, Pricing strategy, Revenue projections

Appendix                   (bg-background)
  → Data sources footnote
```

See [references/page-structure.md](references/page-structure.md) for the complete section-by-section blueprint.

## Section Anatomy

Every section follows the same structure:

```tsx
<section className="py-16 md:py-20">  {/* or py-20 md:py-32 for major sections */}
  <div className="max-w-[1400px] mx-auto px-8 md:px-16">
    <div ref={ref} className={isVisible ? "scroll-visible" : "scroll-hidden"}>
      {/* 1. Label — small caps, colored accent */}
      <span className="font-display text-xs font-semibold uppercase tracking-[0.2em] text-muted-foreground">
        Section Label
      </span>
      {/* 2. Heading — large, bold */}
      <h2 className="font-display text-3xl md:text-4xl lg:text-5xl font-bold tracking-tight text-foreground mt-4 max-w-3xl">
        The bold claim
      </h2>
      {/* 3. Narrative paragraph — sets context before the data */}
      <p className="font-body text-base md:text-lg text-muted-foreground mt-6 max-w-3xl">
        Supporting narrative that explains why this data matters...
      </p>
      {/* 4. Chart or data component — inside a Card */}
      {/* 5. Metric cards — supporting KPIs below the chart */}
      {/* 6. Source footnote — tiny, low-opacity text */}
    </div>
  </div>
</section>
```

## Chart Types by Section

| Section | Chart Type | Why |
|---------|-----------|-----|
| Market Funnel | Custom horizontal bars (CSS) | Shows progressive narrowing; animated widths on scroll |
| Growth Trends | Vertical BarChart (Recharts) | Year-over-year comparison; highlight latest year |
| Pain Points | Horizontal BarChart (Recharts) | Ranked list; highlight top 3 with accent color |
| Customer Persona | Donut (PieChart) + Horizontal BarChart | Segments + industry breakdown side by side |
| Cost Breakdown | Vertical BarChart (Recharts) | Component costs that sum to a total |
| Competitor Landscape | Horizontal BarChart with ReferenceLine | All players sorted by price; your product highlighted |
| TAM/SAM/SOM | Custom horizontal bars (CSS) | Waterfall narrowing; same pattern as market funnel |
| Revenue Projections | Stacked AreaChart with ghost Lines | Interactive: scenario toggles + feature toggles |

See [references/component-templates.md](references/component-templates.md) for complete TSX for each.

## Key Component Patterns

### Metric Cards — The `inner-card-elevated` pattern

Small stat cards used throughout to reinforce key numbers:

```tsx
<div className="inner-card-elevated p-5">
  <div className="font-body text-[10px] text-muted-foreground/60 uppercase tracking-wider mb-1">
    Label
  </div>
  <div className="font-display text-xl font-bold text-foreground tracking-tight">
    CHF 900M
  </div>
  <div className="font-body text-[10px] text-muted-foreground mt-1 leading-relaxed">
    Calculation breakdown
  </div>
</div>
```

Use in grids: `grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4`

### Icon Metric Cards — For richer KPI grids

```tsx
<div className="inner-card-elevated p-4 flex flex-col gap-1.5">
  <div className="flex items-center justify-between">
    <div className="w-8 h-8 rounded-lg bg-foreground/[0.04] flex items-center justify-center">
      <Icon className="w-4 h-4 text-foreground/50" />
    </div>
    <span className="text-[10px] font-display font-semibold rounded-full px-2 py-0.5 bg-green-50 text-green-700">
      +20% YoY
    </span>
  </div>
  <div className="font-display text-xl font-bold text-foreground tracking-tight leading-none mt-1">
    CHF 7.05M
  </div>
  <div className="font-body text-xs text-muted-foreground">Year 5 ARR</div>
</div>
```

### Card Footer Pattern — Key insight + sources

Every chart card ends with a structured footer:

```tsx
<CardFooter className="flex-col items-start gap-3">
  <div>
    <div className="font-body text-xs text-muted-foreground uppercase tracking-wider">
      Key insight
    </div>
    <div className="font-display text-sm font-semibold text-foreground tracking-tight">
      The one-sentence takeaway from this chart.
    </div>
  </div>
  <div className="font-body text-[10px] text-muted-foreground/50 leading-relaxed">
    Sources: Specific citations with years
  </div>
</CardFooter>
```

### Scroll Reveal Hook

Create `src/hooks/useScrollReveal.ts` if it doesn't exist:

```tsx
"use client";
import { useEffect, useRef, useState } from "react";

export function useScrollReveal(threshold = 0.15) {
  const ref = useRef<HTMLDivElement>(null);
  const [isVisible, setIsVisible] = useState(false);

  useEffect(() => {
    const el = ref.current;
    if (!el) return;
    const observer = new IntersectionObserver(
      ([entry]) => { if (entry.isIntersecting) { setIsVisible(true); observer.disconnect(); } },
      { threshold }
    );
    observer.observe(el);
    return () => observer.disconnect();
  }, [threshold]);

  return { ref, isVisible };
}
```

Add matching CSS in `globals.css`:

```css
.scroll-hidden .stagger-1, /* ... */ .scroll-hidden .stagger-8 {
  opacity: 0; transform: translateY(20px);
}
.scroll-visible .stagger-1 { opacity: 1; transform: none; transition: all 0.6s ease; transition-delay: 0.05s; }
/* Increment delay by ~0.1s per stagger class */
```

## Interactive Patterns

### Scenario Toggles (Revenue Projections)

Pill buttons that switch between conservative/base/optimistic:

```tsx
<button
  onClick={() => setScenario(s.key)}
  className={`font-display text-xs font-semibold px-4 py-2 rounded-full transition-all duration-200 ${
    scenario === s.key
      ? "bg-foreground text-background"
      : "bg-foreground/[0.05] text-foreground/60 hover:bg-foreground/[0.1]"
  }`}
>
  {s.label} ({s.penetration})
</button>
```

### Feature Toggles

For add-on revenue layers (crypto, post-PMF pricing, etc.):

```tsx
<button
  onClick={() => setFeature(!featureOn)}
  className={`... ${featureOn ? "ring-1 ring-foreground/20 bg-foreground/10" : "bg-foreground/[0.03]"}`}
>
  + Feature name
</button>
```

### Ghost Lines

Show non-selected scenarios as dashed grey lines behind the main chart:

```tsx
<Line dataKey={`ghost_${key}`} stroke="#D1D5DB" strokeWidth={1.5} strokeDasharray="6 4" dot={false} />
```

## Polish Checklist

- Every chart has `accessibilityLayer` on the root Recharts component
- `CartesianGrid vertical={false}` for clean horizontal gridlines
- Bars have `radius={4}` or `radius={[4, 4, 0, 0]}` for rounded corners
- All charts wrapped in `ChartContainer` with `aspect-auto h-[300px] w-full`
- Custom `ChartTooltipContent` with `formatter` for proper units (CHF, %, etc.)
- `tickLine={false} axisLine={false} tickMargin={10}` on axes
- Highlighted bars use accent color; non-highlighted use `foreground/30`
- All sections use `useScrollReveal` with staggered children
- Source footnotes on every data section: `text-[10px] text-muted-foreground/50`
- Responsive: grids collapse from 4-col → 2-col → 1-col on mobile
- `max-w-[1400px] mx-auto px-8 md:px-16` on every section container

## Data Preparation

See [references/data-preparation.md](references/data-preparation.md) for how to structure research data into chartable datasets for each section type.

## File Structure

```
src/app/market/page.tsx               — Main page (imports all components, defines act structure)
src/components/market/
  ├── MarketHero.tsx                   — Hero with title + subtitle
  ├── MarketFunnel.tsx                 — Custom horizontal bar funnel
  ├── GrowthContext.tsx                — Regulatory/structural explanation
  ├── GrowthTrends.tsx                 — BarChart of growth data
  ├── CoreInsight.tsx                  — Narrative blockquote section
  ├── PainPoints.tsx                   — Horizontal BarChart + metric cards
  ├── CustomerPersona.tsx              — Donut + industry BarChart
  ├── CostBreakdown.tsx                — Vertical BarChart of status quo costs
  ├── ProductTiers.tsx                 — Accordion with expandable features
  ├── ScopeAndArchitecture.tsx         — Table + info cards
  ├── CompetitorLandscape.tsx          — Horizontal BarChart with reference line
  ├── MarketSizing.tsx                 — TAM/SAM/SOM waterfall + metric cards
  ├── PricingStrategy.tsx              — Value breakdown + justification
  ├── RevenueProjections.tsx           — Interactive stacked AreaChart
  └── DataSourcesFootnote.tsx          — Citation footer
```

## Related Skills

- **shadcn-charts** — For chart component installation, setup, and individual chart type templates
- **frontend-design** — For overall aesthetic direction when the user wants a distinctive visual style
