# Cursor Settings

My personal Cursor AI rules and commands.

## Folder Structure

- `rules/` — AI behavior rules (dev workflow, testing, etc.)
- `commands/` — Custom slash commands (WIP)

## Setup

Copy the contents of rule files into:

**Cursor Settings → General → Rules for AI → User Rules**

That's it.

## Watch Your Tokens

Rules get sent with every request, so they eat into your context window. Keep them tight:

- `dev-workflow.md` runs about 600 tokens
- Try to stay under 2000 tokens total for all rules combined
- Cut examples and verbose explanations when possible

## Don't Repeat Yourself

If you add more rule files later, don't duplicate what's already in `dev-workflow.md`:

- Testing workflow → already covered
- Code comments → already covered  
- Research/Context7 usage → already covered
- Communication style → already covered

Check existing rules before adding new ones. One file per concern.
