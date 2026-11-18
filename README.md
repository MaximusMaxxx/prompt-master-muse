<p align="center">
  <img src="assets/logo.png" alt="Prompt Master icon" width="214" height="214">
</p>

<h1 align="center">Prompt Master</h1>

<p align="center"><b>Turn a rough prompt into a clear one, and get a model and effort recommendation.</b><br>One skill, two editions: Claude, and ChatGPT/Codex.</p>

<p align="center">
  <a href="LICENSE"><img src="assets/badge-license.svg" alt="MIT license" width="186" height="32"></a>
  <a href="#claude-edition"><img src="assets/badge-claude.svg" alt="Claude edition" width="186" height="32"></a>
  <a href="#chatgpt-edition"><img src="assets/badge-chatgpt.svg" alt="ChatGPT and Codex edition" width="186" height="32"></a>
</p>

https://github.com/user-attachments/assets/27a8a5e7-c70a-47d0-95b8-8ed3b9e2f5e4

## Pick your install

The two editions have the same commands. Download the one you use, or both.

| You use | Do this | Details |
| --- | --- | --- |
| Claude chat and Claude Code | Download [`prompt-master-claude.zip`](claude/prompt-master-claude.zip) and upload it in **Settings → Skills**. Claude Code gets it automatically, or install it from the [terminal](#terminal-install) | [Install](#install-claude-and-claude-code) |
| ChatGPT and ChatGPT Work | Download [`prompt-master-chatgpt.zip`](chatgpt/prompt-master-chatgpt.zip) and upload it in **Skills → Create** | [Install](#install-chatgpt-and-chatgpt-work) |
| Codex | Run `$skill-installer`, or [link the repo](#terminal-install) to stay up to date | [Install](#install-codex) |

Commands on this page are for Mac and Linux. Windows (PowerShell) versions are in [Terminal install](#terminal-install).

> [!TIP]
> **Check it works:** start a new chat or session and type `pm help`. It shows every command with examples, so use it any time you forget one. An existing chat keeps the instructions it already loaded.

<br>

<p align="center"><img src="assets/hero.svg" alt="A rough line straightens into a clean line" width="100%"></p>

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

### What the presets add

- **code:** language, your code and the exact error, expected vs actual behavior, constraints, output format, how to tell it works.
- **email:** who it's to, the goal, key points, tone, length, the one action you want, a deadline, subject line plus body.
- **study:** your level, topic and goal, time available, teaching from scratch with simple examples, practice questions, a check of understanding.
- **research:** the exact question, scope and time frame, depth, sources, facts kept separate from guesses, uncertainty stated.

<br>

## Claude edition

<a href="claude/prompt-master-claude.zip"><img src="assets/claude-edition.svg" alt="For Claude chat and Claude Code. Download the Claude zip." width="100%" height="84"></a>

### Install (Claude and Claude Code)

Works on the web, desktop and mobile apps.

1. Download [`prompt-master-claude.zip`](claude/prompt-master-claude.zip): open the file on GitHub and click the download button.
2. In Claude, open **Settings → Capabilities** and turn on **Code execution and file creation**. On Team and Enterprise plans, an admin may need to allow skills first.
3. Under **Skills**, choose **Upload skill**, pick the zip, and make sure its toggle is on.

If you sign in to Claude Code with the same Claude account, the skill you uploaded appears there automatically, in the desktop app and in the terminal. You can also run it as `/prompt-master`.

For clickable buttons after a `pm:` rewrite, turn on visuals or interactive content in the same settings.

<br>

## ChatGPT edition

<a href="chatgpt/prompt-master-chatgpt.zip"><img src="assets/chatgpt-edition.svg" alt="For ChatGPT, ChatGPT Work and Codex. Download the ChatGPT zip." width="100%" height="84"></a>

### Install (ChatGPT and ChatGPT Work)

1. Download [`prompt-master-chatgpt.zip`](chatgpt/prompt-master-chatgpt.zip): open the file on GitHub and click the download button.
2. In ChatGPT, open **Skills**, choose **Create**, then **Upload from your computer**, and pick the zip. On workspace plans, an admin may need to allow skill uploads first.

### Install (Codex)

In Codex, type:

```text
$skill-installer install https://github.com/nishkarsh-shah/prompt-master/tree/main/chatgpt/prompt-master
```

This puts the skill in `~/.agents/skills/prompt-master`. Restart Codex if `pm help` doesn't respond. To update, delete that folder and run the install command again.

<br>

## Terminal install

For installing from the terminal instead of uploading a zip.

<details>
<summary><b>Claude Code</b></summary>

An upload in Claude chat may not sync to an API-key login. Use one of these routes instead.

**Stay up to date with the repo** (Mac or Linux, needs git). Clone once and link the skill folder:

```bash
git clone https://github.com/nishkarsh-shah/prompt-master.git ~/prompt-master
mkdir -p ~/.claude/skills && ln -sfn ~/prompt-master/claude/plugin/skills/prompt-master ~/.claude/skills/prompt-master
```

Update any time with:

```bash
git -C ~/prompt-master pull
```

**Install by hand** (no upload, no git). On Mac or Linux this downloads the zip and unpacks it. Run the same command again to update.

```bash
mkdir -p ~/.claude/skills && curl -fsSL -o /tmp/prompt-master-claude.zip https://github.com/nishkarsh-shah/prompt-master/raw/main/claude/prompt-master-claude.zip && unzip -o /tmp/prompt-master-claude.zip -d ~/.claude/skills
```

On Windows (PowerShell):

```powershell
New-Item -ItemType Directory -Force "$HOME\.claude\skills" | Out-Null
Invoke-WebRequest https://github.com/nishkarsh-shah/prompt-master/raw/main/claude/prompt-master-claude.zip -OutFile "$env:TEMP\prompt-master-claude.zip"
Expand-Archive "$env:TEMP\prompt-master-claude.zip" -DestinationPath "$HOME\.claude\skills" -Force
```

**Note:** pick one route. If you also sync from Claude chat and install locally, Prompt Master can show up twice. To switch routes, remove the old copy first: `rm -rf ~/.claude/skills/prompt-master`

</details>

<details>
<summary><b>Codex</b></summary>

**Stay up to date with the repo** (Mac or Linux, needs git). Clone once and link the skill folder. If you already cloned it for Claude Code, skip the first command.

```bash
git clone https://github.com/nishkarsh-shah/prompt-master.git ~/prompt-master
mkdir -p ~/.agents/skills && ln -sfn ~/prompt-master/chatgpt/prompt-master ~/.agents/skills/prompt-master
```

Update any time with:

```bash
git -C ~/prompt-master pull
```

**Install by hand** (no installer, no git). On Mac or Linux this downloads the zip and unpacks it into `~/.agents/skills`. Run the same command again to update. For one project only, unzip into that project's `.agents/skills` folder instead.

```bash
mkdir -p ~/.agents/skills && curl -fsSL -o /tmp/prompt-master-chatgpt.zip https://github.com/nishkarsh-shah/prompt-master/raw/main/chatgpt/prompt-master-chatgpt.zip && unzip -o /tmp/prompt-master-chatgpt.zip -d ~/.agents/skills
```

On Windows (PowerShell):

```powershell
New-Item -ItemType Directory -Force "$HOME\.agents\skills" | Out-Null
Invoke-WebRequest https://github.com/nishkarsh-shah/prompt-master/raw/main/chatgpt/prompt-master-chatgpt.zip -OutFile "$env:TEMP\prompt-master-chatgpt.zip"
Expand-Archive "$env:TEMP\prompt-master-chatgpt.zip" -DestinationPath "$HOME\.agents\skills" -Force
```

</details>

<br>

## Models it recommends

The picker scores how hard, broad, risky and vague the task is. It only recommends the top models or max effort when the score earns it.

| Task | Claude | ChatGPT and Codex |
| --- | --- | --- |
| Lookups, formatting, simple questions | Haiku · low | GPT-5.6 Luna · low |
| Small clear edits and answers | Sonnet · low | GPT-5.6 Terra · low |
| Routine work | Sonnet · medium | GPT-5.6 Sol · medium |
| Multi-file work with a clear goal | Opus · medium | GPT-6 Sol · high |
| Hard debugging, design, subtle trade-offs | Opus · high | GPT-6.1 Sol · high |
| Deep architecture, security | Opus · max | GPT-6 Astra · high |

- **Claude:** a mechanical change to one file or item, such as a rename or a typo fix, always gets Haiku · low.
- **ChatGPT and Codex:** it adds a fallback in case your selector lacks the first pick, and stays on 5.6 until a task needs 6.x, which uses far more of your limits. A light but risky or unclear task steps up within the same family.

<br>

## Good to know

- **Updating:** an uploaded skill doesn't pull changes from GitHub. Download the new zip and upload it again. Terminal installs update with the command in their own section.

- **Buttons:** after a `pm:` answer you get **Rewrite again**, **Why?** and **Undo**. In Claude, some versions only fill the message box when you click, so press Enter to send. ChatGPT shows them where the app supports native action buttons. Where there are no buttons, such as the Claude Code terminal or Codex, type `pm again`, `pm why` or `pm undo`.

- **Recommendations are advice.** The skill never switches models or starts subagents for you; `ep claude:` and `ep codex:` only suggest a plan. Pick the model yourself, and in Claude use the extended thinking toggle for medium effort and above.

- **Your plan:** on a Free plan it never recommends a paid-only model. The Claude edition is tuned for Pro and Max, and on pay-per-token API it leans cheaper when the stakes are low.

- **Privacy:** Prompt Master doesn't collect, store or send any data. Passwords, API keys and card or ID numbers in a draft are replaced with `[redacted]` in the rewrite. See the [privacy policy](claude/plugin/PRIVACY.md).

- **Language:** the rewrite uses the same language as your draft.

<br>

## Customize

Each edition is one instruction file:

- **Claude:** `claude/plugin/skills/prompt-master/SKILL.md`. To change which model it recommends, edit the table in section 6. To add a preset, add a row to the table in section 3.
- **ChatGPT and Codex:** `chatgpt/prompt-master/SKILL.md`.

<details>
<summary><b>Rebuild the zip after a change</b></summary>

Each zip needs `SKILL.md` inside a `prompt-master` folder. From the repo folder, run the one for the edition you changed, then upload the new zip again.

```bash
cd claude/plugin/skills && rm -f ../../prompt-master-claude.zip && zip -r ../../prompt-master-claude.zip prompt-master
```

```bash
cd chatgpt && rm -f prompt-master-chatgpt.zip && zip -r prompt-master-chatgpt.zip prompt-master
```

</details>

## Credits

Both editions were built by Nishkarsh Shah with Claude.

## License

MIT. See [LICENSE](LICENSE).
