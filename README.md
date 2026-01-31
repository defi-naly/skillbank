# Skillbank

Book and framework skills for Claude Code agents. Each skill encodes mental models, frameworks, and principles from influential books.

## Skills (25 books)

### Psychology & Decision-Making
- **thinking-fast-and-slow** - Kahneman's cognitive biases and System 1/2 thinking
- **think-again** - Adam Grant on intellectual humility and rethinking
- **hidden-potential** - Adam Grant on character skills and growth
- **thinking-in-systems** - Donella Meadows on systems thinking and feedback loops

### Interpersonal & Negotiation
- **how-to-win-friends** - Dale Carnegie's influence principles
- **never-split-the-difference** - Chris Voss FBI negotiation tactics

### Startup & Entrepreneurship
- **lean-startup** - Eric Ries's build-measure-learn methodology
- **founders-at-work** - Jessica Livingston's startup founder patterns
- **hard-thing-about-hard-things** - Ben Horowitz on crisis leadership
- **zero-to-one** - Peter Thiel on building new things

### Strategy
- **playing-to-win** - Lafley & Martin's strategy cascade
- **good-strategy-bad-strategy** - Rumelt's strategy kernel

### Network Effects & Platforms
- **networks-crowds-markets** - Easley & Kleinberg on network science and collective dynamics
- **cold-start-problem** - Andrew Chen on launching and scaling network effects
- **modern-monopolies** - Moazed & Johnson on platform business models

### Taleb's Incerto
- **antifragile** - Building systems that gain from disorder
- **black-swan** - Navigating extreme uncertainty
- **skin-in-the-game** - Evaluating trust and designing incentives

### Wealth & Economics
- **almanack-of-naval** - Naval Ravikant on wealth creation and happiness
- **broken-money** - Lyn Alden on monetary systems and hard money
- **technofeudalism** - Varoufakis on platform economics

### Macro & Society
- **fourth-turning** - Strauss-Howe generational theory
- **sovereign-individual** - Davidson & Rees-Mogg on digital autonomy

### Creativity
- **creative-act** - Rick Rubin on the creative process

### Technical
- **understanding-deep-learning** - Simon Prince's ML/AI framework

## Skill Schema

Each skill uses an enhanced retrieval schema:

```yaml
dimensions:        # Multi-dimensional categorization
  domain: [...]    # What field/area
  phase: [...]     # When in the process
  problem_type: [...] # What kind of problem

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
