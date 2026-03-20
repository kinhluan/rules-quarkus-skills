# Skills Relationship

> Document describing the relationship and dependencies between the expert skills in this repository.

---

## Overview

This repository contains a comprehensive set of **12 distinct skills** designed to handle the full lifecycle of Modern Java development with Quarkus and Bazel:

| Skill | Keyword | Category | Scope |
|-------|---------|----------|-------|
| **java-expert** ☕ | `java` | Language | Modern Java (21+), Performance, Clean Code |
| **maven-expert** 📦 | `maven` | Tooling | Dependency management, BOM, Migration |
| **gradle-expert** 🐘 | `gradle` | Tooling | Modern build DSL, Multi-project, Migration |
| **vertx-expert** 🌀 | `vertx` | Foundation | Reactive engine, Event Loop, Non-blocking |
| **graalvm-expert** 🚀 | `graalvm` | Runtime | Native Image (AOT), Polyglot, Reflection |
| **bazel-expert** 🏗 | `bazel` | Infrastructure | General Bazel build system |
| **refactoring-expert** 🛠 | `refactoring` | Foundation | Clean Code & Design Patterns |
| **code-author** ✍️ | `author` | Engineering | Google-style PR Authoring |
| **code-reviewer** 🔍 | `reviewer` | Engineering | Google-style Code Review |
| **quarkus-expert** ⚡ | `quarkus` | Framework | High-perf Quarkus framework |
| **quarkus-debug** 🔍 | `quarkus-debug` | Framework | Advanced Quarkus troubleshooting |
| **rules-quarkus** 🔧 | `rules-quarkus` | Domain-Specific | Quarkus + Bazel integration |

---

## Architecture

```
┌───────────────────────────────────────────────────────────────────┐
│                                                                   │
│   ┌──────────────┐    ┌──────────────┐    ┌──────────────┐        │
│   │ java-expert  │    │ maven-expert │    │ gradle-expert│        │
│   │     ☕       │    │      📦      │    │      🐘      │        │
│   │  (Language)  │    │  (Tooling)   │    │  (Tooling)   │        │
│   └──────┬───────┘    └──────┬───────┘    └──────┬───────┘        │
│          │                   │                   │                │
│          ▼                   ▼                   ▼                │
│   ┌──────────────┐    ┌──────────────────────────────────┐        │
│   │ vertx-expert │    │       rules-jvm-external         │        │
│   │      🌀      │    │         (Integration)            │        │
│   │ (Foundation) │    └──────────────┬───────────────────┘        │
│   └──────┬───────┘                   │                            │
│          │                           ▼               ┌──────────┐ │
│          ▼                  ┌──────────────────┐     │ bazel-   │ │
│   ┌──────────────┐          │  graalvm-expert  │     │ expert   │ │
│   │quarkus-expert│◄─────────┤        🚀        │     │    🏗    │ │
│   │     ⚡       │          │     (Runtime)    │     └────┬─────┘ │
│   │  (Framework) │          └────────┬─────────┘          │       │
│   └──────┬───────┘                   │                    │       │
│          │            Combines       │                    │       │
│          └───────────────┬───────────┴────────────────────┘       │
│                          ▼                                        │
│                ┌──────────────────┐                               │
│                │  rules-quarkus   │                               │
│                │       🔧         │                               │
│                │  (Domain-Specific)│                              │
│                └──────────────────┘                               │
│                                                                   │
└───────────────────────────────────────────────────────────────────┘
```

---

## Layered Architecture

This skills collection follows a **3-layer architecture** for maximum reusability and separation of concerns:

### Layer 1: Foundation (Independent Skills)
These skills have **no dependencies** and provide foundational knowledge:

| Skill | Description |
|-------|-------------|
| **java-expert** ☕ | Modern Java language (21+), JVM internals, performance tuning |
| **maven-expert** 📦 | Maven dependency management, BOMs, project lifecycle |
| **gradle-expert** 🐘 | Gradle DSL, build optimization, multi-project builds |
| **bazel-expert** 🏗 | Bazel rules, Starlark, hermetic builds |
| **refactoring-expert** 🛠 | Clean Code, Refactoring (Guru), Design Patterns, SOLID |
| **code-author** ✍️ | Small CLs, descriptions, feedback handling (Google) |
| **code-reviewer** 🔍 | LGTM standards, speed, mentoring (Google) |

### Layer 2: Framework & Runtime (Depends on Foundation)
These skills build upon Layer 1:

| Skill | Depends On | Description |
|-------|------------|-------------|
| **vertx-expert** 🌀 | `java-expert` | Reactive programming, Event Loop, non-blocking I/O |
| **graalvm-expert** 🚀 | `java-expert` | Native Image AOT compilation, polyglot runtime |
| **quarkus-expert** ⚡ | `java-expert`, `vertx-expert`, `graalvm-expert` | Quarkus framework, augmentation, CDI, Mutiny |
| **quarkus-debug** 🔍 | `java-expert`, `quarkus-expert`, `vertx-expert`, `graalvm-expert` | Deep troubleshooting, Mutiny debugging, Native Image diagnostics |

### Layer 3: Integration (Domain-Specific)
These skills combine multiple layers for specific use cases:

| Skill | Depends On | Description |
|-------|------------|-------------|
| **rules-quarkus** 🔧 | **All 7 skills above** | Quarkus + Bazel integration, migration from Maven/Gradle |

---

## Skill Descriptions

### 1. java-expert ☕ (Independent - Layer 1)
**Purpose:** Modern Java (21+) language expertise.

**Covers:**
- Virtual Threads, Records, Sealed Classes, Pattern Matching
- JVM Tuning (G1GC/ZGC), JFR profiling
- Clean Architecture, Hexagonal patterns
- Concurrency, Streams, Functional programming

**When to use:**
- Deep Java language questions
- Performance optimization
- Code quality and design patterns

---

### 2. maven-expert 📦 (Independent - Layer 1)
**Purpose:** Dependency management and project orchestration.

**Covers:**
- BOMs, transitive dependencies, dependency scopes
- Maven lifecycle, plugins, profiles
- Maven-to-Bazel migration

**When to use:**
- Dependency conflicts
- POM configuration
- Migrating from Maven to Bazel

---

### 3. gradle-expert 🐘 (Independent - Layer 1)
**Purpose:** Modern build DSL and performance.

**Covers:**
- Groovy/Kotlin DSL
- Build Cache, Daemon, Parallel execution
- Version Catalogs, Build Scans
- Gradle-to-Bazel migration

**When to use:**
- Gradle build optimization
- Multi-project builds
- Migrating from Gradle to Bazel

---

### 3b. refactoring-expert 🛠 (Independent - Layer 1)
**Purpose:** Clean Code and Structural design expertise.

**Covers:**
- Code Smells (Bloaters, OO Abusers, Dispensables)
- Refactoring Techniques (guru-based)
- Creational, Structural, Behavioral Patterns
- SOLID, DRY, KISS, YAGNI principles

**When to use:**
- Architectural design decisions
- Code quality improvements
- Pattern implementation guidance

---

### 3c. code-author ✍️ (Independent - Layer 1)
**Purpose:** Professional code change authoring.

**Covers:**
- Small CLs, descriptions, feedback handling
- Separating refactoring from feature changes
- Self-review and style consistency

---

### 3d. code-reviewer 🔍 (Independent - Layer 1)
**Purpose:** High-quality code review conducting.

**Covers:**
- LGTM standards, speed, mentoring
- Distinguishing requirements vs suggestions (Nit)

---

### 4. vertx-expert 🌀 (Depends on java-expert - Layer 2)
**Purpose:** Reactive programming foundation (Quarkus's engine).

**Covers:**
- Event Loop, "Don't Block the Event Loop" principle
- Verticles, Event Bus, polyglot design
- Reactive clients (HTTP, SQL, Redis, Kafka)
- Circuit Breaker, Service Discovery, Clustering
- Vert.x + Quarkus integration

**When to use:**
- Reactive programming patterns
- Event-driven architecture
- High-performance I/O

---

### 5. graalvm-expert 🚀 (Depends on java-expert - Layer 2)
**Purpose:** Native Image (AOT) and polyglot runtime expertise.

**Covers:**
- AOT compilation, Closed-world assumption
- Reflection/Resource/Proxy configuration
- Native Image Agent
- Build-time vs Runtime initialization
- Quarkus Native troubleshooting

**When to use:**
- Building native executables
- Reflection errors in native mode
- Polyglot applications

---

### 6. bazel-expert 🏗 (Independent - Layer 1)
**Purpose:** General Bazel build system expertise.

**Covers:**
- Starlark language, rules vs macros
- Providers, depsets, hermeticity
- Bzlmod, remote execution
- Performance optimization (param files, action mnemonics)

**When to use:**
- Writing custom Bazel rules
- Build performance issues
- Remote build configuration

---

### 7. quarkus-expert ⚡ (Depends on java, vertx, graalvm - Layer 2)
**Purpose:** High-performance Quarkus framework knowledge.

**Covers:**
- Build-time augmentation phase
- CDI, dependency injection
- Mutiny (Uni, Multi) reactive patterns
- Dev Services, Testcontainers
- Extension development (BuildStep, STATIC_INIT vs RUNTIME_INIT)
- Native Image integration

**When to use:**
- General Quarkus development
- Reactive vs imperative decisions
- Custom extension creation
- Native image troubleshooting

---

### 7b. quarkus-debug 🔍 (Depends on java, quarkus, vertx, graalvm - Layer 2)
**Purpose:** Advanced troubleshooting and debugging.

**Covers:**
- Dev Mode debugging, JPDA, Dev UI, Continuous Testing
- Reactive debugging (Mutiny), Context Propagation, Event Loop warnings
- Native Image (AOT) debugging, GraalVM Agent, GDB/LLDB
- Build-time (Augmentation) debugging, bytecode inspection
- Memory leaks, ClassLoader conflicts, Dev Services troubleshooting

**When to use:**
- Deep troubleshooting of Quarkus apps
- Debugging reactive/asynchronous code
- Native image runtime failures
- Build-time augmentation errors

---

### 8. rules-quarkus 🔧 (Depends on all - Layer 3)
**Purpose:** Specialized integration for Quarkus on Bazel.

**Covers:**
- Three-Layer Transformation Pipeline (Compile → Augment → Orchestrate)
- `quarkus_application`, `quarkus_bootstrap`, `quarkus_runner` rules
- 5-Tier Extension Support
- ClassLoader troubleshooting, CDIProvider errors
- Maven/Gradle to Bazel migration

**When to use:**
- Building Quarkus apps with Bazel
- BUILD file errors
- Adding Quarkus extensions to BUILD files
- Migration from Maven/Gradle

---

## Usage Scenarios

| Scenario | Primary Skill | Secondary Skill |
|----------|---------------|-----------------|
| "Build a Native Image for Quarkus" | `@quarkus` | `@graalvm` |
| "Troubleshoot reflection error in native" | `@graalvm` | `@quarkus-debug` |
| "Explain why Event Loop is blocked" | `@vertx` | `@quarkus-debug` |
| "Review this logic for bugs" | `@reviewer` | `@refactoring` |
| "Prepare a PR with Risk assessment" | `@author` | `@reviewer` |
| "Refactor switch into Strategy" | `@refactoring` | `@java` |
| "Migrate from Gradle to Bazel" | `@rules-quarkus` | `@gradle`, `@bazel` |
| "Configure Quarkus on Bazel" | `@rules-quarkus` | `@bazel`, `@quarkus` |
| "Migrate from Maven to Bazel" | `@rules-quarkus` | `@maven`, `@bazel` |
| "Optimize JVM garbage collection" | `@java` | — |
| "Fix dependency version conflict" | `@maven` or `@gradle` | — |
| "Write a custom Bazel rule" | `@bazel` | — |
| "Use Virtual Threads in Quarkus" | `@quarkus` | `@java` |

---

## Skill Interoperability Matrix

This matrix shows which skills **depend on** or **benefit from** other skills:

| Skill | java ☕ | maven 📦 | gradle 🐘 | vertx 🌀 | graalvm 🚀 | bazel 🏗 | refact 🛠 | author ✍️ | review 🔍 | debug 🔍 | quarkus ⚡ | rules 🔧 |
|-------|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| **java-expert** ☕ | — | — | — | — | — | — | — | — | — | — | — | — |
| **maven-expert** 📦 | ◐ | — | — | — | — | — | — | — | — | — | — | — |
| **gradle-expert** 🐘 | ◐ | — | — | — | — | — | — | — | — | — | — | — |
| **vertx-expert** 🌀 | ● | — | — | — | — | — | — | — | — | — | — | — |
| **graalvm-expert** 🚀 | ● | — | — | — | — | — | — | — | — | — | — | — |
| **bazel-expert** 🏗 | ◐ | — | — | — | — | — | — | — | — | — | — | — |
| **refactor-expert** 🛠 | ● | — | — | — | — | — | — | — | — | — | — | — |
| **code-author** ✍️ | ◐ | — | — | — | — | — | ◐ | — | ● | — | ◐ | ◐ |
| **code-reviewer** 🔍 | ● | — | — | ● | ● | — | ● | ● | — | ● | ● | ● |
| **quarkus-debug** 🔍 | ● | — | — | ● | ● | — | — | — | — | — | ● | ● |
| **quarkus-expert** ⚡ | ● | ◐ | ◐ | ● | ● | — | ◐ | — | — | ◐ | — | — |
| **rules-quarkus** 🔧 | ● | ● | ● | ◐ | ◐ | ● | ◐ | ● | ● | ● | ● | — |

**Legend:**
- `●` = **Strong dependency** (requires knowledge from this skill)
- `◐` = **Related** (overlapping scenarios, may combine)
- `—` = No direct dependency

---

## Activation Guide

### Single Skill Activation
Use when the question is **focused on one domain**:

```
@java How do Virtual Threads differ from Platform Threads?
@bazel What's the difference between a rule and a macro?
@maven How do I exclude a transitive dependency?
```

### Multiple Skill Activation
Use when the question **spans multiple domains**:

```
@quarkus @graalvm My Quarkus native build fails with reflection error
@rules-quarkus @gradle How do I migrate this Gradle project to Bazel?
@vertx @java Why is my Event Loop blocked?
```

### AI Auto-Selection
When using `npx skills add`, AI will **automatically select** the appropriate skill based on:
1. Keywords in the query
2. File context (BUILD.bazel → `@bazel`, pom.xml → `@maven`)
3. Project structure (Quarkus app → `@quarkus`)

---

## Future Skills

Potential skills that could be added based on user demand:

| Skill | Keyword | Description | Priority |
|-------|---------|-------------|----------|
| `quarkus-testing` | `quarkus-test` | @QuarkusTest, Testcontainers, ArchUnit | Medium |
| `quarkus-native` | `quarkus-native` | Dedicated GraalVM + Quarkus integration | Medium |
| `kotlin-expert` | `kotlin` | Kotlin language + Quarkus/Bazel | Low |
| `microprofile-expert` | `microprofile` | MicroProfile specs (Config, Health, Metrics) | Low |
| `devops-quarkus` | `quarkus-ops` | Containerization, K8s, CI/CD for Quarkus | Low |

### Skill Splitting Considerations
If any skill grows too large:

| Current Skill | Potential Split |
|---------------|-----------------|
| `rules-quarkus` | `rules-quarkus-core` + `rules-quarkus-extensions` |
| `quarkus-expert` | `quarkus-core` + `quarkus-extensions` |
| `java-expert` | `java-core` + `java-performance` |

---

## Installation

Install all skills via:

```bash
npx skills add kinhluan/rules-quarkus-skills
```

Or install individual skills:

```bash
npx skills add kinhluan/rules-quarkus-skills --skill java-expert
npx skills add kinhluan/rules-quarkus-skills --skill quarkus-expert
```

---

## Design Principles

### 1. Separation of Concerns
Each skill has a **clear, focused scope** with minimal overlap.

### 2. Progressive Disclosure
- Start with domain-specific skills (`rules-quarkus`, `quarkus`)
- Fall back to foundation skills (`java`, `bazel`) for deep dives

### 3. Agent-Agnostic
Skills work with any AI agent (Gemini CLI, Qwen Code, Claude Code, Cursor, etc.)

### 4. Composability
Skills can be **combined** for complex scenarios requiring multiple domains.

---

## References

- [rules_quarkus](https://github.com/kinhluan/rules_quarkus)
- [Quarkus](https://quarkus.io)
- [GraalVM](https://www.graalvm.org)
- [Vert.x](https://vertx.io)
- [Gradle](https://gradle.org)
- [Maven](https://maven.apache.org)
- [Bazel](https://bazel.build)
- [skills.sh](https://skills.sh)
