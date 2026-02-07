---
title: Migration Checklist — Java (OOP) → Go
nav_order: 4
---

# Migration Checklist — Java (OOP) → Go

This page is a **quick reference guide** for developers migrating from Java-style OOP to Go.

It does **not introduce new concepts**.  
It consolidates the key principles, idioms, and design decisions discussed in previous sections.

Use it as a **daily pocket guide**, onboarding checklist, or PR review reference.

## Design & Architecture

- ☐ Prefer **composition** over inheritance  
- ☐ Avoid deep hierarchies and “God objects”  
- ☐ Keep structs small and responsibility-focused  
- ☐ Design for **clarity**, not extensibility by default  
- ☐ Keep packages cohesive and dependency direction clear  

## Structs & Interfaces

- ☐ Use `struct` for data, not as a “class” replacement  
- ☐ Add methods only when behavior belongs to the data  
- ☐ Define **interfaces at the consumer side**  
- ☐ Keep interfaces small (often 1 method)  
- ☐ Avoid getters/setters unless logic is required  
- ☐ Use factory functions (`NewX`) instead of constructors  

## Mindset & Philosophy

- ☐ Favor **explicit code** over magic or automation  
- ☐ Avoid speculative abstractions  
- ☐ Prefer functions over object graphs  
- ☐ Let the compiler enforce correctness  
- ☐ Read standard library code for idioms  

## Memory & Pointers

- ☐ Use pointers only when mutation is required  
- ☐ Avoid pointer-by-default habits  
- ☐ Use values for small, immutable data  
- ☐ Remember: slices and maps are reference types  

## Error Handling

- ☐ Treat errors as part of control flow  
- ☐ Handle errors immediately (`if err != nil`)  
- ☐ Wrap errors with context (`%w`)  
- ☐ Avoid panic except for truly unrecoverable states  

## Testing & Mocking

- ☐ Prefer simple tests over heavy frameworks  
- ☐ Use interfaces for mocking **only when needed**  
- ☐ Favor integration tests over excessive mocking  
- ☐ Keep tests readable and explicit  

## Concurrency

- ☐ Use goroutines for concurrent execution  
- ☐ Communicate via channels when possible  
- ☐ Prefer message passing over shared state  
- ☐ Use `context.Context` for cancellation and timeouts  
- ☐ Avoid overusing mutexes  

## Project Organization

- ☐ Keep `main.go` small and explicit  
- ☐ Use `cmd/` for entry points  
- ☐ Use `internal/` for private code  
- ☐ Use `pkg/` only for reusable libraries  
- ☐ Organize code by **domain**, not technical layer  

## Final Sanity Check

If your Go code feels:

- heavily layered  
- overly abstract  
- framework-driven  

You are likely **writing Java-style OOP in Go**.
