# SecureQuiz — MVP Release Checklist

A criterion passes only when its required test has been run
and the result has been inspected.

## 1. Authentication and Authorization

- [ ] Protected APIs reject unauthenticated requests.
- [ ] Users cannot access resources outside their permissions.
- [ ] Teachers cannot modify another teacher's private quiz.
- [ ] Students cannot access another student's attempt.
- [ ] Students cannot retrieve private answer keys.
- [ ] Privileged roles cannot be self-assigned during registration.

Evidence:
Record test names, results, and relevant commit references.

## 2. Database Integrity

- [ ] Required relationships have appropriate foreign keys.
- [ ] Duplicate classroom membership is prevented.
- [ ] Answers reference valid questions in the applicable exam.
- [ ] Duplicate finalization does not create conflicting outcomes.
- [ ] Required transactions preserve consistent state.

Evidence:
Record migration and database test results.

## 3. Examination Workflow

- [ ] A teacher can create and publish a valid quiz.
- [ ] An eligible student can join an examination.
- [ ] Expired and revoked invitations are rejected.
- [ ] Invalid examination-state transitions are rejected.
- [ ] The server enforces the examination deadline.
- [ ] Valid answers are saved and recovered correctly.
- [ ] Repeated submissions are handled safely.
- [ ] MCQ grading produces the expected result.

Evidence:
Record integration and end-to-end test results.

## 4. Security Events and Monitoring

- [ ] Supported events are validated by the backend.
- [ ] Repeated event identifiers do not duplicate risk points.
- [ ] Client-supplied risk scores are not authoritative.
- [ ] Socket connections and room subscriptions are authorized.
- [ ] Reconnection restores monitoring from server state.
- [ ] Incident records distinguish observed events from inference.

Evidence:
Record security and real-time test results.

## 5. Presence Verification

- [ ] QR challenges expire according to policy.
- [ ] Replayed challenges are rejected.
- [ ] Presence outcomes and exceptions are recorded.
- [ ] The interface does not claim that QR verification
      proves exact physical location.

Evidence:
Record presence verification test results.

## 6. Reliability

- [ ] Failed answer saves are not falsely shown as successful.
- [ ] Refresh and reconnection preserve authorized server state.
- [ ] Concurrent submissions produce one consistent outcome.
- [ ] Database or backend failures are handled safely.
- [ ] Backup and recovery procedures have been tested.

Evidence:
Record failure-injection and recovery test results.

## 7. Browser Compatibility and Privacy

- [ ] Supported browsers are tested on target devices.
- [ ] Limitations are documented.
- [ ] Sensitive data is excluded from inappropriate logs.
- [ ] Access and retention policies are documented.

Evidence:
Record browser/device combinations and privacy checks.

## 8. Deployment

- [ ] Production secrets are configured outside source control.
- [ ] HTTPS and production origins are configured.
- [ ] Database migrations succeed in the deployment environment.
- [ ] Health checks pass.
- [ ] The core examination workflow succeeds after deployment.
- [ ] Recovery procedures are documented and rehearsed.

Evidence:
Record deployment checks and the tested release commit.

## Release Decision

Release is permitted only when all required MVP acceptance
criteria have passed.

Any accepted limitation or deferred feature must be documented.

Release version:
Date:
Commit:
Reviewer:
Outstanding issues: