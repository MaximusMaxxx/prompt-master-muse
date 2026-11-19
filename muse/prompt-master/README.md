# Prompt Master — Muse edition

Turn a rough prompt into a clear one, and get a difficulty and approach note for the task. Ported from the ChatGPT edition in this repo; the rewriting, presets, and commands are the same, with one difference that matters.

## The one difference: no model picker

Muse has no model or effort selector. The free tier runs Muse Spark and the paid tier runs Muse Wonder, and there is no setting to change that. So this edition never recommends a model. The `ep:` and `pm pick:` commands give a difficulty and approach note instead (direct, straightforward, routine, careful, deliberate, high-stakes), scored the same way as the other editions. The saving comes from a clearer prompt with less rework, not from picking a cheaper model.

## Commands

| You type | You get |
| --- | --- |
| `pm: <rough prompt>` | A rewritten prompt, then the answer to it |
| `pm only: <rough prompt>` | Only the rewritten prompt, in a copy-ready block |
| `pm pick: <rough prompt>` | The rewrite, then a difficulty and approach note (no answer) |
| `ep: <task>` | A difficulty and approach note for the task as you wrote it |
| `pm code:` `pm email:` `pm study:` `pm research:` | A preset that shapes the rewrite for that kind of task. Combine them: `pm only email:`, `pm pick code:` |
| `pm critique: <rough prompt>` | A score out of 10, what's missing, and the one fix to make first (no rewrite) |
| `pm why` | What changed in the last rewrite and why |
| `pm again` / `pm undo` | A fresh rewrite, or an answer to your original draft as typed |
| **`pm help`** | **The full command list with examples. Use it whenever you forget a command.** |

Typing is case-insensitive. If key details are missing, it asks up to three quick questions first, and **go** accepts its suggestions. `pm only:`, `pm pick:` and `ep:` never ask: they use `[placeholders]` instead.

Follow-ups are plain-text commands, for example `Reply pm again, pm why or pm undo.` Muse has no native action buttons for skills.

## Install

This is a Muse skill. Add the `muse/prompt-master` folder as a skill in Muse, following Muse's skill setup for this workspace. There is no zip and no agent config file; the `SKILL.md` in this folder is the whole skill.

## Files

| Path | What it holds |
| --- | --- |
| `SKILL.md` | The Muse skill: commands, rewriting rules, presets, difficulty and approach note, follow-ups. |
| `README.md` | This file. |

The ChatGPT edition this was ported from is at `../chatgpt/prompt-master/SKILL.md`. The Claude edition is at `../claude/plugin/skills/prompt-master/SKILL.md`.

## Credits

Original Prompt Master by Nishkarsh Shah (MIT). Muse edition ported by MaximusMaxxx in a fork, at the author's invitation: the ChatGPT edition as the starting point, separate folder, MIT licensed.

## License

MIT. See `../../LICENSE`.
