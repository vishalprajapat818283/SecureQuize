# SecureQuiz — MVP Scope and Non-Goals

## 1. MVP Objective

Deliver a reliable browser-based examination platform with
secure access, persistent answers, live teacher monitoring,
grading, and auditable records.

## 2. Must-Have Features

### Authentication and authorization
- Teacher authentication.
- Student identity and eligibility checks.
- Administrator permissions where required.
- Server-side role and resource-ownership enforcement.

### Classrooms
- Classroom creation and management.
- Student enrollment and eligibility.
- Protection against duplicate membership.

### Quiz authoring
- Quiz creation and configuration.
- Single-answer MCQ questions.
- Options, marks, and private answer keys.
- Controlled publication and editing.

### Invitations and examination entry
- Random invitation tokens.
- Invitation expiry and revocation.
- Student eligibility validation.
- Waiting-room or entry workflow.

### Examination engine
- Attempt lifecycle management.
- Server-authoritative deadlines.
- Answer autosave.
- Safe submission and duplicate-submission handling.
- Recovery after refresh or reconnection.

### Security events and risk assessment
- Collection of supported browser-observable events.
- Backend validation and event deduplication.
- Explainable, rule-based risk assessment.
- Separation of risk, connection health, and presence status.

### Live monitoring
- Live participant status.
- Examination progress.
- Authorized real-time updates.
- Incident timeline.
- Audited teacher actions.

### Classroom presence
- Short-lived QR challenge.
- Challenge expiry and replay protection.
- Teacher confirmation or exception fallback.

### Results and auditing
- Automatic MCQ grading.
- Controlled result publication.
- CSV export.
- Incident reports.
- Audit records.

### Release readiness
- Automated and manual testing.
- Supported-browser documentation.
- Secure deployment configuration.
- Backup and recovery procedures.

## 3. Explicit Non-Goals

The MVP will not promise:

- Guaranteed prevention of cheating.
- Definitive automatic determination that a student cheated.
- Detection of every new tab, external application, screenshot,
  second device, or source of outside assistance.
- Exact physical-location proof from browser events or IP data.
- Universal BLE scanning from ordinary browsers.
- Continuous webcam or microphone monitoring.
- AI-based cheating classification.
- A dedicated Android application before the web MVP is reliable.
- Microservices before there is a demonstrated need.

## 4. Deferred Features

Consider these after the MVP:

- Additional question types.
- Question pools and balanced randomization.
- Institutional single sign-on.
- Network-side presence integration.
- BLE integration through a suitable native application.
- Advanced examination-environment integration.
- Analytics and question-quality reports.
- Additional infrastructure for measured scaling needs.
- Dedicated mobile application.

## 5. Scope Change Rule

Every proposed feature must have:
- A clearly stated user problem.
- A reason it is needed.
- Dependencies.
- Acceptance criteria.
- A test plan.
- A release target.

Features that do not contribute to the MVP acceptance criteria
must remain in the backlog.