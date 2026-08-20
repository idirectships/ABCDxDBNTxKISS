# ABCD × DBNT × KISS — Generic Setup

Works with any AI agent harness that accepts a system prompt or instruction file.

## Setup

1. Copy [METHOD.md](../../METHOD.md) to wherever your harness loads instructions:
   - System prompt: paste the content of METHOD.md
   - Instruction file: copy METHOD.md and reference it at session start
   - AGENTS.md / rules / context: append METHOD.md content

2. Your harness needs file-read and file-write access to save lesson artifacts.

## Trigger phrases

Any of these activates the loop:
- `above and beyond` — bounded adjacent scan
- `do better next time` / `capture this lesson` — lesson encoding
- `compound our learnings` — cross-session synthesis
- `keep it simple` / `should I build this` — survey before building

## Config

The loop writes lesson artifacts to a local `rules/` directory. Configure the path:

```yaml
artifact_root: .dbnt/rules     # where lesson files are written
capture_scope: project         # project or global
```

Create this as `<your-skill-dir>/abcd-dbnt-kiss/config.yaml` or equivalent for your harness.

## Verify

After loading the method, ask:
> "What is the ABCD × DBNT × KISS loop and how does it work?"

The agent should describe all three habits and the ordered workflow.
