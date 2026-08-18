# Technical Architecture

## Design premise

Arctura is designed as an operating platform for accountable local food-access work. The architecture should make three things easier: collecting only the information needed to begin a conversation, separating mission funding from commercial activity, and preserving local decision-making with a consistent control layer.

## Public-facing flow

```text
Public information and field notes
        ↓
Partner, recipient-referral, support, and funding forms
        ↓
Typed validation contract
        ↓
Operations database and human review queue
        ↓
Qualified local partner action or transparent referral response
```

The public site must never portray planning information as live inventory, verified route availability, or a guaranteed service outcome.

## Data minimization

The initial operational schema is deliberately narrow. It supports partner applications, recipient-referral requests, support messages, and funding inquiries. It excludes address collection, identity verification, payment details, health data, recipient case files, and route-level delivery information from public forms.

| Record | Purpose | Examples of data held |
| --- | --- | --- |
| Partner intake | Begin qualification of a local organization | Organization, role, city, contact channel, capacity note |
| Recipient-referral request | Start a non-emergency local referral conversation | City, household-size range, contact email, requested referral type |
| Support case | Create a human follow-up path | Contact email, issue category, message |
| Funding inquiry | Qualify grant, sponsor, gift, or commercial-service interest | Contact, organization, interest type, non-sensitive context |

## Financial separation

Charitable contributions, commercial products, grants, sponsorships, and vendor payments require different treatment. The platform should not collapse them into a single “support” button or a single ledger category.

Commercial checkout can be handled by a storefront platform only for clearly labeled paid goods or services. A charitable gift pathway requires a qualified entity or an appropriate fiscal-sponsorship arrangement with fund control, acknowledgement, and recordkeeping. No public interface should claim tax deductibility until that structure is confirmed.

## Activation gates

No public city activation should proceed without evidence in four areas: governance, food safety, fulfillment, and finance. Each gate should have a named owner, an auditable approval, an exception process, and a review cadence.

## Contribution boundary

This document describes a proposed operational architecture. It is not legal, tax, security, food-safety, insurance, banking, or professional advice. Local counsel, regulators, insurers, community partners, and a qualified governance structure must review the program before it activates services.
