# rules-quarkus-skills

> **Expert AI Agent Skill for rules_quarkus**
> 
> This skill empowers AI agents to expertly build, maintain, and troubleshoot Quarkus applications using Bazel. It captures the "architectural soul" of the `rules_quarkus` project, ensuring hermeticity, performance, and scalability.

---

## 🏗 Architectural Mandates

When working with `rules_quarkus`, you MUST adhere to the **Three-Layer Hermetic Model**:

1.  **Layer 1: Compile (`java_library`)**
    *   Standard bytecode compilation with `javac`.
    *   Use `javacopts = ["-parameters"]` to ensure Quarkus parameter name retention.
2.  **Layer 2: Augment (`quarkus_bootstrap`)**
    *   The "Heavy Lifting" phase. Always use the official `QuarkusBootstrap` API via the `bootstrap_augmentor` tool.
    *   **Mandate:** Ensure all runtime dependencies are flagged with `DependencyFlags.RUNTIME_CP | DependencyFlags.DEPLOYMENT_CP` to prevent "Type not found in index" errors.
    *   **Mandate:** Use absolute paths for resolved artifacts in `ApplicationModelFactory` to avoid sandbox path resolution issues.
3.  **Layer 3: Runtime (`quarkus_runner`)**
    *   Always use the `quarkus_runner` rule (executable = True) instead of `genrule` wrappers.
    *   **Runfiles Support:** The runner script must resolve the `quarkus-app` directory from Bazel's `runfiles` using logic that supports both standard `bazel build` and `bazel run` (supporting `_main` and custom workspace names).

---

## 📦 Extension Strategy (5-Tier Model)

Always categorize and verify extensions according to the 5-Tier support model:

*   **Tier 1 (Core):** Arc (CDI), REST, Mutiny, Jackson, Vert.x.
*   **Tier 2 (Database):** Reactive clients (MySQL, Oracle, PostgreSQL), Redis.
*   **Tier 3 (Messaging):** Kafka, RabbitMQ, gRPC.
*   **Tier 4 (Observability):** Prometheus metrics, Health checks.
*   **Tier 5 (Quarkiverse):** LangChain4j AI, Tika, Unleash, and other community extensions.

**Workflow for adding new extensions:**
1.  Add both `runtime` and `deployment` artifacts to `MODULE.bazel`.
2.  Add necessary `exclusions` to prevent circular dependencies (common in Quarkus deployment modules).
3.  Verify via `examples/demo-extensions` by creating a simple endpoint.

---

## 🛠 Troubleshooting Workflows

### 1. "Unable to locate CDIProvider" or ClassNotFound errors
**Diagnosis:** ClassLoader mismatch during augmentation.
**Fix:** 
- Ensure `getOrCreateAugmentClassLoader()` is called explicitly.
- Verify the **TCCL Switch** (Thread Context ClassLoader) is implemented:
  ```java
  Thread.currentThread().setContextClassLoader(augmentCl);
  ```
- Use reflection to instantiate `AugmentActionImpl` directly from the correct ClassLoader.

### 2. "Argument list too long" in CI
**Diagnosis:** Too many dependencies being passed via command line flags.
**Fix:**
- Enable **Param Files** support in `quarkus_bootstrap.bzl` using `args.use_param_file("@%s")`.
- Ensure `ConfigParser.java` implements `expandArgs` logic to read and expand `@filename` arguments.

### 3. "Type not found in index" errors
**Diagnosis:** Missing `DEPLOYMENT_CP` flag in the `ApplicationModel`.
**Fix:** Audit `ApplicationModelFactory.java` to ensure all `RUNTIME_CP` dependencies also receive the `DEPLOYMENT_CP` flag.

---

## 🚀 Expert Tips

- **Hermeticity:** Never rely on system environment variables during the augmentation phase.
- **Boot Classloader:** Always launch Quarkus via `io.quarkus.bootstrap.runner.QuarkusEntryPoint` and include both `lib/boot/*` and `lib/main/*` in the classpath.
- **Bazel API:** Prefer `java_outputs` over the deprecated `outputs.jars` when collecting artifacts in Starlark rules.

---
*Stay Supersonic, Subatomic, Fast and Correct.*
