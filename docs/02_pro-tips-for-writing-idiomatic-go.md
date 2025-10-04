---
title: 🧰 Pro Tips for Writing Idiomatic Go
nav_order: 2
---

# 🧰 Pro Tips for Writing Idiomatic Go

## General Best Practices

- 🧭 Follow Go naming conventions:

  - Exported names **start with capital letters**.

  - Keep names **short and descriptive**.

- 📂 Organize code by **domain/package**, not layers.

- 🧪 Always test! Use `testing` package and keep tests in `*_test.go` files.

- ⚙️ Use `go fmt`, `go vet`, and `golangci-lint`.

## 1. 🧠 Code Design

- ✅ **Keep functions small and focused** — one responsibility per function.

- 🧪 **Prefer pure functions** when possible (no side effects).

- 🧱 **Use** `struct` to represent entities with state.

- **⚙️ Use methods with receivers** when behavior depends on internal state.

- 🧩 **Use interfaces** to decouple components and make testing easier.

  - Define **interfaces where they are used**, not globally.

- 🚀 **Favor composition** over inheritance.

- 🪶 **Avoid unnecessary abstraction** — Go values clarity over flexibility.

## 2. 📦 Data and Pointers

- 📌 **Use pointers** (`*Type`) when:

  - You need to modify the original value.

  - You want to avoid copying large structs.

- 📄 **Use values** (`Type`) when:

  - The data is small and immutable.

  - You want clear ownership (e.g., `Log` struct in search results).

## 3. 🧱 Structs as "Classes"

- Use `struct` for data + methods with receiver when behavior belongs to the entity.

- Example:

  ```go
    type LogService struct {
      esClient ElasticSearchClient
    }

    func (s *LogService) Process(log Log) error {
      // logic using internal state
    }
  ```

## 4. 🧩 Interfaces

- ✅ Keep them small (1-2 methods).

- 🚀 Define them at the **consumer side**, not producer.

- Example:

  ```go
    type ElasticSearchClient interface {
      Index(ctx context.Context, index string, id string, body interface{}) error
    }
  ```

## 5. 🧠 Error Handling

- Return `(result, error)` and handle errors immediately.

- Prefer clarity over cleverness:

```go
  res, err := doSomething()
  if err != nil {
    return nil, err
  }
```

### 6. 🔄 Concurrency

- 🧵 Use goroutines (`go func() { ... }()`) for async tasks.

- 📡 Use **channels** for safe communication between goroutines.

- 🔐 Protect shared state with **sync.Mutex** or **channel patterns**.
