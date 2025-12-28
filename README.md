# Part of the [CursorCult](https://github.com/CursorCult)

# PUTTPUTT

**Publics Under Thorough Testing, Privates Under Targeted Testing**

**Install**

```sh
pipx install cursorcult
cursorcult link PUTTPUTT
```

Rule file format reference: https://cursor.com/docs/context/rules#rulemd-file-format

**When to use**

- You want ironclad confidence in your public API contract.
- You need to refactor internals safely without rewriting brittle tests.
- You want the speed of unit tests for debugging, but the realism of integration tests for coverage.

**What it enforces**

- **Publics Under Thorough Testing**: 100% coverage must be achieved solely through public APIs using global tests. Private code is exercised implicitly.
- **Privates Under Targeted Testing**: You *may* write targeted local tests for private logic (for speed/debugging), but they do **not** count toward the 100% coverage goal.
- **Strict Dominance**: If a private path is covered *only* by local tests and not by public execution, the code is considered uncovered/broken.

**Credits**

- Developed by Will Wieselquist. Anyone can use it.
