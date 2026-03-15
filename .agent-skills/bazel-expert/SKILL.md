---
name: bazel-expert
description: Expert knowledge for writing idiomatic Bazel rules, Starlark best practices, and build performance optimization. Use for Bazel build system questions.
version: 1.1.0
keywords: [bazel, starlark, monorepo, build-system, hermetic, build]
---

# bazel-expert

> Keyword: bazel | Platforms: gemini,claude,codex

General Bazel & Starlark Expert Skill - Expert guidance on writing idiomatic Bazel rules and optimizing build performance.

## Architectural Mandates

- **Hermeticity:** Actions must only depend on declared inputs
- **Granularity:** Break large targets into smaller `java_library` or `starlark` rules
- **Bzlmod:** Always use Bzlmod for external dependency management

## Starlark Best Practices

- **Avoid Macros for Logic:** Use `rules` for complex logic, `macros` for wrapping
- **Provider Pattern:** Use custom `Providers` to pass complex information between rules
- **Depsets:** Always use `depsets` instead of `lists` for transitive dependencies

## Performance Optimization

- **Param Files:** Use `ctx.actions.args().use_param_file("@%s")` for long command lines
- **Remote Execution:** Ensure rules are compatible with remote execution
- **Action Mnemonics:** Use descriptive `mnemonic` and `progress_message` for debugging

## References

- [Bazel Documentation](https://bazel.build/)
- [Starlark Language Spec](https://github.com/bazelbuild/starlark/blob/master/spec.md)
- [Bzlmod Documentation](https://bazel.build/external/overview)

## Skill Interoperability

The **bazel-expert** 🏗 skill provides the core build infrastructure for:
- **rules-quarkus** 🔧: Integrates Quarkus build and augmentation logic into the Bazel ecosystem.
