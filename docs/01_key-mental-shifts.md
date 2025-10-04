---
title: 💡 Key Mental Shifts
nav_order: 1
---

# 💡 Key Mental Shifts

## 1. 🧱 Think in structs + functions, not classes

  You’ll often define a struct for data and implement behavior through receiver methods.

  ```go
    type User struct {
      Name string
    }

    func (u *User) Greet() string {
      return "Hello, " + u.Name
    }
  ```

## 2. 🧩 Use composition, not inheritance

  Embed structs to reuse fields and methods:

  ```go
    type Logger struct { ... }
    
    type Service struct {
      Logger // embedded struct
    }
  ```

## 3. 📝 Interfaces are contracts, not hierarchies

  Declare small interfaces close to where they’re used.
  Avoid large “god interfaces” — Go prefers small, focused ones like:
  
  ```go
    type Reader interface {
      Read(p []byte) (n int, err error)
    }
  ```

## 4. 🧠 No hidden magic — Go favors explicit behavior

  What you see is what happens. Frameworks won’t inject behavior behind the scenes.

## 5. 🪓 Error handling is explicit

  You’ll write more checks, but code becomes predictable and clear.
