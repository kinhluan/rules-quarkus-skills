---
name: rules-quarkus
description: Expert knowledge for building Quarkus applications with Bazel using the rules_quarkus build system. Use when user asks about Quarkus+Bazel builds, augmentation, or troubleshooting.
version: 1.1.0
keywords: [rules-quarkus, bazel, quarkus, build, integration, starlark]
---

# rules-quarkus

> Keyword: rules-quarkus | Platforms: gemini,claude,codex

Expert AI Agent Skill for **rules_quarkus** - Native Bazel integration for Quarkus that reconciles Quarkus's dynamic build-time "Augmentation" phase with Bazel's hermetic, deterministic build system.

**Solves:** [Quarkus Issue #11305](https://github.com/quarkusio/quarkus/issues/11305) (open since early 2020)

## Repository

- **Source:** https://github.com/kinhluan/rules_quarkus
- **Maintainers:** @kinhluan, @tructxn, @Nhannguyenus24

## Requirements

| Component | Version |
|-----------|---------|
| Bazel | 7.x+ |
| Java | 21 |
| Quarkus | 3.20.1 |

## Architectural Mandates

### Three-Layer Transformation Pipeline

| Layer | Rule | Purpose |
|-------|------|---------|
| **1. Compilation** | `java_library` | Compile source to bytecode, maximize caching efficiency |
| **2. Augmentation** | `quarkus_bootstrap` | Aggregate dependency graph, construct `ApplicationModel`, execute `AugmentAction` in sandbox |
| **3. Orchestration** | `quarkus_runner` | Handle Quarkus classloading, resolve paths from Bazel Runfiles |

### Core Macros

#### `quarkus_application`
Main rule for building executable Quarkus applications:
- Source files and resources
- Runtime and deployment extensions
- Main class configuration

#### `quarkus_library`
Creates reusable libraries for Quarkus applications

### Example BUILD.bazel

```python
load("@rules_quarkus//quarkus:defs.bzl", "quarkus_application")

quarkus_application(
    name = "enterprise-app",
    srcs = glob(["src/main/java/**/*.java"]),
    runtime_extensions = [
        "@maven//:io_quarkus_quarkus_arc",
        "@maven//:io_quarkus_quarkus_rest",
    ],
    deployment_extensions = [
        "@maven//:io_quarkus_quarkus_arc_deployment",
        "@maven//:io_quarkus_quarkus_rest_deployment",
    ],
)
```

## Extension Strategy (5-Tier Model)

| Tier | Category | Examples |
|------|----------|----------|
| Tier 1 (Core) | CDI, REST, HTTP | Arc, Mutiny, Jackson, Vert.x |
| Tier 2 (Data Persistence) | Reactive DB clients | Oracle, MySQL, PostgreSQL, Redis |
| Tier 3 (Messaging) | Async messaging | Kafka, RabbitMQ, gRPC |
| Tier 4 (Observability) | Monitoring | Prometheus metrics, Health checks |
| Tier 5 (Quarkiverse) | Community extensions | LangChain4j (AI/LLM), Tika, Unleash |

## Troubleshooting Workflows

### "Unable to locate CDIProvider" or ClassNotFound errors
- Ensure `getOrCreateAugmentClassLoader()` is called explicitly
- Verify TCCL Switch (Thread Context ClassLoader) is implemented
- Use reflection to instantiate `AugmentActionImpl` from correct ClassLoader

### "Argument list too long" in CI
- Enable **Param Files** support in `quarkus_bootstrap.bzl`
- Implement `expandArgs` logic to read and expand `@filename` arguments

### "Type not found in index" errors
- Audit `ApplicationModelFactory.java` for `DEPLOYMENT_CP` flag

## Key APIs & Components

- **`QuarkusBootstrap` API** - Official API for native integration
- **`ApplicationModel`** - Deterministic metadata representation
- **`AugmentAction`** - Executes bytecode transformation in sandbox
- **`quarkus_bootstrap`** - Custom Bazel rule for augmentation
- **`quarkus_runner`** - Specialized runner for Quarkus classloading

## Expert Tips

- Never rely on system environment variables during augmentation
- Launch Quarkus via `io.quarkus.bootstrap.runner.QuarkusEntryPoint`
- Prefer `java_outputs` over deprecated `outputs.jars` in Starlark
- Ensure hermetic, deterministic builds with fast startup times

## References

- [rules_quarkus GitHub](https://github.com/kinhluan/rules_quarkus)
- [Bazel Support for Quarkus Blog](https://github.com/kinhluan/rules_quarkus/blob/main/docs/blogs/2026-03-11-bazel-support-for-quarkus.md)
- [Quarkus Documentation](https://quarkus.io/guides/)
- [Bazel Documentation](https://bazel.build/)

## Skill Interoperability

The **rules-quarkus** 🔧 skill integrates all other skills to provide a complete Quarkus development experience on Bazel:
- **java-expert** ☕, **vertx-expert** 🌀, **graalvm-expert** 🚀: For framework and runtime support.
- **maven-expert** 📦, **gradle-expert** 🐘: For migrating existing projects.
- **bazel-expert** 🏗: For core build system infrastructure.
- **quarkus-expert** ⚡: For specialized framework knowledge.
