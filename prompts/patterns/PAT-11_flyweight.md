# PAT-11: Flyweight — standalone learning lab

Read AGENTS.md and docs/DESIGN_PATTERNS_LEARNING_TRACK.md. Teach me the Flyweight structural pattern using a tiny pure Java lab, **not** a production refactor unless I approve it.

Problem addressed: Share immutable repeated state to reduce memory.
Candidate OrderFlow use: Catalog metadata for many simulated SKUs.
Implementation exercise: Measure allocations for shared immutable descriptors.
When to avoid it: Only useful when profiling shows actual cost.

First explain the problem, pattern participants, code shape, benefits, cost and alternatives. Give me a manageable challenge to solve independently. Then review my code and request two meaningful JUnit tests. Ask three interview questions. Update learning progress only after actual verification. Stop before the next pattern.
