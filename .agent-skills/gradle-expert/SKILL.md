---
name: gradle-expert
description: Expert knowledge for Gradle Build Tool, dependency management, and Gradle-to-Bazel migration. Use for build configuration and project lifecycle questions.
version: 1.1.0
keywords: [gradle, build, kotlin-dsl, migration, java, groovy]
---

# gradle-expert

> Keyword: gradle | Platforms: gemini,claude,codex

Modern Gradle Build Tool Expert Skill - Specialized in performance, dependency management, and polyglot builds.

## Core Mandates

- **DSL Proficiency:** Expert in both **Groovy DSL** (`build.gradle`) and **Kotlin DSL** (`build.gradle.kts`).
- **Dependency Configurations:** Distinguish between `api`, `implementation`, `runtimeOnly`, and `testImplementation`.
- **Build Performance:** Leverage **Build Cache**, **Daemon**, and **Parallel execution** to optimize feedback loops.
- **Convention over Configuration:** Prefer built-in plugins (`java-library`, `application`, `maven-publish`) over custom logic.

## Gradle-to-Bazel Migration

- **Configuration Mapping:** Translating Gradle `api` to Bazel `exports`, and `implementation` to Bazel `deps`.
- **Dependency Resolution:** Exporting Gradle dependency graphs for use with `rules_jvm_external`.
- **Plugin Translation:** Mapping complex Gradle plugins (e.g., `io.quarkus`) to Bazel rules (`rules_quarkus`).
- **Multi-project Layout:** Handling `settings.gradle` subproject structures in Bazel workspaces.

## Advanced Patterns

- **Build Scan:** Using Gradle Build Scans for debugging performance and dependency issues.
- **Custom Tasks:** Writing idiomatic tasks using the **Task Configuration Avoidance API**.
- **Version Catalogs:** Managing versions and libraries centrally via `libs.versions.toml`.

## Expert Tips

- Avoid using the "all-encompassing" `compile` configuration (deprecated).
- Use `gradle help --dependencies` to visualize the dependency graph.
- Prefer **Kotlin DSL** for better IDE support and type safety in complex builds.

## References

- [Gradle Documentation](https://docs.gradle.org/current/userguide/userguide.html)
- [Quarkus Gradle Guide](https://quarkus.io/guides/gradle-tooling)
- [Gradle-to-Bazel Migration Blog](https://blog.bazel.build/2019/07/01/gradle-to-bazel.html)

## Skill Interoperability

The **gradle-expert** 🐘 skill provides expertise in modern build DSLs and performance, supporting:
- **rules-quarkus** 🔧: Facilitates the migration of Gradle-based projects to Bazel.
