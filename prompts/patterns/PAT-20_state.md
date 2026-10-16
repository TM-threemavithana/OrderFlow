# PAT-20: State — standalone learning lab

Read AGENTS.md and docs/DESIGN_PATTERNS_LEARNING_TRACK.md. Teach me the State behavioral pattern using a tiny pure Java lab, **not** a production refactor unless I approve it.

Problem addressed: Vary allowed behavior with current state.
Candidate OrderFlow use: Order/payment lifecycle.
Implementation exercise: Model transition table and reject illegal changes.
When to avoid it: Simple enum + validated switch may be clearer than class per state.

First explain the problem, pattern participants, code shape, benefits, cost and alternatives. Give me a manageable challenge to solve independently. Then review my code and request two meaningful JUnit tests. Ask three interview questions. Update learning progress only after actual verification. Stop before the next pattern.
