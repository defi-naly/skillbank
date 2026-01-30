# Skillbank

Book and framework skills for Claude Code agents. Each skill encodes mental models, frameworks, and principles from influential books.

## Skills

### Psychology & Decision-Making
- **thinking-fast-and-slow** - Kahneman's cognitive biases and System 1/2 thinking
- **think-again** - Adam Grant on intellectual humility and rethinking
- **hidden-potential** - Adam Grant on character skills and growth

### Interpersonal
- **how-to-win-friends** - Dale Carnegie's influence principles

### Startup & Entrepreneurship
- **lean-startup** - Eric Ries's build-measure-learn methodology
- **founders-at-work** - Jessica Livingston's startup founder patterns
- **hard-thing-about-hard-things** - Ben Horowitz on crisis leadership

### Strategy
- **playing-to-win** - Lafley & Martin's strategy cascade
- **good-strategy-bad-strategy** - Rumelt's strategy kernel

### Technical
- **understanding-deep-learning** - Simon Prince's ML/AI framework

## Skill Schema

Each skill uses an enhanced retrieval schema:

```yaml
dimensions:        # Multi-dimensional categorization
  domain: [...]    # What field/area
  phase: [...]     # When in the process
  problem_type: [...]  # What kind of problem

contexts:          # Conditional routing
  - situation: "..."
    use_when: "..."

combines_with:     # Complementary skills
  - skill-name

contrast_with:     # Discriminative distinctions
  - skill: other-skill
    distinction: "..."
```

## Usage

Reference skills in your Claude Code projects via `.claude/settings.json` or import directly.
