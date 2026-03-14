# Skills Catalog

> Complete catalog of all expert skills in this repository.

---

## Quick Reference

| Skill | Keyword | Layer | Install |
|-------|---------|-------|---------|
| **java-expert** ☕ | `java` | Foundation | `npx skills add kinhluan/rules-quarkus-skills --skill java-expert` |
| **maven-expert** 📦 | `maven` | Foundation | `npx skills add kinhluan/rules-quarkus-skills --skill maven-expert` |
| **gradle-expert** 🐘 | `gradle` | Foundation | `npx skills add kinhluan/rules-quarkus-skills --skill gradle-expert` |
| **bazel-expert** 🏗 | `bazel` | Foundation | `npx skills add kinhluan/rules-quarkus-skills --skill bazel-expert` |
| **vertx-expert** 🌀 | `vertx` | Framework | `npx skills add kinhluan/rules-quarkus-skills --skill vertx-expert` |
| **graalvm-expert** 🚀 | `graalvm` | Runtime | `npx skills add kinhluan/rules-quarkus-skills --skill graalvm-expert` |
| **quarkus-expert** ⚡ | `quarkus` | Framework | `npx skills add kinhluan/rules-quarkus-skills --skill quarkus-expert` |
| **rules-quarkus** 🔧 | `rules-quarkus` | Integration | `npx skills add kinhluan/rules-quarkus-skills --skill rules-quarkus` |

**Install all:** `npx skills add kinhluan/rules-quarkus-skills`

---

## Skill Details

### java-expert ☕

**Keyword:** `java` | **Layer:** Foundation | **Dependencies:** None

<details>
<summary><strong>Click to expand details</strong></summary>

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

**Example:**
```
@java How do Virtual Threads differ from Platform Threads?
@java Optimize this stream operation for better performance
```

</details>

---

### maven-expert 📦

**Keyword:** `maven` | **Layer:** Foundation | **Dependencies:** None

<details>
<summary><strong>Click to expand details</strong></summary>

**Purpose:** Dependency management and project orchestration.

**Covers:**
- BOMs, transitive dependencies, dependency scopes
- Maven lifecycle, plugins, profiles
- Maven-to-Bazel migration

**When to use:**
- Dependency conflicts
- POM configuration
- Migrating from Maven to Bazel

**Example:**
```
@maven How do I exclude a transitive dependency?
@maven Configure multi-module project with shared BOM
```

</details>

---

### gradle-expert 🐘

**Keyword:** `gradle` | **Layer:** Foundation | **Dependencies:** None

<details>
<summary><strong>Click to expand details</strong></summary>

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

**Example:**
```
@gradle How to enable build cache for CI?
@gradle Migrate this build.gradle.kts to Bazel
```

</details>

---

### bazel-expert 🏗

**Keyword:** `bazel` | **Layer:** Foundation | **Dependencies:** None

<details>
<summary><strong>Click to expand details</strong></summary>

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

**Example:**
```
@bazel What's the difference between a rule and a macro?
@bazel Optimize this Starlark rule for remote execution
```

</details>

---

### vertx-expert 🌀

**Keyword:** `vertx` | **Layer:** Framework | **Dependencies:** `java-expert`

<details>
<summary><strong>Click to expand details</strong></summary>

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

**Example:**
```
@vertx Why is my Event Loop blocked?
@vertx How to implement circuit breaker pattern?
```

</details>

---

### graalvm-expert 🚀

**Keyword:** `graalvm` | **Layer:** Runtime | **Dependencies:** `java-expert`

<details>
<summary><strong>Click to expand details</strong></summary>

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

**Example:**
```
@graalvm Reflection error in native build
@graalvm Generate reflection-config.json automatically
```

</details>

---

### quarkus-expert ⚡

**Keyword:** `quarkus` | **Layer:** Framework | **Dependencies:** `java-expert`, `vertx-expert`, `graalvm-expert`

<details>
<summary><strong>Click to expand details</strong></summary>

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

**Example:**
```
@quarkus When to use Virtual Threads vs Mutiny?
@quarkus Create a custom extension with BuildStep
```

</details>

---

### rules-quarkus 🔧

**Keyword:** `rules-quarkus` | **Layer:** Integration | **Dependencies:** All 7 skills above

<details>
<summary><strong>Click to expand details</strong></summary>

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

**Example:**
```
@rules-quarkus CDIProvider error during augmentation
@rules-quarkus Add Kafka extension to BUILD.bazel
@rules-quarkus Migrate from Maven to Bazel
```

</details>

---

## Architecture Overview

```
Layer 3: Integration
┌─────────────────────┐
│   rules-quarkus 🔧  │
└──────────┬──────────┘
           │
Layer 2: Framework & Runtime
┌──────────┼──────────┬──────────────┐
│ vertx 🌀 │ quarkus ⚡ │ graalvm 🚀  │
└──────────┴──────────┴──────────────┘
           │
Layer 1: Foundation
┌──────────┼──────────┬──────────────┬──────────────┐
│ java ☕  │ maven 📦 │ gradle 🐘    │ bazel 🏗     │
└──────────┴──────────┴──────────────┴──────────────┘
```

See [docs/SKILLS-RELATIONSHIP.md](docs/SKILLS-RELATIONSHIP.md) for detailed architecture and dependencies.

---

## Usage Patterns

### Single Skill
```
@java How do Records work?
@bazel Write a Starlark macro for testing
```

### Multiple Skills
```
@quarkus @graalvm Native build fails with reflection error
@rules-quarkus @gradle Migrate this Gradle project to Bazel
```

### Context-Aware
AI auto-selects skills based on:
- File context (`BUILD.bazel` → `@bazel`, `pom.xml` → `@maven`)
- Keywords in query
- Project structure

---

## Related Documentation

- **[docs/SKILLS-RELATIONSHIP.md](docs/SKILLS-RELATIONSHIP.md)** - Detailed skill relationships and architecture
- **[README.md](README.md)** - Quick start guide
- **[skills.sh](https://skills.sh)** - Discover more skills
