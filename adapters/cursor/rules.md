# ABCD × DBNT × KISS — Cursor Rules

Add to `.cursorrules` in your project root, or paste METHOD.md content into your Cursor system prompt.

## Quick setup

```bash
git clone https://github.com/idirectships/ABCDxDBNTxKISS
cat ABCDxDBNTxKISS/METHOD.md >> .cursorrules
```

Or reference the method file directly in your `.cursorrules`:

```
# ABCD × DBNT × KISS improvement loop
# Full method: https://github.com/idirectships/ABCDxDBNTxKISS/blob/main/METHOD.md
[paste contents of METHOD.md here]
```

## Trigger phrases

In any Cursor AI session:
- `above and beyond` — checks adjacent work before handoff
- `do better next time` — encodes a lesson to a durable file
- `keep it simple` — surveys what exists before building

## Config

```yaml
# .cursor/abcd-dbnt-kiss.yaml
artifact_root: .dbnt/rules
capture_scope: project
```
