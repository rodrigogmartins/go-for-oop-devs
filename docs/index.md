---
title: 🧠 Go for OOP Developers
nav_order: 0
---

# 🧠 Go for OOP Developers

A quick guide for developers transitioning from Object-Oriented languages (like Java, C#, or C++) to Go.

If you come from an Object-Oriented Programming (OOP) background, Go might initially feel minimalistic or even “too simple”.
You may look for familiar constructs like classes, inheritance, annotations, generics, or frameworks, and not find them the same way.

But Go is designed with clarity, simplicity, and explicitness in mind — trading some abstraction for ease of reasoning, concurrency, and performance.

This guide highlights the main paradigm shifts you’ll encounter and provides pro-tips for writing idiomatic Go code.

## 🔄 OOP vs Go: Conceptual Shifts

### Classes

**Java (OOP)**  

- Blueprint that encapsulates data + behavior
- Example:

```java
  class Person {
    private String name;
    public Person(String name) { this.name = name; }
    public String getName() { return name; }
  }
```

**Go (Golang)**  

- No classes. Use `struct` to model data and functions with receivers to attach behavior
- Example:

```go
  type Person struct {
    Name string
  }

  func (p *Person) GetName() string {
    return p.Name
  } 
```

---

### Inheritance

**Java (OOP)**  

- Core mechanism for reuse and polymorphism
- Example:

```java
  class Employee extends Person {
    private String role;
  }
```

**Go (Golang)**  

- No inheritance. Use composition and interfaces instead
- Example:

```go
type Employee struct {
  Person
  Role string
}
```

---

### Interfaces

**Java (OOP)**  

- Declared explicitly with implements
- Example:

```java
  interface Speaker {
    void speak();
  }

  class Person implements Speaker {
    public void speak() { System.out.println("Hello!"); }
  }
```

**Go (Golang)**  

- Implicit implementation: any type that has the required methods satisfies the interface
- Example:

```go
  type Speaker interface {
    Speak()
  }

  type Person struct {}

  func (p Person) Speak() {
    fmt.Println("Hello!")
  }
```

---

### Access Modifiers

**Java (OOP)**  

- public, private, protected keywords

**Go (Golang)**  

- Simplicity: Capitalized = exported (public), lowercase = unexported (private)
- Example:

```go
  type Person struct {
    Name string  // exported
    age  int     // unexported
  }
```

---

### Constructors

**Java (OOP)**  

- Defined by the name of the class
- Example:

```java
  class Person {
    private String name;

    public Person(String name) {
      this.name = name;
    }
  }
```

**Go (Golang)**  

- Use factory functions to initialize structs
- Example:

```go
  type Person struct {
    Name string
  }

  func NewPerson(name string) *Person {
    return &Person{Name: name}
  }
```

---

### Annotations / Reflection

**Java (OOP)**  

- Commonly used for frameworks (e.g., `@Autowired`, `@Entity`)
- Example:

```java
  @Entity
  class Person {
    @Id
    private int id;
  }
```

**Go (Golang)**  

- Rarely used; prefer explicit configuration
- Example:

```go
  type Person struct {
    ID int `json:"id"` // struct tags for JSON or DB mapping
  }
```

---

### Exceptions

**Java (OOP)**  

- Error handling via `try/catch`
- Example:

```java
  try {
    int result = divide(10, 0);
  } catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero");
  }
```

**Go (Golang)**  

- No exceptions; handle errors via explicit return values
- Example:

```go
  func divide(a, b int) (int, error) {
    if b == 0 {
      return 0, fmt.Errorf("cannot divide by zero")
    }
    return a / b, nil
  }

  result, err := divide(10, 0)
  if err != nil {
    fmt.Println(err)
  }
```

---

### Framework-driven

**Java (OOP)**  

- Heavy reliance on frameworks (Spring, Hibernate, etc.)

**Go (Golang)**  

- Prefers libraries + composition, not frameworks
- Example:

```go
  // No heavy frameworks, just libraries for routing and DB
  r := gin.Default()
  r.GET("/users", getUsersHandler)
```

---

### Generics

**Java (OOP)**  

- Widely used with collections (`List<T>`, `Map<K,V>`)
- Example:

```java
  List<String> names = new ArrayList<>();
```

**Go (Golang)**  

- Supported since 1.18; encourages simple concrete types when possible
- Example:

```go
  func MapSlice[T any](items []T, fn func(T) T) []T {
    var result []T
    for _, item := range items {
      result = append(result, fn(item))
    }
    return result
  }
```

---

### Dependency Injection

**Java (OOP)**  

- Automated by frameworks (Spring DI)

**Go (Golang)**  

- Manual DI via constructors or function parameters
- Example:

```go
  type Service struct {
    Repo Repository
  }

  func NewService(repo Repository) *Service {
    return &Service{Repo: repo}
  }
```

---

### Multithreading / Concurrency

**Java (OOP)**  

- Threads, executors, futures, Virtual Threads
- Example:

```java
  ExecutorService executor = Executors.newFixedThreadPool(2);
  executor.submit(() -> System.out.println("Running in parallel"));
```

**Go (Golang)**  

- Lightweight goroutines and channels for concurrency
- Example:

```go
  go func() {
    fmt.Println("Running in parallel")
  }()
```