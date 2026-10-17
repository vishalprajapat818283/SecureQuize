# SecureQuiz — Role and Permission Matrix

## Roles

- ADMIN
- TEACHER
- STUDENT

## Permission Matrix

| Operation | ADMIN | TEACHER | STUDENT |
|---|---|---|---|
| Manage institution policies | Yes, if authorized | No | No |
| Manage institution accounts | Yes, if authorized | No | No |
| Create a classroom | According to policy | Yes | No |
| Manage own classroom | According to policy | Yes | No |
| Enroll eligible students | According to policy | Yes, within own classroom | No |
| Create a quiz | According to policy | Yes | No |
| Edit own unpublished quiz | According to policy | Yes | No |
| Edit another teacher's quiz | Explicit authorization required | No | No |
| Publish an examination | According to policy | Yes, within own resources | No |
| Join an eligible examination | No automatic student access | No automatic student access | Yes |
| View own examination questions | No automatic access | No automatic access | Yes, during permitted attempt |
| View answer keys | Explicit operational policy only | Yes, for authorized quizzes | No |
| Save own answers | No | No | Yes, during permitted attempt |
| Read another student's answers | Explicit authorization required | Only through permitted monitoring or grading workflows | No |
| Submit own attempt | No | No | Yes |
| View permitted results | According to policy | Yes, for authorized exams | Yes, when permitted |
| Review security incidents | According to policy | Yes, for authorized examinations | No |
| Perform audited administrative actions | Yes, within granted permissions | Only explicitly granted actions | No |

## Authorization Rules

1. Every protected resource must have an ownership or
   membership rule.
2. The backend must enforce the rule on every protected request.
3. Hiding a frontend button is not authorization.
4. A user cannot gain access by changing an ID in a URL or
   request body.
5. Administrator privileges must be explicit and limited.
6. Administrative and teacher actions must be audited where
   appropriate.
7. Student-facing APIs must not expose answer keys or
   unauthorized student information.

## Resource Boundaries

- Teachers are restricted to their authorized classrooms,
  quizzes, sessions, and results.
- Students are restricted to their own attempts and answers.
- Institution-level access follows explicit policy.
- Real-time room subscriptions follow the same authorization
  rules as protected API endpoints.