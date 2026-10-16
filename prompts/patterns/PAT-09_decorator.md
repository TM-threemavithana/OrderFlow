# PAT-09: Decorator — standalone learning lab

Read AGENTS.md and docs/DESIGN_PATTERNS_LEARNING_TRACK.md. Teach me the Decorator structural pattern using a tiny pure Java lab, **not** a production refactor unless I approve it.

Problem addressed: Add behavior around an object without subclass explosion.
Candidate OrderFlow use: Experimental logging/metering wrapper over notifier.
Implementation exercise: Wrap notifier with timing/retry recording.
When to avoid it: Avoid reimplementing native Spring filter/AOP infrastructure without need.

First explain the problem, pattern participants, code shape, benefits, cost and alternatives. Give me a manageable challenge to solve independently. Then review my code and request two meaningful JUnit tests. Ask three interview questions. Update learning progress only after actual verification. Stop before the next pattern.
