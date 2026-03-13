# rules-quarkus-skills

> **Expert AI Agent Skills for Quarkus + Bazel Development**
>
> This extension provides specialized knowledge for building Quarkus applications with Bazel, including the rules_quarkus build system, Quarkus framework patterns, and Bazel best practices.

---

## 📦 Available Skills

### 1. rules-quarkus
**Keyword:** `rules-quarkus`  
**Description:** Expert knowledge for the rules_quarkus Bazel build system

**When to activate:**
- Building Quarkus apps with Bazel
- Troubleshooting augmentation errors
- Adding new Quarkus extensions to BUILD files

**Key topics:**
- Three-Layer Hermetic Model (Compile → Augment → Runtime)
- 5-Tier Extension support
- CDIProvider and ClassLoader troubleshooting
- Param files for large dependency lists

### 2. quarkus-expert
**Keyword:** `quarkus`  
**Description:** High-performance Quarkus framework expertise

**When to activate:**
- General Quarkus development questions
- Reactive patterns with Mutiny
- Extension development
- Native image troubleshooting

### 3. bazel-expert
**Keyword:** `bazel`  
**Description:** Bazel rules and Starlark best practices

**When to activate:**
- Writing custom Bazel rules
- Optimizing build performance
- Hermeticity and remote execution

---

## 🚀 Installation

### Option 1: Copy to skills directory

```bash
# For Gemini CLI
cp -r .agent-skills/* ~/.gemini/skills/

# For Qwen Code  
cp -r .agent-skills/* ~/.qwen/skills/

# For Claude Code
cp -r .agent-skills/* ~/.claude/skills/
```

### Option 2: Activate directly in session

```bash
# In Gemini CLI or Qwen Code
activate_skill .agent-skills/rules-quarkus
activate_skill .agent-skills/quarkus-expert
activate_skill .agent-skills/bazel-expert
```

---

## 📁 Structure

```
.agent-skills/
├── rules-quarkus/
│   ├── SKILL.md          # Main skill definition
│   └── SKILL.toon        # Compressed format (optional)
├── quarkus-expert/
│   └── SKILL.md
└── bazel-expert/
    └── SKILL.md
```

---

## 🔗 Related Projects

- **rules_quarkus:** https://github.com/kinhluan/rules_quarkus
- **Quarkus:** https://quarkus.io
- **Bazel:** https://bazel.build

---

## License

MIT
