# ABCD × DBNT × KISS

This directory configures the ABCD × DBNT × KISS improvement loop for Codex.

## Setup

The full method is in [METHOD.md](../../METHOD.md) at the repo root.

Add this to your Codex session's AGENTS.md (or paste the METHOD.md content directly):

```
@../../METHOD.md
```

Or copy METHOD.md into your project root:

```bash
git clone https://github.com/idirectships/ABCDxDBNTxKISS
cp ABCDxDBNTxKISS/METHOD.md your-project/AGENTS.md
# or append to existing AGENTS.md:
cat ABCDxDBNTxKISS/METHOD.md >> your-project/AGENTS.md
```

## Trigger phrases

Any of these in a Codex session activates the loop:
- `above and beyond` / `did we live abcd`
- `do better next time` / `capture this lesson`
- `keep it simple` / `should I build this`

## Config

The config file lives at `<your-project>/.dbnt/abcd-dbnt-kiss/config.yaml`:

```yaml
artifact_root: .dbnt/rules
capture_scope: project
team_vocabulary: []
knowledge_source: null
```
