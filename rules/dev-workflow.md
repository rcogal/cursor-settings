# Core Principles

Research before action. Map system end-to-end before changes.
Trust code over docs. Verify against actual implementation.
Execute autonomously after research. Default to action.
Complete full task chains. No partial work or orphaned changes.
Use absolute paths. Eliminate directory ambiguity.

# Before Implementation

Ask these questions and wait for answers:
1. "Do you want unit tests for this change?" → Yes/No
2. "Any specific patterns or constraints to follow?" → Free response

Proceed only after receiving answers.

# Research Phase

Before any code change:
1. Use Context7 to fetch current documentation for unfamiliar libraries
2. Read relevant source files, not just docs
3. Search for existing patterns and similar implementations
4. Trace dependencies and potential side effects
5. Identify test coverage and CI requirements

# Context7 Usage

When working with external libraries or frameworks:
- Call `resolve-library-id` first to get the correct library ID
- Then call `get-library-docs` with relevant topic to fetch current docs
- Prioritize libraries with higher trust scores (7-10)
- Always verify API signatures against fetched docs before implementing
- Re-fetch docs when encountering unexpected behavior or errors

Example workflow:
1. User asks to implement feature with library X
2. resolve-library-id("X") → get library ID
3. get-library-docs(libraryID, topic="relevant-feature") → current API docs
4. Implement using verified, up-to-date patterns

# Testing Standards

**If user wants tests (yes):**
- Follow TDD: write failing test first, then implement
- Test file location: `[filename].test.[ext]` next to source
- Cover: happy path, edge cases, error handling
- Minimum: one test per public function/method

**If user declines tests (no):**
- Proceed without tests
- Add comment: `// TODO: Add test coverage for [function]`
- List untested functions at end of response

# Code Comments

Write comments only when necessary:
- Complex algorithms or non-obvious logic
- Workarounds or hacks (explain why)
- Public API functions (brief purpose)
- Regex patterns (explain what it matches)

Do NOT comment:
- Self-explanatory code
- Simple getters/setters
- Obvious variable names

Prefer clear code over comments. Refactor unclear code instead of explaining it.

# Implementation Standards

- Match existing code style and patterns in the codebase
- Handle errors explicitly, never silently fail
- Preserve backward compatibility unless explicitly breaking
- Use documented API patterns from Context7, not outdated training data

# Verification Checklist

Before considering work complete:
- [ ] Runs without errors end-to-end
- [ ] Tests pass (if tests were requested)
- [ ] Edge cases handled (null, empty, boundary values)
- [ ] No debug code, temp files, or console.logs left behind
- [ ] Changes scoped to task (no unrelated modifications)
- [ ] Library usage matches current documentation

# Communication

Concise, technical responses. No filler.
State assumptions explicitly before acting.
Report blockers immediately, don't guess.
