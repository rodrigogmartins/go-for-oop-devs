---
title: 🚧 Common Pitfalls for OOP Developers
nav_order: 3
---

# 🚧 Common Pitfalls for OOP Developers

## 📘 Table of Contents

- [**1. 🧱 Trying to Build Class Hierarchies**](#1--trying-to-build-class-hierarchies)
- [**2. 🧩 Overusing Interfaces**](#2--overusing-interfaces)
- [**3. 🌀 Expecting Constructors and Setters**](#3--expecting-constructors-and-setters)
- [**4. 🪄 Looking for Framework Magic**](#4--looking-for-framework-magic)
- [**5. 📦 Organizing by Layer Instead of Domain**](#5--organizing-by-layer-instead-of-domain)
- [**6. 🧠 Misusing Pointers**](#6--misusing-pointers)
- [**7. 🔄 Forgetting Error Handling Philosophy**](#7--forgetting-error-handling-philosophy)
- [**8. 🧪 Mocking with Interfaces Too Early**](#8--mocking-with-interfaces-too-early)
- [**9. 🧭 Expecting Runtime Type Safety**](#9--expecting-runtime-type-safety)
- [**10. 🚀 Ignoring Concurrency Primitives**](#10--ignoring-concurrency-primitives)

---

When transitioning from Java or other OOP languages to Go, it’s easy to bring habits that don’t fit the Go philosophy.

Here are some common mistakes and how to avoid them:

## 1. 🧱 Trying to Build Class Hierarchies

- ❌ **Don’t**: Attempt to mimic inheritance with complex struct embedding or design deep hierarchies.

- ✅ **Do**: Use **composition** — embed structs for reuse and define small, focused **interfaces** for polymorphism.

## 2. 🧩 Overusing Interfaces

- ❌ **Don’t**: Create interfaces for every struct “just in case.”

- ✅ **Do**: Define interfaces **where they are used**, not where they are implemented. Go prefers **interface consumers**, not producers.

## 3. 🌀 Expecting Constructors and Setters

- ❌ **Don’t**: Try to enforce encapsulation through private fields and setter/getter methods.

- ✅ **Do**: Use simple **factory functions** (`NewType()`) and **exported fields** when appropriate. Keep things explicit and straightforward.

## 4. 🪄 Looking for Framework Magic

- ❌ **Don’t**: Expect dependency injection frameworks, annotations, or runtime reflection magic.

- ✅ **Do**: Embrace **explicit wiring and simple initialization**. Go favors clarity over automation.

## 5. 📦 Organizing by Layer Instead of Domain

- ❌ **Don’t**: Create separate `services/`, `controllers/`, `repositories/` folders like in typical OOP MVC projects.

- ✅ **Do**: Organize by **feature or domain** (e.g., `internal/logs/`) — this makes code easier to navigate and maintain.

## 6. 🧠 Misusing Pointers

- ❌ **Don’t**: Use pointers everywhere by default.

- ✅ **Do**: Use pointers only when you need to **modify a value**, **avoid copying large structs**, or **represent nil**. Primitive types and small structs often work best as values.

## 7. 🔄 Forgetting Error Handling Philosophy

- ❌ **Don’t**: Expect try/catch or unchecked exceptions.

- ✅ **Do**: Handle errors **explicitly** with `if err != nil` and wrap them when needed. This leads to more predictable, robust programs.

## 8. 🧪 Mocking with Interfaces Too Early

- ❌ **Don’t**: Abstract everything into interfaces just for tests.

- ✅ **Do**: Introduce interfaces **only when you have multiple implementations** or need mocking in tests.

## 9. 🧭 Expecting Runtime Type Safety

- ❌ **Don’t**: Depend on reflection or runtime type information to enforce behavior.

- ✅ **Do**: Leverage Go’s **static typing** and compiler checks; simplicity wins over metaprogramming.

## 10. 🚀 Ignoring Concurrency Primitives

- ❌ **Don’t**: Rely solely on threads or locks as in OOP.

- ✅ **Do**: Learn and use Go’s **goroutines** and **channels** — they’re lightweight and designed for safe, concurrent operations.
