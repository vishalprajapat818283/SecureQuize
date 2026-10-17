# SecureQuize

SecureQuiz is a browser-based examination platform for managing
online assessments, student examination attempts, classroom
presence signals, and teacher monitoring.

## Project Goals

- Provide controlled access to examinations.
- Allow teachers to create and manage quizzes.
- Allow eligible students to answer and submit examinations.
- Save answers reliably and enforce server-side deadlines.
- Record supported browser events.
- Provide explainable risk indicators for teacher review.
- Maintain examination results and audit records.

## Technology Stack

- Frontend: React, Vite, Tailwind CSS
- Backend: Node.js, Express
- Database: MySQL, Prisma
- Real-time communication: Socket.IO

## Architecture

The initial release will use a modular monolith.

Business rules, authorization, examination deadlines, and
answer validation will be enforced by the backend.

## Development Approach

Development follows a phased roadmap with explicit tests and
acceptance criteria.

A task is complete only after its implementation and required
verification have passed.

## Current Status

Project definition and repository setup.

No application features are claimed to be implemented yet.

## Documentation

See [Documentation Index](docs/README.md) for the project
requirements, architecture, security model, database design,
testing strategy, and deployment documentation.