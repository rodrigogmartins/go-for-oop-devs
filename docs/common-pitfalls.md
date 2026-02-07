---
title: Common Pitfalls
nav_order: 3
---

# Common Pitfalls for OOP Developers

This page lists **common mistakes** developers make when bringing Object-Oriented habits into Go code.

If something here feels familiar, it probably means you're writing **Java-style design in Go**.

---

## 1. Trying to Build Class Hierarchies

- ❌ Deep inheritance trees via struct embedding
- ✅ Prefer flat designs with composition and small interfaces

## 2. Overusing Interfaces

- ❌ Interfaces everywhere “just in case”
- ✅ Define interfaces only when multiple implementations are needed

## 3. Expecting Constructors and Setters

- ❌ Java-style encapsulation with getters/setters
- ✅ Use simple factory functions and exported fields

## 4. Looking for Framework Magic

- ❌ Annotation-driven behavior and hidden DI
- ✅ Explicit wiring and library-based design

## 5. Organizing Code by Layers

- ❌ `controllers/`, `services/`, `repositories/`
- ✅ Group code by domain or feature
