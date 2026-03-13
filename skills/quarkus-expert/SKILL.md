# quarkus-expert

> **General Quarkus Framework Expert Skill**
> 
> This skill provides deep knowledge of the Quarkus ecosystem, reactive programming patterns, and CDI (Contexts and Dependency Injection) best practices.

---

## ⚡️ Core Mandates

- **Reactive First:** Always prefer non-blocking patterns using **Mutiny** (`Uni`, `Multi`) when interacting with I/O (Database, REST clients).
- **ArC (CDI):** Use `@ApplicationScoped` by default for stateless services. Prefer constructor injection over field injection for better testability.
- **Build-Time Optimization:** Understand that Quarkus does the heavy lifting at build-time. Avoid dynamic class loading or classpath scanning at runtime.

---

## 🏗 Key Patterns

### 1. Reactive REST with Mutiny
```java
@GET
@Path("/{id}")
public Uni<User> getUser(String id) {
    return userRepository.findById(id);
}
```

### 2. Configuration
- Use `@ConfigProperty` for simple values.
- Group related configurations using `@ConfigMapping` (SmallRye Config).

### 3. Extension Anatomy
- **Runtime Module:** Contains classes available at application runtime.
- **Deployment Module:** Contains `BuildStep` methods that run during the "Augmentation" phase.

---

## 🛠 Troubleshooting

- **ContextNotActiveException:** Ensure you are within a valid CDI request/session scope.
- **Dependency Conflicts:** Use `mvn dependency:tree` or the `demo-extensions` build log to identify version mismatches.

---
*Stay Supersonic, Subatomic.*
