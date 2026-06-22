
# Student Task Management System Case

## Case Description
Student Task Management System is a campus application used by lecturers, students, and administrators to manage course assignments, assignment submission, grading, deadlines, and reporting.

Lecturers can create assignments, set deadlines, review submissions, assign grades, and provide feedback. Students can view assignments, submit files, monitor submission status, and track deadlines. Administrators can manage users, courses, enrollments, and system configuration.

The system must consider usability, security, performance, reliability, and data integrity. In this assignment, the student acts as a Requirements Engineer assisted by AI. AI may generate drafts, but the final requirement baseline must be reviewed, corrected, and approved by the student.

## Initial Business Problem
Assignment-related information can become difficult to manage when lecturers, students, and administrators use separate processes or tools. Lecturers need accurate submission tracking, students need clear deadline and status information, and administrators need consistent user and course data.

The main problem is not only uploading files. The broader problem is maintaining a reliable, traceable, and usable assignment workflow from assignment creation until grading and reporting.

## Initial Project Goals
- Centralize assignment creation, submission, grading, feedback, and reporting.
- Help lecturers monitor submitted, missing, late, graded, and returned assignments.
- Help students track active assignments, deadlines, submission confirmation, and assessment results.
- Help administrators maintain users, courses, enrollments, and assignment-related configuration.
- Ensure requirements are testable, traceable, and separated from unsupported assumptions.

## Stakeholders
| Stakeholder | Role in System | Main Interest |
|---|---|---|
| Lecturer | Creates assignments, monitors submissions, grades work, and gives feedback. | Efficient assignment management and accurate submission visibility. |
| Student | Views assignments, submits files, and checks status, grades, and feedback. | Clear deadlines, reliable submission confirmation, and transparent status. |
| Administrator | Manages users, courses, enrollments, configuration, and reports. | Consistent data, controlled access, and operational reporting. |

## Initial Scope
### In Scope
- Lecturer assignment creation.
- Assignment deadline management.
- Student file submission.
- Submission confirmation and status tracking.
- Lecturer grading and feedback.
- Administrator user management.
- Administrator course and enrollment management.
- Assignment configuration such as file type, file size, and late submission policy.
- Basic reporting for assignment count, submitted count, missing count, and late submission count.

### Out of Scope
- Plagiarism detection.
- Real-time chat between lecturers and students.
- Video conferencing.
- Payment or financial features.
- Full learning material management outside assignment workflow.
- Academic transcript management.

## Known Constraints
- The system must support usability, security, performance, reliability, and data integrity.
- Requirements must be written in a testable and measurable form.
- Functional requirements must be traceable to stakeholder needs or elicitation sources.
- Assumptions that are not directly stated in the case must be labeled explicitly.
- AI-generated output must be reviewed before becoming final output.

## Initial Assumptions
- `ASSUMPTION A-01`: The campus already has lecturer, student, course, and enrollment data.
- `ASSUMPTION A-02`: Users must authenticate before accessing assignment data.
- `ASSUMPTION A-03`: Student submission files are stored by the system and linked to the correct assignment and student.
- `ASSUMPTION A-04`: Late submission policy can be configured by an administrator.
- `ASSUMPTION A-05`: Reporting is limited to assignment and submission activity, not academic transcript reporting.

## Information Boundaries
The assignment case does not provide complete implementation details. Therefore, the following information must not be invented without being labeled as an assumption or open question:

- Authentication method.
- Allowed file types and maximum file size.
- Late submission policy.
- Grade scale or grading rubric.
- Exact performance target.
- Detailed report filters.
- Integration with existing campus systems.

## Open Questions
- `OQ-01`: What authentication method should be used by the campus?
- `OQ-02`: What file types and maximum file size should be accepted for assignment submissions?
- `OQ-03`: Should late submissions be blocked, accepted with a Late status, or controlled per course?
- `OQ-04`: What grade scale should lecturers use?
- `OQ-05`: What exact response time and availability targets are expected?
- `OQ-06`: What report filters are required by lecturers and administrators?

## Requirements Engineering Notes
- Inception output must use this file as the primary case context.
- Elicitation output must connect findings to stakeholder notes or interview answers.
- Specification output must separate functional requirements, non-functional requirements, and business rules.
- Prioritization output must assign MoSCoW priority to every functional requirement.
- Validation output must check clarity, completeness, consistency, feasibility, testability, and traceability.
- Traceability must connect stakeholder, source, requirement, user story, acceptance criteria, and priority.
