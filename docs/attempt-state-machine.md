# SecureQuiz — Attempt State Machine

## 1. States

### CREATED
The attempt exists but the student has not started answering.

### READY
Required entry checks have passed and the attempt is ready
to begin.

### IN_PROGRESS
The student can answer questions according to the examination
policy and server-authoritative deadline.

### SUBMITTED
The student's final submission has been accepted.

### AUTO_SUBMITTED
The server finalized the attempt under the automatic-submission
policy, typically when the deadline expired.

### ABANDONED
The attempt ended without a valid submission under the
documented abandonment policy.

### INVALIDATED
An authorized action invalidated the attempt. The action,
actor, time, and reason must be recorded.

## 2. Allowed Transitions

| Current State | Next State | Conditions |
|---|---|---|
| CREATED | READY | Required entry checks pass |
| CREATED | ABANDONED | Documented abandonment policy applies |
| READY | IN_PROGRESS | The attempt is permitted to start |
| READY | ABANDONED | Documented abandonment policy applies |
| IN_PROGRESS | SUBMITTED | A valid final submission is accepted before the deadline |
| IN_PROGRESS | AUTO_SUBMITTED | Automatic finalization policy applies |
| IN_PROGRESS | ABANDONED | Documented abandonment policy applies |
| CREATED | INVALIDATED | Authorized invalidation |
| READY | INVALIDATED | Authorized invalidation |
| IN_PROGRESS | INVALIDATED | Authorized invalidation |

Unlisted transitions are rejected.

Terminal states are not reopened through ordinary requests.

## 3. Answer Saving

- Answers may be changed only while the attempt permits it.
- The backend validates the question and submitted option.
- The answer must belong to the applicable examination version.
- A successful save is acknowledged by the server.
- The frontend must not display "Saved" before confirmation.
- Retries must not corrupt a newer answer.
- Stale updates must follow documented version or ordering rules.

## 4. Deadline Enforcement

- The server determines the authoritative deadline.
- The client clock is informational only.
- Ordinary answer updates are rejected after the deadline.
- Late queued requests follow the explicit late-answer policy.
- Automatic finalization must be safe to retry.

## 5. Duplicate Submission

If the same submission request is repeated, the system must
not create conflicting final outcomes.

A previously finalized attempt must not accept ordinary
answer updates.

Concurrent submission requests must be handled safely.

## 6. Refresh and Reconnection

After a browser refresh or network reconnection:

1. The client requests the current attempt state.
2. The server returns the authorized authoritative state.
3. The client reconciles pending local changes according
   to the documented conflict policy.
4. The server enforces the deadline and attempt state.
5. The UI reports unsaved or rejected changes accurately.

A local draft is not authoritative proof that the server
accepted an answer.

## 7. Invalidation

Invalidation requires authorization.

Record:
- The actor.
- The target attempt.
- The timestamp.
- The reason.
- Any related incident or administrative action.

## 8. Required Verification

Test:
- Refresh during an active attempt.
- Network loss during answer saving.
- Reconnection after the deadline.
- Repeated submissions.
- Concurrent submissions.
- Submission after finalization.
- Unauthorized invalidation.
- Automatic finalization at the deadline.