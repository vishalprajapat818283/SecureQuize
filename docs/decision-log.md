# SecureQuiz — Architecture Decision Log

This document records important technical and product decisions.

A decision should include its date, context, rationale, and
conditions that would justify revisiting it.

## D001 — Modular Monolith

Status: Accepted

Decision:
Use a modular monolith for the initial MVP.

Rationale:
The application needs clear domain boundaries without the
operational complexity of independently deployed services.

Revisit when:
Measured scaling or deployment requirements justify a change.

## D002 — Frontend Stack

Status: Accepted

Decision:
Use React, Vite, Tailwind CSS, React Router, and Axios.

Rationale:
These tools support a responsive web application with
separate teacher and student experiences.

## D003 — Backend Stack

Status: Accepted

Decision:
Use Node.js and Express.

Rationale:
The backend will expose APIs and coordinate authentication,
examinations, answers, security events, results, and auditing.

## D004 — Relational Database

Status: Accepted

Decision:
Use MySQL with Prisma.

Rationale:
Users, classrooms, quizzes, questions, attempts, answers,
results, and audit records have relational integrity requirements.

## D005 — Real-Time Communication

Status: Accepted

Decision:
Use Socket.IO for live examination monitoring.

Rationale:
Teachers need live participant updates and incident visibility.

Security requirement:
Every protected connection and room subscription must
be authorized.

## D006 — Authentication and Password Storage

Status: Accepted

Decision:
Use Argon2id for password hashing.

Use a secure session/refresh design with appropriate
production cookie settings and CSRF protection when using
cookie-based authentication.

## D007 — Request Validation

Status: Accepted

Decision:
Use Zod or Joi to validate API inputs.

Rationale:
Malformed or unauthorized data must be rejected at the
API boundary.

The specific validation library will be confirmed during P01.

## D008 — Testing

Status: Accepted

Decision:
Use Vitest, Supertest, and Playwright for appropriate
unit, API integration, and end-to-end testing.

Rationale:
The project needs automated verification of backend rules
and complete examination workflows.

## D009 — Security Events

Status: Accepted

Decision:
Use explainable, rule-based risk assessment for the MVP.

Rationale:
Accepted events and risk scores must be auditable and
understandable by teachers.

Constraint:
A risk score is not proof of cheating.

## D010 — Classroom Presence

Status: Accepted

Decision:
Start with short-lived QR challenges and teacher fallback.

Rationale:
The browser cannot universally scan BLE beacons or reliably
prove exact physical location.

## D011 — Initial Deployment

Status: Proposed

Decision:
Evaluate Render and a managed MySQL provider for the
initial deployment.

Before deployment:
Verify current pricing, database availability, connection
requirements, backups, and operational constraints.

## D012 — Scope Control

Status: Accepted

Decision:
Defer optional AI, webcam monitoring, BLE integration,
native applications, and premature microservices.

Rationale:
The initial priority is a reliable, tested web MVP.

## Decision Change Procedure

When changing an accepted decision:

1. Record the problem with the current decision.
2. Evaluate alternatives.
3. Document the reason for the change.
4. Identify affected requirements and implementation tasks.
5. Update the relevant documentation.
6. Record the decision date and new status.