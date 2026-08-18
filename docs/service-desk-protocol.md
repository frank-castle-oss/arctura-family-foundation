# Arctura Service Desk Protocol

**Formation-stage boundary.** Arctura Family Foundation is a working name. This protocol does not authorize telephony, inbox access, outbound messaging, delivery, emergency response, payment collection, fundraising solicitation, legal formation, or a public claim of active service.

## Purpose

The Arctura service desk is a proposed **human-supervised coordination layer** for three carefully separated activities: acknowledging inbound calls and emails, routing people toward verified existing resources, and preparing consent-aware outreach drafts for a designated human to review. It is not a substitute for 211, a public-benefits administrator, emergency services, a food provider, a delivery carrier, or professional legal, medical, financial, or crisis support.

## Proposed Agent Squad

| Role | May do under supervision | May not do | Human release owner |
| --- | --- | --- | --- |
| Intake triage agent | Classify an inbound message, remove unnecessary detail from an internal summary, create a case, and surface the correct escalation path | Assess eligibility, make a delivery promise, collect full addresses or medical information, or send a final response | Duty steward |
| Resource-navigation agent | Draft a minimal, source-linked response that points to verified existing public or local routes | Represent a provider, confirm availability, diagnose need, or replace 211/emergency services | Referral steward |
| Partner and listening liaison | Prepare a concise, consent-aware outreach draft and capture a proposed next step | Search for personal contact data, enroll a person, send outreach, or present a relationship as approved | Partner owner |
| Stewardship and finance gatekeeper | Categorize inquiries as general, grant, sponsorship, commercial, or media; surface the correct boundary | Accept funds, promise tax treatment, negotiate terms, or merge charitable and commercial requests | Governance or finance owner |
| Quality and safeguarding reviewer | Check tone, consent basis, factual source, data minimization, and escalation tags | Override an escalation, suppress a safety concern, or convert a draft into external communication | Designated accountable administrator |

## Human-Control Standard

Every external communication remains **draft-only** until a named human releases it. An agent may prepare a short case summary and proposed reply, but may not autonomously call, email, text, enroll, schedule, negotiate, solicit, or publish. No mass outreach, contact enrichment, automated dialing, prerecorded voice, recording, transcription, or call analytics may be activated without a separate written approval, privacy review, and channel-specific operating decision.

## Inbound Routing and Escalation

| Signal | Service-desk action | Required human action |
| --- | --- | --- |
| Immediate danger, threat, crisis, or urgent medical concern | Present an emergency-routing notice; do not gather narrative detail | Refer the person to local emergency services or a qualified crisis route; document only the minimum internal escalation note |
| Request for food today | Identify 211 and verified local public resources; state that Arctura does not provide emergency delivery | A referral steward verifies any additional local resource before it is shared |
| Benefits or eligibility question | Point to the relevant official public-benefits route | Do not request documents, decide eligibility, or represent a government program |
| Partner, donor, carrier, or local-listening interest | Create a structured case and propose a human-reviewed draft | A partner owner confirms consent, relevance, and next step before any reply or outreach |
| Gift, grant, sponsorship, or commercial inquiry | Separate the inquiry type and surface the formation-stage finance boundary | Finance or governance owner reviews before any commitment or solicitation |
| Press, legal, privacy, removal, or complaint request | Preserve the request without speculative reply | Designated accountable administrator responds or assigns counsel/appropriate owner |

## Minimum Necessary Data

The desk may retain only the channel identifier needed for a reply, the request category, consent/reply basis, a short human-reviewed summary, chosen resource or next step, status, and audit timestamps. It must not request full street address, identity documents, benefits documents, payment data, health information, detailed household history, or recipient lists unless a separately approved legal and operating purpose exists.

## Channel Architecture Boundary

Inbound calls and messages should be event-driven, not polled. For example, Twilio documents that an incoming voice call can invoke an application webhook in real time and advises HTTPS plus request verification for confidentiality and authenticity. [1] No Twilio account, phone number, webhook endpoint, call recording, or other external channel is connected in this project today.

Gmail’s API can publish mailbox-change notifications through Google Cloud Pub/Sub instead of polling, but the mailbox watch expires and must be renewed at least every seven days; Google recommends renewal at least daily. [2] The available Gmail, AgentMail, HubSpot, and Intercom integrations are currently disabled, so none may read messages, create contacts, send drafts, or communicate externally.

## Channel Architecture Options

| Approach | What it delivers | Tradeoffs | Cost | Setup complexity |
| --- | --- | --- | --- | --- |
| **Internal draft desk** | Protected cases, agent roles, escalation tags, and human-approved response drafts from the existing Arctura site | Does not receive an external mailbox or phone line; humans manually copy approved context into their chosen channel | No additional channel-provider cost | Low |
| **Shared-inbox desk** | Event-driven email case creation from a dedicated mailbox; agents draft, while a human replies from the mailbox | Requires mailbox ownership, OAuth, Google Cloud Pub/Sub, watch renewal, privacy controls, and a named duty steward | Provider and cloud costs depend on the selected account and use | Medium |
| **Inbound phone plus inbox desk** | Verified call events and an explicit human answer, callback, or non-recording voicemail protocol alongside the shared inbox | Requires a telephony account, assigned number, webhook verification, real-time call response policy, consent/recording decisions, and staffed coverage | Telephony and number costs depend on the selected provider and use | High |

The first option is the recommended formation-stage sequence because it produces auditable operations without representing that Arctura has a staffed phone line, monitored inbox, or authorization to send outreach. The other options should be selected only after a human owner, operating hours, privacy review, and service-level boundaries are approved.

## Release Checklist

Before a human sends any communication, the reviewer confirms all of the following:

1. The recipient’s contact basis and consent are appropriate for the message.
2. The message does not imply a formed entity, active delivery, financial eligibility, tax deductibility, active partnership, or guaranteed response time.
3. The response uses a verified source or states its uncertainty plainly.
4. The message includes only the minimum information necessary for the stated next step.
5. The correct human owner, escalation tag, and case status are recorded.

## References

[1]: https://www.twilio.com/docs/usage/webhooks/voice-webhooks "Twilio: Voice Webhooks"
[2]: https://developers.google.com/workspace/gmail/api/guides/push "Google for Developers: Configure push notifications in Gmail API"
