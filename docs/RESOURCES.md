# Authoritative Resources / Learning Links

These are reference entry points. Versions change; verify compatibility on the day you add dependencies. Prioritize current official documentation over random tutorials.

## Tools, agents, and planning

- [Antigravity Rules / AGENTS.md](https://antigravity.google/docs/rules/)
- [Antigravity Planning and review](https://antigravity.google/docs/ide/implementation-plan)
- [Antigravity artifact review policy](https://antigravity.google/docs/artifact-review)
- [Antigravity settings](https://antigravity.google/docs/ide-settings)

## Java ecosystem

- [Oracle/OpenJDK Learn Java](https://dev.java/learn/)
- [JDK releases](https://www.oracle.com/java/technologies/java-se-support-roadmap.html)
- [Java language specification](https://docs.oracle.com/javase/specs/)
- [Apache Maven getting started](https://maven.apache.org/guides/getting-started/)
- [JUnit user guide](https://junit.org/junit5/docs/current/user-guide/)
- [Mockito project](https://site.mockito.org/)

## Spring

- [Spring Boot reference](https://docs.spring.io/spring-boot/reference/)
- [Spring Boot system requirements](https://docs.spring.io/spring-boot/system-requirements.html)
- [Spring Initializr](https://start.spring.io/)
- [Spring Boot starter coordinates](https://docs.spring.io/spring-boot/reference/using/build-systems.html)
- [Spring Framework reference](https://docs.spring.io/spring-framework/reference/)
- [Spring Security reference](https://docs.spring.io/spring-security/reference/)
- [Spring Data JPA reference](https://docs.spring.io/spring-data/jpa/reference/)
- [Spring Modulith reference](https://docs.spring.io/spring-modulith/reference/)
- [Spring for Apache Kafka](https://docs.spring.io/spring-kafka/reference/)

## Persistence and infrastructure

- [PostgreSQL official docs](https://www.postgresql.org/docs/current/)
- [Flyway documentation](https://documentation.red-gate.com/fd)
- [Testcontainers for Java](https://java.testcontainers.org/)
- [Docker docs](https://docs.docker.com/)
- [GitHub Actions docs](https://docs.github.com/en/actions)
- [Redis docs](https://redis.io/docs/latest/)
- [Kafka docs](https://kafka.apache.org/documentation/)

## APIs, security, reliability

- [HTTP Semantics RFC 9110](https://www.rfc-editor.org/rfc/rfc9110)
- [OpenAPI Initiative](https://www.openapis.org/)
- [OWASP API Security Top 10](https://owasp.org/API-Security/editions/2023/en/0x11-t10/)
- [OWASP ASVS](https://owasp.org/www-project-application-security-verification-standard/)
- [NIST Secure Software Development Framework](https://csrc.nist.gov/projects/ssdf)
- [OpenTelemetry Java docs](https://opentelemetry.io/docs/languages/java/)
- [Resilience4j docs](https://resilience4j.readme.io/)

## Patterns / architectures

- [Refactoring Guru design pattern catalog](https://refactoring.guru/design-patterns) (learning explanations; verify code quality independently)
- [Martin Fowler — Patterns of Enterprise Application Architecture](https://martinfowler.com/eaaCatalog/)
- [Microservices.io transactional outbox](https://microservices.io/patterns/data/transactional-outbox.html)

## Research note (2026-10-16)

Spring Boot **4.1.1** was released 2026-08-20. Spring Boot's official system-requirements page says Java 17–26 compatible. This project adopts **Java 21 LTS** as the official development baseline (recorded in ADR-003). On the first framework milestone verify exact current dependencies and Spring Boot 4 changes (for MVC use the maintained `spring-boot-starter-webmvc` where appropriate, not an outdated tutorial's assumptions).
