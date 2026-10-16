# Design Patterns Learning Track — All 23 GoF + Enterprise Patterns

**Learn all 23 conceptually; only apply production patterns where a demonstrated requirement makes them simpler, testable or more maintainable.**

## Recommended order

- After `OF-006`: Strategy, Factory Method, Singleton understanding, Builder.
- After `OF-008`–`OF-010`: Observer, State, Iterator, Template Method and remaining small pure Java labs.
- After `OF-013`–`OF-024`: Adapter, Facade, Proxy, Chain of Responsibility, Decorator, Command and other helpful patterns.
- After `OF-027`–`OF-030`: enterprise patterns (transactional outbox, retry/circuit breaker, idempotent consumer).
- The remaining GoF patterns are **isolated exercises**; do not add them to the actual commerce backend merely to collect patterns.

## Standard assessment for each pattern

1. Describe the problem without the pattern and explain the intent.
2. Sketch participants and interactions (small UML if helpful).
3. Write an idiomatic minimal Java example by hand in `learning-labs/design-patterns/<pattern>/`.
4. Write at least two tests: normal behavior and failure/edge condition.
5. Explain one credible OrderFlow use and one reason **not** to use the pattern.
6. Compare it with at least one alternative and answer three interview questions.

## Pattern matrix

| Group | Pattern | Core problem | OrderFlow fit | Prefer lab or real feature |
|---|---|---|---|---|
| Creational | Singleton | One shared instance and controlled lifecycle | Understand singleton-scoped Spring beans, not global mutable business state | Learning lab first |
| Creational | Factory Method | Leave concrete creation decisions to subclasses or implementors | Notification channel handlers | Potential production |
| Creational | Abstract Factory | Create compatible families of related objects | Payment provider client + request/response mapper pairs | Learning lab first |
| Creational | Builder | Readable construction for optional/validated object parameters | Immutable shipment configuration or complicated test fixture | Potential production |
| Creational | Prototype | Copy or clone prototype objects safely | Experiment with immutable pricing templates | Learning lab first |
| Structural | Adapter | Convert external interface to internal expected abstraction | Simulated payment gateway adapter | Potential production |
| Structural | Bridge | Separate orthogonal abstractions to vary independently | Notification channel vs message rendering | Learning lab first |
| Structural | Composite | Treat leaf and aggregate hierarchies uniformly | Product bundle tree or category catalog | Learning lab first |
| Structural | Decorator | Add behavior around an object without subclass explosion | Experimental logging/metering wrapper over notifier | Potential production |
| Structural | Facade | Expose a simpler entry point over multiple collaborating subsystems | Checkout orchestration service | Potential production |
| Structural | Flyweight | Share immutable repeated state to reduce memory | Catalog metadata for many simulated SKUs | Learning lab first |
| Structural | Proxy | Control access via intermediary | Understand Spring transactional/security proxies | Potential production |
| Behavioral | Chain of Responsibility | Compose independent handlers/validators | Checkout validation rules in explicit order | Potential production |
| Behavioral | Command | Represent operations as objects | Stock adjustment/cancel order audit command | Potential production |
| Behavioral | Interpreter | Represent a tiny language with evaluable expressions | Optional toy promotion expression DSL | Learning lab first |
| Behavioral | Iterator | Traverse a collection behind an abstraction | Iterate product catalogs with consistent behavior | Learning lab first |
| Behavioral | Mediator | Coordinate collaborators through a central intermediary | Educational fulfillment simulator orchestration | Learning lab first |
| Behavioral | Memento | Capture and restore a historical state safely | Draft cart undo in pure Java lab | Learning lab first |
| Behavioral | Observer | Notify subscribers of state change | Domain OrderPlaced event handlers | Potential production |
| Behavioral | State | Vary allowed behavior with current state | Order/payment lifecycle | Potential production |
| Behavioral | Strategy | Swap business algorithms behind a common interface | Discount or shipping cost calculation | Potential production |
| Behavioral | Template Method | Define algorithm skeleton with overridable steps | Optional report export workflow | Learning lab first |
| Behavioral | Visitor | Add operations over stable object hierarchies | Report or tax operations across bundle tree | Learning lab first |

## Pattern-by-pattern lab briefs

### PAT-01 — Singleton (Creational)
- **Problem solved:** One shared instance and controlled lifecycle.
- **OrderFlow reference:** Understand singleton-scoped Spring beans, not global mutable business state.
- **Self-implementation exercise:** Build a configuration object and test reference identity.
- **Watch out:** Avoid manual singleton for stateful request handling; prefer dependency injection.
- **Tests:** one successful behavior, one boundary/failure, and a comparison with the simplest non-pattern alternative.
- **Agent prompt:** `prompts/patterns/PAT-01_singleton.md`.

### PAT-02 — Factory Method (Creational)
- **Problem solved:** Leave concrete creation decisions to subclasses or implementors.
- **OrderFlow reference:** Notification channel handlers.
- **Self-implementation exercise:** Construct a notifier family and test subtype creation.
- **Watch out:** A simple constructor may suffice.
- **Tests:** one successful behavior, one boundary/failure, and a comparison with the simplest non-pattern alternative.
- **Agent prompt:** `prompts/patterns/PAT-02_factory_method.md`.

### PAT-03 — Abstract Factory (Creational)
- **Problem solved:** Create compatible families of related objects.
- **OrderFlow reference:** Payment provider client + request/response mapper pairs.
- **Self-implementation exercise:** Two mock provider families with incompatible wire formats.
- **Watch out:** Overkill when one adapter is enough.
- **Tests:** one successful behavior, one boundary/failure, and a comparison with the simplest non-pattern alternative.
- **Agent prompt:** `prompts/patterns/PAT-03_abstract_factory.md`.

### PAT-04 — Builder (Creational)
- **Problem solved:** Readable construction for optional/validated object parameters.
- **OrderFlow reference:** Immutable shipment configuration or complicated test fixture.
- **Self-implementation exercise:** Fluent builder with required fields, validation and tests.
- **Watch out:** Do not create a builder for tiny records.
- **Tests:** one successful behavior, one boundary/failure, and a comparison with the simplest non-pattern alternative.
- **Agent prompt:** `prompts/patterns/PAT-04_builder.md`.

### PAT-05 — Prototype (Creational)
- **Problem solved:** Copy or clone prototype objects safely.
- **OrderFlow reference:** Experiment with immutable pricing templates.
- **Self-implementation exercise:** Copy nested configuration; show shallow vs deep copy tests.
- **Watch out:** Avoid naive Object.clone() and shared mutable nested state.
- **Tests:** one successful behavior, one boundary/failure, and a comparison with the simplest non-pattern alternative.
- **Agent prompt:** `prompts/patterns/PAT-05_prototype.md`.

### PAT-06 — Adapter (Structural)
- **Problem solved:** Convert external interface to internal expected abstraction.
- **OrderFlow reference:** Simulated payment gateway adapter.
- **Self-implementation exercise:** Adapt `FakePayApi` to `PaymentGateway`.
- **Watch out:** Do not leak provider DTOs into domain.
- **Tests:** one successful behavior, one boundary/failure, and a comparison with the simplest non-pattern alternative.
- **Agent prompt:** `prompts/patterns/PAT-06_adapter.md`.

### PAT-07 — Bridge (Structural)
- **Problem solved:** Separate orthogonal abstractions to vary independently.
- **OrderFlow reference:** Notification channel vs message rendering.
- **Self-implementation exercise:** Email/SMS simulator with plain/HTML templates.
- **Watch out:** Prefer simple composition when variation axes are small.
- **Tests:** one successful behavior, one boundary/failure, and a comparison with the simplest non-pattern alternative.
- **Agent prompt:** `prompts/patterns/PAT-07_bridge.md`.

### PAT-08 — Composite (Structural)
- **Problem solved:** Treat leaf and aggregate hierarchies uniformly.
- **OrderFlow reference:** Product bundle tree or category catalog.
- **Self-implementation exercise:** Nested bundle and leaf price calculation tests.
- **Watch out:** Danger of cycles and duplicate counting.
- **Tests:** one successful behavior, one boundary/failure, and a comparison with the simplest non-pattern alternative.
- **Agent prompt:** `prompts/patterns/PAT-08_composite.md`.

### PAT-09 — Decorator (Structural)
- **Problem solved:** Add behavior around an object without subclass explosion.
- **OrderFlow reference:** Experimental logging/metering wrapper over notifier.
- **Self-implementation exercise:** Wrap notifier with timing/retry recording.
- **Watch out:** Avoid reimplementing native Spring filter/AOP infrastructure without need.
- **Tests:** one successful behavior, one boundary/failure, and a comparison with the simplest non-pattern alternative.
- **Agent prompt:** `prompts/patterns/PAT-09_decorator.md`.

### PAT-10 — Facade (Structural)
- **Problem solved:** Expose a simpler entry point over multiple collaborating subsystems.
- **OrderFlow reference:** Checkout orchestration service.
- **Self-implementation exercise:** Small facade combining validation + pricing + cart.
- **Watch out:** Facade must not become a god object.
- **Tests:** one successful behavior, one boundary/failure, and a comparison with the simplest non-pattern alternative.
- **Agent prompt:** `prompts/patterns/PAT-10_facade.md`.

### PAT-11 — Flyweight (Structural)
- **Problem solved:** Share immutable repeated state to reduce memory.
- **OrderFlow reference:** Catalog metadata for many simulated SKUs.
- **Self-implementation exercise:** Measure allocations for shared immutable descriptors.
- **Watch out:** Only useful when profiling shows actual cost.
- **Tests:** one successful behavior, one boundary/failure, and a comparison with the simplest non-pattern alternative.
- **Agent prompt:** `prompts/patterns/PAT-11_flyweight.md`.

### PAT-12 — Proxy (Structural)
- **Problem solved:** Control access via intermediary.
- **OrderFlow reference:** Understand Spring transactional/security proxies.
- **Self-implementation exercise:** Create safe local access-checking proxy and explore self-invocation limits.
- **Watch out:** Proxy boundaries and AOP caveats; do not assume private methods are intercepted.
- **Tests:** one successful behavior, one boundary/failure, and a comparison with the simplest non-pattern alternative.
- **Agent prompt:** `prompts/patterns/PAT-12_proxy.md`.

### PAT-13 — Chain of Responsibility (Behavioral)
- **Problem solved:** Compose independent handlers/validators.
- **OrderFlow reference:** Checkout validation rules in explicit order.
- **Self-implementation exercise:** Quantity/ownership/stock validation chain with halt conditions.
- **Watch out:** Unclear ordering may create unpredictable behavior.
- **Tests:** one successful behavior, one boundary/failure, and a comparison with the simplest non-pattern alternative.
- **Agent prompt:** `prompts/patterns/PAT-13_chain_of_responsibility.md`.

### PAT-14 — Command (Behavioral)
- **Problem solved:** Represent operations as objects.
- **OrderFlow reference:** Stock adjustment/cancel order audit command.
- **Self-implementation exercise:** Implement reversible nonpersistent command demo.
- **Watch out:** Undo must not pretend financial state changes can always be reversed.
- **Tests:** one successful behavior, one boundary/failure, and a comparison with the simplest non-pattern alternative.
- **Agent prompt:** `prompts/patterns/PAT-14_command.md`.

### PAT-15 — Interpreter (Behavioral)
- **Problem solved:** Represent a tiny language with evaluable expressions.
- **OrderFlow reference:** Optional toy promotion expression DSL.
- **Self-implementation exercise:** Parse `MIN_TOTAL > 100` simple safe grammar.
- **Watch out:** Never evaluate arbitrary Java/scripting supplied by user.
- **Tests:** one successful behavior, one boundary/failure, and a comparison with the simplest non-pattern alternative.
- **Agent prompt:** `prompts/patterns/PAT-15_interpreter.md`.

### PAT-16 — Iterator (Behavioral)
- **Problem solved:** Traverse a collection behind an abstraction.
- **OrderFlow reference:** Iterate product catalogs with consistent behavior.
- **Self-implementation exercise:** Custom read-only iterator showing fail-fast rules.
- **Watch out:** Java Collection already provides Iterator; understand rather than force.
- **Tests:** one successful behavior, one boundary/failure, and a comparison with the simplest non-pattern alternative.
- **Agent prompt:** `prompts/patterns/PAT-16_iterator.md`.

### PAT-17 — Mediator (Behavioral)
- **Problem solved:** Coordinate collaborators through a central intermediary.
- **OrderFlow reference:** Educational fulfillment simulator orchestration.
- **Self-implementation exercise:** Minimal event coordinator mediates three actors.
- **Watch out:** Avoid all-powerful orchestrator with unrelated responsibilities.
- **Tests:** one successful behavior, one boundary/failure, and a comparison with the simplest non-pattern alternative.
- **Agent prompt:** `prompts/patterns/PAT-17_mediator.md`.

### PAT-18 — Memento (Behavioral)
- **Problem solved:** Capture and restore a historical state safely.
- **OrderFlow reference:** Draft cart undo in pure Java lab.
- **Self-implementation exercise:** Snapshot immutable cart and restore with tests.
- **Watch out:** Not a substitute for durable audit/event sourcing.
- **Tests:** one successful behavior, one boundary/failure, and a comparison with the simplest non-pattern alternative.
- **Agent prompt:** `prompts/patterns/PAT-18_memento.md`.

### PAT-19 — Observer (Behavioral)
- **Problem solved:** Notify subscribers of state change.
- **OrderFlow reference:** Domain OrderPlaced event handlers.
- **Self-implementation exercise:** In-memory event listener then examine Spring events.
- **Watch out:** Do not confuse in-memory listeners with reliable Kafka delivery.
- **Tests:** one successful behavior, one boundary/failure, and a comparison with the simplest non-pattern alternative.
- **Agent prompt:** `prompts/patterns/PAT-19_observer.md`.

### PAT-20 — State (Behavioral)
- **Problem solved:** Vary allowed behavior with current state.
- **OrderFlow reference:** Order/payment lifecycle.
- **Self-implementation exercise:** Model transition table and reject illegal changes.
- **Watch out:** Simple enum + validated switch may be clearer than class per state.
- **Tests:** one successful behavior, one boundary/failure, and a comparison with the simplest non-pattern alternative.
- **Agent prompt:** `prompts/patterns/PAT-20_state.md`.

### PAT-21 — Strategy (Behavioral)
- **Problem solved:** Swap business algorithms behind a common interface.
- **OrderFlow reference:** Discount or shipping cost calculation.
- **Self-implementation exercise:** Fixed/percentage discounts with test coverage.
- **Watch out:** Avoid creating dozens of near-identical strategy classes.
- **Tests:** one successful behavior, one boundary/failure, and a comparison with the simplest non-pattern alternative.
- **Agent prompt:** `prompts/patterns/PAT-21_strategy.md`.

### PAT-22 — Template Method (Behavioral)
- **Problem solved:** Define algorithm skeleton with overridable steps.
- **OrderFlow reference:** Optional report export workflow.
- **Self-implementation exercise:** Abstract exporter with CSV/JSON hooks.
- **Watch out:** Composition often easier than inheritance.
- **Tests:** one successful behavior, one boundary/failure, and a comparison with the simplest non-pattern alternative.
- **Agent prompt:** `prompts/patterns/PAT-22_template_method.md`.

### PAT-23 — Visitor (Behavioral)
- **Problem solved:** Add operations over stable object hierarchies.
- **OrderFlow reference:** Report or tax operations across bundle tree.
- **Self-implementation exercise:** Visitor traverses fixed leaf/composite tree.
- **Watch out:** Adding new element types makes visitors costly.
- **Tests:** one successful behavior, one boundary/failure, and a comparison with the simplest non-pattern alternative.
- **Agent prompt:** `prompts/patterns/PAT-23_visitor.md`.


## Enterprise and Spring patterns (not part of the GoF 23)

| Pattern / idiom | OrderFlow purpose | Suggested stage |
|---|---|---|
| Dependency Injection / IoC | Compose services without hard-coded construction | OF-013 |
| Repository | Encapsulate persistence operations | OF-005, OF-017 |
| DTO and Data Mapper | Keep HTTP schema distinct from domain/JPA | OF-013–014 |
| Service Layer | Coordinate use cases and transactions | OF-018 |
| Unit of Work / JPA persistence context | Coordinate changes in a transaction | OF-017–018 |
| Transactional Outbox | Publish committed domain events reliably | OF-028 |
| Idempotent Consumer | Protect against duplicate deliveries | OF-028 |
| Cache-Aside | Cache catalog reads with invalidation | OF-029 |
| Retry with Backoff / Circuit Breaker | Handle external dependency failures | OF-030 |
| CQRS, Saga, API Gateway | Advanced *comparison labs* only when justified | OF-036 |

**Additional practice:** SOLID, cohesion vs coupling, composition vs inheritance, refactoring, clean code, DDD aggregates and architecture decision records. These are not all GoF patterns.
