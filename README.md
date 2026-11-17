# Prompt Master

A skill that turns a rough, hastily typed prompt into a clear one, and recommends which model and effort level to use for it. It comes in two editions with the same commands: one for Claude, one for ChatGPT and Codex. Download the one you use, or both.

| Edition | For | Download | Folder |
| --- | --- | --- | --- |
| Claude | Claude chat on the web, desktop and mobile, and Claude Code | [`prompt-master-claude.zip`](claude/prompt-master-claude.zip) | [`claude/`](claude) |
| ChatGPT | ChatGPT, ChatGPT Work and Codex | [`prompt-master-chatgpt.zip`](chatgpt/prompt-master-chatgpt.zip) | [`chatgpt/`](chatgpt) |

Type `pm:` before a rough prompt and the skill rewrites it, shows you the rewrite, and answers it. Type `ep:` before a task and it recommends a model and effort level without doing the task.

> [!TIP]
> **Forgot a command? Type `pm help`** to see the full list with examples, right in the chat.

## Which install do I need?

| You use | Do this | Details |
| --- | --- | --- |
| Claude chat (web, desktop, mobile) | Upload the zip in **Settings → Skills** | [Install](#install-claude-chat) |
| Claude Code | Upload it in Claude chat and it syncs here, or install it from the terminal | [Install](#install-claude-code) |
| ChatGPT and ChatGPT Work | Upload the zip in **Skills → Create** | [Install](#install-chatgpt-and-chatgpt-work) |
| Codex | Run `$skill-installer`, or link the repo to stay up to date | [Install](#install-codex) |

Commands on this page are for Mac and Linux. Windows (PowerShell) versions are in the collapsed sections.

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
pm email: ask my team to move Friday's meeting to Monday
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

<a href="claude/prompt-master-claude.zip"><img src="assets/claude-edition.svg" alt="For Claude chat and Claude Code. Download the Claude zip." width="100%"></a>

### Install (Claude chat)

Works on the web, desktop and mobile apps.

1. Download [`prompt-master-claude.zip`](claude/prompt-master-claude.zip): open the file on GitHub and click the download button.
2. In Claude, open **Settings → Capabilities** and turn on **Code execution and file creation**. On Team and Enterprise plans, an admin may need to allow skills first.
3. Under **Skills**, choose **Upload skill**, pick the zip, and make sure its toggle is on.

> [!TIP]
> **Check it works:** start a new chat and type `pm help`. An existing chat keeps the instructions it already loaded.

**Update:** an uploaded skill doesn't pull changes from GitHub. Download the new zip and upload it again.

For clickable buttons after a `pm:` rewrite, turn on visuals or interactive content in the same settings.

<br>

### Install (Claude Code)

Pick one of two routes:

- **Sync from Claude chat:** upload the skill in Claude chat, as above. If you sign in to Claude Code with the same Claude account, it appears there automatically, in the desktop app and in the terminal.
- **Install it locally:** use one of the options below. This works without uploading anything, and with an API-key login.

> [!TIP]
> **Check it works:** start a new session and type `pm help`, or run it as `/prompt-master`. In the terminal there are no buttons, so type `pm again`, `pm why` or `pm undo`.

**Update:** if it syncs from Claude chat, upload the new zip there. If you installed it locally, use the update step of the option you chose.

> [!NOTE]
> Pick one route. If you also link or copy the skill into `~/.claude/skills` (below), Prompt Master can show up twice. To switch routes, remove the old copy first: `rm -rf ~/.claude/skills/prompt-master`

<details>
<summary><b>Stay up to date with the repo</b> (Mac or Linux, needs git)</summary>

Clone the repo once and link the skill folder. Updating is then one `git pull`.

```bash
git clone https://github.com/nishkarsh-shah/prompt-master.git ~/prompt-master
mkdir -p ~/.claude/skills && ln -sfn ~/prompt-master/claude/plugin/skills/prompt-master ~/.claude/skills/prompt-master
```

Update any time with:

```bash
git -C ~/prompt-master pull
```

Start a new session and type `pm help` to check.

</details>

<details>
<summary><b>Install by hand</b> (no upload, no git)</summary>

**Mac or Linux:** this downloads the zip and unpacks it. Run the same command again to update.

```bash
mkdir -p ~/.claude/skills && curl -fsSL -o /tmp/prompt-master-claude.zip https://github.com/nishkarsh-shah/prompt-master/raw/main/claude/prompt-master-claude.zip && unzip -o /tmp/prompt-master-claude.zip -d ~/.claude/skills
```

**Windows (PowerShell):**

```powershell
New-Item -ItemType Directory -Force "$HOME\.claude\skills" | Out-Null
Invoke-WebRequest https://github.com/nishkarsh-shah/prompt-master/raw/main/claude/prompt-master-claude.zip -OutFile "$env:TEMP\prompt-master-claude.zip"
Expand-Archive "$env:TEMP\prompt-master-claude.zip" -DestinationPath "$HOME\.claude\skills" -Force
```

Start a new session and type `pm help` to check.

</details>

<details>
<summary><b>Signed in to Claude Code with an API key?</b></summary>

An upload in Claude chat may not sync to an API-key login. If it doesn't appear, use "Stay up to date with the repo" or "Install by hand" above instead.

</details>

<br>

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

<br>

## ChatGPT edition

<a href="chatgpt/prompt-master-chatgpt.zip"><img src="assets/chatgpt-edition.svg" alt="For ChatGPT, ChatGPT Work and Codex. Download the ChatGPT zip." width="100%"></a>

### Install (ChatGPT and ChatGPT Work)

1. Download [`prompt-master-chatgpt.zip`](chatgpt/prompt-master-chatgpt.zip): open the file on GitHub and click the download button.
2. In ChatGPT, open **Skills**, choose **Create**, then **Upload from your computer**, and pick the zip. On workspace plans, an admin may need to allow skill uploads first.

> [!TIP]
> **Check it works:** start a new chat and type `pm help`.

**Update:** an uploaded skill doesn't pull changes from GitHub. Download the new zip and upload it again.

<br>

### Install (Codex)

In Codex, type:

```text
$skill-installer install https://github.com/nishkarsh-shah/prompt-master/tree/main/chatgpt/prompt-master
```

This puts the skill in `~/.agents/skills/prompt-master`.

> [!TIP]
> **Check it works:** type `pm help`. Restart Codex if it doesn't respond.

**Update:** the installer copies the files, so delete `~/.agents/skills/prompt-master` and run the install command again.

<details>
<summary><b>Stay up to date with the repo</b> (Mac or Linux, needs git)</summary>

Clone the repo once and link the skill folder. Updating is then one `git pull`. If you already cloned it for Claude Code, skip the first command.

```bash
git clone https://github.com/nishkarsh-shah/prompt-master.git ~/prompt-master
mkdir -p ~/.agents/skills && ln -sfn ~/prompt-master/chatgpt/prompt-master ~/.agents/skills/prompt-master
```

Update any time with:

```bash
git -C ~/prompt-master pull
```

</details>

<details>
<summary><b>Install by hand</b> (no installer, no git)</summary>

**Mac or Linux:** this downloads the zip and unpacks it into `~/.agents/skills`. Run the same command again to update. For one project only, unzip into that project's `.agents/skills` folder instead.

```bash
mkdir -p ~/.agents/skills && curl -fsSL -o /tmp/prompt-master-chatgpt.zip https://github.com/nishkarsh-shah/prompt-master/raw/main/chatgpt/prompt-master-chatgpt.zip && unzip -o /tmp/prompt-master-chatgpt.zip -d ~/.agents/skills
```

**Windows (PowerShell):**

```powershell
New-Item -ItemType Directory -Force "$HOME\.agents\skills" | Out-Null
Invoke-WebRequest https://github.com/nishkarsh-shah/prompt-master/raw/main/chatgpt/prompt-master-chatgpt.zip -OutFile "$env:TEMP\prompt-master-chatgpt.zip"
Expand-Archive "$env:TEMP\prompt-master-chatgpt.zip" -DestinationPath "$HOME\.agents\skills" -Force
```

</details>

<br>

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

<br>

## Good to know

- **Buttons:** after a `pm:` answer you get **Rewrite again**, **Why?** and **Undo**. In Claude, some versions only fill the message box when you click, so press Enter to send. ChatGPT shows them where the app supports native action buttons. Where there are no buttons, such as the Claude Code terminal or Codex, type `pm again`, `pm why` or `pm undo`.
- **Recommendations are advice.** The skill never switches models or starts subagents for you; `ep claude:` and `ep codex:` only suggest a plan. Pick the model yourself, and in Claude use the extended thinking toggle for medium effort and above.
- **Plan:** on a Free plan it never recommends a paid-only model. The Claude edition is tuned for Pro and Max, and on pay-per-token API it leans cheaper when the stakes are low.
- **Privacy:** Prompt Master doesn't collect, store or send any data. Passwords, API keys and card or ID numbers in a draft are replaced with `[redacted]` in the rewrite. See the [privacy policy](claude/plugin/PRIVACY.md).
- **Language:** the rewrite uses the same language as your draft.

## Customize

Each edition is one instruction file:

- **Claude:** `claude/plugin/skills/prompt-master/SKILL.md`. To change which model it recommends, edit the table in section 6. To add a preset, add a row to the table in section 3.
- **ChatGPT and Codex:** `chatgpt/prompt-master/SKILL.md`.

After any change, rebuild the zip and upload it again:

```bash
cd claude/plugin/skills && rm -f ../../prompt-master-claude.zip && zip -r ../../prompt-master-claude.zip prompt-master
```

```bash
cd chatgpt && rm -f prompt-master-chatgpt.zip && zip -r prompt-master-chatgpt.zip prompt-master
```

Each zip must have `SKILL.md` inside a `prompt-master` folder.

## Credits

Both editions were built by Nishkarsh Shah with Claude.

## License

MIT. See [LICENSE](LICENSE).
