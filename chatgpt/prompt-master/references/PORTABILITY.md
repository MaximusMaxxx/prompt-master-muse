# Prompt Master portability notes

Original project: https://github.com/nishkarsh-shah/prompt-master (MIT).

## Preserved
- `pm:`, `pm only:`, `pm pick:`, `ep:`, presets `code`, `email`, `study`, `research`, `pm critique`, `pm why`, `pm again`, `pm undo`, `pm help`.
- 0–3 scoring of reasoning, scope, risk, and vagueness with score `2R + S + K + V` and original 0–1 / 2–4 / 5–7 / 8–11 / 12–15 bands.
- Original-draft follow-ups and privacy-redaction behavior.

## Adapted
- Haiku/Sonnet/Opus model rows -> capability tiers + effort, because actual OpenAI model availability varies by product, plan and time.
- Claude `show_widget` and HTML `sendPrompt` -> actionable ChatGPT buttons using supported host actions where available; graceful text-command fallback in Codex and unsupported clients. See `INTERACTIVE_CONTROLS.md`.
- ChatGPT Work is a product mode; the skill cannot launch the mode itself or confer missing capabilities.
- Codex efficiency via `ep codex:` is advisory; the skill does not change model settings, spawn agents, or measure tokens by itself.

## Installation

ChatGPT: upload this packaged skill through the supported Skills creation/import interface (typically `/skills`), if available on your account. Work uses skills only where supported by the product setup.

Codex: install the folder so `SKILL.md` is at `~/.agents/skills/prompt-master/SKILL.md`, or use the skill installer offered by your Codex version. Restart or refresh Codex's skill discovery if it was already open. Exact menus may vary.

Do not place multiple skills inside one upload archive. This package contains exactly one.

## Explicit named-model recommendations

The OpenAI edition now explicitly names model versions in `ep:`, `ep codex:`, and `pm pick:` instead of only a capability tier. ChatGPT Chat, Work, and Codex have distinct selectors: consult the `SKILL.md` model matrix, recommend only models plausible for the surface, and always state a named fallback and workspace-availability caveat. Recommendations never switch the selected model or guarantee reduced usage.


## Claude feature parity restored

Preserve the original boxed clarification block, `go`/`defaults` continuation, exact empty-draft replies, single-item mechanical override, Free/pay-per-token model-selection constraints, never saying "gear", no all-caps emphasis/restating, XML tags for pasted source content, and preset priority over no-padding. Native OpenAI controls remain requested only where supported; otherwise provide textual alternatives. The model override refers to the *lightest named model actually available* in OpenAI, not Claude Haiku, and does not waive safety verification.
