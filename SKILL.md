---
name: coding-efficiency
description: Disciplined, minimal-diff coding workflow. Use for any task that writes, edits, refactors, fixes, builds, or creates code, including small changes, scripts, and functions. Keeps changes small, verified, and consistent with the existing codebase.
---

# Coding Efficiency

Make the smallest correct change, verify it, and follow the codebase's existing style.

## Before writing code

1. **Restate the task in one line.** Make the requested outcome concrete. If a design-changing ambiguity prevents a clear restatement, ask one focused question rather than guessing.
2. **Inspect the codebase.** Find a similar feature, helper, test, or convention. Follow its naming, structure, imports, formatting, and error-handling patterns.
3. **Reuse before creating.** Search for an existing utility or dependency that already solves the need. Do not add a dependency for functionality that can be implemented in about ten clear lines.
4. **Set the smallest scope.** Identify the files that need to change. If the necessary scope is broad, explain why and propose a plan before editing. Do not expand scope for unrelated cleanup.

## While writing

- Make the smallest diff that fully solves the request. Avoid drive-by refactors, renames, and reformatting of untouched code.
- Match the repository's style, even when another style would be your preference. Prefer readable, conventional code over cleverness.
- Handle real failure cases relevant to the change, such as null values, empty input, network errors, or permission failures. Do not add speculative complexity for imaginary cases.
- Do not invent APIs, methods, flags, or symbols. If their existence is uncertain, verify them in source, project documentation, or installed tooling before use.
- Do not leave TODOs, placeholder stubs, or commented-out code. Complete the work or explicitly explain what remains blocked.

## After writing

1. Run the most relevant available verification: targeted tests first, then the appropriate build, full tests, or linter when practical. Do not claim checks passed unless they ran successfully.
2. Re-read the diff as a reviewer. Check for unused imports, debug output, off-by-one errors, accidental unrelated edits, and missed call sites.
3. If a signature or behavior changed, search for all callers and update or verify them.
4. If no verification could be run, state plainly that the change is **not verified** and why.

## Escalate instead of guessing

Pause and ask or propose a plan when requirements conflict, an ambiguity changes the design, the work requires a destructive or irreversible action (such as deleting data, force-pushing, or a migration), or the only apparent solution touches many unrelated files. Do not perform destructive actions without explicit authorization.

## Report

End with 2–4 concise lines covering:

- What changed and where.
- How it was verified (or that it was not verified).
- Anything the user should double-check or any remaining blocker.

Do not re-paste unchanged code.