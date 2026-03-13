# bazel-expert

> **General Bazel & Starlark Expert Skill**
> 
> This skill provides expert guidance on writing idiomatic Bazel rules, managing complex dependency graphs, and optimizing build performance.

---

## 🏗 Architectural Mandates

- **Hermeticity:** Actions must only depend on declared inputs. Never access the network or un-declared system files during execution.
- **Granularity:** Break large targets into smaller `java_library` or `starlark` rules to maximize caching and incremental builds.
- **Bzlmod:** Always use Bzlmod for external dependency management in new projects.

---

## 🛠 Starlark Best Practices

- **Avoid Macros for Logic:** Use `rules` for complex logic and `macros` only for wrapping multiple rules together.
- **Provider Pattern:** Use custom `Providers` to pass complex information between rules (e.g., custom metadata for Quarkus extensions).
- **Depsets:** Always use `depsets` instead of `lists` for collecting transitive dependencies to avoid $O(n^2)$ memory and time complexity.

---

## ⚡️ Performance Optimization

- **Param Files:** Use `ctx.actions.args().use_param_file("@%s")` for any action that might exceed the command-line length limit.
- **Remote Execution:** Ensure all rules are compatible with remote execution (no hardcoded absolute paths, use `toAbsolutePath()` carefully).
- **Action Mnemonics:** Use descriptive `mnemonic` and `progress_message` for all actions to aid in debugging and profiling.

---
*Fast and Correct.*
