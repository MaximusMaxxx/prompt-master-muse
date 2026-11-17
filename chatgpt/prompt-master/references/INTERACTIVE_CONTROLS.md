# Native interactive controls in Prompt Master

The skill instructs the assistant to generate clickable actions; the SKILL.md is **not itself a UI program**. A client must support native action controls for buttons to execute. Buttons cannot be guaranteed by the skill on Codex CLI/Desktop, in all Work clients, or across all ChatGPT versions.

## ChatGPT native response example (DIL-capable host only)

After displaying the rewritten prompt:

```jsx
<row gap={2} wrap="wrap">
  <button size="sm" variant="outline" onClick={() => GenUI.issueNewTurn("pm again")}>Try again</button>
  <button size="sm" variant="outline" onClick={() => GenUI.issueNewTurn("pm why")}>Why?</button>
  <button size="sm" variant="outline" onClick={() => GenUI.issueNewTurn("pm undo")}>Undo</button>
</row>
```

For `pm only:` and `pm pick:`, replace the buttons with real actions operating on the content of the response:

```jsx
<row gap={2} wrap="wrap">
  <button size="sm" variant="outline" onClick={() => GenUI.copy("ACTUAL REWRITTEN PROMPT CONTENT")}>Copy prompt</button>
  <button size="sm" variant="outline" onClick={() => GenUI.issueNewTurn("pm again")}>Refine</button>
  <button size="sm" onClick={() => GenUI.issueNewTurn("pm: ACTUAL REWRITTEN PROMPT CONTENT")}>Answer it</button>
</row>
```

Replace uppercase example text **with the exact visible rewritten prompt** when authoring the response. Never expose that placeholder to the user. For prompts containing quotes, line breaks or backslashes, serialize the complete text as a correct JS string expression. Avoid emitting secret tokens in prompts or buttons.

For `ep:` use similar action buttons only when meaningful and include the actual task in the generated prompt. No button should claim to change models; `ep` recommendations are advisory.

## Fallback

When native controls aren't available, finish with one brief line such as `Next: pm again · pm why · pm undo`. Do not claim text is clickable. Never generate fake buttons, unsupported tools or HTML script injection. Button actions are new chat turns, not hidden subagent dispatches; they may consume model usage.
