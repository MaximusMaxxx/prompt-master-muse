# Prompt Master

A skill that turns a rough, hastily typed prompt into a clear one, and recommends which model and effort level to use for it. It comes in two editions with the same commands: one for Claude, one for ChatGPT and Codex. Download the one you use, or both.

| Edition | For | Download | Folder |
| --- | --- | --- | --- |
| Claude | Claude chat on the web, desktop and mobile, and Claude Code | [`prompt-master-claude.zip`](claude/prompt-master-claude.zip) | [`claude/`](claude) |
| ChatGPT | ChatGPT, ChatGPT Work and Codex | [`prompt-master-chatgpt.zip`](chatgpt/prompt-master-chatgpt.zip) | [`chatgpt/`](chatgpt) |

Type `pm:` before a rough prompt and the skill rewrites it, shows you the rewrite, and answers it. Type `ep:` before a task and it recommends a model and effort level without doing the task.

> [!TIP]
> **Forgot a command? Type `pm help`** to see the full list with examples, right in the chat.

## Commands

| You type | You get |
| --- | --- |
| `pm: <rough prompt>` | A rewritten prompt, then the answer to it |
| `pm only: <rough prompt>` | Only the rewritten prompt, in a copy-ready block |
| `pm pick: <rough prompt>` | The rewrite, then a model and effort recommendation for it (no answer) |
| `ep: <task>` | A model and effort recommendation for the task as you wrote it |
| `ep claude: <task>` | Claude edition only: the same, plus a short Claude Code plan, plan mode and subagent advice |
| `ep codex: <task>` | ChatGPT edition only: the same, plus a short Codex plan and subagent advice |
| `pm code:` `pm email:` `pm study:` `pm research:` | A preset that shapes the rewrite for that kind of task. Combine them: `pm only email:`, `pm pick code:` |
| `pm critique: <rough prompt>` | A score out of 10, what's missing, and the one fix to make first (no rewrite) |
| `pm why` | What changed in the last rewrite and why |
| `pm again` / `pm undo` | A fresh rewrite, or an answer to your original draft as typed |
| **`pm help`** | **The full command list with examples. Use it whenever you forget a command.** |

Typing is case-insensitive. If key details are missing (numbers, an attached file, a vague goal), it asks up to three quick questions first, and **go** accepts its suggestions. `pm only:`, `pm pick:` and the `ep` commands never ask: they use `[placeholders]` instead.

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

<br>

## Claude edition

### Install (Claude chat on the web, desktop or mobile)

1. Download [`prompt-master-claude.zip`](claude/prompt-master-claude.zip): open the file on GitHub and click the download button. To build it yourself, run `zip -r ../../prompt-master-claude.zip prompt-master` inside the `claude/plugin/skills` folder, so that `SKILL.md` sits inside a `prompt-master` folder in the zip.
2. In Claude, open **Settings → Capabilities** and make sure **Code execution and file creation** is on. On Team and Enterprise plans, an admin may need to allow skills first.
3. Under **Skills**, choose **Upload skill** and pick the zip. Make sure its toggle is on.
4. Start a new chat and type `pm help` to check that it works. An existing chat keeps the instructions it already loaded.

For clickable buttons after a `pm:` rewrite, turn on visuals or interactive content in the same settings.

### Install (Claude Code)

Nothing extra to do if you signed in to Claude Code with your Claude account: the skill you uploaded above syncs to Claude Code automatically, in the desktop app and in the terminal. Start a new session and type `pm help`, or run it as `/prompt-master`. In the terminal there are no buttons, so type `pm again`, `pm why` or `pm undo`.

If you sign in with an API key instead, the upload doesn't sync. Install it by hand: download the zip, then run this from the folder it's in (Mac or Linux):

```bash
mkdir -p ~/.claude/skills && unzip prompt-master-claude.zip -d ~/.claude/skills
```

### Models it recommends

The picker scores how hard, broad, risky and vague the task is, and only recommends Opus or max effort when the score earns it:

| Task | Recommended |
| --- | --- |
| Lookups, formatting, simple questions | Haiku · low |
| Small clear edits and answers | Sonnet · low |
| Routine work | Sonnet · medium |
| Hard debugging, multi-file work, design | Opus · high |
| Deep architecture, security, subtle problems | Opus · max |

A mechanical change to one file or item, such as a rename or a typo fix, always gets Haiku · low.

### Good to know

- **Buttons:** after a `pm:` answer you get **Rewrite again**, **Why?** and **Undo** buttons. In some versions a click only fills the message box, so press Enter to send. They send `pm again`, `pm why` and `pm undo`, which you can also type.
- **Recommendations are advice.** Chat can't switch models for you. Pick the model in the selector, and use the extended thinking toggle for medium effort and above.
- **Plan:** `ep:` is tuned for Pro and Max plans. If you say you're on Free, it never recommends Opus. On pay-per-token API, it leans cheaper when the stakes are low.
- **Privacy:** passwords, API keys and card or ID numbers in a draft are replaced with `[redacted]` in the rewrite.
- **Language:** the rewrite uses the same language as your draft.
- **Cost:** the skill's instructions load once per chat that uses it, under 3k tokens, plus a short description that is always present.

### Customize

Everything lives in one file, `claude/plugin/skills/prompt-master/SKILL.md`. To change which model it recommends, edit the table in section 6. To add a preset, add a row to the table in section 3. Re-zip (and replace `claude/prompt-master-claude.zip`) and upload again after any change.

<br>

## ChatGPT edition

### Install

**ChatGPT and ChatGPT Work**

1. Download [`prompt-master-chatgpt.zip`](chatgpt/prompt-master-chatgpt.zip): open the file on GitHub and click the download button.
2. In ChatGPT, open **Skills**, choose **Create**, then **Upload from your computer**, and pick the zip. On workspace plans, an admin may need to allow skill uploads first.
3. Start a new chat and type `pm help` to check that it works.

**Codex**

The easiest way is Codex's built-in skill installer. In Codex, type:

```text
$skill-installer install https://github.com/nishkarsh-shah/prompt-master/tree/main/chatgpt/prompt-master
```

Or copy it in by hand: download the zip, then run this from the folder it's in (Mac or Linux). It puts the skill at `~/.agents/skills/prompt-master/SKILL.md`; for one project only, unzip it into that project's `.agents/skills` folder instead.

```bash
mkdir -p ~/.agents/skills && unzip prompt-master-chatgpt.zip -d ~/.agents/skills
```

Then type `pm help` to check. Restart Codex if it doesn't respond.

### Models it recommends

The picker names a model and an effort, plus a fallback if the first isn't in your selector. The names are recommendations, not proof that your plan has them.

The same picks apply in ChatGPT, Work and Codex. 6.x models use much more of your limits, so it stays on 5.6 until a task needs more:

| Task | Recommended |
| --- | --- |
| Lookups, formatting, renames | GPT-5.6 Luna · low |
| Small clear edits and answers | GPT-5.6 Terra · low |
| Routine work | GPT-5.6 Sol · medium |
| Hard debugging, multi-file work | GPT-6 Sol · high |
| Design, subtle trade-offs | GPT-6.1 Sol · high |
| Deep architecture, security | GPT-6 Astra · high |

For a light task that is risky or unclear, it steps up to the newer model in the same family: GPT-6 Luna, GPT-6.1 Terra or GPT-6 Sol.

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
