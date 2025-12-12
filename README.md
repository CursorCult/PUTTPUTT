# PUTTPUTT

The PUTT PUTT Rule: **PUBLICS UNDER TOTAL TESTING**.

**Install**

```sh
pipx install cursorcult
cursorcult link PUTTPUTT
```

Rule file format reference: https://cursor.com/docs/context/rules#rulemd-file-format

**When to use**

- You want high confidence in all exposed APIs.
- You ship libraries or stable internal interfaces relied on by others.
- You’re tightening quality gates in a mature or safety‑critical codebase.

**What it enforces**

- The entire codebase reaches 100% test coverage.
- Tests only call public entities; private/internal code is exercised indirectly.
- Public surfaces are treated as non‑negotiable quality boundaries.

**Credits**

- Developed by Will Wieselquist. Anyone can use it.
