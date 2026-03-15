---
name: java-expert
description: Expert knowledge for Modern Java (21+) development, including Virtual Threads, performance tuning, and idiomatic clean code. Use for deep Java language/logic questions.
version: 1.0.0
keywords: [java, jdk21, virtual-threads, performance, jvm, backend]
---

# java-expert

> Keyword: java | Platforms: gemini,claude,codex

High-Performance Modern Java Expert Skill - Specialized in Java 21+ and cloud-native architecture.

## Core Mandates

- **Java 21+ First:** Mandate `var` (LVTI) where readable, Records for DTOs, and Pattern Matching for `instanceof` and `switch`.
- **Concurrency:** Prefer Virtual Threads (`@RunOnVirtualThread` in Quarkus or `Executors.newVirtualThreadPerTaskExecutor()`) over traditional Thread Pools for I/O-bound tasks.
- **Immutability:** Use `record`, `final` fields, and `unmodifiable` collections (`List.of`, `Map.of`).
- **Functional Style:** Leverage Streams, `Optional`, and Functional Interfaces to reduce boilerplate and side effects.
- **Visibility:** Default to `package-private` or `private`. Only `public` what must be exposed (API/SPI).

## Architectural Patterns

### Hexagonal / Clean Architecture
- **Domain:** Pure Java, zero external dependencies (no Quarkus/Spring in domain classes).
- **Ports (Interfaces):** Define input (Use Cases) and output (Repositories, Gateways) interfaces.
- **Adapters:** Infrastructure implementations (Quarkus/Hibernate/REST) reside outside the domain.

### Performance & Memory
- **Garbage Collection:** Favor **G1GC** for typical workloads or **ZGC** for ultra-low latency (<1ms).
- **Memory Management:** Minimize object allocation in hot loops. Use `StringBuilder` instead of `+` in loops.
- **Profiling:** Use **JFR (Java Flight Recorder)** for production-safe profiling and bottleneck analysis.

## Testing Strategy

- **JUnit 5 & AssertJ:** The industry standard for fluent, readable assertions.
- **Mockito:** Deep stubbing and spying for complex dependencies.
- **ArchUnit:** Enforce architectural rules (e.g., "Domain must not depend on Infrastructure").
- **Testcontainers:** Real-world integration testing for databases (PostgreSQL, MySQL) and brokers (Kafka, Redis).

## Bytecode & Classloading

- **Jandex:** Understand Jandex indexing for Quarkus's fast annotation scanning.
- **Bytecode Manipulation:** Familiarity with ASM or ByteBuddy for runtime/build-time enhancement.
- **ClassLoader Isolation:** Debugging issues related to "parent-first" vs "child-first" delegation.

## Expert Tips

- Avoid `System.out.println()`; always use a logger (SLF4J/Logback).
- Prefer `Interface-based` design for testability.
- Use `Sealed Classes` to define closed hierarchy types for better exhaustiveness checking in `switch`.

## References

- [Java 21 Documentation](https://docs.oracle.com/en/java/javase/21/)
- [Effective Java (Joshua Bloch)](https://www.oreilly.com/library/view/effective-java/9780134686097/)
- [Java Flight Recorder (JFR) Guide](https://docs.oracle.com/en/java/javase/21/jfr/java-flight-recorder.html)
- [JUnit 5 User Guide](https://junit.org/junit5/docs/current/user-guide/)

## Skill Interoperability

The **java-expert** ☕ skill provides the foundational language expertise (JDK 21+, Virtual Threads) required by:
- **vertx-expert** 🌀: Uses modern Java for high-performance reactive programming.
- **quarkus-expert** ⚡: Leverages the JVM features for the Quarkus framework.
