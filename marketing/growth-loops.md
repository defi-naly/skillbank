---
name: growth-loops
description: Use when designing viral loops, choosing growth engines, diagnosing why growth has stalled, or building self-sustaining acquisition and engagement systems.
---

# Growth Loops

## When to Use

- Designing acquisition and engagement systems for a product
- Diagnosing why growth has stalled or plateaued
- Choosing between growth strategies (viral, paid, retention)
- Evaluating viral coefficient and loop efficiency
- Planning channel strategy and anticipating channel decay
- Building network density for network-effect products

## The Three Engines of Growth

Every sustainable business runs on one primary engine. Know which is yours.

### 1. Sticky Engine (Retention-Driven)

Growth through retention. New customers exceed churned customers.

```
Growth Rate = New Customer Rate - Churn Rate
```

**Focus on:**
- Reducing churn above all else
- Increasing engagement depth and frequency
- Building habits and switching costs
- Making the product indispensable

**Metrics that matter:** DAU/MAU ratio, retention curves by cohort, churn rate, engagement frequency.

**When to use:** Products where the value compounds with use (SaaS, tools, data-accumulating products).

### 2. Viral Engine (Referral-Driven)

Growth through customers recruiting more customers.

```
Viral Coefficient (K) = Invites per User × Conversion Rate per Invite
```

If K > 1, exponential growth. If K < 1, growth eventually stalls without other inputs.

**Focus on:**
- Making sharing natural and frictionless
- Reducing friction in the referral flow
- Incentivizing both referrer and referred
- Embedding virality into the core product action

**Two types of virality:**
- **Organic**: Sharing is intrinsic to using the product (Slack, Figma, Dropbox)
- **Incentivized**: Rewards for referrals (Uber credits, Dropbox storage)

Organic virality is more durable. Incentivized virality has diminishing returns.

**When to use:** Products with inherent social or collaborative components.

### 3. Paid Engine (Acquisition-Driven)

Growth through paid customer acquisition.

```
Sustainable if: Customer Lifetime Value (LTV) > Customer Acquisition Cost (CAC)
```

**Focus on:**
- Increasing LTV (upsells, retention, pricing)
- Decreasing CAC (better targeting, creative, conversion)
- Optimizing channel mix and attribution
- Finding scalable channels before they saturate

**When to use:** Products with high margins and clear monetization.

## The Engagement Loop

For network-effect products, the core growth loop looks like this:

```
New User Joins
      │
      ▼
Experiences Value (magic moment)
      │
      ▼
Creates Content / Supply
      │
      ▼
Attracts More Users
      │
      ▼
Network Becomes More Valuable
      │
      ▼
User Engages More + Invites Others
      │
      └──────────┘ (loop)
```

### Three Growth Effects in Networks

**1. Acquisition Effect** — Each user brings more users through virality, word of mouth, and social proof.

**2. Engagement Effect** — More users = more value = more engagement. More content to consume, more people to interact with, more utility.

**3. Economic Effect** — Costs decrease and value increases at scale. More supply = competitive pricing. More demand = seller benefits. Efficiency compounds.

## Designing the Magic Moment

The magic moment is the instant a user first experiences the product's core value.

**Examples:**
- Slack: When your team actually starts using it
- Uber: When a car arrives in 3 minutes
- Facebook: When you find 10 friends
- Tinder: First match

**Design principles:**
- Identify your magic moment precisely
- Minimize time-to-magic-moment relentlessly
- Remove every obstacle between signup and magic moment
- Measure activation rate: what % of new users reach it?

## Channel Strategy

### The Law of Shitty Clickthroughs

Every growth channel's performance degrades over time.

**Why:**
- Early adopters are different from late adopters
- Channels get crowded by competitors
- Users develop immunity to tactics
- Platform algorithms change

**Implication:** You need continuous channel innovation. Never depend on a single channel. Start testing the next channel before the current one peaks.

### Channel Selection Framework

| Factor | Question |
|--------|----------|
| **Fit** | Does this channel reach our target users? |
| **Cost** | What's the CAC through this channel? |
| **Scale** | Can this channel support our growth targets? |
| **Control** | How much do we own vs. rent? |
| **Decay rate** | How quickly will this channel saturate? |

### Owned vs. Rented Channels

| Owned | Rented |
|-------|--------|
| Email list, community, SEO | Paid ads, social algorithms, influencers |
| Compounds over time | Decays over time |
| You control the rules | Platform controls the rules |
| Slow to build | Fast to start |

**Strategy:** Use rented channels to build owned channels. Paid ads that build an email list. Social content that drives community signup. Influencer partnerships that create direct relationships.

## Seeding and Density

For network products, density matters more than size.

**100 users in one building > 10,000 scattered globally**

### The Atomic Network

The smallest network that is stable and self-sustaining. Solve for this first before trying to scale.

**Examples:**
- Slack: one team
- Uber: one neighborhood
- Tinder: one college campus
- Airbnb: one city during a conference

### Seeding Strategies

1. **Come for the tool, stay for the network** — Provide standalone value before network kicks in (Instagram's filters, Dropbox's file sync)
2. **Subsidize the hard side** — Pay or incentivize the supply side (drivers, hosts, creators)
3. **Do things that don't scale** — Manual outreach, white-glove onboarding, personal matching
4. **Invite-only and FOMO** — Controlled growth creates exclusivity and desire

## Diagnosing Growth Problems

| Symptom | Likely Cause | Fix |
|---------|-------------|-----|
| Not growing | Atomic network not working, insufficient density | Narrow focus, seed manually |
| Growing but not retaining | Magic moment unclear or unreached | Improve activation flow |
| Hit a wall | Market saturated, channel decay | New use cases, markets, or channels |
| Growing then collapsing | Quality degradation, context collapse | Curation, verification, segment separation |
| Viral coefficient < 1 | Sharing isn't natural or frictionless | Embed virality in core product action |

## Ceiling Breakers

When growth plateaus, these strategies break through:

1. **New use cases** — Facebook: Photos → Events → Groups → Video
2. **New geographies** — Replicate atomic network strategy in new markets
3. **New user segments** — Adjacent audiences, different price tiers
4. **Network quality improvements** — Better matching, curation, verification
5. **Adjacent networks** — Link to complementary networks

## Metrics Dashboard

| Metric | What It Measures | Target Direction |
|--------|-----------------|-----------------|
| Viral coefficient (K) | Referral efficiency | > 1 for viral growth |
| Activation rate | % reaching magic moment | Higher |
| DAU/MAU | Engagement stickiness | Higher (>30% is strong) |
| Retention by cohort | Are newer cohorts retaining better? | Improving curves |
| Organic vs. paid ratio | Network strength | Higher organic share |
| Time to magic moment | Onboarding efficiency | Shorter |
| CAC/LTV ratio | Unit economics | LTV > 3× CAC |

## Application Checklist

- [ ] Identify which engine of growth is primary for your product
- [ ] Define the magic moment precisely
- [ ] Map the complete growth loop (acquisition → activation → engagement → referral)
- [ ] Measure viral coefficient if applicable
- [ ] Track retention by cohort, not cumulative totals
- [ ] Audit channel health: which channels are decaying?
- [ ] Ensure you're building owned channels, not just renting
- [ ] If network product: define the atomic network and hard side
- [ ] Diagnose current growth bottleneck using the table above

## Anti-Patterns

**"We just need more users"** — Wrong. You need the RIGHT users in the RIGHT density. Diffuse growth kills network products.

**One-channel dependency** — Every channel decays. If 80%+ of growth comes from one source, you're fragile.

**Vanity metrics obsession** — Total signups, page views, downloads. Track cohort retention, activation rate, and revenue per user instead.

**Skipping activation for acquisition** — Pouring users into a leaky bucket. Fix retention before scaling acquisition.

**"Build it and they will come"** — The cold start problem guarantees they won't. You need a deliberate seeding strategy.

---
*Synthesized from: The Lean Startup (Ries), The Cold Start Problem (Chen), Networks, Crowds, and Markets (Easley/Kleinberg), Zero to One (Thiel)*
