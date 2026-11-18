# Terminal install

For installing from the terminal instead of uploading a zip. Jump to [Claude Code](#claude-code) or [Codex](#codex).

[← Back to the README](../README.md)

## Claude Code

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


## Codex
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
