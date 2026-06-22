
# Project Inception and Stakeholder Discovery

## Purpose
This skill guides AI to perform the inception stage of requirements engineering for the Student Task Management System. It identifies the business problem, project goals, stakeholders, stakeholder needs, initial scope, assumptions, constraints, and open questions before detailed requirements are written.

The problem solved by this skill is preventing AI from jumping directly into features without first understanding the business context and stakeholder needs.

## When to Use
Use this skill at the beginning of the project, before requirements elicitation, specification, prioritization, validation, or change management.

Use it when:
- A case description is available but detailed requirements have not been defined.
- Stakeholders need to be identified.
- Project scope needs to be separated into in-scope and out-of-scope items.
- Assumptions and missing information need to be documented.

## Inputs
The following information must be available before this skill is executed:

- `CASE.md`
- `inputs/stakeholder-notes.md`
- `inputs/assumptions.md`
- Assignment instructions related to the Student Task Management System case.

## Required Context
AI must read the following files before producing output:

- `CASE.md`
- `inputs/stakeholder-notes.md`
- `inputs/assumptions.md`

AI must treat `CASE.md` as the primary source of truth. Stakeholder notes and assumptions may support the analysis, but unsupported details must not be presented as facts.

## Workflow
1. Read all required context files.
2. Summarize the business problem in a maximum of two paragraphs.
3. Separate the business problem from possible software solutions.
4. Identify initial business goals that can be evaluated later.
5. Identify primary and secondary stakeholders.
6. Describe the needs of each stakeholder.
7. Define in-scope and out-of-scope items.
8. Identify constraints from the case and assignment instructions.
9. List assumptions using the label `ASSUMPTION`.
10. Mark missing or unclear information using the label `OPEN QUESTION`.
11. Check whether any output item is unsupported by the source.
12. Run the quality checks.
13. Stop and ask for clarification if the available information is not enough to produce a reliable inception output.

## Output Format
The output must use the following structure:

```md
# Project Inception Output

## Business Problem

## Business Goals

## Stakeholders
| Stakeholder | Type | Needs | Source |
|---|---|---|---|

## Scope
### In Scope
### Out of Scope

## Assumptions

## Constraints

## Open Questions

## Quality Check Result
```

## Rules
- Do not create detailed functional requirements in this stage.
- Do not invent features that are not supported by the case.
- Do not assume all stakeholders have the same needs.
- Separate facts from assumptions.
- Label every assumption with `ASSUMPTION`.
- Label every missing or unclear item with `OPEN QUESTION`.
- Use clear and testable wording when describing goals.
- Do not use vague claims such as "better system" or "easy process" without explaining what they mean.
- Keep scope boundaries clear.

## Quality Checks
Before finalizing the output, check that:

- The business problem is explained without depending only on technology.
- The output separates problem, goals, stakeholders, scope, assumptions, constraints, and open questions.
- Every primary stakeholder has at least one identified need.
- In-scope and out-of-scope items are clearly separated.
- Assumptions are not mixed with facts.
- No unsupported feature has been added.
- Open questions are specific enough to guide the next elicitation stage.
- The output can be used as input for the elicitation skill.

## Failure Conditions
The skill must stop or request clarification if:

- `CASE.md` is missing or empty.
- Stakeholder information is not available.
- The case description is too vague to identify scope.
- Required context files contradict each other.
- A stakeholder need cannot be linked to the case, stakeholder notes, or assumptions.
- The AI would need to invent major facts to complete the output.

## Example Invocation
Read `CASE.md`, `inputs/stakeholder-notes.md`, and `inputs/assumptions.md`.

Execute `skills/01-inception/SKILL.md` exactly as written.

Save the raw result to `outputs/raw/inception-ai-output.md`.

Do not invent missing facts. Mark assumptions and open questions explicitly.

## Expected Output Example
```md
## Stakeholders
| Stakeholder | Type | Needs | Source |
|---|---|---|---|
| Lecturer | Primary | Create assignments, set deadlines, monitor submissions, grade work, and provide feedback. | CASE.md, stakeholder notes |
| Student | Primary | View active assignments, submit files, receive confirmation, and monitor deadlines. | CASE.md, stakeholder notes |
| Administrator | Primary | Manage users, courses, configuration, and assignment activity reports. | CASE.md, stakeholder notes |

## Open Questions
- OPEN QUESTION: What file types and maximum file size should be allowed for submissions?
- OPEN QUESTION: Should late submissions be blocked or accepted with a Late status?
```
