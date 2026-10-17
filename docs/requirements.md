# SecureQuiz — Product Requirements

## 1. Problem Statement

Online examinations require controlled access, reliable answer
submission, consistent grading, and useful visibility into
examination sessions.

Teachers need to manage examinations, monitor participation,
review relevant events, and access results. Students need a
reliable way to join eligible examinations, answer questions,
and submit their attempts.

SecureQuiz aims to provide these capabilities through a
browser-based examination platform with server-side
authorization, persistent answers, live monitoring, and
auditable examination records.

## 2. Product Goal

Build a responsive browser-based platform that supports the
examination lifecycle, from quiz creation through result
publication.

The backend is responsible for authorization, exam deadlines,
answer validation, grading, risk assessment, and audit records.

## 3. Primary Users

### Teacher

Teachers can:
- Create and manage their own quizzes.
- Manage classrooms and student eligibility.
- Schedule, start, pause, and end examinations.
- Monitor examination progress.
- Review recorded events and incidents.
- Access results and authorized reports.

Teachers cannot access another teacher's private resources
unless explicitly authorized.

### Student

Students can:
- Join eligible examinations.
- Complete required entry checks.
- View permitted examination questions.
- Save and update their own answers while permitted.
- Submit their own examination attempts.
- View results when publication policy permits.

Students cannot access another student's attempts, private
answer keys, or teacher-only monitoring information.

### Administrator

Administrators can:
- Manage institution-level accounts and policies.
- Perform explicitly authorized administrative operations.
- Access operational records permitted by their role.

Administrative actions must follow authorization rules and
be recorded where appropriate.

## 4. Core Workflows

### Teacher workflow

1. Authenticate.
2. Create or select a classroom.
3. Create a quiz and its questions.
4. Configure examination settings.
5. Publish the quiz and configure student access.
6. Start and monitor an examination.
7. Review incidents and participant status.
8. Grade and publish results.
9. Access permitted reports and audit records.

### Student workflow

1. Open an examination invitation.
2. Authenticate or otherwise satisfy the configured
   identity and eligibility requirements.
3. Complete the required entry checks.
4. Join the examination.
5. Answer questions and save progress.
6. Submit before the server-authoritative deadline.
7. View permitted results after publication.

## 5. System Responsibilities

The backend must:
- Authenticate users and enforce authorization.
- Validate all protected operations.
- Protect answer keys and private student data.
- Enforce examination and attempt state transitions.
- Enforce deadlines independently of the client clock.
- Validate and persist answers.
- Prevent duplicate finalization.
- Validate and deduplicate security events.
- Calculate explainable risk assessments.
- Maintain relevant audit records.

## 6. Initial Question Type

The initial MVP supports single-answer multiple-choice
questions with options, marks, and private answer keys.

Additional question types are deferred.

## 7. Initial Platform

The first release is a responsive web application.

A dedicated Android application is not required for the MVP.

## 8. Success

The MVP is successful when the core teacher and student
workflows work reliably, critical security tests pass,
results are correct, and the application can be deployed
and recovered using documented procedures.

## 9. Limitations

Browser-observable events are incomplete signals.

The system must not claim that a focus change, fullscreen
exit, clipboard event, QR response, or risk score definitively
proves cheating or exact physical location.