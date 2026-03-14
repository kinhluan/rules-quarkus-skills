# Skills Relationship

> Document describing the relationship and dependencies between the expert skills in this repository.

---

## Overview

This repository contains a comprehensive set of **8 distinct skills** designed to handle the full lifecycle of Modern Java development with Quarkus and Bazel:

| Skill | Keyword | Category | Scope |
|-------|---------|----------|-------|
| **java-expert** ☕ | `java` | Language | Modern Java (21+), Performance, Clean Code |
| **maven-expert** 📦 | `maven` | Tooling | Dependency management, BOM, Migration |
| **gradle-expert** 🐘 | `gradle` | Tooling | Modern build DSL, Multi-project, Migration |
| **vertx-expert** 🌀 | `vertx` | Foundation | Reactive engine, Event Loop, Non-blocking |
| **graalvm-expert** 🚀 | `graalvm` | Runtime | Native Image (AOT), Polyglot, Reflection |
| **bazel-expert** 🏗 | `bazel` | Infrastructure | General Bazel build system |
| **quarkus-expert** ⚡ | `quarkus` | Framework | High-perf Quarkus framework |
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

## Skill Descriptions

### 1. java-expert ☕ (Independent)
**Purpose:** Modern Java (21+) language expertise.
**Covers:** Virtual Threads, Records, Sealed Classes, JVM Tuning (G1GC/ZGC), JFR, Clean Architecture.

### 2. maven-expert 📦 (Independent)
**Purpose:** Dependency management and project orchestration.
**Covers:** BOMs, Transitive dependencies, Maven Lifecycle, Maven-to-Bazel migration.

### 3. gradle-expert 🐘 (Independent)
**Purpose:** Modern build DSL and performance.
**Covers:** Groovy/Kotlin DSL, Build Cache, Multi-project, Gradle-to-Bazel migration.

### 4. vertx-expert 🌀 (Depends on java-expert)
**Purpose:** Reactive programming foundation (Quarkus's engine).
**Covers:** Event Loop, Verticles, Event Bus, Non-blocking I/O, Reactive Clients.

### 5. graalvm-expert 🚀 (Depends on java-expert)
**Purpose:** Native Image (AOT) and polyglot runtime expertise.
**Covers:** Reflection/Resource config, Native Image Agent, Polyglot SDK, SubstrateVM.

### 6. bazel-expert 🏗 (Independent)
**Purpose:** General Bazel build system expertise.
**Covers:** Starlark, Rules, Macros, Hermeticity, Bzlmod, Performance optimization.

### 7. quarkus-expert ⚡ (Depends on java, vertx & graalvm)
**Purpose:** High-performance Quarkus framework knowledge.
**Covers:** Augmentation, CDI, Mutiny, Native Image integration, Dev Services.

### 8. rules-quarkus 🔧 (Depends on all above)
**Purpose:** Specialized integration for Quarkus on Bazel.
**Covers:** `quarkus_application`, `quarkus_bootstrap`, ClassLoader troubleshooting, Hermetic augmentation.

---

## Usage Scenarios

| Scenario | Primary Skill | Secondary Skill |
|----------|---------------|-----------------|
| "Build a Native Image for Quarkus" | `@quarkus` | `@graalvm` |
| "Troubleshoot reflection error in native" | `@graalvm` | `@quarkus` |
| "Explain why Event Loop is blocked" | `@vertx` | `@java` |
| "Migrate from Gradle to Bazel" | `@rules-quarkus` | `@gradle`, `@bazel` |
| "Configure Quarkus on Bazel" | `@rules-quarkus` | `@bazel`, `@quarkus` |
| "Migrate from Maven to Bazel" | `@rules-quarkus` | `@maven`, `@bazel` |

---

## Installation

Install all skills via:

```bash
npx skills add kinhluan/rules-quarkus-skills
```

---

## References

- [rules_quarkus](https://github.com/kinhluan/rules_quarkus)
- [Quarkus](https://quarkus.io)
- [GraalVM](https://www.graalvm.org)
- [Vert.x](https://vertx.io)
- [Gradle](https://gradle.org)
- [Maven](https://maven.apache.org)
- [Bazel](https://bazel.build)
