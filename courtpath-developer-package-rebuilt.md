# CourtPath Developer Package

## Product frame
CourtPath should be built as a trust-centered, matter-based court workflow platform that helps people and organizations move from confusion to organized action, filing readiness, and human escalation when risk rises.[file:1116][file:1164][file:1163] The product should not behave like a generic legal chatbot; it should behave like an operational system for managing court-related matters with visible sources, deadlines, documents, next actions, and review history.[file:1116][file:1113][file:1171]

## Build objective
The engineering objective is to turn CourtPath into a production-ready web application anchored by one canonical object: the matter.[file:1116][file:1164][file:1171] Every workflow—intake, timeline, documents, filing readiness, alerts, case lookup, referral routing, professional review, and export—should write back to that matter record so the product compounds structure instead of generating isolated outputs.[file:1116][file:1171]

## Scope position
The first real release should stay Illinois-first and workflow-first rather than trying to solve all legal processes in all jurisdictions at once.[file:1164][file:1163][file:1171] That means grounding the product in Illinois-style self-help, approved forms, e-filing preparation, court-help pathways, and matter triage while preserving a system design that can expand later.[file:1164][file:1163][file:1171]

## Product principles
The rebuilt developer package should treat these principles as non-negotiable implementation rules.[file:1116][file:1164][file:1163][file:1171]

- Matter-centered architecture over document-centered architecture.[file:1116][file:1171]
- Plain language for public users and higher-control workflows for professional users.[file:1163][file:1164]
- Persistent distinction between official sources, guided resources, user uploads, professional notes, and AI-generated explanations.[file:1163][file:1164][file:1171]
- One primary next action per screen in public mode to reduce overwhelm.[file:1163][file:1113]
- Escalation logic whenever the product detects urgency, complexity, or unsafe ambiguity.[file:1116][file:1163][file:1171]
- Auditability for any action that changes user-visible state or professional workflow state.[file:1116][file:1164][file:1171]

## Canonical system object
The **matter** is the system anchor and should be treated as the top-level aggregate for product and data design.[file:1116][file:1164][file:1171] A matter should unify user identity context, issue type, jurisdiction, timeline events, documents, filings, task state, alerts, research notes, referrals, and audit history so both public and professional users are always looking at the same underlying reality through different permission layers.[file:1164][file:1171]

## User modes
CourtPath should support three primary product modes plus a limited guest path.[file:1164][file:1171]

| Role | Purpose | Core capabilities |
|---|---|---|
| Guest | Lightweight exploration before account creation.[file:1164] | Browse, start intake, limited progress retention, no durable matter ownership.[file:1164] |
| Public user | Self-represented individual, family user, or small business operator.[file:1116][file:1171] | Create matter, complete intake, upload documents, review timelines, follow filing-readiness steps, receive alerts, and access human-help options.[file:1116][file:1163][file:1171] |
| Professional user | Reviewer, navigator, advocate, intake staff, or operations user.[file:1116][file:1171] | Queue management, matter review, assignments, internal notes, escalation handling, consultation export, and audit visibility.[file:1163][file:1171] |
| Admin | Platform or organization administrator.[file:1164][file:1171] | Source registry, rule settings, permissions, template configuration, and system oversight.[file:1164][file:1171] |

## Experience architecture
The end-to-end experience should follow one continuous path from situation intake to managed matter, then from managed matter to either filing completion, issue resolution, or human handoff.[file:1116][file:1163][file:1113] This keeps the live product aligned with the prototype promise that CourtPath shows what happened, what is missing, what is urgent, and when human help is needed.[file:1113]

## Core workflows

### 1. Public intake to matter creation
A public user should start with the situation in plain language, select issue type, enter county and court context, disclose dates or case number if known, complete urgency questions, and create a matter with a preliminary status, urgency score, and next-step recommendation.[file:1116][file:1163][file:1164] This workflow must preserve progress, validate missing required answers, and route high-risk users toward early help options instead of forcing them through a full self-help path first.[file:1116][file:1163]

### 2. Matter workspace workflow
Once a matter exists, the workspace should act as the operational home screen, showing matter summary, risk state, next recommended action, task progress, recent activity, source summary, and access to documents, alerts, and help routing.[file:1116][file:1163][file:1164] The prototype already demonstrates this pattern, and the production build should preserve it while making all main actions stateful and durable.[file:1113]

### 3. Case lookup and timeline workflow
The system should support case lookup by case number when available, guided alternate search when not, and a readable timeline that transforms procedural activity into understandable events rather than raw docket fragments.[file:1163][file:1164][file:1171] Users should be able to open an event, understand why it matters, and convert important events into tasks or reminders tied to the matter.[file:1163]

### 4. Document and filing-readiness workflow
The product should let users upload papers, tag documents, review what is missing, and move through a filing-readiness checklist that covers form selection, completion, PDF preparation, signature state, packet completeness, and filing status outcomes.[file:1116][file:1163][file:1164][file:1171] If a filing is rejected, the system should capture the reason and generate a corrective branch rather than leaving the user in a dead end.[file:1171]

### 5. Alerts and next-step workflow
Every matter should support alert generation based on deadlines, new activity, unresolved blockers, or review thresholds.[file:1116][file:1164][file:1171] Alerts should always include source labeling, timestamping, severity, and a clear next action so the system remains understandable under pressure.[file:1163][file:1164]

### 6. Escalation and help-routing workflow
When the matter crosses a defined risk or complexity threshold, CourtPath should recommend legal aid, limited-scope attorneys, internal staff review, or other support paths rather than extending unsafe automation.[file:1116][file:1163][file:1171] Help routing must feel like a built-in part of the product, not an afterthought added after self-help failure.[file:1163][file:1113]

### 7. Professional queue and review workflow
Professional users should work from a queue filtered by urgency, stage, referral status, and ownership.[file:1163][file:1164][file:1171] They must be able to inspect risk flags, review missing items, add notes, assign matters, update review state, trigger escalations, and export consultation summaries without altering the public trust model or obscuring audit history.[file:1163][file:1171]

## Screen system
The first production-grade screen map should align the roadmap, wireframe package, prototype, and PRD into one implementation order.[file:1116][file:1164][file:1163][file:1113]

| Screen | Product purpose | Primary user |
|---|---|---|
| Landing / welcome | Explain CourtPath, define boundaries, route into the correct mode.[file:1163][file:1164] | Public / professional |
| Sign in / account setup | Establish secure account or limited guest path.[file:1163][file:1164] | Public / professional |
| Onboarding expectations | Explain what CourtPath can do, cannot do, and when human help is needed.[file:1163] | Public |
| Intake wizard | Capture issue type, jurisdiction, urgency, and key dates.[file:1116][file:1163][file:1164] | Public |
| Matter created state | Confirm matter creation and recommend the first action.[file:1163] | Public |
| Matter workspace overview | Central operating surface for tasks, activity, sources, and help routing.[file:1116][file:1163][file:1113] | Public / professional |
| Case lookup | Connect matter to records workflow.[file:1163][file:1164] | Public / professional |
| Docket timeline | Make matter history readable and actionable.[file:1163][file:1164] | Public / professional |
| Filing list / documents | Show filings, evidence, availability, and next actions.[file:1163] | Public / professional |
| Filing-readiness screen | Move user through packet completeness and filing preparation.[file:1116][file:1163][file:1164] | Public |
| Alerts center | Surface changes, reminders, and follow-up actions.[file:1163][file:1164] | Public / professional |
| Help options / escalation | Route to court help, legal aid, attorney options, or internal review.[file:1116][file:1163] | Public |
| Professional matter queue | Manage many matters by urgency and status.[file:1163][file:1164][file:1171] | Professional |
| Professional review panel | Add notes, verify sources, manage workflow state, and hand off matters.[file:1163][file:1171] | Professional |
| Export / consultation packet | Prepare matter summary for attorney or support review.[file:1163][file:1113][file:1171] | Public / professional |
| Admin console | Manage templates, rules, sources, and permissions.[file:1164][file:1171] | Admin |

## Navigation model
Top-level navigation should stay simple and stable across the product.[file:1163][file:1164]

- Public navigation: Home, My Matters, Search Case, Alerts, Help Options, Account.[file:1163]
- Professional navigation: Dashboard, Matter Queue, Search Case, Alerts, Referrals, Team Admin.[file:1163]
- In-matter navigation: Overview, History, Filings, Tasks, Alerts, Sources, Help Options.[file:1164]

## Information hierarchy
The interface should show users the same hierarchy everywhere.[file:1163][file:1113]

1. Current matter and risk state.
2. One primary next action.
3. Current deadlines or urgent blockers.
4. Most recent verified activity.
5. Supporting documents and evidence.
6. Help and escalation paths.

This hierarchy is visible in the prototype and should remain central to the build system.[file:1113]

## Data model
The first implementation needs a relational, auditable model centered on matters and their child objects.[file:1164][file:1171]

### Core entities

| Entity | Purpose | Key fields |
|---|---|---|
| User | Identity and access context. | id, role, name, email, phone, language, organization_id.[file:1171] |
| Organization | Professional or partner account owner. | id, name, type, jurisdiction_scope.[file:1171] |
| Matter | Central record tying all workflows together. | id, owner_user_id, organization_id, title, issue_category, county, court, case_number, status, urgency_score, next_action, created_at, updated_at.[file:1164][file:1171] |
| IntakeResponse | Structured intake answers and derived classifications. | id, matter_id, step, answers_json, completed_at. |
| MatterParty | Parties associated with the matter. | id, matter_id, role, display_name.[file:1171] |
| MatterEvent | Timeline or docket event. | id, matter_id, event_type, event_date, description, source_record_id.[file:1171] |
| Document | Uploaded, generated, or linked document. | id, matter_id, document_type, source_type, format, signed_status, filing_status, storage_key.[file:1171] |
| FilingAttempt | Submission cycle and rejection handling. | id, matter_id, submitted_at, status, rejection_reason, corrected_at.[file:1171] |
| Task | Next-step or follow-up item. | id, matter_id, task_type, title, due_at, status, assigned_user_id. |
| Alert | Triggered reminder or risk notice. | id, matter_id, severity, message, due_at, resolved_at.[file:1116][file:1171] |
| SourceRecord | Provenance for user-visible content. | id, matter_id, source_type, source_name, access_path, retrieved_at, authority_level, confidence_note.[file:1164] |
| Referral | Human-help routing record. | id, matter_id, referral_type, destination, status, reason. |
| ReviewNote | Internal or external note object. | id, matter_id, author_user_id, note_type, body, visibility_scope. |
| ResearchNote | Comparable-matter or issue note with limitations. | id, matter_id, category, summary, confidence_label.[file:1171] |
| AuditLog | Append-only record of state transitions. | id, actor_type, actor_id, matter_id, action_type, metadata_json, created_at.[file:1171] |

### Suggested relationships

- One user can own many matters.[file:1164][file:1171]
- One organization can contain many users and many matters.[file:1164][file:1171]
- One matter can have many intake responses, parties, events, documents, tasks, alerts, referrals, notes, filing attempts, and audit logs.[file:1164][file:1171]
- Any object that changes user-visible matter state should write an audit log.[file:1116][file:1171]

## State model
The state model should be explicit so front-end behavior, backend logic, and reporting remain aligned.[file:1116][file:1171]

### Matter statuses
- draft
- intake_in_progress
- ready_for_forms
- packet_in_review
- ready_to_file
- filed
- accepted
- rejected
- resubmission_needed
- escalated
- closed

### Document statuses
- not_started
- generated
- uploaded
- official_linked
- signature_needed
- ready
- filed
- accepted
- rejected

### Task statuses
- not_started
- in_progress
- blocked
- complete
- canceled

### Alert severities
- info
- upcoming
- warning
- urgent

### Escalation types
- legal_aid_referral
- limited_scope_attorney
- internal_reviewer
- accessibility_support
- language_support

## Permissions model
Role-based permissions should be enforced from the beginning because CourtPath has both public and institutional workflows.[file:1164][file:1171]

| Role | Read | Write | Restricted actions |
|---|---|---|---|
| Guest | Public pages, temporary intake state.[file:1164] | Limited temporary form progress. | No durable matter storage, no professional notes. |
| Public user | Own matter records and visible resources.[file:1116][file:1171] | Intake answers, uploads, user notes, export request, help request. | Cannot access internal notes, team queues, admin settings. |
| Shared helper | Invited matter access only.[file:1164] | Limited support notes or uploads if allowed. | No admin or queue controls. |
| Professional user | Assigned or permitted matters, queue views.[file:1163][file:1171] | Review notes, assignments, status updates, referrals. | Cannot silently alter official-source labels or destroy audit history.[file:1164] |
| Organization admin | Organization views, team management, workflow settings.[file:1164] | Team rules, assignments, partner settings. | Cannot redefine platform-wide source taxonomy. |
| Platform admin | Full system configuration.[file:1171] | Sources, rules, templates, permissions. | Should still be audited on critical changes. |

## Trusted-source architecture
Every user-visible content block should carry source metadata because trust is a product feature, not a footer disclaimer.[file:1163][file:1164][file:1171]

### Source taxonomy
- `official_court_source` — official court forms, instructions, or court records.[file:1171]
- `guided_legal_help_source` — structured legal-help resources or guided interviews.[file:1171]
- `efile_process_source` — filing-process and submission guidance.[file:1171]
- `user_upload` — user-provided notices, evidence, or correspondence.[file:1171]
- `professional_note` — staff or reviewer-added notes.[file:1171]
- `ai_explanation` — non-authoritative summary, checklist, or explanation.[file:1171]

### Display rule
The UI must never present interpretive assistance as though it were an official court record.[file:1164][file:1171] Source labels, timestamps, confidence notes, and authority level should therefore be persistent in timeline entries, filing details, alerts, and summary panels.[file:1163][file:1164]

## Rules engine
CourtPath needs a rules layer for intake, filing readiness, alerts, and escalation rather than embedding all logic inside ad hoc UI code.[file:1116][file:1171]

### Intake and triage rules
- Classify matter branch from issue type, location, known court, case number presence, and key dates.[file:1163][file:1164]
- Detect deadline pressure and unsafe ambiguity from user answers.[file:1163][file:1171]
- Generate a preliminary next-action recommendation on matter creation.[file:1116][file:1164]

### Filing-readiness rules
- Required packet items must exist for the selected matter branch.[file:1116][file:1171]
- Signature-required items must be complete before ready-to-file status.[file:1171]
- PDF and formatting checks must surface readiness or corrective tasks.[file:1163][file:1171]
- Filing rejection reasons should map into structured corrective workflows rather than freeform notes only.[file:1171]

### Alert rules
- Trigger alerts for due dates, hearings, rejected filings, newly logged events, unresolved blockers, and stale verification windows.[file:1116][file:1164][file:1171]
- Every alert should include severity, timestamp, source label, and a single action target.[file:1163][file:1164]

### Escalation rules
Escalation should trigger when any of the following is detected.[file:1116][file:1163][file:1171]

- Imminent deadline with incomplete packet.[file:1171]
- Sensitive or safety-related issue type.[file:1171]
- Repeated rejection after correction attempt.[file:1171]
- User-reported barriers such as disability, limited English proficiency, or low comprehension.[file:1171]
- Procedural complexity or legal strategy questions beyond safe product guidance.[file:1171]

## Safety layer
The AI and workflow system should be explicitly constrained.[file:1171]

### Allowed behavior
- Explain process in plain language.[file:1171]
- Organize facts, dates, and documents.[file:1171]
- Identify missing steps or missing packet items.[file:1116][file:1171]
- Generate non-authoritative summaries and checklists.[file:1171]
- Recommend escalation and human help when needed.[file:1116][file:1171]

### Disallowed behavior
- Present itself as a lawyer.[file:1171]
- Guarantee outcomes or strategic success.[file:1171]
- Blur the distinction between official and generated content.[file:1164][file:1171]
- Suppress escalation where risk is clearly high.[file:1171]

## UI system requirements
The interface should be designed first for overwhelmed public users, while allowing professional depth through role-based controls.[file:1163][file:1164][file:1113]

### Required UX rules
- One clear primary action per screen in public mode.[file:1163][file:1113]
- Plain-language labels over legal jargon when possible.[file:1163][file:1164]
- Persistent source labels and timestamps on meaningful records.[file:1163][file:1164]
- Visible risk badges and escalation callouts.[file:1163][file:1113]
- Mobile-first flows for intake, alerts, and filing-readiness steps.[file:1163][file:1113]
- Distinct empty, loading, success, validation, and exception states for every critical screen.[file:1116][file:1169]

### Reusable components
- Source label chip.[file:1163]
- Risk badge.[file:1163]
- Next-action card.[file:1163]
- Matter summary card.[file:1163]
- Alert card.[file:1163]
- Filing row.[file:1163]
- Timeline event block.[file:1163]
- Escalation callout.[file:1163]
- Help option card.[file:1163]
- Empty-state card with clear next action.[file:1163]

## Frontend architecture
The frontend should be a responsive web application with a shared matter-centered shell and role-based surfaces.[file:1164][file:1171]

### Recommended approach
- React or Next.js application with server-backed state.[file:1171]
- Shared layout shell for public and professional users, with navigation differences controlled by permissions.[file:1164][file:1171]
- Strong client-side form state for intake and checklist flows.
- Durable server state for matters, documents, tasks, alerts, referrals, and notes.[file:1171]
- Progressive mobile layouts for intake, alerts, and matter overview.[file:1113][file:1163]

## Backend architecture
The backend should be modeled as a typed API plus relational core with background jobs for heavy or asynchronous operations.[file:1171]

### Recommended stack
| Layer | Recommendation |
|---|---|
| Frontend | React or Next.js with role-based views.[file:1171] |
| Backend API | Node.js or Python service with typed contracts.[file:1171] |
| Database | PostgreSQL.[file:1171] |
| File storage | S3-compatible object storage.[file:1171] |
| Search | PostgreSQL full text or OpenSearch for matter and document retrieval.[file:1171] |
| Jobs | Background worker for OCR, exports, alerts, reminders, and document classification.[file:1171] |
| Auth | Role-based authentication with organization support.[file:1171] |
| Analytics | Product analytics for completion, rejection, escalation, and handoff outcomes.[file:1171] |

### Backend services
- Matter service.
- Intake service.
- Document registry service.
- Filing-readiness rules service.
- Alerts service.
- Escalation and referral service.
- Source registry service.
- Export service.
- Audit logging service.[file:1171]

## API outline
The API should reflect the matter-centered product model.[file:1171]

### Public endpoints
- `POST /matters` — create matter.[file:1171]
- `GET /matters/:id` — fetch matter summary.[file:1171]
- `PATCH /matters/:id` — update matter metadata.[file:1171]
- `POST /matters/:id/intake/complete` — finalize an intake step.[file:1171]
- `POST /matters/:id/events` — create or save event.[file:1171]
- `POST /matters/:id/documents` — upload document metadata.[file:1171]
- `POST /matters/:id/filing-readiness/check` — run readiness rules.[file:1171]
- `POST /matters/:id/escalations` — request help or escalation.[file:1171]
- `GET /matters/:id/export` — build consultation packet summary.[file:1171]

### Professional endpoints
- `GET /queues/intake`.[file:1171]
- `GET /queues/review`.[file:1171]
- `PATCH /matters/:id/assign`.[file:1171]
- `POST /matters/:id/review-notes`.[file:1171]
- `POST /matters/:id/research-notes`.[file:1171]
- `POST /matters/:id/filings`.[file:1171]
- `PATCH /filings/:id/status`.[file:1171]

### Admin endpoints
- `GET /sources`.[file:1171]
- `POST /sources`.[file:1171]
- `GET /templates`.[file:1171]
- `POST /templates`.[file:1171]
- `PATCH /rules/escalation`.[file:1171]
- `GET /audit`.[file:1171]

## Nonfunctional requirements
Nonfunctional requirements should be treated as build constraints, not cleanup tasks.[file:1116][file:1164][file:1171]

### Accessibility
The product must support mobile-friendly layouts, large touch targets, understandable language, readable contrast, and low-friction navigation for stressed users.[file:1116][file:1164][file:1163]

### Security and privacy
Use strong authentication, encrypted transport, role-based access, conservative data retention, and careful permissions for document access because legal matters may contain sensitive personal information.[file:1164][file:1171]

### Reliability
Every alert, source retrieval, and status update should display clear timestamps and visible source indicators so users know when the information was last refreshed.[file:1164][file:1163]

### Auditability
Matter creation, source retrieval, note addition, alert generation, referral presentation, filing state changes, and staff interventions should all produce durable audit records.[file:1116][file:1171]

## Release plan
The release plan should follow the staged logic already established in the PRD and builder roadmap.[file:1116][file:1164]

| Release | Scope | Outcome |
|---|---|---|
| R1 | Illinois-first public MVP: auth, intake, matter creation, dashboard, timeline, documents, next-action engine, help options.[file:1164][file:1171] | Prove trust model and matter architecture.[file:1164] |
| R2 | Filing-readiness workflow, alerts center, consultation export, stronger source registry.[file:1164][file:1171] | Prove operational value and readiness guidance.[file:1116][file:1164] |
| R3 | Professional queue, assignments, review notes, referral lifecycle, audit explorer.[file:1164][file:1171] | Prove dual-audience workflow and pilot operations.[file:1116][file:1164] |
| R4 | Research workspace, richer automations, expanded case-type support, multi-jurisdiction framework.[file:1164][file:1171] | Extend without losing trust controls.[file:1116][file:1164] |

## Engineering backlog
The immediate backlog should convert strategy into implementation order.[file:1164][file:1171]

1. Define database schema for matters and child entities.[file:1171]
2. Build authentication and role model.[file:1164][file:1171]
3. Build intake wizard APIs and UI.[file:1116][file:1163][file:1171]
4. Build matter dashboard and matter navigation shell.[file:1116][file:1113][file:1171]
5. Add timeline and event creation / ingestion model.[file:1116][file:1163][file:1171]
6. Create document registry with source labeling.[file:1163][file:1171]
7. Implement filing-readiness rules and state outputs.[file:1116][file:1171]
8. Add alerts engine and user-visible alert center.[file:1116][file:1164][file:1171]
9. Build escalation UI and referral records.[file:1116][file:1163][file:1171]
10. Build professional queue and review tools.[file:1163][file:1171]
11. Add export service for consultation packets.[file:1163][file:1113][file:1171]
12. Add analytics instrumentation for activation, delay, rejection, and escalation outcomes.[file:1116][file:1171]

## Acceptance guidance
For engineering, the practical rule is that every major screen and module must define pass/fail behavior, not just aspirational copy.[file:1116] Each feature should therefore include required states for loading, empty, validation error, success, restricted access, and exception handling before implementation is considered complete.[file:1116][file:1169]

## Delivery note
This package should function as the canonical builder-facing brief that sits between the PRD and actual implementation work.[file:1112][file:1116] The PRD remains the source of truth for product scope, but this developer package should become the source of truth for flows, objects, permissions, service boundaries, release order, and engineering execution detail.[file:1112][file:1116][file:1171]
