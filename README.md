# Prompt Master

A skill that turns a rough, hastily typed prompt into a clear one, and recommends which model and effort level to use for it. It comes in two editions with the same commands: one for Claude, one for ChatGPT and Codex. Download the one you use, or both.

| Edition | For | Download | Folder |
| --- | --- | --- | --- |
| Claude | Claude chat on the web, desktop and mobile | [`prompt-master-claude.zip`](claude/prompt-master-claude.zip) | [`claude/`](claude) |
| ChatGPT | ChatGPT, ChatGPT Work and Codex | [`prompt-master-chatgpt.zip`](chatgpt/prompt-master-chatgpt.zip) | [`chatgpt/`](chatgpt) |

Type `pm:` before a rough prompt and the skill rewrites it, shows you the rewrite, and answers it. Type `ep:` before a task and it recommends a model and effort level without doing the task.

## Commands

| You type | You get |
| --- | --- |
| `pm: <rough prompt>` | A rewritten prompt, then the answer to it |
| `pm only: <rough prompt>` | Only the rewritten prompt, in a copy-ready block |
| `pm pick: <rough prompt>` | The rewrite, then a model and effort recommendation for it (no answer) |
| `ep: <task>` | A model and effort recommendation for the task as you wrote it |
| `ep codex: <task>` | ChatGPT edition only: the same, plus a short Codex plan and subagent advice |
| `pm code:` `pm email:` `pm study:` `pm research:` | A preset that shapes the rewrite for that kind of task. Combine them: `pm only email:`, `pm pick code:` |
| `pm critique: <rough prompt>` | A score out of 10, what's missing, and the one fix to make first (no rewrite) |
| `pm why` | What changed in the last rewrite and why |
| `pm again` / `pm undo` | A fresh rewrite, or an answer to your original draft as typed |
| `pm help` | The command list |

Typing is case-insensitive. If key details are missing (numbers, an attached file, a vague goal), it asks up to three quick questions first, and **go** accepts its suggestions. `pm only:`, `pm pick:` and `ep:` never ask: they use `[placeholders]` instead.

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

## Claude edition

### Install (Claude chat on the web, desktop or mobile)

1. Download [`prompt-master-claude.zip`](claude/prompt-master-claude.zip): open the file on GitHub and click the download button. To build it yourself, run `zip -r prompt-master-claude.zip prompt-master` inside the `claude` folder, so that `SKILL.md` sits inside a `prompt-master` folder in the zip.
2. In Claude, open **Settings → Capabilities** and make sure **Code execution and file creation** is on. On Team and Enterprise plans, an admin may need to allow skills first.
3. Under **Skills**, choose **Upload skill** and pick the zip. Make sure its toggle is on.
4. Start a new chat and type `pm help` to check that it works. An existing chat keeps the instructions it already loaded.

For clickable buttons after a `pm:` rewrite, turn on visuals or interactive content in the same settings.

### Good to know

- **Buttons:** after a `pm:` answer you get **Rewrite again**, **Why?** and **Undo** buttons. In some versions a click only fills the message box, so press Enter to send. They send `pm again`, `pm why` and `pm undo`, which you can also type.
- **Recommendations are advice.** Chat can't switch models for you. Pick the model in the selector, and use the extended thinking toggle for medium effort and above. The picker recommends Haiku, Sonnet or Opus with an effort level.
- **Plan:** `ep:` is tuned for Pro and Max plans. If you say you're on Free, it never recommends Opus. On pay-per-token API, it leans cheaper when the stakes are low.
- **Privacy:** passwords, API keys and card or ID numbers in a draft are replaced with `[redacted]` in the rewrite.
- **Language:** the rewrite uses the same language as your draft.
- **Cost:** the skill's instructions load once per chat that uses it, about 2.5k tokens, plus a short description that is always present.

### Customize

Everything lives in one file, `claude/prompt-master/SKILL.md`. To change which model it recommends, edit the table in section 6. To add a preset, add a row to the table in section 3. Re-zip (and replace `claude/prompt-master-claude.zip`) and upload again after any change.

## ChatGPT edition

### Install

**ChatGPT and ChatGPT Work**

1. Download [`prompt-master-chatgpt.zip`](chatgpt/prompt-master-chatgpt.zip): open the file on GitHub and click the download button.
2. Open the skills screen in ChatGPT (typically `/skills`; the menu varies by plan and version) and upload the zip. Upload this zip on its own: an archive must hold a single skill.
3. Start a new chat and type `pm help` to check that it works.

**Codex**

Codex needs the skill folder copied into `~/.agents/skills/` by hand. This is the tested method; I haven't verified another one. After downloading the zip, run this from the folder it's in (Mac or Linux):

```bash
mkdir -p ~/.agents/skills && unzip prompt-master-chatgpt.zip -d ~/.agents/skills
```

That puts the skill at `~/.agents/skills/prompt-master/SKILL.md`. Restart Codex if it was already open, then type `pm help`.

### Models it recommends

The picker names a model and an effort, plus a fallback if the first isn't in your selector. The names are recommendations, not proof that your plan has them.

- **ChatGPT Chat:** GPT-6 (Instant, Medium, High or Extra High), GPT-5.6 Sol as the fallback, and GPT-6 Pro (Astra) only if you have it.
- **ChatGPT Work and Codex:** GPT-5.6 Luna for the lightest tasks, GPT-5.6 Terra for routine work, GPT-5.6 Sol for hard work, and GPT-6 Astra for the hardest, where offered.

### Good to know

- **Buttons:** where the app supports native action buttons you get follow-ups; otherwise the skill ends with a line you can type, such as `pm again · pm why · pm undo`.
- **Recommendations are advice.** The skill never switches models or starts subagents for you. `ep codex:` only suggests a plan.
- **Plan:** on a Free plan it never recommends a paid-only model.
- **Privacy:** secrets in a draft are replaced with `[redacted]`.
- **Customize:** edit `chatgpt/prompt-master/SKILL.md`, re-zip and replace `chatgpt/prompt-master-chatgpt.zip`.

## Credits

Both editions were built by Nishkarsh Shah with Claude.

## License

MIT. See [LICENSE](LICENSE).
