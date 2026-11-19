# Prompt Master — Muse edition: manual test log

Date: 2026-11-19. Tester: MaximusMaxxx. Method: applied `muse/prompt-master/SKILL.md` to sample prompts by hand (repo has no test suite). Each test notes the expected behavior per the skill, the actual output, and pass/fail.

## Test 1: `ep: fix a race condition in my job queue`

Expected per SKILL.md section 5: a difficulty and approach note only, no model name, no rewrite, no answer. Score R/S/K/V, then the tier.

Scoring: R=3 (hard debugging), S=1 (one item, the job queue), K=2 (consequential but reversible), V=1 (slight ambiguity, no code shown). Score = 2*3 + 1 + 2 + 1 = 10. Tier 10-11 = Deliberate.

Actual output:

```
Approach: Deliberate

Why: hard debugging in one component, with a real risk if the fix is wrong.
Faster: Routine, a direct fix attempt without a reproduction, may miss the race.
More careful: High-stakes, reproduce first, then fix and verify under load.
```

Pass. No model named, no rewrite, no answer. The core port change (no model picker) works as intended.

## Test 2: `pm only: write a email to my boss about vacation`

Expected per SKILL.md section 4: the rewrite only, in a fenced code block, no execution, no extra prose. The email preset applies (recipient, purpose, key points, tone/length, response/action and timing, subject and body); missing facts become `[placeholder]`.

Actual output:

```
Please write a professional email to my boss requesting vacation. Include the dates I want off as [placeholder], the reason for the time off as [placeholder], and how my work will be covered while I am away as [placeholder]. Keep the tone polite and concise. Provide a subject line and the email body.
```

Pass. Rewrite only, in a code block, grammar fixed ("a email" to "an email"), preset dimensions present as instructions or placeholders, first person, no execution.

## Test 3: `pm critique: write a good email`

Expected per SKILL.md section 4: `Draft score: n/10`, `Strengths: ...`, `Missing or weak: ...` (up to three), `Fix first: ...`. No rewrite, no answer.

Actual output:

```
Draft score: 2/10

Strengths: states the desired output, an email.

Missing or weak:
• No recipient or purpose, so the email has no direction.
• No key points or content, so there is nothing to write about.
• No tone or length, so the result could miss the mark.

Fix first: say who the email is to and what it is about.
```

Pass. Format matches, score reflects the vagueness, no rewrite, no answer.

## Test 4: `pm help`

Expected per SKILL.md section 4: list available commands and one-line examples, without performing work.

Actual output: the command list (`pm:`, `pm only:`, `pm pick:`, `ep:`, `pm code:`, `pm email:`, `pm study:`, `pm research:`, `pm critique:`, `pm why`, `pm again`, `pm undo`, `pm help`), each with a one-line example. No work performed.

Pass. All 13 commands listed, including `ep:` as a difficulty and approach note (not a model recommendation), and no `ep codex:` (correctly dropped for Muse).

## Summary

4 of 4 tests pass. The port works as intended. Key result: `ep:` gives an approach note with no model name, which is the one behavior that had to change for Muse. Nothing is committed or pushed; the changes are local in `~/workspace/prompt-master` (new `muse/` folder, modified root `README.md`).
