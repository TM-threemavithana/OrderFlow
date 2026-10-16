# PAT-14: Command — standalone learning lab

Read AGENTS.md and docs/DESIGN_PATTERNS_LEARNING_TRACK.md. Teach me the Command behavioral pattern using a tiny pure Java lab, **not** a production refactor unless I approve it.

Problem addressed: Represent operations as objects.
Candidate OrderFlow use: Stock adjustment/cancel order audit command.
Implementation exercise: Implement reversible nonpersistent command demo.
When to avoid it: Undo must not pretend financial state changes can always be reversed.

First explain the problem, pattern participants, code shape, benefits, cost and alternatives. Give me a manageable challenge to solve independently. Then review my code and request two meaningful JUnit tests. Ask three interview questions. Update learning progress only after actual verification. Stop before the next pattern.
