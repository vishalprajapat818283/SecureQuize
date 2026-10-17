# SecureQuiz — Security Model

## 1. Security Principles

- The backend is authoritative for protected operations.
- Authentication does not automatically grant resource access.
- Authorization is checked on every protected operation.
- Client-supplied user IDs and role claims are not trusted.
- Private answer keys are never exposed through student APIs.
- Deadlines and grading rules are enforced server-side.
- Important state changes are recorded for auditing.
- Security events are validated before acceptance.

## 2. Authentication and Authorization

Every protected API operation must authenticate the caller
and check the caller's permissions.

Resource access must respect ownership and membership.

Examples:
- A teacher cannot access another teacher's private quiz.
- A student cannot access another student's attempt.
- A student cannot retrieve answer keys.
- An unauthorized user cannot join a private examination.
- Administrative privileges cannot be self-assigned by a client.

Protected Socket.IO connections and room subscriptions must
also enforce authorization.

## 3. Answer Security

The server stores the authoritative answer key.

Student-facing responses contain only the information needed
to answer questions.

The backend validates that submitted answers refer to valid
questions and options belonging to the applicable examination.

Grading is performed using trusted server-side data.

## 4. Examination Integrity

The server determines:
- Whether an examination is open.
- Whether an attempt can start.
- Whether an answer can be changed.
- Whether a submission is accepted.
- Whether a deadline has expired.
- Whether an attempt has already been finalized.

Client clocks and frontend controls are not authoritative.

Duplicate requests must not produce conflicting final outcomes.

## 5. Browser-Observable Events

The platform may record supported events such as:
- Page visibility changes.
- Window focus changes.
- Fullscreen exits.
- Supported clipboard interactions.
- Connection loss and reconnection.

These events are incomplete signals.

A focus change does not prove cheating.
A fullscreen exit does not lock or compromise the operating system.
A clipboard restriction does not prevent all text extraction.
Connection loss is an operational event, not proof of misconduct.

## 6. Risk Assessment

The backend determines accepted event severity and risk points.

The client cannot authoritatively supply the risk score.

Events must be validated, deduplicated, and rate-limited.

Risk assessments must retain enough information to explain
their contributing events and applicable policy version.

A risk score prioritizes review; it does not prove misconduct.

Serious consequences require an appropriate authorized
review process.

## 7. Classroom Presence

A short-lived QR challenge can support a presence workflow.

A QR response does not prove exact physical location.
A QR code can be photographed or shared.

Challenges must expire and have replay protections.

Teacher confirmation and documented exception handling
must be available where required.

IP addresses and network information must not be represented
as definitive proof of classroom presence.

## 8. Privacy

Collect only the data needed for documented purposes.

Do not enable continuous webcam or microphone recording
as part of the initial MVP.

Document access permissions and retention rules for
student data, answers, security events, and reports.

Do not put passwords, tokens, answer keys, or unnecessary
student data into logs.

## 9. Incident Review

The teacher dashboard should distinguish:
- Observed events.
- Connection problems.
- Presence verification outcomes.
- Calculated risk indicators.
- Human review decisions.
- Actions taken and their reasons.

The interface must not present an inference as an observed fact.

## 10. Security Verification

Tests must cover:
- Unauthenticated API requests.
- Unauthorized resource access.
- Cross-student and cross-teacher access.
- Answer-key confidentiality.
- Invalid or expired invitations.
- Server-authoritative deadlines.
- Duplicate submissions.
- Duplicate security events.
- Unauthorized socket-room subscriptions.