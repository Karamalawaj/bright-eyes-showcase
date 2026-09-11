# Bright Eyes

> Ophthalmology clinic workflow prototype · Flutter / Firebase · 2024

Bright Eyes models the core workflow of a single ophthalmology clinic with separate patient and clinic/doctor experiences, including onboarding, scheduling, registered-patient management, and structured right/left-eye examination reports.

## Product Preview

<div align="center">
  <img width="31%" src="https://github.com/user-attachments/assets/c52b525a-c9bb-40d8-994a-d767ad626c10" />
  <img width="31%" src="https://github.com/user-attachments/assets/e71ddd1e-0bc0-4ac7-99f6-3c1386d03499" />
  <img width="31%" src="https://github.com/user-attachments/assets/7c506f9e-b4d8-4666-bc40-fd82177221e4" />
</div>

<br>

<div align="center">
  <img width="31%" src="https://github.com/user-attachments/assets/6671f503-91f8-4d94-86f6-9a637a66b69f" />
  <img width="31%" src="https://github.com/user-attachments/assets/fc9321b7-4d87-4809-9b46-4be662e9b47c" />
  <img width="31%" src="https://github.com/user-attachments/assets/62908be7-d96b-4715-bebf-f10a292a5e09" />
</div>

<details>
<summary><strong>View 4 more screenshots</strong></summary>
<br>
<div align="center">
  <img width="31%" src="https://github.com/user-attachments/assets/6a69c2c6-ad33-40dd-96a5-abb42957b8c8" />
  <img width="31%" src="https://github.com/user-attachments/assets/6bf0edc2-d22f-435c-b11d-cae115755cb6" />
  <img width="31%" src="https://github.com/user-attachments/assets/41a34cbe-ed7f-4445-8a10-100424e74953" />
</div>
<br>
<div align="center">
  <img width="31%" src="https://github.com/user-attachments/assets/8d7a921d-aa69-424a-bd91-f82655c02147" />
</div>
</details>

## Patient Experience
- Account registration and authentication
- Patient profile setup
- Clinic-opened appointment dates
- Appointment time selection with conflict prevention
- Appointment tracking and cancellation
- Read-only access to structured eye-examination results
- Eye-health awareness content

## Clinic / Doctor Experience
- Controlled clinic/doctor access path
- Registered-patient management
- Scheduling and appointment administration
- Structured right/left-eye examination fields
- Editable clinical values with patient read-only access

## Engineering Focus
- Cross-platform UI built with Flutter and Dart
- Firebase Authentication for patient account flows
- Cloud Firestore for persistent application data
- GetX for navigation and controller/state usage
- Appointment conflict checks around configured booking intervals
- Structured ophthalmology report data for both eyes
- Separation between editable clinic workflows and read-only patient report access

## Tech Stack
`Flutter` · `Dart` · `Firebase Authentication` · `Cloud Firestore` · `GetX` · `intl` · `Awesome Dialog` · `Animated Text Kit` · `Staggered Animations` · `Flutter TypeAhead`

## Architecture Snapshot

```text
Patient UI                    Clinic / Doctor UI
    │                                │
    └──────────────┬─────────────────┘
                   ▼
             Flutter / GetX
                   │
       ├── Authentication Flows
       ├── Appointment Scheduling
       ├── Patient Management
       └── Structured Eye Reports
                   │
                   ▼
          Firebase Services
```

This public architecture intentionally stays high-level and excludes credentials, security rules, private configuration, and unnecessary implementation detail.

## Production Readiness

The prototype now has a concrete [production-readiness roadmap](PRODUCTION_READINESS.md) covering authorization, Firestore security, appointment race-condition prevention, clinical auditability, privacy/configuration, testing, monitoring, backups, and release checks. It is an engineering plan rather than a claim of healthcare or regulatory compliance.

## Project Scope
Bright Eyes is a working learning/portfolio prototype rather than a production medical-record system. Production use would require hardened authorization, stronger backend/security controls, and healthcare-specific compliance review.

The later **HealHub** project expands this direction into broader multi-clinic and multi-role healthcare workflows.

## Project Status
**Working prototype · Private source · Portfolio showcase**

## Source Policy
**Portfolio showcase only. The production/full source repository is private and protected. Source code, credentials, private configuration, and sensitive implementation details are intentionally not published.**

## Rights
© Karam Alawaj. All rights reserved. No license is granted to copy, redistribute, reuse, or republish proprietary source or implementation details.
