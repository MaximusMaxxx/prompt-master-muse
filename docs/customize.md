# Customize

[← Back to the README](../README.md)

Each edition is one instruction file:

- **Claude:** [`claude/plugin/skills/prompt-master/SKILL.md`](../claude/plugin/skills/prompt-master/SKILL.md). To change which model it recommends, edit the table in section 6. To add a preset, add a row to the table in section 3.
- **ChatGPT and Codex:** [`chatgpt/prompt-master/SKILL.md`](../chatgpt/prompt-master/SKILL.md).

## Rebuild the zip after a change

Each zip needs `SKILL.md` inside a `prompt-master` folder. From the repo folder, run the one for the edition you changed, then upload the new zip again.

```bash
cd claude/plugin/skills && rm -f ../../prompt-master-claude.zip && zip -r ../../prompt-master-claude.zip prompt-master
```

```bash
cd chatgpt && rm -f prompt-master-chatgpt.zip && zip -r prompt-master-chatgpt.zip prompt-master
```
