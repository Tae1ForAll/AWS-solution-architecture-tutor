---
name: tutor
description: Teach the next (or a named) AWS certification topic following the CLAUDE.md teaching structure. Use when the user says "teach me", "next topic", "continue", or names an AWS topic to learn.
---

# Tutor – teach one topic

Arguments (optional): a topic or section ID, e.g. `1.02` or `IAM roles`.

## Steps

1. **Pick the topic**
   - If an argument is given, find the matching section in `domains/*/README.md`.
   - Otherwise read `learning/progress.md` and the domain READMEs and pick the
     first section that is `In progress`, else the first `Not started`.
   - Briefly check `learning/weak-topics.md` for related open items to weave in.

2. **Check scope** – read the section's task statement in
   `resources/exam-guide/solutions-architect-associate-03.pdf` and check
   `resources/exam-guide/scope-summary.md`. Never teach out-of-scope services
   as exam content. Also use any relevant material in `resources/notes/` and
   `resources/whitepapers/`.

3. **Teach ONE topic** using the 8-part structure from `CLAUDE.md`:
   Definition → Simple Explanation → How It Works → Practical Example →
   When to Use It → Comparisons → Exam Considerations → Knowledge Check.
   - Label sources: *(from your documents)*, *(AWS docs)*, *(illustrative example)*.
   - Never invent features, limits or pricing. State uncertainty explicitly.
   - If the topic is large, split it and teach only the first part.

4. **Stop and wait** after the Knowledge Check question. Do not continue
   until the user answers.

5. **After the user answers**, give feedback, then offer the quiz (`/quiz`).

6. **Record**
   - Save the lesson to `domains/<domain>/lessons/NN-topic-name.md`
     (concise summary + key exam points, not a full transcript).
   - Set the section status to `Taught` (never `Understood` from a lesson alone).
   - Add a Session Log entry in `learning/progress.md` and update the summary table.
