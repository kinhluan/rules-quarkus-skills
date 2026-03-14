---
name: maven-expert
description: Expert knowledge for Apache Maven, dependency management, BOMs, and Maven-to-Bazel migration. Use for build configuration and project lifecycle questions.
---

# maven-expert

> Keyword: maven | Platforms: gemini,claude,codex

Apache Maven Build Tool Expert Skill - The foundation of Java dependency management and project structure.

## Core Mandates

- **BOM Management:** Always prefer **BOM (Bill of Materials)** to manage versions (e.g., `quarkus-bom`, `jackson-bom`) to avoid dependency hell.
- **Dependency Scope:** Rigorously use `compile`, `provided`, `runtime`, and `test` scopes for cleaner artifacts.
- **Transitive Discipline:** Use `mvn dependency:tree` to identify and `exclude` conflicting transitive dependencies.
- **Reproducible Builds:** Lock down plugin versions in `<pluginManagement>`.

## Maven-to-Bazel Migration

- **Dependency Extraction:** Identify external dependencies for `maven_install` in `rules_jvm_external`.
- **Pom-to-Build:** Mapping Maven `<groupId>:<artifactId>` to Bazel `@maven//:group_artifact` targets.
- **Resource Management:** Translating Maven's `src/main/resources` convention to Bazel `resources` attributes.

## Optimization & Plugins

- **Multi-module Projects:** Efficiently managing parent-child relationships and `<relativePaths>`.
- **Essential Plugins:** Config and optimization for `maven-compiler-plugin`, `maven-surefire-plugin`, and `maven-shade-plugin`.
- **Profiles:** Using `-P` profiles for environment-specific configurations (dev, staging, prod).

## Expert Tips

- Avoid `<version>LATEST</version>` or `<version>RELEASE</version>`; it breaks build reproducibility.
- Use `mvn dependency:analyze` to find unused declared dependencies.
- Prefer `provided` scope for libraries that should be part of the runtime container (like Quarkus-core during augmentation).

## References

- [Apache Maven Documentation](https://maven.apache.org/guides/index.html)
- [Quarkus Maven Guide](https://quarkus.io/guides/maven-tooling)
- [rules_jvm_external (Bazel Maven support)](https://github.com/bazelbuild/rules_jvm_external)

## Skill Interoperability

The **maven-expert** 📦 skill acts as a source for dependency management and project orchestration, supporting:
- **rules-quarkus** 🔧: Facilitates the migration of Maven-based projects to Bazel.
