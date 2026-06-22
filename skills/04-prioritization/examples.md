
# Examples for Negotiation and Prioritization

## Example Invocation
```text
Read CASE.md, outputs/reviewed/01-inception.md,
outputs/reviewed/02-elicitation.md, outputs/reviewed/03-requirements.md,
and outputs/reviewed/04-user-stories.md.

Execute skills/04-prioritization/SKILL.md exactly as written.
Save the first AI output to outputs/raw/prioritization-ai-output.md.
After review, save final output to outputs/reviewed/05-prioritization.md.
Use MoSCoW priority for every functional requirement.
Do not add new requirements.
```

## Example Input Summary
Candidate functional requirements:

- `FR-01`: Lecturers create assignments.
- `FR-02`: Students submit assignment files.
- `FR-03`: Students view active assignments and deadlines.
- `FR-04`: Students view assignment status.
- `FR-05`: Lecturers view submission lists.
- `FR-06`: Lecturers enter grades and feedback.
- `FR-07`: Administrators manage lecturer and student accounts.
- `FR-08`: Administrators manage courses and enrollments.
- `FR-09`: Administrators configure accepted file types, maximum file size, and late submission policy.
- `FR-10`: Administrators view assignment activity reports.

## Expected Output Example
```md
# Negotiation and Prioritization Output

## Prioritization Criteria
| Priority | Meaning in This Project |
|---|---|
| Must | Required for the first usable assignment workflow or access control. |
| Should | Important for control, policy, or monitoring but can be delayed after the first baseline. |
| Could | Useful but lower priority enhancement. |
| Won't for now | Outside scope or intentionally deferred. |

## Prioritized Requirements
| Requirement ID | Requirement Summary | Stakeholder | Dependency | Priority | Reason |
|---|---|---|---|---|---|
| FR-01 | Lecturer creates assignments. | Lecturer | None | Must | Assignments must exist before students can view or submit work. |
| FR-02 | Student submits assignment files. | Student | FR-01, FR-08, FR-09 | Must | File submission is the core student workflow. |
| FR-03 | Student views active assignments and deadlines. | Student | FR-01, FR-08 | Must | Students need assignment visibility to complete tasks. |
| FR-04 | Student views assignment status. | Student | FR-02, FR-06 | Must | Status tracking confirms submission and grading progress. |
| FR-05 | Lecturer views submission list. | Lecturer | FR-01, FR-02, FR-08 | Must | Lecturers need submission visibility before grading. |
| FR-06 | Lecturer enters grades and feedback. | Lecturer | FR-02, FR-05 | Must | Grading and feedback are required by the case. |
| FR-07 | Administrator manages users. | Administrator | None | Must | User management controls who can access the system. |
| FR-08 | Administrator manages courses and enrollments. | Administrator | FR-07 | Must | Course and enrollment data determine assignment access. |
| FR-09 | Administrator configures file and late submission rules. | Administrator | FR-02 | Should | Configuration improves policy control but can begin with default settings. |
| FR-10 | Administrator views assignment activity reports. | Administrator | FR-01, FR-02, FR-08 | Should | Reports support monitoring but are not required for the first submission flow. |

## Dependencies
| Requirement | Depends On | Reason |
|---|---|---|
| FR-02 | FR-01, FR-08, FR-09 | A student can submit only when an assignment, course enrollment, and file policy exist. |
| FR-04 | FR-02, FR-06 | Status depends on submission and grading events. |
| FR-05 | FR-01, FR-02, FR-08 | Lecturer submission list depends on assignment, submissions, and enrollment. |
| FR-10 | FR-01, FR-02, FR-08 | Reports depend on assignment and submission data. |

## Stakeholder Conflicts
| Conflict ID | Stakeholders | Conflict | Proposed Resolution |
|---|---|---|---|
| CF-01 | Lecturer, Administrator | Lecturers may want flexible late submission handling, while administrators need consistent policy control. | Use configurable late submission policy and prioritize it as Should. |
| CF-02 | Administrator, Lecturer | Administrators may want broad reporting, while lecturers need grading workflow first. | Keep initial reports limited to assignment and submission activity counts. |

## Trade-Off Decisions
| Decision ID | Trade-Off | Decision | Reason |
|---|---|---|---|
| TD-01 | Complete reporting vs core submission workflow. | Prioritize reports as Should. | Reporting is useful, but submission and grading are more central to the case. |
| TD-02 | Flexible configuration vs faster baseline delivery. | Prioritize configuration as Should with default first-release settings. | The first baseline can function with defaults while configuration is refined. |

## Deferred or Excluded Items
- Plagiarism detection remains out of scope.
- Real-time chat remains out of scope.
- Video conferencing remains out of scope.

## Quality Check Result
Passed. All functional requirements are prioritized, dependencies are documented, and trade-off reasons are explained.
```

## Bad Output Example
```md
All requirements are Must because all requirements are important.
```

## Why This Output Is Bad
- It does not show actual prioritization.
- It hides trade-offs.
- It does not explain stakeholder value.
- It does not identify dependencies or conflicts.
- It cannot guide validation or release planning.

## Good Practice Notes
- Must should mean required for the minimum viable assignment workflow.
- Priority should be justified with stakeholder value, dependency, or scope impact.
- A lower priority does not mean the requirement is bad; it means it is less critical for the first baseline.
- Conflicts should be documented even when they are resolved.
