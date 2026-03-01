---
name: codex-todo-hub-observer
description: Use when the user wants to rebuild, score, or skill-ify an Obsidian TODO by grounding it in codexhub and nearby project artifacts. Use for requests like "TODOを再構築", "情報源付きでTODO化", "codexhub基準で整理", or when "同様に" means append under the same user TODO note instead of creating a separate note.
---

# Codex TODO Hub Observer

## Overview

Rebuild the user's active Obsidian TODO in place, using `codexhub` as the location anchor and current local artifacts as evidence.  
The output is a source-scored Codex TODO, not a generic task list.

## Fixed Anchor

Start from this path:

```text
/home/claw/Desktop/codexhub
```

Treat `codexhub` only as:

- the Codex-shaped mirror of `Desktop/hub`
- a low-noise bootstrap layer for path discovery
- a hint, not final runtime truth

Do not describe it beyond that unless the user explicitly asks.

## Workflow

1. Open the user's current TODO note first and assume edits happen in that same note unless the user explicitly asks for a separate note.
2. Normalize the meaning of "同様に" early:
- default meaning is "append under the current TODO"
- do not create sibling notes unless clearly requested
3. Before blaming sync, push, or JJ, check for path mismatch first.
- If the missing TODO already points at another path, treat that as the primary cause.
- In this workflow, path confusion is more likely than a missing push.
4. Re-anchor with `codexhub`.
- Read `README.md` first.
- Read `openclaw/paths.json` when path resolution matters.
- Read `openclaw/config.json` or `openclaw/skills.json` only if they change task selection.
5. Gather only the artifacts that materially affect the TODO.
- Current Obsidian note(s)
- Today-created or today-modified vault notes tied to the incident or task
- Relevant `.openclaw/workspace` files
- Relevant `Desktop/codexhub` files
- Relevant project READMEs or generated queues when they directly affect prioritization
6. Rebuild the TODO in place.
- Keep the user's original task block
- Add Codex-owned sections under it
- Prefer Obsidian links for vault notes: `[[...]]`
- Use file links only for paths outside the vault
7. Convert the result into an evidence-driven list.
- Add checkboxes
- Group by severity when the list is large: `Sev1`, `Sev2`, `Sev3`
- For each Codex task, attach `情報源`
- For each Codex task, attach `有意性スコア`
8. Score significance by evidence density, not by vibes.
- `5`: multiple sources plus a live path
- `4`: multiple sources
- `3`: one primary source plus one support source
- `2`: one direct note only
- `1`: weak clue or inferred lead
9. Add a coverage block when the user wants "網羅".
- List the generated notes, queues, and external structures that were observed
- Treat that list as the scoring population for the current pass
10. Remove low-value "discoveries" from the final wording.
- If a clarification became obvious during the turn, bake it into the procedure
- Do not narrate the obvious correction as a fresh insight
- The goal is less semantic fog from the first read

## Built-In Assumptions

Apply these from the start in this workflow:

- The user cares about practical leverage, not a neutral summary
- `codexhub` is for orientation, not runtime truth
- A TODO that "disappeared" is often at a different path, not necessarily unsynced
- If the user is comparing Lyra and Anya tasks, the real target may be Codex's observation plan
- When a TODO is for observing agents, parallel task blocks are useful

## Output Shape

Use this shape unless the user asks for a different structure:

```markdown
# <user TODO title>

## 優先TODO
### Sev1
- [ ] ...

## Codex TODO: <scope>
目的: ...
ゴール: ...
有意性スコア: ...

### Sev1
- [ ] `有意性スコア: 5/5` ...
  情報源: [[...]], [external](file:///...)

## 観測できた生成物
- [ ] [[...]]
- [ ] [external](file:///...)

## 情報源
- [[...]]
- [external](file:///...)
```

## Guardrails

- Do not split work into multiple notes unless explicitly requested.
- Do not treat `jj git push` as the explanation for a missing TODO until path mismatch is ruled out.
- Do not over-explain `hub` or `codexhub`; only preserve the part that changes action.
- Do not keep "I noticed later" style narration in the final skill output.
- Prefer the user's active note as the durable surface for the reconstructed TODO.
