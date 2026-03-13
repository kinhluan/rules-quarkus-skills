# bazel-expert

> **High-Performance Bazel & Starlark Expert Skill**
> 
> This skill provides expert guidance on building, maintaining, and optimizing large-scale Bazel workspaces. It focuses on the "Fast and Correct" philosophy, ensuring reproducibility, scalability, and extreme build efficiency.

---

## 🏗 Architectural Mandates

- **Hermeticity:** Actions must depend only on declared inputs. No network access or non-deterministic system file reads during execution.
- **Granularity:** Use fine-grained targets. Large targets break caching; small targets maximize it and enable faster incremental builds.
- **Explicitness:** Never use `glob` for dependencies. Dependencies must be explicit to keep the build graph predictable and cache-friendly.
- **Reproducibility:** Always pin external dependencies with a `sha256` checksum to prevent non-deterministic build failures.
- **Visibility:** Use visibility as an architectural tool. Enforce strict boundaries between modules to prevent "spaghetti" dependency graphs in monorepos.

---

## 🛠 Advanced Query & Analysis

- **Bazel Query:** Use `bazel query` for exploring the graph. Master `rdeps` (reverse dependencies) to perform impact analysis.
- **CQuery (Configured Query):** Use `cquery` when you need to analyze the graph after flag/configuration resolution.
- **AQuery (Action Query):** Use `aquery` to inspect the actual commands, environment variables, and inputs of generated actions.
- **CI Logic:** Programmatically determine which targets need to be built/tested based on changed files since the last stable commit.

---

## ⚡️ Performance Optimization

- **Multi-Layer Caching:**
    *   **Repository Cache:** Share downloaded external artifacts across workspaces.
    *   **Disk Cache:** Persist build artifacts locally across `bazel clean`.
    *   **Remote Cache:** Enable team-wide artifact sharing via gRPC/HTTP backends (e.g., Buildbarn, EngFlow).
- **Remote Execution (RBE):** Design rules to be RBE-compatible by avoiding hardcoded absolute paths and ensuring all toolchains are explicitly declared.
- **Resource Throttling:** Use `.bazelrc` to manage resource consumption (e.g., `build --local_cpu_resources=HOST_CPUS-2`) to keep developer machines responsive.

---

## 🔍 Profiling & Debugging

- **Bottleneck Analysis:** Generate and analyze `profile.json` using `--profile=/tmp/prof.json` to identify slow actions and critical path delays.
- **Cache Miss Debugging:** Use `--execution_log_json_file` to compare execution logs and find non-deterministic inputs causing cache misses.
- **Explainability:** Use `--explain=/tmp/explain.txt --verbose_explanations` to understand why Bazel is re-running a specific action.

---

## 🔌 Starlark & Rule Development

- **Depsets:** Always use `depsets` for transitive dependencies to maintain $O(n)$ memory complexity. NEVER use lists for large transitive collections.
- **Provider Pattern:** Use custom `Providers` to pass structured metadata between rules (e.g., Quarkus extension metadata or deployment info).
- **Param Files:** Use `ctx.actions.args().use_param_file("@%s")` for any action that might exceed the OS command-line length limit.
- **Platforms & Toolchains:** Use `platform` and `toolchain` rules instead of hardcoded paths to ensure cross-platform compatibility and RBE readiness.

---
*Fast and Correct.*
