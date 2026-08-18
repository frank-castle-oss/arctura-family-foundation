# Arctura Family Foundation — Automation and Orchestration Policy

> **Name status:** “Arctura Family Foundation” is a working name only. The legal entity is pending creation and final-name selection.

## Principle

Automation exists to reduce clerical delay, not to replace accountable human judgment. Arctura will not automate eligibility decisions, recipient prioritization, food-safety acceptance, partner approval, payment authorization, public impact publication, or any delivery commitment.

## Current state

**No recurring jobs are active.** The foundation is in partnership formation. Creating schedules before a deployed, authenticated operations model and named owners exist would increase operational risk without increasing community reliability.

## Future eligible workflows

| Workflow | Trigger | Automation boundary | Human approval gate | Preconditions |
| --- | --- | --- | --- | --- |
| New partner-intake digest | Daily, UTC | Summarize new submissions for assigned reviewers | Partner owner qualifies or declines | Named reviewer, secure notification channel, retention policy |
| Expiring supply-offer reminder | Periodic, UTC | Flag offers approaching expiry | Food-safety owner confirms action | Verified supplier, retention policy, no recipient-facing promise |
| Fulfillment exception reminder | Event-driven or short interval | Escalate unresolved exception status | Operations lead resolves or closes | Active city, carrier agreement, incident playbook |
| Restricted-fund review reminder | Monthly, UTC | Surface unreconciled finance records | Finance owner reconciles | Qualified entity or fiscal sponsor, ledger owner, finance controls |
| Editorial review queue | Weekly, UTC | Assemble draft review list | Editor approves every publication | Source policy, named editor, public-claim review |

## Technical standard

When justified, recurring work will use the platform-managed heartbeat model rather than in-process timers. Each callback will use a dedicated `/api/scheduled/*` path, authenticated cron identity, durable task identifier, idempotent handler, structured errors, and an auditable owner. The schedule will be created only after the callback has been deployed and the responsible owner has approved its scope.

## Prohibited automation

Arctura will not schedule mass outreach without documented consent, scrape personal contact data, create recipient profiles from third-party sources, auto-enroll donors, auto-approve partner applications, auto-disburse funds, or generate public impact claims without verified evidence and human review.
