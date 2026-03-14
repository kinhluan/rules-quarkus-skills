# rules-quarkus-skills - Project Context

> **Expert AI skills for Modern Java development with Quarkus and Bazel**

---

## Project Overview

This repository contains **8 AI agent skills** that provide specialized knowledge for the full lifecycle of Modern Java development:

| Layer | Skills |
|-------|--------|
| **Foundation** | `java-expert`, `maven-expert`, `gradle-expert`, `bazel-expert` |
| **Framework & Runtime** | `vertx-expert`, `graalvm-expert`, `quarkus-expert` |
| **Integration** | `rules-quarkus` |

**Primary Purpose:** Accelerate development of [rules_quarkus](https://github.com/kinhluan/rules_quarkus) - a native Bazel integration for Quarkus that solves [Quarkus Issue #11305](https://github.com/quarkusio/quarkus/issues/11305).

**Target Platforms:** Gemini CLI, Qwen Code, Claude Code, Cursor, and any AI agent supporting skill/plugin systems.

---

## Project Structure

```
rules-quarkus-skills/
├── .agent-skills/              # Agent-agnostic skills (PUBLISHED)
│   ├── java-expert/
│   ├── maven-expert/
│   ├── gradle-expert/
│   ├── bazel-expert/
│   ├── vertx-expert/
│   ├── graalvm-expert/
│   ├── quarkus-expert/
│   └── rules-quarkus/
├── docs/                       # Documentation
│   ├── skills-catalog.md       # Complete skills catalog
│   └── skills-relationship.md  # Architecture & dependencies
├── .github/workflows/
│   └── validate.yml            # CI validation
├── GEMINI.md                   # Extension metadata
├── CONTRIBUTING.md             # Contribution guidelines
├── LICENSE                     # MIT License
└── README.md                   # Quick start guide
```

### Ignored Directories (Local Development Only)

Agent-specific config directories are gitignored:
`.adal/`, `.agent/`, `.claude/`, `.qwen/`, `.windsurf/`, `.cursor/`, etc.

---

## Skill Architecture

### 3-Layer Architecture

```
Layer 3: Integration
┌─────────────────────┐
│   rules-quarkus 🔧  │ ← Depends on ALL 7 skills below
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

### Skills Summary

| Skill | Keyword | Layer | Description |
|-------|---------|-------|-------------|
| **java-expert** | `java` | Foundation | Java 21+, Virtual Threads, JVM tuning, Clean Architecture |
| **maven-expert** | `maven` | Foundation | Dependency management, BOMs, migration to Bazel |
| **gradle-expert** | `gradle` | Foundation | Build DSL, optimization, migration to Bazel |
| **bazel-expert** | `bazel` | Foundation | Starlark rules, hermetic builds, Bzlmod |
| **vertx-expert** | `vertx` | Framework | Reactive programming, Event Loop, non-blocking I/O |
| **graalvm-expert** | `graalvm` | Runtime | Native Image AOT, polyglot, reflection config |
| **quarkus-expert** | `quarkus` | Framework | CDI, Mutiny, augmentation, Dev Services |
| **rules-quarkus** | `rules-quarkus` | Integration | Quarkus + Bazel integration, troubleshooting |

---

## Skill Format

Each skill directory contains:

```
.agent-skills/<skill-name>/
├── SKILL.md          # Human-readable skill definition (REQUIRED)
└── SKILL.toon        # Token-optimized format (OPTIONAL)
```

### SKILL.md Structure

```markdown
---
name: <skill-name>
description: <Brief description for AI activation>
---

# <Skill Name>

> Keyword: <keyword> | Platforms: gemini,claude,codex

## Core Mandates / Architectural Mandates

## Key Patterns / Components

## Troubleshooting

## References

## Skill Interoperability
```

---

## Development & Validation

### CI/CD Pipeline

GitHub Actions validates skills on push/PR:

```yaml
# .github/workflows/validate.yml
- Validate SKILL.md files exist
- Validate YAML frontmatter
- Validate SKILL.toon format (if present)
- Validate skills.json (if present)
- Check README.md, LICENSE exist
- Markdown syntax validation
```

### Adding a New Skill

1. Create directory: `.agent-skills/<skill-name>/`
2. Add `SKILL.md` with YAML frontmatter and "Core Mandates" section
3. (Optional) Add `SKILL.toon` for token-optimized consumption
4. Update `README.md` and `GEMINI.md`
5. Run validation: `gh workflow run validate.yml`

### Coding Standards

- **Mandates First:** Every skill must have "Core Mandates" or "Architectural Mandates"
- **Language:** English for all technical content
- **Obsidian Style:** Use callouts (`> [!TIP]`) and Mermaid diagrams

---

## Usage

### Installation (End Users)

```bash
# Install all skills
npx skills add kinhluan/rules-quarkus-skills

# Install specific skill
npx skills add kinhluan/rules-quarkus-skills --skill java-expert
```

### Manual Installation

```bash
# For Gemini CLI
cp -r .agent-skills/* ~/.gemini/skills/

# For Qwen Code
cp -r .agent-skills/* ~/.qwen/skills/

# For Claude Code
cp -r .agent-skills/* ~/.claude/skills/
```

### In-Session Activation

```bash
activate_skill .agent-skills/rules-quarkus
activate_skill .agent-skills/quarkus-expert
```

### Usage Examples

```
@rules-quarkus CDIProvider error during augmentation
@quarkus When to use Virtual Threads vs Mutiny?
@bazel Optimize this Starlark rule for remote execution
@graalvm Reflection error in native build
@java How do Virtual Threads improve I/O performance?
@vertx Why is my Event Loop blocked?
@maven How do I exclude a transitive dependency?
```

---

## Key Technologies

| Technology | Version | Purpose |
|------------|---------|---------|
| Java | 21+ | Primary language |
| Quarkus | 3.20.1 | Application framework |
| Bazel | 7.x+ | Build system |
| Vert.x | - | Reactive engine (Quarkus foundation) |
| GraalVM | - | Native Image AOT compilation |
| Maven/Gradle | - | Build tools (migration scenarios) |

---

## Related Projects

| Project | Description |
|---------|-------------|
| [rules_quarkus](https://github.com/kinhluan/rules_quarkus) | Native Bazel build system for Quarkus |
| [Quarkus](https://quarkus.io) | Supersonic Subatomic Java Framework |
| [Bazel](https://bazel.build) | Fast, scalable build system |
| [skills.sh](https://skills.sh) | AI skills marketplace |

---

## Important Notes

1. **Agent-Agnostic Design:** `.agent-skills/` works with any AI agent. Agent-specific directories (`.qwen/`, `.claude/`, etc.) are for local development only and should NOT be committed.

2. **Skill Interoperability:** Skills are designed to work together. `rules-quarkus` depends on all 7 other skills for comprehensive Quarkus+Bazel expertise.

3. **Three-Layer Transformation Pipeline** (rules-quarkus core concept):
   - **Layer 1:** `java_library` - Compile source to bytecode
   - **Layer 2:** `quarkus_bootstrap` - Augmentation phase
   - **Layer 3:** `quarkus_runner` - Orchestration and classloading

4. **5-Tier Extension Model** (for Quarkus extensions):
   - Tier 1: Core (Arc, REST, Jackson, Vert.x)
   - Tier 2: Data Persistence (MySQL, Oracle, Redis)
   - Tier 3: Messaging (Kafka, RabbitMQ, gRPC)
   - Tier 4: Observability (Metrics, Health)
   - Tier 5: Quarkiverse (LangChain4j, experimental)

---

## Files Reference

| File | Purpose |
|------|---------|
| `README.md` | Quick start guide with skills table |
| `GEMINI.md` | Extension metadata and activation guide |
| `CONTRIBUTING.md` | Guidelines for adding new skills |
| `docs/skills-catalog.md` | Detailed catalog of all 8 skills |
| `docs/skills-relationship.md` | Architecture, dependencies, activation guide |
| `.github/workflows/validate.yml` | CI validation pipeline |
| `.gitignore` | Excludes agent-specific directories |

---

**Motto:** Fast, Correct, and Scalable.
