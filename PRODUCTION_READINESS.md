# Bright Eyes — Production Readiness Roadmap

Bright Eyes is currently a working Flutter/Firebase prototype. This roadmap captures the concrete engineering work required before treating it as a production clinic application.

## 1. Access control and data boundaries

- Define explicit roles for patient, doctor, clinic staff, and administrator.
- Replace UI-only restrictions with server-enforced authorization rules.
- Review Firestore rules so users can only access records required by their role.
- Separate patient-visible report fields from editable clinical fields.
- Add authorization tests for allowed and denied reads/writes.

**Done when:** every sensitive collection has an explicit access rule and automated tests cover representative allow/deny cases.

## 2. Appointment integrity

- Move final booking validation to a trusted backend transaction or Cloud Function.
- Enforce uniqueness for clinic/date/time-slot combinations.
- Prevent race conditions when two patients select the same slot simultaneously.
- Define cancellation and rescheduling rules centrally.
- Add tests for simultaneous booking attempts and stale availability data.

**Done when:** the backend, not only the UI, guarantees that a slot cannot be double-booked.

## 3. Clinical data safety

- Define which fields are clinical records versus general profile data.
- Add change history/audit events for edits to examination results.
- Record who changed a clinical value and when.
- Prevent patients from modifying clinician-authored findings.
- Avoid storing unnecessary sensitive data.

**Done when:** clinical edits are attributable, traceable, and protected by role-based permissions.

## 4. Privacy and configuration

- Keep Firebase configuration, service credentials, signing material, and private environment values outside the public repository.
- Document environment setup without publishing secrets.
- Establish a process for credential rotation if a key is exposed.
- Define retention/deletion behavior for accounts and associated data.
- Review UAE healthcare/privacy requirements before production deployment.

**Done when:** the application can be deployed from documented configuration while secrets remain outside source control.

## 5. Reliability and observability

- Add structured error reporting for authentication, booking, and data-write failures.
- Track failed bookings and unexpected permission errors.
- Add user-safe fallback states for network loss and Firebase outages.
- Define backup/export and restore procedures for critical application data.
- Add basic operational health checks for backend services.

**Done when:** common failures are visible to maintainers and users receive clear recovery paths.

## 6. Testing baseline

Prioritize tests around the workflows that can cause real user harm or data inconsistency:

1. authentication and role routing;
2. appointment availability and conflict prevention;
3. create/cancel/reschedule flows;
4. clinician editing versus patient read-only access;
5. validation of right/left-eye report fields;
6. offline/retry behavior for critical writes.

Suggested layers:

- unit tests for validation and scheduling logic;
- widget tests for critical Flutter screens;
- Firebase emulator tests for security rules;
- integration tests for end-to-end booking and report workflows.

## 7. Release checklist

Before any production-like release:

- [ ] security rules reviewed and tested
- [ ] secrets scan completed
- [ ] test suite passing
- [ ] production Firebase project separated from development
- [ ] crash/error monitoring enabled
- [ ] privacy policy and consent flows reviewed
- [ ] backup/restore procedure tested
- [ ] release notes prepared
- [ ] rollback path documented

## Recommended implementation order

1. **Authorization + Firestore rules** — highest priority because all other features depend on correct data boundaries.
2. **Server-side booking integrity** — removes the main scheduling race-condition risk.
3. **Automated tests** — locks in the behavior of the first two hardening steps.
4. **Audit trail for clinical edits** — improves accountability of sensitive changes.
5. **Monitoring, backups, and release process** — makes the system maintainable after deployment.

This roadmap intentionally avoids claiming regulatory compliance. Formal production use would require a dedicated legal/security review appropriate to the deployment environment and the data being handled.
