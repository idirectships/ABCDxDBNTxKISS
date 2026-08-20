# ABCD × DBNT × KISS

**Three habits for AI agents.** Bounded initiative, compounding lessons, and a bias against building what already exists.

---

## The three habits

**ABCD — Above & Beyond the Call of Duty.** When a task is done, the agent asks: what breaks next if I stop here? If one small, in-scope step prevents downstream rework — take it. If the extra step needs new scope or a judgment call — ask, don't invent.

**DBNT — Do Better Next Time.** Every notable success or failure gets encoded as a small, durable rule artifact — a file the next session actually loads, not a memory the next session doesn't have.

**KISS — Keep It Simple.** Before standing up any new store, service, or capability, the agent proves the need: search what already exists, by *function* — what the thing does, not what it's called. Extending an existing path costs one change. A parallel new system must pay for its own plumbing and drifts from day one.

These aren't checklist steps run at the end. They're how the agent shows up in every piece of work.

---

## Install

Choose your harness:

### Claude Code

```bash
git clone https://github.com/idirectships/ABCDxDBNTxKISS
cp -r ABCDxDBNTxKISS/skills/abcd-dbnt-kiss ~/.claude/skills/
```

Claude Code picks up the skill on the next session start. The first run asks up to 4 questions to fit your setup — or skip and use defaults.

### Codex

See [`adapters/codex/AGENTS.md`](adapters/codex/AGENTS.md).

```bash
git clone https://github.com/idirectships/ABCDxDBNTxKISS
cat ABCDxDBNTxKISS/METHOD.md >> your-project/AGENTS.md
```

### Cursor

See [`adapters/cursor/rules.md`](adapters/cursor/rules.md).

```bash
git clone https://github.com/idirectships/ABCDxDBNTxKISS
cat ABCDxDBNTxKISS/METHOD.md >> .cursorrules
```

### Any other harness

See [`adapters/generic/HOWTO.md`](adapters/generic/HOWTO.md).

Load `METHOD.md` into your harness's system prompt or instruction file. The method is plain markdown — it works anywhere an agent can read instructions.

---

**Verify** — ask your agent:

```
did we live abcd
```

The agent should describe the three-habit loop and ask what you want to improve.

---

## Using it

Any natural-language improvement phrase triggers the full loop:

- `"above and beyond"` or `"did we live abcd"` — disposition check
- `"do better next time"` or `"capture this lesson"` — encode what happened
- `"compound our learnings"` or `"what keeps recurring"` — cross-session synthesis
- `"keep it simple"` or `"should I build this"` or `"does this already exist"` — survey before building

The skill reads context and selects its own mode. You never pick a command.

---

## Beta notes

This skill was extracted from a production multi-agent system and adapted for standalone use. Some vocabulary — "capture," "lanes," "receipts" — still reflects that origin.

**What we want to know:**

- Does it act when it should, and ask when it should?
- After a correction, does a usable rule file appear — and does the *next* session actually behave differently?
- Ask for a capability that overlaps something existing. Does the agent find the existing thing first?

**Report friction verbatim.** The exact prompt, the exact behavior, what you expected instead. Rough edges are the point of a beta.

Feedback goes back through the person who shared this with you, or open a GitHub issue here.

---

## License

MIT — Copyright (c) 2026 GUSystems
