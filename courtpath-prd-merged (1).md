# CourtPath PRD

## Product purpose
CourtPath is a trust-centered court navigation and legal-workflow platform that helps people and organizations organize court-related matters, understand next steps, prepare documents, track deadlines, and escalate to human help when needed.[cite:333][cite:342] A product requirements document should define the product purpose, key features, user needs, and success criteria so the team has a shared source of truth during development.[cite:333]

## Product goals
- Reduce confusion during court-related workflows.
- Help users move from a stressful situation to an organized matter workspace.
- Improve filing readiness and deadline awareness.
- Support both public users and professional or partner users.
- Preserve trust through clear boundaries, source visibility, and escalation paths.

These goals reflect the role of a PRD as a guide to product behavior, functionality, and delivery alignment.[cite:333][cite:339]

## User segments
- Self-represented individuals.
- Families managing disputes or filings.
- Small business owners handling court-related matters.
- Nonprofit and legal-aid intake teams.
- Professional support users and administrators.

User-centered requirements should be linked to user stories so features stay tied to real workflows instead of abstract functionality.[cite:333][cite:342]

## Core modules
1. Guided intake.
2. Matter dashboard.
3. Timeline and event log.
4. Document vault.
5. Filing-readiness workflow.
6. Alerts and next-step engine.
7. Referral and human-help routing.
8. Admin and partner workspace.

## User stories and acceptance criteria

### Module 1 — Guided intake
**User story:** As a public user, the user wants to describe a court-related problem in plain language so the platform can organize the situation into a workable matter.[cite:342][cite:337]

**Acceptance criteria:**
- Given a new user starts intake, when they answer guided questions, then the system creates a matter record with category, status, urgency, and next-step recommendations.[cite:337][cite:336]
- Given required intake questions are incomplete, when the user tries to continue, then the system shows clear validation messages.[cite:337]
- Given the user exits intake, when they return later, then the system reopens their in-progress matter draft within the current session.[cite:333]

### Module 2 — Matter dashboard
**User story:** As a user, the user wants one central matter dashboard so documents, deadlines, tasks, and status are visible in one place.[cite:342]

**Acceptance criteria:**
- Given a matter exists, when the dashboard loads, then it displays matter title, urgency, task progress, upcoming deadlines, and recent activity.[cite:333][cite:337]
- Given there are no uploaded documents yet, when the dashboard loads, then the user sees an empty state with a clear next action.[cite:333]

### Module 3 — Timeline and event log
**User story:** As a user, the user wants to build a timeline of events so the matter history is easier to understand and communicate.[cite:342]

**Acceptance criteria:**
- Given the user adds an event, when they save it, then the event appears in chronological order on the matter timeline.[cite:337]
- Given an event is edited, when the changes are saved, then the updated event replaces the prior version in the timeline display.[cite:337]

### Module 4 — Document vault
**User story:** As a user, the user wants to store matter-related files in one place so paperwork is easier to find and organize.[cite:342]

**Acceptance criteria:**
- Given a user uploads a supported file, when the upload succeeds, then the document is attached to the matter and visible in the vault.[cite:333]
- Given a user views documents, when filters are applied, then the list updates by type, status, or date.[cite:333]

### Module 5 — Filing-readiness workflow
**User story:** As a user, the user wants a filing-readiness checklist so they can see what is missing before trying to submit paperwork.[cite:342][cite:333]

**Acceptance criteria:**
- Given the matter has required filing steps, when the filing module opens, then the user sees completed, incomplete, and blocked items.[cite:337]
- Given a required step is missing, when the user attempts to mark the matter ready, then the system blocks completion and explains what remains.[cite:336][cite:337]

### Module 6 — Alerts and next-step engine
**User story:** As a user, the user wants reminders and priority guidance so they do not miss deadlines or important actions.[cite:342]

**Acceptance criteria:**
- Given a deadline exists, when it approaches a configured threshold, then the system marks it as upcoming and highlights it in the dashboard.[cite:333]
- Given a matter has unresolved blockers, when the user returns to the workspace, then the next-step panel prioritizes the most important action.[cite:333]

### Module 7 — Referral and human-help routing
**User story:** As a user, the user wants to know when human help is recommended so they can escalate before making a serious mistake.[cite:342]

**Acceptance criteria:**
- Given the matter matches a high-risk rule, when the system evaluates the matter, then it shows a recommendation to seek human help.[cite:337]
- Given referral options are available, when the user opens support options, then the platform shows available pathways by matter type and urgency.[cite:333]

### Module 8 — Admin and partner workspace
**User story:** As a partner or admin user, the user wants to review matters and support users through a structured queue so help can be delivered consistently.[cite:342]

**Acceptance criteria:**
- Given a partner user logs in, when they open their workspace, then they see assigned matters, priority flags, and recent updates.[cite:333]
- Given permissions differ by role, when a user opens restricted areas, then only authorized actions are available.[cite:333]

## Nonfunctional requirements
- Accessible, mobile-friendly interface.
- Clear loading, empty, success, and error states.
- Secure document handling and permission boundaries.
- Auditability of key actions and matter updates.
- Clear product language for the general public.

A PRD should include product behavior and constraints, not only feature wishes, so engineering can treat it as a real implementation guide.[cite:333][cite:339]

## Success metrics
- Intake completion rate.
- Matter creation rate.
- Filing-readiness completion rate.
- Deadline engagement rate.
- Referral click-through rate.
- Pilot activation and partner usage.

## Release sequence
- MVP: intake, dashboard, timeline, document vault, filing-readiness basics, alerts.
- Pilot: partner workspace, referral logic, deeper workflows, analytics.
- Expansion: multi-jurisdiction support, advanced document automation, richer integrations.

## Notes for design and engineering
The PRD should stay linked to wireframes, design exploration, and user stories so implementation stays aligned as the product evolves.[cite:333][cite:339] Acceptance criteria should be treated as pass/fail conditions for feature completion, whether they are written in simple checklist form or given/when/then format.[cite:337][cite:344]


## Module 9 Immigration Status and Records Flow

CourtPath should add a Phase 2 module focused on immigration status access, records guidance, and follow-up workflow support for emigrants and family helpers.[cite:1200][cite:1277][cite:1280][cite:1285][cite:1282] The module should help users identify whether they need the USCIS, EOIR, or CBP I-94 path, understand which identifier is required, launch the correct official source, and record next steps inside the matter workspace.[cite:1280][cite:1285][cite:1282]

### User story

As a user, the user wants a guided migration and immigration-status flow so they can check official case or record status, stay organized, and know what to do next without guessing which system applies.[cite:1280][cite:1285][cite:1282]

### Acceptance criteria

- Given the user opens Immigration Status & Records, when guided intake begins, then the system routes the user to USCIS, EOIR, or CBP I-94 based on their need.[cite:1280][cite:1285][cite:1282]
- Given the user enters the chosen path, when the system prepares the status check, then it explains the required identifier in plain language before routing to the official source.[cite:1280][cite:1285]
- Given the user returns from an official source, when they log the result, then the system saves notes, screenshots, latest checked date, and follow-up actions in the matter workspace.[cite:1200][cite:1285][cite:1282]
- Given a hearing date, re-check need, or unresolved blocker exists, when the user saves the workflow, then the system can create a reminder tied to that immigration module record.[cite:1285][cite:1200]
- Given the module is visible in product navigation, when a public or investor-facing user reviews the prototype, then an entry point labeled Immigration Status & Records or Migration Flow is clearly visible.[cite:1199][cite:1200]

## Updated release sequence

- MVP intake, dashboard, timeline, document vault, filing-readiness basics, alerts.
- Pilot partner workspace, referral logic, deeper workflows, analytics.
- Phase 2 expansion immigration status and records flow, multilingual support for this module, and module-specific reminders and document capture.[cite:1280][cite:1285][cite:1282]
- Expansion multi-jurisdiction support, advanced document automation, richer integrations.
