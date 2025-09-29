---
title: 🧠 Go for OOP Developers
nav_order: 0
---

# 🧠 Go for OOP Developers

A quick guide for developers transitioning from Object-Oriented languages (like Java, C#, or C++) to Go.

---

## 📘 Table of Contents

- [**1. 🚀 Introduction**](#1--introduction)
- [**2. 🧭 Summary**](#2--summary)
- [**3. 🔄 OOP vs Go: Conceptual Shifts**](#3--oop-vs-go-conceptual-shifts)
- [**4. 🧰 General Best Practices**](#4--general-best-practices)
- [**5. 🤝 Collaboration & Contributions**](#5--collaboration--contributions)

## 1. 🚀 Introduction

If you come from an Object-Oriented Programming (OOP) background, Go might initially feel minimalistic or even “too simple”.
You may look for familiar constructs like classes, inheritance, annotations, generics, or frameworks, and not find them the same way.

But Go is designed with clarity, simplicity, and explicitness in mind — trading some abstraction for ease of reasoning, concurrency, and performance.

This guide highlights the main paradigm shifts you’ll encounter and provides pro-tips for writing idiomatic Go code.

## 2. 🧭 Summary

Go isn’t OOP — it’s **simple, pragmatic, and compositional**.

Embrace **structs, interfaces, and composition**, and you’ll write **cleaner, faster, and more maintainable** systems.

## 3. 🔄 OOP vs Go: Conceptual Shifts

| Concept                  | In OOP (e.g., Java)                                | In Go (Golang)                                                                          |
| ------------------------ | -------------------------------------------------- | --------------------------------------------------------------------------------------- |
| Classes                  | Blueprints that encapsulate data + behavior        | No classes. Use struct to model data and functions with receivers to attach behavior    |
| Inheritance              | Core mechanism for reuse and polymorphism          | No inheritance. Use composition and interfaces instead                                  |
| Interfaces               | Declared and implemented explicitly via implements | Implicit implementation: any type that has the required methods satisfies the interface |
| Access Modifiers         | public, private, protected keywords                | Simplicity: Capitalized = exported (public), lowercase = unexported (private)           |
| Constructors             | Defined by name of class                           | Use factory functions, e.g. NewSomething()                                              |
| Annotations / Reflection | Commonly used for frameworks                       | Rarely used — prefer explicit configuration                                             |
| Exceptions               | Error handling via try/catch                       | No exceptions. Handle errors via explicit error returns                                 |
| Framework-driven         | Heavy reliance on frameworks (Spring, etc.)        | Go prefers libraries + composition, not frameworks                                      |
| Generics                 | Widely used                                        | Go supports generics (since 1.18), but encourages simple concrete types where possible  |
| Dependency Injection     | Automated by frameworks                            | Manual DI via constructors or function parameters                                       |
| Multithreading           | Threads, executors, futures                        | Lightweight goroutines and channels for concurrency                                     |

> 🧭 Go’s philosophy: “Composition over inheritance, simplicity over abstraction.”

## 4. 🧰 General Best Practices

- 🧭 Follow Go naming conventions:

  - Exported names **start with capital letters**.

  - Keep names **short and descriptive**.

- 📂 Organize code by **domain/package**, not layers.

- 🧪 Always test! Use `testing` package and keep tests in `*_test.go` files.

- ⚙️ Use `go fmt`, `go vet`, and `golangci-lint`.

## 📘 Detailed Contents

- [**💡 Key Mental Shifts**](./01_key-mental-shifts.md)
- [**🧰 Pro Tips for Writing Idiomatic Go**](./02_pro-tips-for-writing-idiomatic-go.md)
- [**🚧 Common Pitfalls for OOP Developers**](./03_pro-tips-for-writing-idiomatic-go.md)
- [**🧭 Migration Checklist — From Java (OOP) to Go 🦫**](./04_migration-checklist--from-java-oop-to-go.md)
- [**📚 References & Further Reading**](./05_references-further-reading.md)
