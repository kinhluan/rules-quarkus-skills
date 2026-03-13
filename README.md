# rules-quarkus-skills

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Validate Skills](https://github.com/kinhluan/rules-quarkus-skills/actions/workflows/validate.yml/badge.svg)](https://github.com/kinhluan/rules-quarkus-skills/actions/workflows/validate.yml)
[![Gemini CLI](https://img.shields.io/badge/Gemini%20CLI-Skill-blue)](https://geminicli.com)
[![Qwen Code](https://img.shields.io/badge/Qwen%20Code-Skill-purple)](https://github.com/QwenLM/qwen-code)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-orange)](https://claude.ai/code)

> **Expert AI skills for building Quarkus applications with Bazel**
>
> Created to support development of [**rules_quarkus**](https://github.com/kinhluan/rules_quarkus) - Native Bazel integration for Quarkus.

---

## 🎯 Why This Exists

I created this skills collection to accelerate development of **rules_quarkus**, which solves a challenge that has been open since early 2020 ([Quarkus Issue #11305](https://github.com/quarkusio/quarkus/issues/11305)): **reconciling Quarkus's dynamic build-time "Augmentation" phase with Bazel's hermetic, deterministic build system**.

### The Problem

Quarkus augmentation (CDI proxy generation, bytecode indexing, metadata optimization) was tightly coupled with Maven/Gradle. Early attempts using `genrule` wrappers around Maven/Gradle sacrificed:
- ❌ Incremental builds
- ❌ Remote caching
- ❌ Hermeticity

### The Solution: Native Integration (V2)

Using the official **`QuarkusBootstrap` API**, rules_quarkus treats Quarkus as build-time primitives rather than external CLI, enabling:
- ✅ Hermetic builds
- ✅ Incremental builds
- ✅ Remote caching
- ✅ Deterministic outputs

These skills encode the **Three-Layer Transformation Pipeline** and architectural patterns from rules_quarkus, enabling AI assistants to provide expert-level guidance when debugging build issues or adding new extensions.

---

## 📦 Available Skills

### 1. rules-quarkus 🔧

| | |
|---|---|
| **Keyword** | `rules-quarkus` |
| **Category** | Backend / Build Systems |
| **Platforms** | Gemini CLI, Qwen Code, Antigravity |

**What it covers:**

#### Three-Layer Transformation Pipeline

| Layer | Rule | Purpose |
|-------|------|---------|
| **1. Compilation** | `java_library` | Compile source to bytecode, maximize caching efficiency |
| **2. Augmentation** | `quarkus_bootstrap` | Aggregate dependency graph, construct `ApplicationModel`, execute `AugmentAction` in sandbox |
| **3. Orchestration** | `quarkus_runner` | Handle Quarkus classloading, resolve paths from Bazel Runfiles |

#### Core Macros
- **`quarkus_application`** - Main rule for building executable Quarkus apps
- **`quarkus_library`** - Create reusable libraries

#### 5-Tier Extension Support

| Tier | Category | Extensions |
|------|----------|------------|
| **Tier 1** | Core | Arc (CDI), REST (JAX-RS), Jackson, Vert.x |
| **Tier 2** | Data Persistence | Reactive MySQL, Oracle, Redis |
| **Tier 3** | Messaging | Kafka, RabbitMQ, gRPC |
| **Tier 4** | Observability | Prometheus Metrics, Health Checks |
| **Tier 5** | Quarkiverse | LangChain4j (AI/LLM), Experimental Integrations |

#### Troubleshooting
- CDIProvider errors, ClassLoader issues
- "Argument list too long" in CI
- Type not found in index errors
- TCCL (Thread Context ClassLoader) switches

**When to use:**
- Building Quarkus apps with Bazel
- Debugging augmentation failures
- Adding new Quarkus extensions to BUILD files
- Resolving ClassNotFound or Type not found errors

---

### 2. quarkus-expert ⚡

| | |
|---|---|
| **Keyword** | `quarkus` |
| **Category** | Backend / Frameworks |
| **Platforms** | Gemini CLI, Qwen Code, Antigravity |

**What it covers:**
- **Build-Time First**: Augmentation phase optimization
- **Java 21+**: Virtual threads, modern patterns
- **Reactive**: Mutiny (Uni, Multi), non-blocking I/O
- **Persistence**: Hibernate Panache, Reactive SQL clients
- **Cloud-Native**: OpenTelemetry, Health checks, Security
- **Extension Development**: BuildStep, STATIC_INIT vs RUNTIME_INIT

**When to use:**
- General Quarkus framework questions
- Reactive programming with Mutiny
- Creating custom Quarkus extensions
- Native image troubleshooting

---

### 3. bazel-expert 🏗

| | |
|---|---|
| **Keyword** | `bazel` |
| **Category** | Infrastructure / Build Tools |
| **Platforms** | Gemini CLI, Qwen Code, Antigravity |

**What it covers:**
- **Starlark Best Practices**: Rules vs Macros, Providers, depsets
- **Hermeticity**: Declared inputs, no network access
- **Performance**: Param files, remote execution, action mnemonics
- **Bzlmod**: Modern dependency management

**When to use:**
- Writing custom Bazel rules
- Optimizing build performance
- Debugging hermeticity issues
- Remote build configuration

---

## 🚀 Installation

### Option 1: Copy to config directory (Recommended)

```bash
# For Gemini CLI
cp -r .agent-skills/* ~/.gemini/skills/

# For Qwen Code
cp -r .agent-skills/* ~/.qwen/skills/

# For Claude Code
cp -r .agent-skills/* ~/.claude/skills/

# For Google Antigravity
cp -r .agent-skills/* ~/.gemini/antigravity/skills/
```

### Option 2: Activate in session

```bash
# In Gemini CLI or Qwen Code
activate_skill .agent-skills/rules-quarkus
activate_skill .agent-skills/quarkus-expert
activate_skill .agent-skills/bazel-expert
```

---

## 💡 Usage Examples

### Example 1: Debugging augmentation error
```
@rules-quarkus I'm getting "Unable to locate CDIProvider" during augment phase.
What should I check?
```

### Example 2: Adding new extension
```
@rules-quarkus How do I add the Kafka extension to my BUILD file?
What are the runtime and deployment artifacts I need?
```

### Example 3: Performance optimization
```
@bazel My build is slow due to large dependency graphs.
How can I optimize the depset usage in my Starlark rules?
```

### Example 4: Reactive patterns
```
@quarkus When should I use Virtual Threads vs Mutiny Uni/Multi?
What are the trade-offs?
```

---

## 📁 Project Structure

```
rules-quarkus-skills/
├── .agent-skills/
│   ├── rules-quarkus/
│   │   ├── SKILL.md          # Human-readable documentation
│   │   └── SKILL.toon        # Compressed format (token-efficient)
│   ├── quarkus-expert/
│   │   ├── SKILL.md
│   │   └── SKILL.toon
│   └── bazel-expert/
│       ├── SKILL.md
│       └── SKILL.toon
├── GEMINI.md                  # Extension metadata
├── README.md                  # This file
└── LICENSE                    # MIT License
```

---

## 🔗 Related Projects

| Project | Description |
|---------|-------------|
| [**rules_quarkus**](https://github.com/kinhluan/rules_quarkus) | Native Bazel build system for Quarkus |
| [Quarkus](https://quarkus.io) | Supersonic Subatomic Java Framework |
| [Bazel](https://bazel.build) | Fast, scalable build system |
| [Gemini CLI](https://geminicli.com) | Google's AI-powered CLI tool |
| [Qwen Code](https://github.com/QwenLM/qwen-code) | Alibaba's AI coding assistant |
| [Claude Code](https://claude.ai/code) | Anthropic's AI coding assistant |

---

## 📝 License

[MIT](LICENSE) © 2026 Bùi Huỳnh Kinh Luân

---

Supersonic, Subatomic, and now: Fast, Correct, and Scalable.