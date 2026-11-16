# Prompt Master

A Claude skill that turns a rough, hastily typed prompt into a clear one, and recommends which model and effort level to use for it.

Type `pm:` before a rough prompt and Claude rewrites it, shows you the rewrite, and answers it. Type `ep:` before a task and Claude recommends a model and effort level without doing the task.

## Commands

| You type | You get |
| --- | --- |
| `pm: <rough prompt>` | A rewritten prompt, then Claude's answer to it |
| `pm only: <rough prompt>` | Only the rewritten prompt, in a copy-ready block |
| `pm pick: <rough prompt>` | The rewrite, then a model and effort recommendation for it (no answer) |
| `ep: <task>` | A model and effort recommendation for the task as you wrote it |
| `pm code:` `pm email:` `pm study:` `pm research:` | A preset that shapes the rewrite for that kind of task. Combine them: `pm only email:`, `pm pick code:` |
| `pm critique: <rough prompt>` | A score out of 10, what's missing, and the one fix to make first (no rewrite) |
| `pm why` | What changed in the last rewrite and why |
| `pm again` / `pm undo` | A fresh rewrite, or an answer to your original draft as typed |
| `pm help` | The command list |

Typing is case-insensitive. If key details are missing (numbers, an attached file, a vague goal), Claude asks up to three quick questions first. `pm only:`, `pm pick:` and `ep:` never ask: they use `[placeholders]` instead.

### Examples

```
pm: help me write a post about my coffee shop's new pumpkin latte
pm email: ask my landlord to fix the heater
pm only code: my python script crashes on startup with KeyError: 'config'
pm pick: plan a database migration for a payments system
ep: rename foo to bar in utils.ts
pm critique: make it better
```

### What the presets add

- **code:** language, your code and the exact error, expected vs actual behavior, constraints, output format, how to tell it works.
- **email:** who it's to, the goal, key points, tone, length, the one action you want, a deadline, subject line plus body.
- **study:** your level, topic and goal, time available, teaching from scratch with simple examples, practice questions, a check of understanding.
- **research:** the exact question, scope and time frame, depth, sources, facts kept separate from guesses, uncertainty stated.

## Install (Claude chat on the web, desktop or mobile)

1. Download [`prompt-master.zip`](prompt-master.zip) from this repository: open the file on GitHub and click the download button. To build it yourself, run `zip -r prompt-master.zip prompt-master` from the repository folder, so that `SKILL.md` sits inside a `prompt-master` folder in the zip.
2. In Claude, open **Settings → Capabilities** and make sure **Code execution and file creation** is on. On Team and Enterprise plans, an admin may need to allow skills first.
3. Under **Skills**, choose **Upload skill** and pick the zip. Make sure its toggle is on.
4. Start a new chat. An existing chat keeps the instructions it already loaded.

For clickable buttons after a `pm:` rewrite, turn on visuals or interactive content in the same settings.

## Good to know

- **Buttons:** after a `pm:` answer you get **Rewrite again**, **Why?** and **Undo** buttons. In some versions a click only fills the message box, so press Enter to send. They send `pm again`, `pm why` and `pm undo`, which you can also type.
- **Recommendations are advice.** Chat can't switch models for you. Pick the model in the selector, and use the extended thinking toggle for medium effort and above.
- **Plan:** `ep:` is tuned for Pro and Max plans. If you say you're on Free, it never recommends Opus. On pay-per-token API, it leans cheaper when the stakes are low.
- **Privacy:** passwords, API keys and card or ID numbers in a draft are replaced with `[redacted]` in the rewrite.
- **Language:** the rewrite uses the same language as your draft.
- **Cost:** the skill's instructions load once per chat that uses it, about 2.5k tokens, plus a short description that is always present.

## Customize

Everything lives in one file, `prompt-master/SKILL.md`. To change which model Claude recommends, edit the table in section 6. To add a preset, add a row to the table in section 3. Re-zip (and replace `prompt-master.zip` here) and upload again after any change.

## License

MIT. See [LICENSE](LICENSE).
