---
name: quiz
description: Run an AWS certification-style scenario quiz on a topic and record the results. Use when the user asks for a quiz, practice questions, or accepts a quiz offer after a lesson.
---

# Quiz – scenario questions

Arguments (optional): topic / section ID and number of questions (default 3–5).

## Steps

1. **Choose topic** – the argument, else the most recently taught section in
   `learning/progress.md`. Include 1 question from an open item in
   `learning/weak-topics.md` if relevant.

2. **Write questions** in AWS exam style:
   - A short realistic scenario with a clear requirement
     ("MOST cost-effective", "LEAST operational overhead", "highly available").
   - 4 options (A–D), all plausible; occasionally "choose TWO".
   - Base answers only on verified AWS behaviour.

3. **Ask all questions, then STOP.** Never reveal or hint at answers before
   the user responds.

4. **Mark the answers.** For each question:
   - Why the correct answer is correct.
   - Why each incorrect option is wrong.
   - Name the specific misunderstanding behind any wrong answer.

5. **Record**
   - Append to `learning/quiz-history.md` (summary row + detailed record).
   - Add each misunderstanding to `learning/weak-topics.md` → Open.
     If a previously open weak topic is now answered correctly, move it to Resolved
     with the evidence.
   - Update the section status in `domains/*/README.md`:
     `Understood` only if the user scored well **and** got no core-concept
     question wrong; otherwise leave as `Taught`.
   - Update the summary table in `learning/progress.md`.
