<h1 align="center">Hi there 👋, I'm Lama Barhoom</h1>

<p align="center">
  💻 Software Engineer &nbsp;•&nbsp; 🎓 Intelligent Systems & Computer Engineering Student &nbsp;•&nbsp; 🌍 Palestine
</p>

<p align="center">
  <em>Building clean systems — one thoughtful design decision at a time.</em>
</p>

---

## 👩‍💻 About Me

I'm a junior software developer with a strong focus on building **clean, maintainable, and well-structured systems**. I care deeply about code quality, clear domain modeling, and writing software that is easy to understand, test, and evolve.

I enjoy working close to the core business logic — applying principles like **Domain-Driven Design** and **Clean Architecture** — and continuously refactoring code to make it better.

- 🎓 Studying **Intelligent Systems and Computer Engineering**
- 💡 I love transforming complex challenges into simple, elegant solutions
- 🌱 Currently deepening my skills in **Kotlin**, **Java**, **Python**, and **Clean Architecture**
- 🎯 I prefer **fewer projects with better structure** over many unfinished ones

---

## 🛠️ Tech Stack

**Languages**
- Java · Kotlin · Python · HTML · CSS

**Architecture & Concepts**
- Domain-Driven Design (DDD)
- Clean Architecture
- Use Cases & Separation of Concerns
- Result-based error handling

**Frameworks & Libraries**
- Ktor · Koin

**Tools & Platforms**
- Git & GitHub · Gradle · Linux & Bash
- IntelliJ IDEA · VS Code

**Databases & Backend**
- SQLite · Firebase (basic usage)

---

## ⭐ Featured Project

### 📌 Ecosystem Management System — Kotlin / Java

A backend-oriented project built to practice **Domain-Driven Design** through real-world refactoring and use case–driven design. The focus is on domain purity, explicit validation, and clear dependency boundaries.

---

### 🏗️ Architectural Overview

The project follows a **domain-first, use case–driven architecture**, where business rules and validation logic are completely isolated from data access and parsing concerns.

```
src/main/kotlin
│
├─ domain
│   ├─ model
│   │   ├─ entity / value objects
│   │   ├─ request                → Use case input models
│   │   └─ exception              → Business rule violations
│   │
│   ├─ validation
│   │   └─ Result                 → Domain validation result abstraction
│   │
│   ├─ repository
│   │   └─ Interfaces only (contracts)
│   │
│   └─ usecase
│       └─ Application-specific business actions
│
├─ data
│   ├─ datasource
│   │   ├─ DataSource             → Interface to resolve datasource conflicts
│   │   ├─ CsvDataSource          → CSV-based datasource implementation
│   │   └─ ResultExtension        → Data-level Result helpers
│   │
│   ├─ csv
│   │   └─ CsvParser              → Parses raw CSV into *Raw models
│   │
│   ├─ mapper
│   │   ├─ AttendanceMapper
│   │   ├─ MenteeMapper
│   │   ├─ PerformanceSubmissionMapper
│   │   ├─ ProjectMapper
│   │   └─ TeamMapper
│   │
│   ├─ model
│   │   ├─ *Raw models            → Exact representation of CSV data
│   │   └─ exception              → Parsing / IO / format errors
│   │
│   ├─ validation
│   │   ├─ Validator
│   │   ├─ CsvRowStructureValidator
│   │   └─ FileSystemValidator
│   │
│   └─ repository
│       └─ Repository implementations
│
└─ app
    └─ MainKt                     → Application entry point & wiring
```

---

### 🔑 Key Architectural Decisions

**1. Datasource Abstraction Layer**
- `data.datasource` defines a single interface to resolve conflicts between multiple data sources and prevent repositories from depending on concrete parsers
- Enables switching or combining data sources without touching repositories or domain logic

**2. Parsing Is a Data Concern**
- CSV parsing is isolated inside `CsvDataSource` / `CsvParser`
- Raw models (`*Raw`) represent data exactly as read from CSV
- Parsing logic never leaks into domain models, use cases, or repository contracts

**3. Explicit Validation with Result Objects**
- Both `domain` and `data` layers define their own `Result` abstractions
- Validation outcomes are always explicit and predictable

**4. Strict Exception Boundaries**
- `domain.model.exception` → Business rule violations
- `data.model.exception` → Parsing, IO, and format errors
- No cross-layer exception leakage

---

### 🔁 End-to-End Data Flow

```
CSV Files
  ↓ FileSystemValidator
  ↓ CsvParser
  ↓ Raw Models (*Raw)
  ↓ Data Validation (structure & format)
  ↓ Mappers
  ↓ Domain Models
  ↓ Use Case Invocation
  ↓ Request Model (domain.model.request)
  ↓ Domain Model Behavior
  ↓ Domain Validation
  ↓ Domain Result
```

**Error Flow:**
```
Data Errors        → data.model.exception
Domain Violations  → domain.model.exception
       ↓
  Mapped to Result
       ↓
  Handled explicitly by the caller
```

---

### 🎯 What This Project Demonstrates

- ✅ Real understanding of DDD without over-engineering
- ✅ Clean separation between business logic, validation, and data parsing
- ✅ Conscious architectural trade-offs
- ✅ Domain remains completely pure — it never trusts raw data
- ✅ Data layer never applies business rules
- ✅ Every use case represents a clear business intention

---

## 📈 GitHub Activity

I use GitHub to:
- Practice clean architecture patterns
- Experiment with refactoring
- Track my learning progress over time
- Share structured, readable, and intention-revealing code

---

## 🤝 Let's Connect

If you're interested in **clean code**, **thoughtful architecture**, or **learning by doing** — feel free to explore my repositories and reach out!

> *"Good software is not about writing clever code — it's about writing code that others (and future you) can understand."*
