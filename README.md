# rules-quarkus-skills

[![Release](https://img.shields.io/github/v/release/kinhluan/rules-quarkus-skills)](https://github.com/kinhluan/rules-quarkus-skills/releases)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Validate Skills](https://github.com/kinhluan/rules-quarkus-skills/actions/workflows/validate.yml/badge.svg)](https://github.com/kinhluan/rules-quarkus-skills/actions/workflows/validate.yml)

> **Expert AI skills for Modern Java development with Quarkus and Bazel**
>
> 8 comprehensive skills covering Java, Quarkus, Bazel, Vert.x, GraalVM, and migration from Maven/Gradle.

---

## 🚀 Quick Start

```bash
npx skills add kinhluan/rules-quarkus-skills
```

This installs all 8 skills to your AI agent (Gemini CLI, Qwen Code, Claude Code, Cursor, etc.).

---

## 📦 Available Skills

| Skill | Keyword | Description |
|-------|---------|-------------|
| **java-expert** ☕ | `java` | Modern Java 21+, Virtual Threads, JVM tuning |
| **maven-expert** 📦 | `maven` | Dependency management, BOMs, migration |
| **gradle-expert** 🐘 | `gradle` | Build DSL, optimization, migration |
| **bazel-expert** 🏗 | `bazel` | Starlark rules, hermetic builds |
| **vertx-expert** 🌀 | `vertx` | Reactive programming, Event Loop |
| **graalvm-expert** 🚀 | `graalvm` | Native Image AOT, polyglot |
| **quarkus-expert** ⚡ | `quarkus` | Quarkus framework, CDI, Mutiny |
| **rules-quarkus** 🔧 | `rules-quarkus` | Quarkus + Bazel integration |

👉 **See [docs/skills-catalog.md](docs/skills-catalog.md) for full details and examples.**

---

## 📚 Documentation

| Doc | Description |
|-----|-------------|
| **[📋 Skills Catalog](docs/skills-catalog.md)** | Complete catalog with details for all 8 skills |
| **[🔗 Skills Relationship](docs/skills-relationship.md)** | Architecture, dependencies, and activation guide |

---

## 🎯 About this Skills Ecosystem

This is not just a collection of rules, but a **Multi-Layered Expert Assistant** for modern enterprise Java development. It bridges the gap between the speed of **Quarkus**, the scalability of **Bazel**, and the robustness of **Modern Java**.

### The Problem We Solve
[Quarkus Issue #11305](https://github.com/quarkusio/quarkus/issues/11305) identified a fundamental conflict between Quarkus's dynamic build-time "Augmentation" and Bazel's strictly hermetic model. Our ecosystem provides the **deep knowledge** needed to orchestrate this integration across every layer:

1.  **Language Layer:** Native Java 21+ and Virtual Thread expertise.
2.  **Foundation Layer:** Reactive engine (Vert.x) and Build tool (Maven/Gradle) transition.
3.  **Infrastructure Layer:** Hermetic Bazel rules and GraalVM Native Image optimization.
4.  **Application Layer:** High-performance Quarkus development.

**Learn more about the architecture in [docs/skills-relationship.md](docs/skills-relationship.md).**

---

## 💡 Usage Examples

```
@rules-quarkus CDIProvider error during augmentation
@quarkus When to use Virtual Threads vs Mutiny?
@bazel Optimize this Starlark rule for remote execution
@graalvm Reflection error in native build
@java How do Virtual Threads improve I/O performance?
```

---

## 📁 Project Structure

```
rules-quarkus-skills/
├── .agent-skills/          # Agent-agnostic skills (published)
│   ├── java-expert/
│   ├── maven-expert/
│   ├── gradle-expert/
│   ├── bazel-expert/
│   ├── vertx-expert/
│   ├── graalvm-expert/
│   ├── quarkus-expert/
│   └── rules-quarkus/
├── docs/                   # Detailed documentation
│   ├── skills-catalog.md   # Complete skills catalog
│   └── skills-relationship.md  # Architecture & dependencies
├── .github/                # GitHub Actions
├── GEMINI.md               # Extension metadata
├── README.md               # This file
└── LICENSE
```

> [!NOTE]
> Agent-specific directories (`.qwen/`, `.claude/`, etc.) are gitignored and only exist for local development.

---

## 🔗 Related Projects

| Project | Description |
|---------|-------------|
| [**rules_quarkus**](https://github.com/kinhluan/rules_quarkus) | Native Bazel build system for Quarkus |
| [Quarkus](https://quarkus.io) | Supersonic Subatomic Java Framework |
| [Bazel](https://bazel.build) | Fast, scalable build system |
| [skills.sh](https://skills.sh) | AI skills marketplace |

---

## 📝 License

[MIT](LICENSE) © 2026 Bùi Huỳnh Kinh Luân

---

**Fast, Correct, and Scalable.**