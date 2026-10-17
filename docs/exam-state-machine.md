# SecureQuiz — Examination State Machine

## 1. States

### DRAFT
The teacher is preparing the examination.

Questions and settings may be edited according to policy.

### SCHEDULED
The examination has been published and is awaiting its
configured start window.

### LOBBY_OPEN
Eligible students can enter and complete required checks.

### IN_PROGRESS
The examination is active and eligible attempts may submit
answers according to the examination policy.

### PAUSED
The teacher has temporarily paused the examination.

The server must enforce the documented pause behavior.

### ENDED
The examination has ended. Ordinary answer updates are no
longer accepted unless an explicit exception policy applies.

### RESULTS_PUBLISHED
Results are available to permitted users.

Corrections must follow a separately authorized and audited
process.

### CANCELLED
The examination has been cancelled and cannot proceed through
the normal examination lifecycle.

## 2. Allowed Transitions

| Current State | Next State | Actor | Conditions |
|---|---|---|---|
| DRAFT | SCHEDULED | Authorized teacher | Configuration is valid and publication succeeds |
| DRAFT | LOBBY_OPEN | Authorized teacher | Immediate-start policy permits it |
| SCHEDULED | LOBBY_OPEN | Authorized teacher or server policy | Configured entry window permits opening |
| SCHEDULED | CANCELLED | Authorized teacher | Cancellation is permitted |
| LOBBY_OPEN | IN_PROGRESS | Authorized teacher or documented start policy | Examination is eligible to start |
| LOBBY_OPEN | CANCELLED | Authorized teacher | Cancellation is permitted |
| IN_PROGRESS | PAUSED | Authorized teacher | Pause is permitted |
| IN_PROGRESS | ENDED | Authorized teacher or server policy | End conditions are satisfied |
| PAUSED | IN_PROGRESS | Authorized teacher | Resume is permitted |
| PAUSED | ENDED | Authorized teacher | End is permitted |
| ENDED | RESULTS_PUBLISHED | Authorized teacher or publication policy | Grading and publication checks pass |

Any transition not listed above is rejected.

## 3. Transition Rules

- The backend validates every transition.
- The frontend cannot directly change authoritative state.
- Only authorized actors can initiate permitted transitions.
- Important transitions record actor, time, and relevant context.
- Invalid transitions return a controlled error.
- Repeated requests must not produce contradictory states.
- Cancellation and pause behavior must be explicit.
- Results are not published until the publication rules pass.

## 4. Pause Policy

The MVP must document whether a pause freezes examination
timers or merely prevents new answers.

The server must enforce the chosen policy consistently.

The frontend must not independently decide how much time
remains.

## 5. Deadline Policy

The server is authoritative for examination deadlines.

Changing the student's device clock cannot extend an attempt.

Late answers must follow the documented deadline policy.

## 6. Invalid Transition Examples

- Starting a cancelled examination.
- Publishing results before the examination has ended.
- Resuming an examination that was never paused.
- Opening a scheduled examination before its permitted window.
- Editing a published examination without the permitted
  versioning or correction process.

## 7. Required Verification

Test valid and invalid transitions, unauthorized transitions,
repeated transition requests, and pause/end behavior.

The resulting state must remain consistent after failed requests.