---
description: "Enforce total test coverage through public APIs; optional targeted testing for privates."
alwaysApply: true
---

# PUTT PUTT Rule

**Publics Under Thorough Testing, Privates Under Targeted Testing**

## Core invariants

### 1. **Publics Under Thorough Testing**

* **Requirement:** 100% line, branch, and error-path coverage
* **Mechanism:** **Global tests only**
* **Access constraint:** Tests may invoke **only public APIs**
* **Implication:**
  All private code **must be exercised implicitly** through public execution paths.
* **Invariant:** If a private path cannot be reached through public APIs, the design is suspect.

---

### 2. **Privates Under Targeted Testing**

* **Permission, not requirement:** Targeted tests **may** exist for private code
* **Scope:** **Local tests only** (same module or package)
* **Purpose constraint:**

  * Regression localization
  * Fast failure isolation
  * Algorithmic edge cases that are slow or opaque to reach via public flows
* **Non-authoritative:**
  Private tests **do not count** toward global coverage requirements.
* **Invariant:**
  Targeted tests assist diagnosis; they do **not** justify uncovered public paths.

---

## Coverage dominance rule

| Code path           | Must be covered by               | May also be covered by        |
| ------------------- | -------------------------------- | ----------------------------- |
| Public code         | Global tests via public APIs     | Local tests                   |
| Private code        | **Global tests via public APIs** | Local targeted tests          |
| Branch / error path | Global tests                     | Local tests (diagnostic only) |

**Key rule:**

> If a private path is only covered by local tests and not by global public execution, the PUTT PUTT rule is violated.

---

## DesignToTest guidance (merged)

Design interfaces so correctness can be tested quickly, locally, and with minimal setup.

- Every non-trivial behavior should be reachable through a small, explicit interface.
- Avoid monolithic functions or classes that require heavy environment setup to test.
- Extract "engine/kernel" logic into deterministic units with clear inputs and outputs.
- It is acceptable to make core operations public or protected to enable direct, high-signal tests.
- Refactor toward these properties before adding brittle, high-setup tests.

---

## Anti-patterns (explicitly forbidden)

* ❌ Using private tests to justify missing public coverage
* ❌ Treating private helpers as stable APIs
* ❌ Designing private code paths unreachable from any public API
* ❌ Global tests importing or mocking private symbols

---

## Final one-line definition

> **PUTT PUTT:** All code is thoroughly covered through public APIs; private code may additionally receive targeted local tests for diagnostic precision, but never as a substitute for public execution coverage.
