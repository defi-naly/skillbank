# Component Templates

Complete, copy-paste TSX templates for every market research page section. Each template is a standalone client component with sample data — replace the data with your research.

All templates assume:
- shadcn/ui Card, Badge, Table, Chart components installed
- `useScrollReveal` hook at `@/hooks/useScrollReveal`
- Recharts installed via `shadcn add chart`
- Tailwind CSS with shadcn neutral palette

---

## Market Hero

```tsx
export default function MarketHero() {
  return (
    <section className="pt-32 pb-20 md:pt-40 md:pb-28">
      <div className="max-w-[1400px] mx-auto px-8 md:px-16">
        <div className="hero-anim-1">
          <span className="font-display text-xs font-semibold uppercase tracking-[0.2em] text-muted-foreground">
            Market Opportunity
          </span>
        </div>
        <h1 className="hero-anim-2 font-display text-4xl md:text-6xl lg:text-7xl font-bold tracking-tight text-foreground mt-4 max-w-4xl">
          The market opportunity
        </h1>
        <p className="hero-anim-3 font-body text-lg md:text-xl text-muted-foreground mt-6 max-w-2xl">
          Why [market] is ready for [your solution]
        </p>
      </div>
    </section>
  );
}
```

---

## Market Funnel — Custom Horizontal Bars

```tsx
"use client";

import { useScrollReveal } from "@/hooks/useScrollReveal";
import { Card, CardHeader, CardTitle, CardDescription, CardContent, CardFooter } from "@/components/ui/card";

const funnelData = [
  { label: "Total market", value: 624219, barColor: "bg-foreground/30", dotColor: "bg-foreground/30" },
  { label: "Target segment", value: 200000, barColor: "bg-foreground/50", dotColor: "bg-foreground/50" },
  { label: "Sub-segment", value: 170000, barColor: "bg-foreground/70", dotColor: "bg-foreground/70" },
  { label: "On platform X", value: 100000, barColor: "bg-amber-500", dotColor: "bg-amber-500" },
  { label: "Paying premium", value: 45000, barColor: "bg-teal-600", dotColor: "bg-teal-600" },
  { label: "Year 5 target", value: 1350, barColor: "bg-foreground/40", dotColor: "bg-foreground/40" },
];

export default function MarketFunnel() {
  const { ref, isVisible } = useScrollReveal(0.15);
  const maxValue = funnelData[0].value;
  const barScale = 80;
  const minWidth = 5;

  return (
    <section className="py-16 md:py-20">
      <div className="max-w-[1400px] mx-auto px-8 md:px-16">
        <div ref={ref} className={isVisible ? "scroll-visible" : "scroll-hidden"}>
          <span className="font-display text-xs font-semibold uppercase tracking-[0.2em] text-muted-foreground stagger-1">
            Market Funnel
          </span>
          <h2 className="font-display text-3xl md:text-4xl lg:text-5xl font-bold tracking-tight text-foreground mt-4 max-w-3xl stagger-2">
            Why this market, why now
          </h2>
          <p className="font-body text-base md:text-lg text-muted-foreground mt-8 max-w-3xl stagger-3">
            Narrative explaining the funnel narrowing logic...
          </p>

          <Card className="mt-10 stagger-4">
            <CardHeader>
              <CardTitle className="font-display text-sm font-semibold">Market funnel</CardTitle>
              <CardDescription>From total market to year 5 target</CardDescription>
            </CardHeader>
            <CardContent>
              <div className="flex flex-col lg:flex-row lg:gap-10">
                {/* Bars */}
                <div className="relative flex-1 min-w-0">
                  <div className="space-y-2.5">
                    {funnelData.map((item, i) => {
                      const width = Math.max((item.value / maxValue) * barScale, minWidth);
                      const labelFits = width > 18;
                      return (
                        <div key={item.label} className="flex items-center gap-2.5">
                          <span className="font-display text-xs font-semibold text-muted-foreground w-4 text-right flex-shrink-0">
                            {i + 1}
                          </span>
                          <div className="flex-1 relative h-9 md:h-10">
                            <div
                              className={`absolute inset-y-0 left-0 rounded-full ${item.barColor} transition-all duration-700 ease-out flex items-center`}
                              style={{ width: isVisible ? `${width}%` : "0%", transitionDelay: `${i * 100 + 200}ms` }}
                            >
                              {labelFits && (
                                <span className="font-body text-[10px] md:text-xs font-semibold text-white whitespace-nowrap pl-4 relative z-10">
                                  {item.label}
                                </span>
                              )}
                            </div>
                            {!labelFits && (
                              <span
                                className="absolute top-1/2 -translate-y-1/2 font-body text-[10px] md:text-xs font-semibold text-foreground whitespace-nowrap"
                                style={{ left: `calc(${width}% + 10px)` }}
                              >
                                {item.label}
                              </span>
                            )}
                          </div>
                        </div>
                      );
                    })}
                  </div>
                </div>

                {/* Legend */}
                <div className="grid grid-cols-2 gap-x-6 gap-y-4 mt-8 lg:mt-0 lg:w-[280px] xl:w-[320px] lg:flex-shrink-0 content-start">
                  {funnelData.map((item) => (
                    <div key={item.label} className="flex items-start gap-2">
                      <span className={`w-2.5 h-2.5 rounded-full flex-shrink-0 mt-0.5 ${item.dotColor}`} />
                      <div className="min-w-0">
                        <span className="font-body text-[10px] md:text-xs text-muted-foreground leading-tight block">
                          {item.label}
                        </span>
                        <span className="font-display text-lg font-bold text-foreground tracking-tight">
                          {item.value.toLocaleString()}
                        </span>
                      </div>
                    </div>
                  ))}
                </div>
              </div>
            </CardContent>
            <CardFooter className="flex-col items-start gap-1">
              <div className="font-body text-xs text-muted-foreground uppercase tracking-wider">Addressable market</div>
              <div className="font-display text-2xl font-bold text-foreground tracking-tight">45,000 target customers</div>
            </CardFooter>
          </Card>
        </div>
      </div>
    </section>
  );
}
```

---

## Pain Points — Horizontal BarChart + Metric Cards

```tsx
"use client";

import { BarChart, Bar, XAxis, YAxis, Cell } from "recharts";
import { useScrollReveal } from "@/hooks/useScrollReveal";
import { ChartContainer, ChartTooltip, ChartTooltipContent, type ChartConfig } from "@/components/ui/chart";
import { Card, CardHeader, CardTitle, CardDescription, CardContent, CardFooter } from "@/components/ui/card";

const burdenData = [
  { task: "Top pain #1", pctCiting: 50 },
  { task: "Top pain #2", pctCiting: 46 },
  { task: "Top pain #3", pctCiting: 46 },
  { task: "Secondary pain #4", pctCiting: 38 },
  { task: "Secondary pain #5", pctCiting: 30 },
  { task: "Secondary pain #6", pctCiting: 25 },
];

const chartConfig = {
  pctCiting: { label: "% citing this", theme: { light: "#18181B", dark: "#E4E4E7" } },
} satisfies ChartConfig;

const metrics = [
  { value: "31 hrs", label: "per month on admin", sub: "Source, Year" },
  { value: "$30B", label: "avoidable cost per year", sub: "Source, Year" },
  { value: "60%", label: "say burden is high", sub: "Source, Year" },
];

export default function PainPoints() {
  const { ref, isVisible } = useScrollReveal(0.15);

  return (
    <section className="py-20 md:py-32">
      <div className="max-w-[1400px] mx-auto px-8 md:px-16">
        <div ref={ref} className={isVisible ? "scroll-visible" : "scroll-hidden"}>
          <span className="font-display text-xs font-semibold uppercase tracking-[0.2em] text-muted-foreground stagger-1">
            The Pain
          </span>
          <h2 className="font-display text-3xl md:text-4xl lg:text-5xl font-bold tracking-tight text-foreground mt-4 max-w-3xl stagger-2">
            The problem in numbers
          </h2>
          <p className="font-body text-base md:text-lg text-muted-foreground mt-6 max-w-3xl stagger-3">
            Narrative about the pain, with the key stats woven in...
          </p>

          {/* Metric cards */}
          <div className="grid grid-cols-1 md:grid-cols-3 gap-4 mt-10 stagger-4">
            {metrics.map((m) => (
              <div key={m.label} className="inner-card-elevated p-6">
                <div className="font-display text-3xl md:text-4xl font-bold text-foreground tracking-tight">{m.value}</div>
                <div className="font-body text-sm text-muted-foreground mt-1">{m.label}</div>
                <div className="font-body text-[10px] text-muted-foreground/60 mt-0.5">{m.sub}</div>
              </div>
            ))}
          </div>

          <Card className="mt-6 stagger-5">
            <CardHeader>
              <CardTitle className="font-display text-sm font-semibold">Top pain points</CardTitle>
              <CardDescription>% rating each area as high burden</CardDescription>
            </CardHeader>
            <CardContent>
              <ChartContainer config={chartConfig} className="aspect-auto h-[300px] w-full">
                <BarChart accessibilityLayer data={burdenData} layout="vertical" margin={{ top: 4, right: 24, left: 4, bottom: 0 }}>
                  <XAxis type="number" tickLine={false} axisLine={false} tick={{ fontSize: 11 }} tickFormatter={(v: number) => `${v}%`} domain={[0, 60]} />
                  <YAxis type="category" dataKey="task" tickLine={false} axisLine={false} tick={{ fontSize: 11 }} width={160} />
                  <ChartTooltip content={<ChartTooltipContent formatter={(value) => <span className="font-mono font-medium text-foreground tabular-nums">{value}%</span>} />} />
                  <Bar dataKey="pctCiting" radius={[0, 4, 4, 0]} animationDuration={800}>
                    {burdenData.map((_, i) => (
                      <Cell key={i} fill={i < 3 ? "var(--accent-color, #D42A2A)" : "hsl(var(--foreground) / 0.3)"} />
                    ))}
                  </Bar>
                </BarChart>
              </ChartContainer>
            </CardContent>
            <CardFooter className="flex-col items-start gap-3">
              <div>
                <div className="font-body text-xs text-muted-foreground uppercase tracking-wider">Key insight</div>
                <div className="font-display text-sm font-semibold text-foreground tracking-tight">
                  The top 3 pains are exactly what your product solves.
                </div>
              </div>
            </CardFooter>
          </Card>
        </div>
      </div>
    </section>
  );
}
```

---

## Competitor Landscape — Horizontal BarChart with ReferenceLine

```tsx
"use client";

import { BarChart, Bar, XAxis, YAxis, Cell, ReferenceLine } from "recharts";
import { useScrollReveal } from "@/hooks/useScrollReveal";
import { ChartContainer, ChartTooltip, ChartTooltipContent, type ChartConfig } from "@/components/ui/chart";
import { Card, CardHeader, CardTitle, CardDescription, CardContent, CardFooter } from "@/components/ui/card";

const competitorData = [
  { name: "Free tool", annual: 0, type: "Software" },
  { name: "Basic SaaS", annual: 120, type: "Software" },
  { name: "Mid SaaS", annual: 420, type: "Software" },
  { name: "Premium SaaS", annual: 1428, type: "Software" },
  { name: "Your Product", annual: 2090, type: "You" },
  { name: "Digital alt.", annual: 2280, type: "Digital" },
  { name: "Incumbent (low)", annual: 3600, type: "Traditional" },
  { name: "Incumbent (avg)", annual: 5000, type: "Traditional" },
  { name: "Incumbent (high)", annual: 6000, type: "Traditional" },
];

const typeColors: Record<string, string> = {
  Software: "#A1A1AA",
  Digital: "#3B82F6",
  You: "#D42A2A",
  Traditional: "#18181B",
};

const chartConfig = {
  annual: { label: "Annual cost", theme: { light: "#18181B", dark: "#E4E4E7" } },
} satisfies ChartConfig;

const legendItems = [
  { label: "Software", color: "#A1A1AA" },
  { label: "Digital alternative", color: "#3B82F6" },
  { label: "Your product", color: "#D42A2A" },
  { label: "Traditional", color: "#18181B" },
];

export default function CompetitorLandscape() {
  const { ref, isVisible } = useScrollReveal(0.15);
  const YOUR_PRICE = 2090;

  return (
    <section className="py-20 md:py-32">
      <div className="max-w-[1400px] mx-auto px-8 md:px-16">
        <div ref={ref} className={isVisible ? "scroll-visible" : "scroll-hidden"}>
          <span className="font-display text-xs font-semibold uppercase tracking-[0.2em] text-muted-foreground stagger-1">
            The Gap
          </span>
          <h2 className="font-display text-3xl md:text-4xl lg:text-5xl font-bold tracking-tight text-foreground mt-4 max-w-3xl stagger-2">
            Nobody fills the middle
          </h2>

          <Card className="mt-10 stagger-4">
            <CardHeader>
              <CardTitle className="font-display text-sm font-semibold">Competitive pricing landscape</CardTitle>
              <CardDescription>Annual cost, sorted by price</CardDescription>
            </CardHeader>
            <CardContent>
              {/* Legend */}
              <div className="flex flex-wrap gap-x-5 gap-y-1.5 mb-4">
                {legendItems.map((item) => (
                  <div key={item.label} className="flex items-center gap-1.5">
                    <span className="w-2.5 h-2.5 rounded-full flex-shrink-0" style={{ backgroundColor: item.color }} />
                    <span className="font-body text-[10px] text-muted-foreground">{item.label}</span>
                  </div>
                ))}
              </div>

              <ChartContainer config={chartConfig} className="aspect-auto h-[400px] w-full">
                <BarChart accessibilityLayer data={competitorData} layout="vertical" margin={{ top: 4, right: 24, left: 4, bottom: 0 }}>
                  <XAxis type="number" tickLine={false} axisLine={false} tick={{ fontSize: 11 }}
                    tickFormatter={(v: number) => v === 0 ? "Free" : `${(v / 1000).toFixed(v >= 1000 ? 1 : 0)}k`}
                    domain={[0, 6500]}
                  />
                  <YAxis type="category" dataKey="name" tickLine={false} axisLine={false} tick={{ fontSize: 10 }} width={120} />
                  <ChartTooltip content={<ChartTooltipContent formatter={(value, _, item) => (
                    <span className="font-mono font-medium text-foreground tabular-nums">
                      ${Number(value).toLocaleString()}/year ({item.payload.type})
                    </span>
                  )} />} />
                  <ReferenceLine x={YOUR_PRICE} stroke="#D42A2A" strokeDasharray="4 4" strokeWidth={1.5} />
                  <Bar dataKey="annual" radius={[0, 4, 4, 0]} animationDuration={800}>
                    {competitorData.map((entry) => (
                      <Cell key={entry.name} fill={typeColors[entry.type] || "#A1A1AA"} />
                    ))}
                  </Bar>
                </BarChart>
              </ChartContainer>
            </CardContent>
          </Card>
        </div>
      </div>
    </section>
  );
}
```

---

## Revenue Projections — Interactive Stacked AreaChart

This is the most complex component. Key patterns:

```tsx
"use client";

import { useState, useMemo } from "react";
import { AreaChart, Area, XAxis, YAxis, CartesianGrid, Line } from "recharts";
import { ChartContainer, ChartTooltip, ChartTooltipContent, type ChartConfig } from "@/components/ui/chart";
import { Card, CardHeader, CardTitle, CardDescription, CardAction, CardContent } from "@/components/ui/card";

type Scenario = "conservative" | "base" | "optimistic";

const customerTrajectories: Record<Scenario, number[]> = {
  conservative: [112, 338, 675, 900, 1125],
  base: [225, 675, 1575, 2475, 3375],
  optimistic: [375, 1250, 2813, 4375, 5625],
};

const BASE_PRICE = 2090;
const scenarios: { key: Scenario; label: string; penetration: string }[] = [
  { key: "conservative", label: "Conservative", penetration: "2.5%" },
  { key: "base", label: "Base case", penetration: "7.5%" },
  { key: "optimistic", label: "Optimistic", penetration: "12.5%" },
];

function computeRevenue(scenario: Scenario) {
  return customerTrajectories[scenario].map((total, i) => ({
    year: `Year ${i + 1}`,
    baseRevenue: total * BASE_PRICE,
    customers: total,
  }));
}

function formatCompact(value: number): string {
  if (value >= 1_000_000) return `$${(value / 1_000_000).toFixed(2)}M`;
  if (value >= 1_000) return `$${Math.round(value / 1_000)}k`;
  return `$${value}`;
}

export default function RevenueProjections() {
  const [scenario, setScenario] = useState<Scenario>("base");

  const data = useMemo(() => computeRevenue(scenario), [scenario]);

  // Ghost lines for non-selected scenarios
  const ghostData = useMemo(() => {
    return scenarios.filter((s) => s.key !== scenario).map((s) => ({
      key: s.key,
      data: computeRevenue(s.key),
    }));
  }, [scenario]);

  // Merge into single dataset
  const chartData = useMemo(() => {
    return data.map((d, i) => {
      const row: Record<string, string | number> = { year: d.year, baseRevenue: d.baseRevenue };
      ghostData.forEach((g) => { row[`ghost_${g.key}`] = g.data[i].baseRevenue; });
      return row;
    });
  }, [data, ghostData]);

  const yr5 = data[4];

  const chartConfig: ChartConfig = {
    baseRevenue: { label: "Base subscription", color: "oklch(0.205 0 0)" },
  };
  ghostData.forEach((g) => {
    chartConfig[`ghost_${g.key}`] = { label: g.key, color: "#D1D5DB" };
  });

  return (
    <section className="py-20 md:py-32">
      <div className="max-w-[1400px] mx-auto px-8 md:px-16">
        {/* Hero metric */}
        <Card className="mt-8">
          <CardHeader>
            <div>
              <CardTitle className="font-display text-sm font-semibold">Annual recurring revenue</CardTitle>
              <CardDescription>Year 5 projection</CardDescription>
            </div>
            <CardAction>
              <div className="flex flex-wrap gap-2">
                {scenarios.map((s) => (
                  <button
                    key={s.key}
                    onClick={() => setScenario(s.key)}
                    className={`font-display text-xs font-semibold px-4 py-2 rounded-full transition-all duration-200 ${
                      scenario === s.key
                        ? "bg-foreground text-background"
                        : "bg-foreground/[0.05] text-foreground/60 hover:bg-foreground/[0.1]"
                    }`}
                  >
                    {s.label} ({s.penetration})
                  </button>
                ))}
              </div>
            </CardAction>
          </CardHeader>
          <CardContent>
            <div className="font-display text-4xl md:text-5xl font-bold tracking-tight text-foreground">
              {formatCompact(yr5.baseRevenue)}
            </div>
          </CardContent>
        </Card>

        {/* Chart */}
        <Card className="mt-4">
          <CardHeader>
            <CardTitle className="font-display text-sm font-semibold">ARR projection</CardTitle>
            <CardDescription>5-year revenue — dashed lines show alternate scenarios</CardDescription>
          </CardHeader>
          <CardContent>
            <ChartContainer config={chartConfig} className="aspect-auto h-[360px] w-full">
              <AreaChart accessibilityLayer data={chartData} margin={{ top: 8, right: 16, left: 8, bottom: 0 }}>
                <defs>
                  <linearGradient id="fillBase" x1="0" y1="0" x2="0" y2="1">
                    <stop offset="0%" stopColor="oklch(0.205 0 0)" stopOpacity={0.15} />
                    <stop offset="100%" stopColor="oklch(0.205 0 0)" stopOpacity={0.02} />
                  </linearGradient>
                </defs>
                <CartesianGrid strokeDasharray="3 3" vertical={false} />
                <XAxis dataKey="year" tickLine={false} axisLine={false} tick={{ fontSize: 12 }} />
                <YAxis tickLine={false} axisLine={false} tick={{ fontSize: 11 }}
                  tickFormatter={(v: number) => v >= 1_000_000 ? `${(v / 1_000_000).toFixed(1)}M` : `${Math.round(v / 1_000)}k`}
                />
                <ChartTooltip content={<ChartTooltipContent />} />

                {/* Ghost lines */}
                {ghostData.map((g) => (
                  <Line key={g.key} type="monotone" dataKey={`ghost_${g.key}`} stroke="#D1D5DB" strokeWidth={1.5} strokeDasharray="6 4" dot={false} activeDot={false} legendType="none" />
                ))}

                {/* Primary area */}
                <Area type="monotone" dataKey="baseRevenue" stackId="revenue" stroke="oklch(0.205 0 0)" fill="url(#fillBase)" strokeWidth={2} />
              </AreaChart>
            </ChartContainer>
          </CardContent>
        </Card>
      </div>
    </section>
  );
}
```

---

## Product Tiers — Accordion Rows

```tsx
"use client";

import { useState } from "react";
import { ChevronDown } from "lucide-react";
import type { LucideIcon } from "lucide-react";

interface Feature {
  icon: LucideIcon;
  name: string;
  metric: string;
  metricLabel: string;
  summary: string;
  description: string;
}

function TierRow({ feature, isExpanded, onToggle }: { feature: Feature; isExpanded: boolean; onToggle: () => void }) {
  const Icon = feature.icon;
  return (
    <div className="bento-card-v2 p-6 md:p-8" onClick={onToggle}>
      <div className="flex flex-col md:flex-row md:items-start md:justify-between gap-4">
        <div className="flex items-start gap-4 min-w-0 flex-1">
          <div className="w-10 h-10 rounded-xl bg-foreground/[0.04] flex items-center justify-center flex-shrink-0">
            <Icon className="w-5 h-5 text-foreground/50" />
          </div>
          <div className="min-w-0">
            <h4 className="font-display text-base font-bold text-foreground">{feature.name}</h4>
            <p className="font-body text-sm text-muted-foreground mt-1">{feature.summary}</p>
          </div>
        </div>
        <div className="flex-shrink-0 md:text-right pl-14 md:pl-0">
          <span className="font-display text-xl md:text-2xl font-bold text-foreground">{feature.metric}</span>
          <span className="block font-body text-xs text-muted-foreground mt-0.5">{feature.metricLabel}</span>
        </div>
      </div>
      <button
        className="flex items-center gap-1.5 mt-4 pl-14 text-xs font-medium text-muted-foreground hover:text-foreground transition-colors"
        onClick={(e) => { e.stopPropagation(); onToggle(); }}
      >
        <ChevronDown className={`w-3.5 h-3.5 transition-transform duration-300 ${isExpanded ? "rotate-180" : ""}`} />
        {isExpanded ? "Hide details" : "Show details"}
      </button>
      <div className={`overflow-hidden transition-all duration-400 ease-[cubic-bezier(0.16,1,0.3,1)] ${isExpanded ? "max-h-60 opacity-100 mt-4" : "max-h-0 opacity-0 mt-0"}`}>
        <div className="pl-14 border-l-2 border-foreground/[0.06] ml-[18px]">
          <p className="font-body text-sm text-muted-foreground leading-relaxed">{feature.description}</p>
        </div>
      </div>
    </div>
  );
}
```

---

## Data Sources Footnote

```tsx
export default function DataSourcesFootnote() {
  return (
    <section className="py-12 md:py-16">
      <div className="max-w-[1400px] mx-auto px-8 md:px-16">
        <div className="space-y-3">
          <p className="font-display text-xs font-semibold uppercase tracking-[0.2em] text-muted-foreground/40">
            Data sources & methodology
          </p>
          <p className="font-body text-xs text-muted-foreground/60 leading-relaxed max-w-4xl">
            <span className="font-semibold text-muted-foreground/80">Market size:</span>{" "}
            Your market sizing sources and methodology here...
          </p>
          <p className="font-body text-xs text-muted-foreground/60 leading-relaxed max-w-4xl">
            <span className="font-semibold text-muted-foreground/80">Competitor pricing:</span>{" "}
            All competitor pricing from published pricing pages as of [date]...
          </p>
          {/* Add more paragraphs per topic */}
        </div>
      </div>
    </section>
  );
}
```
