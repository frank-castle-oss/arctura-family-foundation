# Inkbox.ai + Vapi Service-Desk Architecture

## Formation-Stage Decision Record

The requested combination is **Inkbox.ai and Vapi**, not a generic shared-inbox provider. Arctura will treat Inkbox as the prospective identity and communication layer and Vapi as the prospective voice-assistant platform. Neither service is connected, authorized, funded, or configured in this project. This document is an architecture and safeguarding record—not an activation instruction.

## Verified Vapi Event Boundary

Vapi documents that its server URLs can deliver real-time conversation data, including call status, transcript updates, function calls, assistant requests, end-of-call reports, and hang notifications. [1] Vapi also documents a custom-credential system for authenticating server requests, supporting bearer token, OAuth 2.0, HMAC, and legacy secret-header models. [2]

For Arctura, those capabilities do **not** authorize the storage of transcripts, recordings, or summaries. The proposed endpoint must accept only provider-authenticated operational events and retain only a minimal human-reviewed case summary where a named steward has approved that purpose.

## Verified Inkbox Event Boundary

Inkbox documents an agent identity with a mailbox, a stable public tunnel, and an optional phone number, with filtering controls for who may reach that identity. [3] Inkbox webhooks are delivered through channel-agnostic subscription resources that bind one owner to an HTTPS destination and selected event types; its SDK provides a verification method that uses the organization’s signing-key secret. [4]

Inkbox should therefore be treated as the prospective identity and inbox layer. Its mailbox and phone capabilities must remain disabled until Arctura has chosen a single public identity, defined inbound filtering, and named the human owner who can release an external response. No address book, credential vault, contact synchronization, or message send is authorized by this planning record.

## Non-Negotiable Defaults

| Area | Default | Activation condition |
| --- | --- | --- |
| Voice calls | Inbound-only and human-supervised | Named duty steward, staffed coverage, approved script, and confirmed emergency-routing policy |
| Recording and transcripts | Off or not retained in Arctura systems by default | Separate privacy, consent, retention, and jurisdiction review |
| Inbox access | Disconnected | Exact Inkbox account, credential scope, mailbox/phone configuration, and human release owner are approved |
| Outbound communication | Draft-only | A human approves and releases each message or call action outside the service desk |
| Provider events | Authenticated only | Credential verification, replay protection, audit trail, and minimal-data handling are implemented and reviewed |

## Proposed Event Flow

```text
Inkbox identity / Vapi inbound call event
             ↓  authenticated provider event only
Arctura protected webhook boundary
             ↓  minimal case summary and escalation tag
Protected service desk
             ↓  draft-only recommendation
Named duty steward
             ↓  explicit human release outside the system
External reply or call action
```

The flow deliberately excludes autonomous outreach, automatic calls, automatic messages, mass contact, contact enrichment, payment handling, delivery promises, and public service-availability claims.

## Provider Responsibility Boundary

| Layer | Proposed responsibility | Explicitly excluded until separately approved |
| --- | --- | --- |
| Inkbox.ai | One controlled agent identity, inbound email events, and authenticated inbox event delivery | Self-provisioning, sending mail, contact enrichment, shared credential access, iMessage, and phone-number activation |
| Vapi | Voice-assistant event handling and authenticated call-event delivery for an approved inbound voice path | Voice recording, transcript retention, autonomous function calls, outbound campaigns, and automatic transfers |
| Arctura service desk | Internal case creation, escalation tags, draft creation, administrator approval, and recorded human release | Direct provider credentials in the client, external send actions, delivery commitments, and automated outreach |

Before provider configuration, the design must resolve whether the public phone number is provisioned and governed by Inkbox or Vapi. It must not create two uncoordinated public numbers.

## Provider-Neutral Activation Baseline

This baseline applies regardless of which inbox or voice providers are ultimately selected. It is the control plane the protected Arctura service desk must satisfy before any external identity, mailbox, number, webhook, or assistant is connected.

| Control | Required baseline | Evidence before activation |
| --- | --- | --- |
| Shared-inbox ownership | One named duty steward owns the mailbox scope, operating hours, and release queue | Administrator record identifying owner, coverage window, and escalation backup |
| Single-number governance | One accountable owner governs the public inbound number and its routing policy | Written decision naming the provider, number purpose, business hours, transfer route, and decommission process |
| Authenticated event intake | Every provider event is authenticated, timestamped, replay-protected, and reduced to a minimum necessary case summary | Credential-verification test, replay-control test, and audit event record |
| No-recording default | Audio, transcripts, raw messages, and provider summaries are disabled or excluded from Arctura retention unless a separately approved policy allows them | Written privacy, consent, retention, and deletion decision reviewed for the applicable jurisdiction |
| Human release gate | A generated or drafted reply cannot leave the system until a named human approves and records the release reason | Protected approval state, approver identity, release timestamp, and no-send regression coverage |
| Emergency and exception routing | Urgent, crisis, privacy, legal, benefits, food-access, and finance signals route to a named human pathway rather than an automated outcome | Current escalation directory and duty-steward review |

The selected Inkbox.ai-and-Vapi pattern is an optional implementation profile under this baseline; it does not replace the baseline and may not be activated until all six controls are evidenced.

## References

[1]: https://docs.vapi.ai/server-url "Vapi: Server URLs"
[2]: https://docs.vapi.ai/server-url/server-authentication "Vapi: Server Authentication"
[3]: https://inkbox.ai/docs/get-started/introduction "Inkbox: Introduction"
[4]: https://inkbox.ai/docs/webhooks "Inkbox: Webhooks"
