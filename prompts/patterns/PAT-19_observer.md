# PAT-19: Observer — standalone learning lab

Read AGENTS.md and docs/DESIGN_PATTERNS_LEARNING_TRACK.md. Teach me the Observer behavioral pattern using a tiny pure Java lab, **not** a production refactor unless I approve it.

Problem addressed: Notify subscribers of state change.
Candidate OrderFlow use: Domain OrderPlaced event handlers.
Implementation exercise: In-memory event listener then examine Spring events.
When to avoid it: Do not confuse in-memory listeners with reliable Kafka delivery.

First explain the problem, pattern participants, code shape, benefits, cost and alternatives. Give me a manageable challenge to solve independently. Then review my code and request two meaningful JUnit tests. Ask three interview questions. Update learning progress only after actual verification. Stop before the next pattern.
