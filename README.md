# Skillbank

Actionable skills for Claude Code agents, synthesized from 25 books. Organized by use case, not by source material.

## Skills (31 skills across 6 categories)

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

### Marketing (6 skills)
Negotiation, persuasion, growth, positioning, and storytelling.

| Skill | Use When |
|-------|----------|
| `negotiation` | Closing deals and handling objections with tactical empathy |
| `persuasion` | Winning people over through genuine connection |
| `growth-loops` | Designing viral loops and self-sustaining growth engines |
| `positioning-messaging` | Crafting positioning and narrative that differentiates |
| `community-building` | Building community that drives retention and organic growth |
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

### Development (2 skills)
Code scaffolding and technical reference.

| Skill | Use When |
|-------|----------|
| `repo-scaffold` | Scaffolding a pnpm + Turborepo monorepo with full tooling |
| `deep-learning` | Building ML models, choosing architectures, debugging training |

## Source Material

Original book skills are preserved in `_sources/` for reference. Each synthesized skill draws from multiple books — see the skill file for attribution.

### Books (25)

Almanack of Naval, Antifragile, Black Swan, Broken Money, Cold Start Problem, Creative Act, Founders at Work, Fourth Turning, Good Strategy Bad Strategy, Hard Thing About Hard Things, Hidden Potential, How to Win Friends, Lean Startup, Modern Monopolies, Networks Crowds Markets, Never Split the Difference, Playing to Win, Skin in the Game, Sovereign Individual, Technofeudalism, Think Again, Thinking Fast and Slow, Thinking in Systems, Understanding Deep Learning, Zero to One

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
