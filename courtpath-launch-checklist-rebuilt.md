# CourtPath Launch Checklist — Rebuilt

CourtPath should launch as a controlled, trust-centered legal workflow product rather than as a generic app deployment.[file:1178][file:1164] The first production release should stay Illinois-first and prove one matter-centered workflow before broader expansion.[file:1164]

## Launch posture

The original checklist correctly identified the core technical accounts and services: GitHub, Vercel, Supabase, Clerk, and optional Resend.[file:1178] The stronger version reframes these as part of a staged release system tied to product safety, source visibility, protected uploads, and help-routing behavior.[file:1178][file:1164][file:1113]

CourtPath should not treat production as the first real test environment.[file:1178] Preview should be the place where authentication, API routes, matter creation, uploads, seeded fallback behavior, and any live notification logic are tested before promotion.[file:1178]

## Stack setup

Set up the technical foundation in this order:[file:1178]

1. Create the GitHub repository as the canonical source of truth.[file:1178][file:1112]
2. Create a Vercel project connected to that repository.[file:1178]
3. Create a Supabase project for the database and protected storage.[file:1178]
4. Create a Clerk application for authentication and organization-aware access if organizations are truly in launch scope.[file:1178]
5. Create a Resend account only if live outbound email is part of the pilot release.[file:1178]

Use these environment variables as the minimum launch baseline:[file:1178]

| Variable | Source | Requirement |
|---|---|---|
| `NEXT_PUBLIC_SUPABASE_URL` | Supabase dashboard.[file:1178] | Public-safe project URL.[file:1178] |
| `SUPABASE_SERVICE_ROLE_KEY` | Supabase API keys.[file:1178] | Server-only secret; never expose client-side.[file:1178] |
| `NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY` | Clerk dashboard.[file:1178] | Client-safe authentication key.[file:1178] |
| `CLERK_SECRET_KEY` | Clerk dashboard.[file:1178] | Server-only secret.[file:1178] |
| `RESEND_API_KEY` | Resend dashboard.[file:1178] | Needed only for live email delivery.[file:1178] |

Maintain these variables separately for Local, Preview, and Production so configuration quality can be audited by environment rather than guessed.[file:1178]

## Data and auth hardening

Run the database and storage setup in a controlled order: schema first, then row-level security, then storage policies.[file:1178] After SQL execution, confirm that private buckets were actually created and that uploads are only allowed through intended policies rather than public access.[file:1178]

Clerk should be configured only for the user types CourtPath actually supports at launch.[file:1178][file:1164] If public users are the only real pilot users, do not overexpose organization complexity before those workflows are tested.[file:1164][file:1178]

## Deployment flow

Use this launch sequence:[file:1178]

1. Push the codebase to GitHub.[file:1178]
2. Import the repository into Vercel.[file:1178]
3. Add all environment variables in Vercel by environment.[file:1178]
4. Trigger a Preview deployment.[file:1178]
5. Verify sign-in, API routes, matter list loading, and seeded fallback behavior.[file:1178]
6. Promote to Production only after storage, auth, and core workflows pass QA.[file:1178]

For CourtPath specifically, promotion should also be blocked if the release does not preserve the product’s trust model: visible source handling, matter organization, filing-readiness support, and help escalation when risk rises.[file:1164][file:1113]

## Background jobs

OCR, exports, and retryable notifications should not run synchronously in user-facing requests.[file:1178] A real background-job provider should be chosen before launch if OCR or retryable notification behavior is part of the live pilot experience.[file:1178]

## Security review

Do not launch until the following are confirmed:[file:1178]

- `SUPABASE_SERVICE_ROLE_KEY` is used only server-side.[file:1178]
- No server secrets appear in public environment variables or client bundles.[file:1178]
- Row-level security is enabled on all protected tables.[file:1178]
- Private document buckets are not public.[file:1178]
- Clerk roles and organization flows match the actual supported launch roles.[file:1178][file:1164]

Because CourtPath handles sensitive matter information, these controls are not optional polish items; they are release gates.[file:1164][file:1178]

## Product QA

Before launch, test these workflows end to end:[file:1178]

- User sign-up and sign-in.[file:1178]
- Matter creation through the app’s matter flow.[file:1178][file:1113]
- Matter list or workspace rendering in the main UI.[file:1178][file:1113]
- Document upload to protected Supabase Storage.[file:1178]
- OCR queue request creation if OCR is in scope.[file:1178]
- Notification send request if email is in scope.[file:1178]
- Failure states, including missing environment variables and rejected uploads.[file:1178]

The prototype already centers CourtPath around intake, matter workspace, filing readiness, and help routing, so launch QA should verify those specific journeys rather than generic page loads.[file:1113]

## Go-live gate

Launch only when all of the following are true:[file:1178]

- Production environment variables are complete.[file:1178]
- Database schema, RLS, and storage policies have all been applied.[file:1178]
- Preview testing passed for auth, uploads, API reads, and notifications in scope.[file:1178]
- A background-job provider has been chosen for OCR and retries when required.[file:1178]
- Legal, privacy, and compliance review is complete for the intended user population.[file:1178]

For CourtPath, the best launch is a safe and believable pilot, not the broadest possible release.[file:1164]
