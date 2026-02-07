---
title: Idiomatic Go Pro Tips
nav_order: 2
---

# Idiomatic Go Pro Tips

This section highlights **practical guidelines** to help developers coming from Object-Oriented languages write Go code that feels **natural, simple, and maintainable**.

Most of these tips exist to **prevent common OOP anti-patterns** from leaking into Go code.

---

## General Guidelines

- Follow Go naming conventions:
  - **Exported identifiers start with capital letters**
  - Prefer **short, meaningful names** over verbose ones

- Organize code by **domain or responsibility**, not by technical layers  
  (avoid `controller`, `service`, `repository` packages by default)

- Prefer the standard toolchain:
  - `go fmt` for formatting
  - `go vet` for static analysis
  - `golangci-lint` for broader linting

- Tests are part of the language:
  - Use the `testing` package
  - Keep tests in `*_test.go` files

---

## 1. Code Design (Unlearning OOP Habits)

- Keep functions **small and focused**
  - Large “do-everything” methods are harder to reason about

- Prefer **simple functions** over deep object graphs

- Use `struct` to represent **state**, not behavior hierarchies

- Use **methods with receivers** only when behavior depends on internal state

- Avoid speculative abstractions  
  If you don’t have multiple implementations yet, don’t design for them

## 2. Interfaces: Decoupling Without Hierarchies

- Interfaces should be:
  - Small (often 1 method)
  - Defined **where they are consumed**, not globally

- Do not mirror Java-style service interfaces by default

```go
type ElasticSearchClient interface {
    Index(ctx context.Context, index string, id string, body interface{}) error
}
```

This keeps dependencies explicit and testing simple.

## 3. Structs Are Not Classes

In Go, `struct` is a **data container**, not a class.

Use methods when behavior:

- Depends on internal state
- Logically belongs to the data

```go
type LogService struct {
    esClient ElasticSearchClient
}

func (s *LogService) Process(log Log) error {
    // logic using internal state
}
```

Avoid turning structs into “Java-style services” with excessive methods.

## 4. Values vs Pointers

Understanding this distinction is critical in Go.

Use **pointers** when:

- You need to mutate the original value
- The struct is large and copying is expensive

Use **values** when:

- The data is small
- Immutability improves clarity

This replaces many patterns that rely on object references in OOP.

## 5. Error Handling is Control Flow

Errors are returned, not thrown.

Handle them **immediately** and explicitly.

```go
res, err := doSomething()
if err != nil {
    return nil, err
}
```

Avoid wrapping large blocks in abstractions just to “hide” error handling.

## 6. Concurrency Is a Language Feature

Go treats concurrency as a first-class concept.

- Use goroutines for concurrent execution
- Use channels to communicate safely
- Protect shared state with `sync.Mutex` or channel-based designs

Avoid translating thread-pool or executor-based designs directly from Java.

## Final Advice

If your Go code feels overly abstract, heavily layered, or framework-driven,  
you are likely **writing Java in Go syntax**.

Idiomatic Go favors:

- Explicit code
- Shallow designs
- Clear data flow
- Simple abstractions
