---
name: modern-monopolies
description: "Moazed & Johnson's framework for understanding and building platform businesses."

dimensions:
  domain: [platform-strategy, business-models, market-dynamics, competitive-strategy]
  phase: [business-design, scaling, market-dominance, competitive-positioning]
  problem_type: [platform-vs-linear, network-effects-types, value-creation, market-structure]

contexts:
  - situation: "evaluating business model"
    use_when: "deciding between platform vs linear/pipeline business model"
  - situation: "building a marketplace"
    use_when: "understanding core transactions, producer-consumer dynamics"
  - situation: "competing against platforms"
    use_when: "need to understand platform economics and vulnerabilities"
  - situation: "analyzing tech companies"
    use_when: "understanding why platforms dominate and how they scale"
  - situation: "designing platform features"
    use_when: "optimizing for network effects and core transactions"

combines_with:
  - cold-start-problem       # tactical launch of platform businesses
  - networks-crowds-markets  # theoretical foundation of network dynamics
  - technofeudalism          # critique of platform power dynamics
  - zero-to-one              # building monopolies through differentiation

contrast_with:
  - skill: cold-start-problem
    distinction: "Modern Monopolies is STRATEGIC platform design; Cold Start is TACTICAL network launch"
  - skill: technofeudalism
    distinction: "Modern Monopolies is HOW to build platforms; Technofeudalism is CRITIQUE of platform power"
---

# Modern Monopolies

## The Platform Revolution

The most valuable companies of the 21st century are platforms, not linear businesses.

**The shift:**
- Old economy: Make things and sell them (linear/pipeline)
- New economy: Enable exchanges between producers and consumers (platform)

**The top 5 most valuable companies are all platforms:**
- Apple, Microsoft, Google, Amazon, Meta

**Why platforms win:**
- Near-zero marginal cost to scale
- Network effects create compounding advantage
- Winner-take-all or winner-take-most markets
- Asset-light (own the network, not the inventory)

## Linear vs Platform Business Models

### Linear (Pipeline) Business

```
Supplier → [Company creates value] → Consumer

Value flows in one direction, like a pipeline.
```

**Characteristics:**
- Company owns/creates the product
- Value chain is sequential
- Scale requires capital investment
- Competitive advantage from operational excellence

**Examples:** Manufacturing, traditional retail, most pre-internet businesses

### Platform Business

```
        ┌──────────────────┐
        │    PLATFORM      │
        │  ┌────────────┐  │
        │  │   Core     │  │
Producers ◄──│Transaction│──► Consumers
        │  └────────────┘  │
        └──────────────────┘

Platform enables exchange. Value creation is distributed.
```

**Characteristics:**
- Platform doesn't own the product/service
- Enables direct producer-consumer exchange
- Scale requires network growth
- Competitive advantage from network effects

**Examples:** Uber, Airbnb, Amazon Marketplace, YouTube

### The Fundamental Difference

| Linear | Platform |
|--------|----------|
| Creates value | Enables value exchange |
| Owns supply | Aggregates supply |
| Scales with capital | Scales with network |
| Margins compress with scale | Margins improve with scale |
| Linear growth | Exponential potential |

## The Core Transaction

Every platform exists to facilitate one core transaction between producers and consumers.

### Identifying the Core Transaction

**The formula:**
```
[Producer] provides [value unit] to [Consumer] through [platform]
```

**Examples:**

| Platform | Producer | Value Unit | Consumer |
|----------|----------|------------|----------|
| Uber | Driver | Ride | Rider |
| Airbnb | Host | Stay | Guest |
| YouTube | Creator | Video | Viewer |
| Amazon MP | Seller | Product | Buyer |
| LinkedIn | Job poster | Opportunity | Job seeker |

### Designing for the Core Transaction

**Every feature should do one of three things:**
1. Help producers create/deliver value units
2. Help consumers find/consume value units
3. Enable the exchange between them

**Ruthless focus:** Features that don't support the core transaction are distractions.

### The Exchange

**Four functions platforms perform:**

1. **Audience building:** Attract and retain both sides
2. **Matchmaking:** Connect producers and consumers
3. **Tools and services:** Enable the transaction
4. **Rules and standards:** Govern behavior

## Types of Network Effects

Network effects are the source of platform power. But not all network effects are equal.

### Direct (Same-Side) Network Effects

More users of the same type = more value.

**Examples:**
- Phone networks (more people to call)
- Social networks (more people to connect with)
- Messaging apps (more people to message)

**Strength:** Very strong. Pure network effect.

### Indirect (Cross-Side) Network Effects

More users of one type = more value for the other type.

**Examples:**
- More riders → more valuable for drivers (and vice versa)
- More app users → more valuable for developers (and vice versa)
- More viewers → more valuable for creators (and vice versa)

**Strength:** Requires balance. Chicken-and-egg challenge.

### Data Network Effects

More users = more data = better product for everyone.

**Examples:**
- Waze: More drivers → better traffic data → better routes
- Google: More searches → better algorithm → better results

**Strength:** Creates compounding advantage over time.

### Local vs Global Network Effects

**Local:** Network effect limited to geography or subset.
- Uber works city by city
- Yelp reviews are location-specific

**Global:** Network effect works everywhere.
- Facebook friends span the globe
- Wikipedia knowledge is universal

**Strategic implication:** Local network effects can be attacked market by market.

## Platform Economics

### Supply and Demand Aggregation

Platforms aggregate fragmented supply and fragmented demand.

**Before platforms:**
- Supply: Scattered, hard to find, variable quality
- Demand: Scattered, hard to reach, high acquisition cost
- Result: High friction, inefficient markets

**After platforms:**
- Supply: Aggregated, searchable, quality-rated
- Demand: Aggregated, targeted, low acquisition cost
- Result: Low friction, efficient markets

### Winner-Take-All Dynamics

Platform markets often consolidate to one dominant player.

**Drivers:**
1. **Network effects:** Being biggest is self-reinforcing
2. **Multi-homing costs:** Using multiple platforms is costly
3. **Data advantages:** More data = better product
4. **Switching costs:** Users invested in one platform

**Result:** Power law distributions. #1 takes most value.

### Monetization Strategies

| Strategy | How It Works | Example |
|----------|--------------|---------|
| **Transaction fee** | % of each exchange | Uber, Airbnb |
| **Access fee** | Subscription to participate | LinkedIn Premium |
| **Enhanced listing** | Pay for visibility | Amazon Sponsored |
| **Advertising** | Sell attention | Google, Facebook |
| **Freemium** | Free core, paid upgrades | Spotify |

**Key insight:** Monetization should NOT kill the core transaction. Tax the network lightly at first.

## Building a Platform

### Phase 1: Solve the Chicken-and-Egg

**The problem:** No supply without demand, no demand without supply.

**Strategies:**

1. **Single-user value first**
   - Provide value even without network
   - Example: Instagram filters before social

2. **Seed supply**
   - Manually onboard producers
   - Subsidize the hard side
   - Example: Uber paying drivers guaranteed rates

3. **Piggyback existing networks**
   - Import users from elsewhere
   - Example: PayPal on eBay

4. **Marquee user**
   - Get one important producer
   - Example: Exclusive content deals

5. **Be your own producer**
   - Create supply yourself initially
   - Example: Reddit founders seeding content

### Phase 2: Achieve Liquidity

**Liquidity:** When the probability of a successful transaction is high.

**Metrics:**
- Match rate
- Time to transaction
- Repeat usage

**The goal:** Reach minimum viable liquidity in a focused market before expanding.

### Phase 3: Scale Network Effects

Once liquidity achieved:
- Expand geographically
- Add producer/consumer segments
- Build adjacent networks

**Maintain quality:** Scaling too fast can kill liquidity and trust.

## Platform Governance

### Setting the Rules

Platforms must govern behavior on both sides.

**What to govern:**
- Who can participate (access)
- What can be exchanged (content)
- How exchanges happen (process)
- What behavior is acceptable (conduct)

**The balance:**
- Too loose: Quality degrades, trust erodes
- Too strict: Participants leave for less restrictive platforms

### Trust and Safety

Platforms are responsible for exchange quality:

- Verification (identity, credentials)
- Reviews and ratings
- Dispute resolution
- Fraud prevention
- Safety standards

**Trust is the platform's most valuable asset.** Erode it and the network collapses.

### Managing Multi-Homing

Users often participate in multiple competing platforms.

**Strategies to reduce multi-homing:**
- Loyalty programs
- Exclusive features
- Integration depth
- Social connections (can't move alone)

**Accept some multi-homing:** Fighting it completely is usually impossible.

## Platform Competition

### How Platforms Compete

**1. For users (both sides)**
- Lower fees/better terms
- Better experience
- Exclusive features

**2. For network effects**
- Faster to liquidity
- Density in key markets
- Superior matchmaking

**3. For data**
- More data = better product
- Data network effects compound

### Attacking Platforms

**Strategies for challengers:**

1. **Niche focus**
   - Own a segment the platform ignores
   - Example: Lyft focusing on friendlier service

2. **Vertical integration**
   - Own both platform AND supply
   - Example: Tesla selling direct

3. **Technological shift**
   - New technology resets networks
   - Mobile disrupted web

4. **Geographic focus**
   - Win local before going global
   - Own one market completely

5. **Unbundling**
   - Attack one use case
   - Serve it better than the general platform

### Defending Platforms

**Strategies for incumbents:**

1. **Strengthen network effects**
   - Increase engagement
   - Build more connections

2. **Acquire threats**
   - Buy challengers before they scale

3. **Expand to adjacent markets**
   - Pre-empt competitive entry points

4. **Increase switching costs**
   - More data
   - More connections
   - More features

## Platform Evaluation Framework

### Assessing Platform Strength

**Questions to ask:**

1. **What's the core transaction?** Is it clear and defensible?
2. **Which network effects exist?** Direct, indirect, data?
3. **How strong is liquidity?** Transaction success rate?
4. **What's the multi-homing rate?** Are users exclusive?
5. **Who controls supply?** Fragmented or concentrated?
6. **What's the take rate?** Sustainable?
7. **What are the trust mechanisms?** Strong or weak?

### Building vs Buying Platforms

**Build when:**
- Core transaction is novel
- Network effects are your competitive advantage
- You can seed supply

**Use existing platforms when:**
- They have liquidity you need
- Building would take too long
- You can differentiate on the platform

## Key Mental Models

| Concept | Meaning |
|---------|---------|
| **Core transaction** | The fundamental exchange the platform enables |
| **Network effects** | Value increasing with participants |
| **Multi-homing** | Users on multiple platforms |
| **Liquidity** | Reliable transaction success |
| **Take rate** | Platform's cut of transactions |
| **Winner-take-all** | Market consolidation to one player |

## Application Checklist

When building or analyzing a platform:

- [ ] What's the core transaction?
- [ ] Who are producers vs consumers?
- [ ] What network effects exist?
- [ ] What's the chicken-and-egg strategy?
- [ ] How will liquidity be achieved?
- [ ] What governance is needed?
- [ ] How defensible is the network?
- [ ] What's the monetization strategy?
- [ ] Where are multi-homing risks?
- [ ] What would disrupt this platform?

## Anti-Patterns

- **"We'll take a big cut from day one"** → Kills core transaction before network builds
- **"We need features for everyone"** → Lose focus on core transaction
- **"We'll launch everywhere at once"** → Never achieve local liquidity
- **"The technology IS the platform"** → The network is the platform; tech is just infrastructure
- **"We'll just copy the leader"** → Network effects can't be copied, only built
- **"We need to own the supply"** → That's a linear business, not a platform
- **"Quality control kills growth"** → Low quality kills the network
