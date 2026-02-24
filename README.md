# Skillbank

Actionable skills for Claude Code agents, synthesized from books and practitioner playbooks. Organized by use case, not by source material.

## Skills (61 skills across 6 categories)

### Strategy (6 skills)
Competitive positioning, risk, systems thinking, and decision-making.

| Skill | Use When |
|-------|----------|
| `competitive-positioning` | Defining and defending a unique market position |
| `risk-under-uncertainty` | Evaluating risk and building antifragile systems |
| `systems-thinking` | Mapping feedback loops and finding leverage points |
| `decision-frameworks` | Overcoming cognitive biases with structured processes |
| `strategic-diagnosis` | Diagnosing the real problem before jumping to solutions |
| `optionality` | Designing strategies with convex payoffs and flexibility |

### Product (6 skills)
Idea validation, iteration, network effects, and platform design.

| Skill | Use When |
|-------|----------|
| `idea-validation` | Finding 0→1 opportunities and validating before building |
| `mvp-iteration` | Running build-measure-learn cycles and rapid iteration |
| `network-effects` | Designing, launching, and scaling network-effect products |
| `platform-design` | Building multi-sided platforms and marketplaces |
| `founder-playbook` | Applying patterns and avoiding pitfalls from successful founders |
| `pricing-monetization` | Pricing products and monetizing platforms |

### Marketing (35 skills)
Negotiation, persuasion, growth, positioning, storytelling, CRO, SEO, paid ads, email, and conversion optimization.

| Skill | Use When |
|-------|----------|
| `ab-test-setup` | Planning, designing, or implementing A/B tests and experiments |
| `ad-creative` | Generating, iterating, or scaling ad creative at volume |
| `ai-seo` | Optimizing content for AI search engines and LLM citations |
| `analytics-tracking` | Setting up, improving, or auditing analytics and measurement |
| `churn-prevention` | Reducing churn, building cancel flows, recovering failed payments |
| `cold-email` | Writing B2B cold outreach and follow-up sequences |
| `community-building` | Building community that drives retention and organic growth |
| `competitor-alternatives` | Creating competitor comparison and alternative pages |
| `content-strategy` | Planning content strategy, topics, and editorial direction |
| `copy-editing` | Editing, reviewing, or improving existing marketing copy |
| `copywriting` | Writing or rewriting marketing copy for any page type |
| `email-sequence` | Creating or optimizing email sequences and drip campaigns |
| `form-cro` | Optimizing lead capture, contact, and application forms |
| `free-tool-strategy` | Planning or building free tools for lead gen and SEO |
| `growth-loops` | Designing viral loops and self-sustaining growth engines |
| `launch-strategy` | Planning product launches, feature announcements, go-to-market |
| `marketing-ideas` | Generating marketing ideas and growth strategies for SaaS |
| `marketing-psychology` | Applying psychological principles and behavioral science |
| `negotiation` | Closing deals and handling objections with tactical empathy |
| `onboarding-cro` | Optimizing post-signup onboarding and user activation |
| `page-cro` | Optimizing any marketing page for conversions |
| `paid-ads` | Running paid campaigns on Google, Meta, LinkedIn, Twitter/X |
| `paywall-upgrade-cro` | Creating or optimizing in-app paywalls and upgrade screens |
| `persuasion` | Winning people over through genuine connection |
| `popup-cro` | Creating or optimizing popups, modals, and overlays |
| `positioning-messaging` | Crafting positioning and narrative that differentiates |
| `pricing-strategy` | Making pricing, packaging, and monetization decisions |
| `product-marketing-context` | Creating shared product context for marketing skills |
| `programmatic-seo` | Creating SEO-driven pages at scale with templates and data |
| `referral-program` | Designing referral, affiliate, and ambassador programs |
| `schema-markup` | Adding or optimizing structured data and JSON-LD |
| `seo-audit` | Auditing and diagnosing technical and on-page SEO issues |
| `signup-flow-cro` | Optimizing signup, registration, and trial activation flows |
| `social-content` | Creating and optimizing social media content across platforms |
| `storytelling` | Telling compelling stories for marketing and sales |

### Leadership (6 skills)
Crisis management, hiring, personal development, and creativity.

| Skill | Use When |
|-------|----------|
| `crisis-leadership` | Leading through crises and making hard calls |
| `hiring-culture` | Building teams, hiring well, and scaling culture |
| `personal-leverage` | Building wealth through leverage, not time-for-money |
| `creative-process` | Breaking through creative blocks and shipping authentic work |
| `intellectual-humility` | Rethinking assumptions and fostering productive disagreement |
| `talent-development` | Developing potential through character skills and feedback |

### Economics (5 skills)
Monetary systems, macro cycles, sovereignty, and platform power.

| Skill | Use When |
|-------|----------|
| `monetary-systems` | Understanding money, fiat dysfunction, and hard money |
| `macro-cycles` | Navigating generational cycles and institutional decay |
| `digital-sovereignty` | Planning for individual autonomy and crypto implications |
| `platform-power` | Understanding platform rent extraction and escape strategies |
| `geopolitical-positioning` | Navigating jurisdictions and regulatory environments |

### Development (3 skills)
Code scaffolding, technical reference, and frontend design.

| Skill | Use When |
|-------|----------|
| `repo-scaffold` | Scaffolding a pnpm + Turborepo monorepo with full tooling |
| `deep-learning` | Building ML models, choosing architectures, debugging training |
| `frontend-design` | Building distinctive, production-grade frontend interfaces |

## Source Material

Original book skills are preserved in `_sources/` for reference. Each synthesized skill draws from multiple books — see the skill file for attribution.

### Books (25)

Almanack of Naval, Antifragile, Black Swan, Broken Money, Cold Start Problem, Creative Act, Founders at Work, Fourth Turning, Good Strategy Bad Strategy, Hard Thing About Hard Things, Hidden Potential, How to Win Friends, Lean Startup, Modern Monopolies, Networks Crowds Markets, Never Split the Difference, Playing to Win, Skin in the Game, Sovereign Individual, Technofeudalism, Think Again, Thinking Fast and Slow, Thinking in Systems, Understanding Deep Learning, Zero to One

### External Sources

- **Marketing skills** (29 skills) — [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills). Practitioner playbooks for CRO, SEO, paid ads, email, copywriting, and conversion optimization.
- **Frontend design skill** — [anthropics/skills](https://github.com/anthropics/skills). Anthropic's official frontend design skill for building distinctive, production-grade interfaces.

## Usage

Reference skills in your Claude Code projects via `.claude/settings.json`:

```json
{
  "skills": ["github:defi-naly/skillbank/strategy/competitive-positioning.md"]
}
```

Or install all skills in a category:

```bash
# Copy a category into your project
cp -r strategy/ /your-project/.claude/skills/strategy/
```
