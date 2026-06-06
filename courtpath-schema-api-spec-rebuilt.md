# CourtPath Schema and API Specification — Rebuilt

## Purpose

This rebuilt specification turns the original schema draft into a tighter implementation contract for CourtPath’s first production-grade workflow: an Illinois-first, matter-centered court-navigation platform for public users and professional support teams. It keeps the original legal and trust boundaries intact while making the system more usable for engineering, architecture review, and clickable technical walkthroughs. [file:1181][file:1116][file:1171][file:1164]

## System stance

CourtPath should be built around one canonical object: the **matter**. The PRD defines the product as a trust-centered workflow that organizes deadlines, documents, alerts, and escalation around a single matter workspace, and the developer package reinforces that the matter record is the system anchor rather than isolated forms or chatbot sessions. [file:1116][file:1171]

The schema therefore should prioritize clean relationships, auditable state transitions, visible source metadata, and strict role boundaries. The wireframe package also requires every screen to answer what is happening, what is official, and what should happen next, which means the data model must preserve provenance and actionability at every layer. [file:1163][file:1181]

## Architecture contract

The original spec already assumes PostgreSQL, object storage, a REST API, background jobs, and role-based authorization, and those assumptions remain sound for the first build. [file:1181] The roadmap and developer package support the same direction by defining a staged Illinois-first release, shared matter model, background processing, and structured queues for professional workflows. [file:1164][file:1171]

Recommended implementation contract:

- PostgreSQL as system of record for structured entities and audit trails. [file:1181][file:1171]
- Object storage for user uploads, generated exports, and filing packet assets. [file:1181][file:1171]
- REST endpoints first, with typed request/response contracts and predictable resource shapes. [file:1181]
- Background jobs for OCR, exports, reminders, classification, and status sync. [file:1181][file:1171]
- Role-based authorization aligned to public, professional, org-manager, and admin modes. [file:1181]

## Core domain model

The original schema identifies the main tables as users, organizations, matters, matter_parties, matter_events, documents, form_templates, filing_attempts, alerts, research_notes, escalations, and audit_logs. That is the correct first-pass backbone because it matches the PRD modules, the developer package entity list, and the roadmap’s matter-centered information architecture. [file:1181][file:1116][file:1171][file:1164]

The most important design rule is this: every user-visible workflow should resolve back to a matter, and every consequential state change should produce an audit trail. The developer package states this explicitly for user-visible state, and the schema already requires audit coverage for creation, status changes, uploads, filings, escalations, exports, source changes, and assignments. [file:1171][file:1181]

### Canonical entities

| Entity | Purpose | Key implementation note |
|---|---|---|
| `users` | Identity and access context | Must support direct public users and staff/org roles. [file:1181] |
| `organizations` | Legal-aid, law-firm, navigator, or business account scope | Needed for team workflows and jurisdiction filtering. [file:1181] |
| `matters` | Central record for the user’s court workflow | Must remain the primary object for dashboards, queues, filings, alerts, and exports. [file:1181][file:1171] |
| `matter_parties` | Named parties attached to a matter | Required for legible summaries and consultation exports. [file:1181] |
| `matter_events` | Timeline and activity log | Maps directly to the PRD timeline module and wireframe docket history. [file:1116][file:1163][file:1181] |
| `documents` | Uploaded, official, generated, and support files | Must preserve source type, filing state, signature state, and storage metadata. [file:1181] |
| `form_templates` | Form/source routing table | Needed to map workflows to official forms, guided forms, and explainers. [file:1181][file:1171] |
| `filing_attempts` | Submission cycles and rejection handling | Critical for correction loops and clerk-response state. [file:1181][file:1171] |
| `alerts` | Deadline, blocker, and review prompts | Supports the PRD alerts module and roadmap monitoring layer. [file:1116][file:1164][file:1181] |
| `research_notes` | Safe research support and issue spotting | Must remain clearly non-predictive and reviewable. [file:1181][file:1171] |
| `escalations` | Human-help routing and support handoff | Required for legal-aid, attorney, language, accessibility, or internal review routing. [file:1181] |
| `audit_logs` | Append-only accountability ledger | Required for regulated, trust-sensitive behavior. [file:1181][file:1171] |

## Relationship rules

The spec should make the relational contract more explicit than the original draft. The original document and developer package already imply the core one-to-many structure, but engineering handoff improves when those relationships are stated unambiguously. [file:1181][file:1171]

Recommended relationship rules:

- One `organization` has many `users`. [file:1181]
- One `public_user` can own many `matters`. [file:1181]
- One `matter` can have zero or one handling `organization`, and zero or one currently assigned professional user. [file:1181]
- One `matter` has many `matter_parties`, `matter_events`, `documents`, `alerts`, `research_notes`, `escalations`, and `filing_attempts`. [file:1181][file:1171]
- One `filing_attempt` can include many `documents`, but a document should only point to one active filing attempt at a time in the MVP. [file:1181]
- One `audit_log` row may reference a matter-scoped entity or a platform-level admin action. [file:1181]

## Status model

The matter lifecycle in the original spec is already strong: `draft`, `intake_in_progress`, `ready_for_forms`, `packet_in_review`, `ready_to_file`, `filed`, `accepted`, `rejected`, `resubmission_needed`, `escalated`, and `closed`. These states line up with the PRD release logic and the developer package’s self-represented and professional review workflows. [file:1181][file:1116][file:1171]

The key improvement is to treat statuses as workflow contracts rather than labels. Each transition should have an allowed actor set, a required trigger, an optional side effect, and a mandatory audit event. [file:1181][file:1171]

### Matter transition rules

| From | To | Typical trigger | Notes |
|---|---|---|---|
| `draft` | `intake_in_progress` | Matter shell created | Public or staff user begins intake. [file:1181] |
| `intake_in_progress` | `ready_for_forms` | Intake completion endpoint succeeds | Should generate deadlines/alert candidates. [file:1181] |
| `ready_for_forms` | `packet_in_review` | Required docs exist and user requests review | Can be self-initiated or staff-assisted. [file:1181][file:1171] |
| `packet_in_review` | `ready_to_file` | Readiness engine returns no blockers | Requires packet completeness and signature logic. [file:1181] |
| `ready_to_file` | `filed` | Filing attempt submitted | System should create filing attempt and audit event. [file:1181] |
| `filed` | `accepted` | Clerk/processing confirmation | Public user should not directly set this state. [file:1181] |
| `filed` | `rejected` | Rejection received | Must auto-create corrective tasks/alerts. [file:1181] |
| `rejected` | `resubmission_needed` | Correction branch opened | Keeps rejection visible without losing progress. [file:1181][file:1171] |
| any active state | `escalated` | Human-help threshold reached | Must preserve reason and escalation record. [file:1181] |
| any terminal state | `closed` | Matter completed or archived | Should remain queryable and auditable. [file:1181] |

## Trusted-source model

This is one of the strongest parts of the CourtPath concept and it should stay central. The wireframe package requires strong visual separation between official court material, guidance content, user uploads, and AI-generated assistance, and the schema/API spec reflects that through `source_type`, `source_ref`, trusted URLs, and review-state expectations. [file:1163][file:1181]

Every user-visible substantive item should carry provenance fields, because CourtPath’s trust model depends on users being able to tell official content from interpretive or generated content. The PRD, roadmap, and developer package all reinforce this same boundary. [file:1116][file:1164][file:1171][file:1181]

### Required provenance payload

```json
{
  "source_type": "official_court_source",
  "source_label": "Illinois Courts approved form",
  "source_ref": "https://www.illinoiscourts.gov/documents-and-forms/approved-forms/",
  "generated_by": null,
  "review_state": "not_applicable"
}
```

This provenance envelope should be attachable to events, documents, alerts, summaries, and research outputs. [file:1181]

## API contract

The original document already defines sensible API conventions: `/api/v1`, bearer auth, ISO 8601 timestamps, cursor pagination, and structured JSON errors. That is a good MVP contract because it is predictable for both frontend and backend teams. [file:1181]

The most important endpoint families are matters, intake, documents, filing-readiness, filings, escalations, queues, templates, sources, and audit access. Those endpoint groups are consistent with both the developer package API outline and the roadmap’s first release scope. [file:1181][file:1171][file:1164]

### Recommended endpoint groups

| Group | Primary purpose |
|---|---|
| `/matters` | Create, read, update, assign, and summarize matters. [file:1181][file:1171] |
| `/matters/:id/intake/*` | Capture and complete intake stages. [file:1181] |
| `/matters/:id/events` | Build the matter timeline and docket-style activity trail. [file:1181][file:1116] |
| `/matters/:id/documents` | Register uploads and manage filing packet assets. [file:1181] |
| `/matters/:id/filing-readiness/*` | Run readiness checks and return blockers/warnings. [file:1181] |
| `/matters/:id/filings` and `/filings/:id/status` | Submit and update filing attempts. [file:1181] |
| `/matters/:id/escalations` | Trigger or request human-help routing. [file:1181] |
| `/queues/*` | Staff review, intake, and priority work queues. [file:1181][file:1171] |
| `/templates` and `/sources` | Admin/source registry for official and guided assets. [file:1181][file:1171] |
| `/audit` | Audit inspection and compliance review. [file:1181] |

## Rules engine contract

The filing-readiness contract is already close to production useful. It evaluates document format, flattened PDF checks, signature state, deadlines, and user context, then returns blockers, warnings, and a recommended next action. That lines up directly with the filing-readiness module in the PRD and the filing layer in the developer package. [file:1181][file:1116][file:1171]

The escalation engine is equally important because CourtPath should not drift into pretending to provide strategic legal advice. The original spec correctly triggers escalation around imminent deadlines, repeated rejection, accommodation barriers, strategy requests, and configured sensitive case types. [file:1181]

### Rules-engine output contract

```json
{
  "ready_to_file": false,
  "score": 88,
  "blockers": ["missing_signature"],
  "warnings": ["verify_flattened_pdf"],
  "recommended_next_action": "Collect signature and rerun readiness check"
}
```

This output should drive both backend decisioning and frontend next-action UI. [file:1181][file:1164]

## Permissions

The permissions matrix in the original spec is directionally right and should remain simple in the MVP: public users manage their own matters, professionals work assigned or organization-scoped matters, org managers handle team-level operations, and admins manage system-wide controls. [file:1181]

The main rule to preserve is that public users cannot directly set authoritative filing outcomes such as `accepted` or `rejected`, and professional intervention should remain auditable and role-bounded. That is consistent with the original validation rules and the roadmap’s trust-centered model. [file:1181][file:1164]

## Validation and invariants

The original validation list is strong and should be promoted to explicit invariants for implementation. These include required county and case type, hearing-date ordering, required documents before submission, flattening checks for required official forms, automatic alert generation on rejection, and restricted authority over filing outcome states. [file:1181]

Recommended invariant examples:

- `county` and `case_type` are mandatory for matter creation. [file:1181]
- `hearing_date >= received_date` when both exist. [file:1181]
- A filing attempt cannot move to `submitted` without at least one attached document. [file:1181]
- Required official forms with flattening requirements must pass flattening checks before readiness succeeds. [file:1181]
- Rejected filing updates must create an alert and a corrective workflow branch. [file:1181] 
- Public users cannot directly set terminal clerk-result states. [file:1181]

## Build order

The best build order remains matter foundation first, then documents, readiness, filings, queues, exports, escalation, and finally admin/source controls. That sequence appears in both the schema spec and the developer package, and it matches the roadmap’s release plan. [file:1181][file:1171][file:1164]

### Recommended technical sequence

1. Schema migrations for users, organizations, matters, events, documents, alerts, and audit logs. [file:1181]
2. Auth and role middleware. [file:1181]
3. Matter CRUD and intake completion. [file:1181]
4. Document registry and metadata flow. [file:1181]
5. Readiness engine and blocker generation. [file:1181]
6. Filing attempts and rejection handling. [file:1181][file:1171]
7. Professional queues and assignment APIs. [file:1181][file:1171]
8. Escalation and consultation export services. [file:1181][file:1171]
9. Trusted-source rendering and research note support. [file:1181]
10. Admin controls for templates and source registry. [file:1181]

## Implementation note

The right move is still to keep the first production workflow narrow, such as small claims, debt-response, or another Illinois-first branch where statewide forms, guided interviews, and e-filing mechanics are already familiar. That recommendation is consistent across the schema spec, roadmap, and developer package, and it is what keeps CourtPath’s architecture ambitious while keeping the first release buildable. [file:1181][file:1164][file:1171]
