# quarkus-expert

> **High-Performance Quarkus Framework Expert Skill**
> 
> This skill provides deep, production-grade knowledge of the Quarkus ecosystem, focusing on the "Supersonic Subatomic" philosophy. It covers everything from reactive patterns to cloud-native security and extension development.

---

## ⚡️ Core Mandates

- **Build-Time First:** Move as much processing as possible to the "Augmentation" phase. Minimize runtime classpath scanning and reflection.
- **Java 21+ Excellence:** Leverage **Virtual Threads** (`@RunOnVirtualThread`) for blocking operations to maintain high throughput without complex reactive code.
- **Reactive Discipline:** Use **Mutiny** (`Uni`, `Multi`) for non-blocking I/O. Never mix blocking drivers (e.g., standard JDBC) with reactive engines without careful thread management.
- **Dependency Discipline:** Always use the **Quarkus BOM** to manage versions. Avoid version overrides unless absolutely necessary.
- **Constructor Injection:** Mandate constructor injection over field injection for better testability and ArC (CDI) optimization.

---

## 🏗 Architectural Patterns

### 1. Persistence Strategy
- **Imperative:** Use **Hibernate ORM with Panache** (Active Record or Repository pattern) for standard relational data.
- **Reactive:** Use **Reactive SQL Clients** (MySQL, PostgreSQL, Oracle) for maximum I/O efficiency.
- **Dev Services:** Leverage Quarkus Dev Services for zero-config databases and brokers during development.

### 2. Cloud-Native Observability
- **OpenTelemetry (OTel):** Standardize on OTel for tracing and metrics (supersedes OpenTracing).
- **Health Checks:** Implement both `Liveness` (is it alive?) and `Readiness` (is it ready to serve?) probes using MicroProfile Health.

### 3. Security Architecture
- Use **Proactive Authentication** and RBAC with `@RolesAllowed`.
- Prefer OIDC/JWT for stateless microservices.

---

## 🧪 Testing Depth

- **Integration Testing:** Use `@QuarkusTest` for full-stack integration tests.
- **Mocking:** Utilize `@InjectMock` and `@InjectSpy` to isolate components under test.
- **Parity:** Use **Testcontainers** (often via Dev Services) to ensure the test environment matches production.

---

## 🔌 Extension Development (Expert Level)

- **Build-Time (Deployment):** Understand how to write `BuildStep` methods to register beans, generate bytecode, or process configuration.
- **Runtime Init:** Differentiate between `STATIC_INIT` (happens once during build/native init) and `RUNTIME_INIT`.

---

## 🛠 Troubleshooting

- **ClassLoader Leaks:** Monitor for issues when using custom dynamic class loading (not recommended).
- **ContextNotActiveException:** Ensure CDI contexts are properly propagated, especially when using Mutiny across different threads.
- **Native Image Failures:** Analyze `reports/` and provide `reflection-config.json` for libraries not yet Quarkus-native-ready.

---
*Supersonic, Subatomic, Fast and Correct.*
