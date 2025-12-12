---
description: "Enforce total test coverage through public-only tests"
alwaysApply: true
---

# PUTT PUTT Rule (PUBLICS UNDER TOTAL TESTING)

The PUTT PUTT Rule mandates that the entire codebase achieves **100% test coverage**. However, tests may only use public functions, classes, or modules.

If it’s exposed, it’s fully exercised—no exceptions, no partial paths, no uncovered lines.

We say PUTT PUTT twice because the requirement is non‑negotiable: total coverage, through public APIs, every time.

## Notes

- This rule is language agnostic.
- “Public” means any API surface that consumers can call/import/use outside its defining module or package.
- Coverage must include all branches and error paths across the whole codebase.
- Tests should not reference private/internal code directly or use it outside its enclosing unit. Internal paths are covered indirectly through tests of the public surface.
