# CourtPath Builder-Ready Roadmap

## Overview

CourtPath should be built as a sophisticated legal-navigation web application that serves both public users and professional users through one trust-centered platform.[cite:16][cite:1] The first implementation should be Illinois-first because Illinois already provides structured self-help, e-filing, court-help, referral, and growing remote access infrastructure that can anchor a realistic first release.[cite:1][cite:2][cite:6][cite:120]

This roadmap translates the product concept into screens, objects, permissions, workflows, feature priorities, and staged delivery decisions so a designer, engineer, advisor, or pilot partner can understand what gets built first.[cite:16]

## Product Goal

The core product goal is to help a user understand what is happening in a court matter, what step comes next, and when the matter should move from self-help into human support.[cite:16][cite:14][cite:95] For professional and business users, the goal is to provide a structured client-support workflow with clearer intake, better matter organization, safer escalation, and traceable source handling.[cite:16]

## Release Strategy

The initial build should focus on one production-grade workflow, not broad national coverage.[cite:1][cite:2] The recommended release order is below.

| Release | Scope | Purpose |
|---|---|---|
| R1 | Illinois-first public MVP | Prove user flow, trust model, and matter architecture [cite:1][cite:2] |
| R2 | Professional workspace | Add staff review, queues, and referral collaboration [cite:16][cite:95] |
| R3 | Expanded case-type support | Add more templates, workflows, and research tools [cite:16] |
| R4 | Multi-jurisdiction framework | Extend once source quality and safety controls are stable [cite:67][cite:120] |

## R1 Feature Set

Release 1 should include the following feature blocks.

### 1. Authentication and account model

- Public user account.
- Guest mode with limited functionality.
- Professional account by invitation or approval.
- Matter-level permissions for users and staff.[cite:16]

### 2. Intake and triage

- Guided intake questionnaire.
- Case-type classification.
- County and court selection.
- Urgency and risk prompts.
- Case number path if known.
- Matter creation on completion.[cite:16]

### 3. Matter workspace

- Matter summary card.
- Risk level flag.
- Latest activity panel.
- Task list.
- Next recommended action.
- Source summary panel.
- Referral status panel.[cite:16]

### 4. Case lookup and history review

- Search by case number when available.
- Search-assist guidance when only party or court details are known.
- Docket history timeline.
- Filing list with access-status labels.
- Save item to matter function.[cite:67][cite:120]

### 5. Filing-readiness flow

- Checklist for preparing documents.
- Approved forms guidance.
- PDF and upload preparation guidance.
- EFSP step walkthrough.
- Acceptance or rejection follow-up checklist.[cite:2][cite:6][cite:12]

### 6. Alerts and monitoring

- Follow a matter.
- Alert on new docket activity or status changes.
- Alert explanation panel with source and timestamp.
- Warnings when official verification is still required.[cite:67][cite:120]

### 7. Referral and attorney options

- Legal-aid options.
- Court-help resources.
- Limited-scope options.
- General referral options.
- Matter summary export for consultations.[cite:1][cite:14][cite:95][cite:133]

## Screen Map

The first build should include the following core screens.

| Screen | Purpose | Primary user |
|---|---|---|
| Landing / welcome | Explain platform and set expectations | Public |
| Sign in / create account | Start secure use | Public and professional |
| Onboarding | Explain safety boundaries and capabilities | Public |
| Intake wizard | Gather issue details and classify need | Public |
| Matter dashboard | Show case summary and next step | Public and professional |
| Case lookup screen | Connect matter to records workflow | Public and professional |
| Docket timeline | Make case history readable | Public and professional |
| Filing-readiness screen | Prepare for e-filing or clerk steps | Public |
| Alerts center | Display tracked updates | Public and professional |
| Attorney options screen | Route users to help | Public |
| Professional queue | Staff view of managed matters | Professional |
| Matter admin panel | Internal notes, review, handoff | Professional |

## Navigation Structure

The recommended top-level navigation is:

1. Home
2. Matters
3. Search / Lookup
4. Alerts
5. Help Options
6. Admin or Team Workspace for professional users.[cite:16]

Within a matter, the recommended sub-navigation is:

1. Overview
2. History
3. Filings
4. Tasks
5. Alerts
6. Sources
7. Help Options.[cite:16]

## Data Model

The first implementation needs a clean and auditable data model.

### Core objects

| Object | Description |
|---|---|
| User | Person using the platform |
| Organization | Professional or business account owner |
| Matter | Core record tying all activity together |
| IntakeResponse | Answers collected during triage |
| CaseLink | External court-record linkage or lookup reference |
| DocketEvent | Individual case-history entry |
| FilingRecord | A filing or document entry tied to a matter |
| Task | Recommended action or follow-up item |
| Alert | Notification tied to a case or matter change |
| SourceRecord | Provenance entry for any data shown to the user |
| Referral | Legal-aid, attorney, or partner handoff |
| Note | User or staff annotation |

### Matter object fields

The Matter object should contain at minimum:

- Matter ID.
- User ID or organization ID.
- Matter title.
- Issue category.
- Court and county.
- Case number if known.
- Current status.
- Risk level.
- Recommended next action.
- Referral status.
- Last verified timestamp.[cite:16]

### SourceRecord fields

The SourceRecord object is strategically important and should include:

- Source type, such as official court, clerk, public portal, legal-aid guidance, user upload, or AI-generated summary.[cite:16]
- Source name.
- Access path or URL.
- Retrieval timestamp.
- Confidence or completeness note.
- Whether the item is authoritative, supportive, or interpretive.[cite:16]

## Permissions Model

CourtPath should use role-based permissions from the start.

| Role | Permissions |
|---|---|
| Guest | Limited browsing, no saved matter |
| Public user | Create and manage own matters |
| Supporter / shared helper | Limited access to invited matter |
| Staff reviewer | Review assigned matters, add internal notes |
| Organization admin | Manage team and workflows |
| Platform admin | Manage system configuration |

Professional users should never silently alter a public user’s official record view without a visible audit trail.[cite:16]

## Workflow Logic

### Intake decision flow

1. User enters issue details.
2. System classifies general matter type.
3. System checks whether case number exists.
4. System identifies likely next module.
5. System calculates preliminary risk level.
6. System creates matter and next-action recommendation.[cite:16]

### Risk logic

The first version should not try to produce legal predictions. Instead, it should assign a product risk level based on operational cues such as deadline pressure, missing records, adverse ruling signals, active hearing proximity, rejected filing, or signs that legal representation may be needed.[cite:16]

Recommended operational levels:

- **Green:** self-help likely appropriate for the current step.
- **Yellow:** proceed carefully, verify source, review deadlines.
- **Red:** show attorney and legal-aid options immediately.[cite:16][cite:95]

### Next-action engine

Each matter should always surface one primary next action. Candidate next actions include:

- Find the right form.[cite:2]
- Review the latest docket event.[cite:67]
- Verify whether a filing was accepted.[cite:2]
- Request a document copy.[cite:67]
- Prepare for e-filing through an EFSP.[cite:6][cite:12]
- Contact court help or legal aid.[cite:1][cite:14]
- Explore limited-scope representation.[cite:95][cite:117]

## Design and UX Requirements

The interface should be designed for overwhelmed users first and power users second.[cite:16] That means:

- Plain-language labels.
- One primary action per screen.
- Strong visual distinction between official records, guidance content, and AI help.[cite:16]
- Calm tone and low-clutter layout.
- Mobile-friendly design because many self-represented users will rely on phones.[cite:2]
- Professional mode should reveal additional controls without changing the public user’s mental model.[cite:16]

## Integrations and Source Layers

The builder should separate the system into source layers rather than hardwiring all content together.

### Source layer categories

| Layer | Example |
|---|---|
| Official court services | Illinois Courts, eFileIL, approved forms [cite:1][cite:2][cite:6] |
| Public record access | County clerk tools, re:SearchIL, public access services [cite:67][cite:120] |
| Legal information | Illinois Court Help, Illinois Legal Aid Online [cite:14][cite:1] |
| Referral networks | CARPLS, legal-aid groups, bar referral sources [cite:1][cite:133] |
| User-provided content | Uploaded PDFs, notes, correspondence |
| AI-assist layer | Summaries, task extraction, document explanation [cite:16] |

The application should never blur these layers together in a way that makes interpretive assistance look like an official court record.[cite:16]

## Non-Functional Requirements

### Auditability

Every key event should be logged, including matter creation, source retrieval, alert generation, referral presentation, and staff intervention.[cite:16]

### Security and privacy

Because matters may involve sensitive legal issues, the application should use strong authentication, encrypted transport, role-based access, and conservative retention policies.[cite:16]

### Reliability

Alerts and case-history updates should carry visible timestamps and source indicators so users understand when data was last refreshed.[cite:67][cite:120]

### Accessibility

The product should use accessible language, mobile-friendly layouts, large touch targets, and readable contrast because many users may already be under stress or facing literacy and technology barriers.[cite:2][cite:9]

## Backlog Priorities

### Priority 1

- Account creation.
- Intake wizard.
- Matter creation.
- Matter dashboard.
- Case lookup guidance.
- Docket timeline.
- Next-action engine.
- Help options screen.[cite:16]

### Priority 2

- Filing-readiness workflow.
- Alerts center.
- Source registry UI.
- Matter export for attorney consultations.
- Shared helper access.[cite:2][cite:16]

### Priority 3

- Professional queue.
- Internal notes.
- Referral lifecycle tracking.
- Partner configuration tools.
- Comparable-case research workspace.[cite:16]

## Recommended Team Sequence

The most efficient build order is:

1. Product and UX definition.
2. Matter data model.
3. Intake and matter dashboard.
4. Lookup and history layer.
5. Filing-readiness flow.
6. Alerts and referral logic.
7. Professional workspace.[cite:16]

This order works because the matter object is the system anchor; without it, alerts, filings, referrals, and team workflows stay fragmented.[cite:16]

## Pilot Recommendation

The first pilot should target one Illinois use case with a partner group or controlled user cohort.[cite:1][cite:14] Strong candidates include:

- Debt collection defense workflow.
- Housing and eviction-adjacent workflow.
- Post-judgment or motion support workflow.
- General civil self-help intake and referral triage.[cite:16]

The best pilot is the one where the user most clearly needs structure, record visibility, and a next-step engine rather than deep custom legal analysis.[cite:16]

## Delivery Recommendation

The immediate next build artifact should be a screen-by-screen wireframe package based on this roadmap, followed by a prioritized engineering backlog.[cite:16] That will let the concept move from strategy into actual product design and development without losing the trust model or dual-audience vision that make CourtPath distinct.[cite:16][cite:1][cite:95]


TITLE CourtPath Builder-Ready Roadmap - Phase 2 Immigration Status & Records...
- Guided triage between USCIS, EOIR, and CBP I-94 paths.[cite:1280][cite:1285][cite:1282]
- Identifier readiness prompts for receipt number, A-Number, or travel/admission details.[cite:1280][cite:1285][cite:1282]
- Official-link routing with clear source labeling.[cite:1277][cite:1290][cite:1282]
- Status capture, notes, screenshots, and task reminders inside the matter workspace.[cite:1200][cite:1285]
- Multilingual support priority if launch geography demands it.[cite:1283][cite:1200]
- Navigation entry labeled Immigration Status & Records, with Migration Flow accepted as alternate investor-facing language.[cite:1200]
