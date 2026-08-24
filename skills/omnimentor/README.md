# OmniMentor — Packaged for Claude Code + ChatGPT

OmniMentor is a practical-first learning coach: it makes you *do* the thing you're learning (practice before theory, hints before answers, a next step every time), across Programming / DSA / System Design / Theory / General-skill modes, with adaptive study timelines and 18 slash-commands.

This package ships **one shared behavior core** in **two installable forms**, so it runs natively in either tool instead of being pasted each time.

## What "standalone app" means here (honest framing)

OmniMentor is an *instructions* artifact, not compiled software — nothing executes "inside" the model. What you get is the next best thing: OmniMentor installed as a **first-class skill** (Claude Code) and a **named Custom GPT** (ChatGPT), invoked by name, no paste-in.

## Files

| File | Purpose |
|---|---|
| `OmniMentor-core.md` | **Source of truth.** The full, host-agnostic behavior spec. Everything else derives from this. |
| `omnimentor/SKILL.md` | The Claude Code skill (frontmatter trigger + full core). Already saved to your account — this copy is for versioning. |
| `OmniMentor-ChatGPT-instructions.txt` | Paste-ready compact brief for the ChatGPT GPT **Instructions** box (6,956 chars — fits the 8k cap). |
| `OmniMentor-ChatGPT-setup.md` | Step-by-step ChatGPT build guide (fields, capabilities, fallbacks). |
| `README.md` | This file. |

## Install — Claude Code

**Already done:** the skill is saved to your account as `omnimentor`, available in every conversation now. Invoke it with `/omnimentor`, or just start a learning request or an OmniMentor command (`/learn rust`, `/dsa two pointers`, `/timeline devops 3 months`) and it triggers.

- To **version it** or put it in a specific project, drop the `omnimentor/` folder into that project's `.claude/skills/`.
- To **change or remove it**, re-save from `OmniMentor-core.md` (overwrite) or delete the saved skill.
- Note: OmniMentor's `/learn`, `/dsa`, etc. are conventions the skill interprets — they won't appear in the `/` autocomplete menu (only `/omnimentor` does). Type them anyway; they work.

## Install — ChatGPT

See `OmniMentor-ChatGPT-setup.md`. Short version: create a Custom GPT, paste Name + Description + the compact brief into **Configure**, upload `OmniMentor-core.md` as a **Knowledge** file, turn **Code Interpreter ON**. Fallbacks (Projects, or first-message paste) are covered there for accounts without GPT-builder access.

## The shared-core model (how to keep both in sync)

`OmniMentor-core.md` is the only place you edit behavior. After a change:

1. **Always** — re-save the Claude skill from the core (overwrite), **and** re-upload the core as the GPT's knowledge file.
2. **If you changed an always-on rule, a mode, or a command** — also update `OmniMentor-ChatGPT-instructions.txt` and re-paste it into the GPT's Instructions box.
3. **Detail-only changes** (resolution order, carve-outs) — knowledge re-upload is enough; the compact brief points to the file for those.

This asymmetry exists only because ChatGPT caps the Instructions field at ~8k chars while a Claude skill has no such limit — so the skill carries the full core inline, and the GPT splits it into brief + knowledge.

## Known ceilings (true of any prompt-based coach)

- **No memory across chats** on its own. OmniMentor handles this by treating any recap you give as a hypothesis and verifying it with a quick diagnostic before trusting your stated level.
- **Code correctness isn't guaranteed by inspection.** Where the host can run code (ChatGPT Code Interpreter, or a Claude Code session with file access), OmniMentor prefers running your code over eyeballing it — turn that on for real verification.

## Quick smoke test (either tool)

- `/dsa two sum` → should ask a guiding question, not reveal "use a hash map."
- `/timeline python 2 months` → should return the 5-part plan with the exact phase-table columns.
- `what's the syntax for a python list comprehension?` → should answer directly and stop (transactional escape hatch), no quiz tacked on.
