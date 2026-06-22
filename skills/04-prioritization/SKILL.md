
# Negotiation and Prioritization

## Purpose
This skill guides AI to negotiate and prioritize functional requirements for the Student Task Management System. It identifies stakeholder conflicts, requirement dependencies, MoSCoW priority categories, trade-off decisions, and reasons for each prioritization decision.

The problem solved by this skill is preventing AI from treating all requirements as equally important without explaining stakeholder value, dependency, feasibility, or trade-off.

## When to Use
Use this skill after functional requirements, non-functional requirements, business rules, user stories, and acceptance criteria have been created and reviewed.

Use it when:
- Functional requirements need MoSCoW priority.
- Stakeholder conflicts must be identified.
- Requirement dependencies must be documented.
- Trade-off decisions must be explained.
- The project needs output for `outputs/reviewed/05-prioritization.md`.

## Inputs
The following information must be available before this skill is executed:

- `CASE.md`
- `outputs/reviewed/01-inception.md`
- `outputs/reviewed/02-elicitation.md`
- `outputs/reviewed/03-requirements.md`
- `outputs/reviewed/04-user-stories.md`

## Required Context
AI must read the following files before producing output:

- `CASE.md`
- `outputs/reviewed/01-inception.md`
- `outputs/reviewed/02-elicitation.md`
- `outputs/reviewed/03-requirements.md`
- `outputs/reviewed/04-user-stories.md`

AI must treat reviewed requirements as the approved candidate set. AI must not add new requirements during prioritization.

## Workflow
1. Read all required context files.
2. List every functional requirement from `outputs/reviewed/03-requirements.md`.
3. Identify the stakeholder value of each functional requirement.
4. Identify dependencies between requirements.
5. Identify stakeholder conflicts or competing needs.
6. Define MoSCoW criteria for this project.
7. Assign each functional requirement one priority: Must, Should, Could, or Won't for now.
8. Provide a clear reason for each priority decision.
9. Identify trade-offs between value, risk, scope, effort, and dependency.
10. Record negotiation notes for conflicts or difficult priority decisions.
11. Check that not all requirements are assigned Must without justification.
12. Run the quality checks.
13. Stop and request clarification if a priority cannot be justified from stakeholder value or dependency.

## Output Format
The output must use the following structure:

```md
# Negotiation and Prioritization Output

## Prioritization Criteria
| Priority | Meaning in This Project |
|---|---|

## Prioritized Requirements
| Requirement ID | Requirement Summary | Stakeholder | Dependency | Priority | Reason |
|---|---|---|---|---|---|

## Dependencies
| Requirement | Depends On | Reason |
|---|---|---|

## Stakeholder Conflicts
| Conflict ID | Stakeholders | Conflict | Proposed Resolution |
|---|---|---|---|

## Trade-Off Decisions
| Decision ID | Trade-Off | Decision | Reason |
|---|---|---|---|

## Deferred or Excluded Items

## Quality Check Result
```

## Rules
- Every functional requirement must have exactly one MoSCoW priority.
- Priority must include a reason.
- Do not mark all requirements as Must.
- Do not add new requirements in this skill.
- Do not remove requirements without explaining the decision.
- Dependencies must be explicit.
- Stakeholder conflicts must be documented instead of hidden.
- Trade-off decisions must explain what is gained and what is delayed, reduced, or excluded.
- A Must requirement must support the core assignment workflow or required access control.
- A Should requirement is important but can be delayed if the core workflow still works.
- A Could requirement is useful but not necessary for the first baseline.
- A Won't for now item is outside current scope or intentionally deferred.

## Quality Checks
Before finalizing the output, check that:

- All functional requirements from `outputs/reviewed/03-requirements.md` are included.
- Every priority has a clear reason.
- Must requirements represent the minimum viable assignment workflow.
- Dependencies are consistent with the requirement flow.
- Stakeholder conflicts are identified or explicitly marked as none found.
- Trade-offs are explained.
- No unsupported requirement has been added.
- The output can be used as input for validation and traceability.

## Failure Conditions
The skill must stop or request clarification if:

- `outputs/reviewed/03-requirements.md` is missing or empty.
- Functional requirements do not have IDs.
- A requirement is duplicated or unclear.
- A dependency cannot be understood from the available context.
- A priority cannot be justified.
- Stakeholder conflicts affect the core workflow and cannot be resolved or documented.
- The AI would need to invent business value or implementation effort to decide priority.

## Example Invocation
Read `CASE.md`, `outputs/reviewed/01-inception.md`, `outputs/reviewed/02-elicitation.md`, `outputs/reviewed/03-requirements.md`, and `outputs/reviewed/04-user-stories.md`.

Execute `skills/04-prioritization/SKILL.md` exactly as written.

Save raw AI output to `outputs/raw/prioritization-ai-output.md`.

After human review, save final output to `outputs/reviewed/05-prioritization.md`.

Do not add new requirements. Prioritize every functional requirement using MoSCoW and explain each decision.

## Expected Output Example
```md
## Prioritization Criteria
| Priority | Meaning in This Project |
|---|---|
| Must | Required for assignment creation, submission, grading, access control, or course/user linkage. |
| Should | Important for control or monitoring, but the core workflow can still run without it in the first baseline. |
| Could | Useful enhancement with lower immediate value. |
| Won't for now | Outside current scope or intentionally deferred. |

## Prioritized Requirements
| Requirement ID | Requirement Summary | Stakeholder | Dependency | Priority | Reason |
|---|---|---|---|---|---|
| FR-01 | Lecturer creates assignments. | Lecturer | None | Must | Students cannot submit work before assignments exist. |
| FR-02 | Student submits assignment file. | Student | FR-01, FR-08, FR-09 | Must | Submission is the core student workflow. |
| FR-09 | Administrator configures file and late submission rules. | Administrator | FR-02 | Should | Configuration improves policy control, but default settings can support the first baseline. |

## Trade-Off Decisions
| Decision ID | Trade-Off | Decision | Reason |
|---|---|---|---|
| TD-01 | Flexible late submission policy vs simpler first release. | Keep late policy configurable but prioritize it as Should. | Core submission can start with default rules, while configuration can be refined later. |
```
