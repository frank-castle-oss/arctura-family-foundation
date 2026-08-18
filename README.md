# Arctura Family Foundation

> **Building accountable local infrastructure for dignified food access.**

This repository shares the public operating model, implementation approach, and web platform for **Arctura Family Foundation**, a working name for an initiative whose legal entity is **pending creation and final-name selection**. It is an open reference for food-recovery partners, community organizations, funders, delivery operators, and technologists interested in more reliable food-access systems.

## What this project is building

Arctura is designed as a **local-cell operating model**. Before a city activates public food-access delivery, it must establish responsible governance, verified local partners, food-safety controls, funded fulfillment capacity, and a clear path for exceptions.

The public platform currently includes a transparent partnership-formation site, partner and recipient-referral intake workflows, a funder and sponsor inquiry flow, an editorial layer, and local planning pages for Los Angeles, Austin, and Denver. The city pages are **planning pages**. They do not represent active delivery coverage, real-time inventory, or a promise of service.

| Area | Public status |
| --- | --- |
| Partner intake | Implemented with a minimal-data workflow |
| Recipient referral intake | Implemented; not an emergency-service or delivery guarantee |
| Funder and sponsor intake | Implemented with commercial and charitable-flow separation |
| Editorial field notes | Implemented as source-aware original commentary |
| Local planning pages | Implemented for Los Angeles, Austin, and Denver |
| Public food delivery | Not active |
| Tax-deductible donation rail | Not represented as active until a qualified entity or fiscal-sponsorship structure is confirmed |

## Architecture

The application uses React, TypeScript, Vite, Express, tRPC, Drizzle, and a MySQL-compatible database. Shopify is reserved for clearly labeled **commercial** products and services; it is not used to process charitable gifts.

```text
Public site → typed tRPC procedures → validated intake contracts → operations database
                                       ↘ commerce adapter → Shopify checkout for paid offerings
```

The database schema intentionally collects only the information required to begin a conversation: partner and contact details, minimal referral-request details, support messages, and funding-interest context. It does not collect street addresses, payment details, health information, or identity documents through the public forms.

## Finance and contribution boundaries

Arctura keeps financial flows distinct. A paid digital product or service is a commercial transaction. A charitable contribution may only be described as such through a qualified entity or a valid fiscal-sponsorship arrangement with the required fund control and acknowledgement process. Grants, sponsorships, and vendor disbursements require their own approval and reconciliation paths.

> The materials in this repository are operational resources, not legal, tax, banking, food-safety, or professional advice. Local counsel, insurance, regulatory, and community review are required before any service activation.

## Repository guide

| Path | Purpose |
| --- | --- |
| `client/` | Public website, editorial pages, city planning pages, and intake experience |
| `server/` | Typed procedures, validation contracts, commerce boundary, and database helpers |
| `drizzle/` | Database schema and generated migrations |
| `references/` | Integration notes that do not contain credentials |
| `research-*.md` | Public-facing market, vendor, and payment-rail research records |
| `arctura-*-*.md` | Operating charter and staged operating-stack documentation |

## Local development

Install dependencies, then run the application and tests:

```bash
pnpm install
pnpm dev
pnpm check
pnpm test
```

Database changes are defined in `drizzle/schema.ts`. Generate a migration with `pnpm drizzle-kit generate`, review the generated SQL, and apply it through the project’s migration process. Never place database URLs, storefront tokens, private partner lists, recipient information, or payment credentials in source control.

## Contributing

We welcome contributions that strengthen privacy, accessibility, safeguarding, food-safety operations, local partner coordination, and transparent impact measurement. Please open an issue before proposing a large architectural change, and do not submit real recipient, donor, vendor, payment, or partner data.

## Public-sharing boundary

This public repository deliberately excludes environment files, deployment configuration, analytics identifiers, payment credentials, storefront tokens, private support submissions, database contents, and any operational material that could expose individuals or partner security.

For the public operating model, start with the [Arctura Foundation Operating Charter](./arctura-foundation-operating-charter.md) and the [staged operating stack](./arctura-operating-stack.md).
