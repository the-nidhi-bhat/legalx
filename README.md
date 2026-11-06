# LEGALX

A dark, mobile-first product prototype for turning plain-language agreements into structured Contract IR, independently verifying legal-to-code parity, and simulating milestone escrow execution on Sepolia.

> Drafting assistance, not legal advice. Demo transactions are simulated and no real funds move.

## Product surface

- Marketing landing page with product narrative, verification proof, image-led hero, and responsive navigation.
- Demo launch flow into an authenticated-looking workspace shell.
- Agreement creator: describe, clarify, review, generate, and verify.
- Agreements, parity verification, smart-contract execution, milestones, transactions, activity, notifications, team, profile, and settings pages.
- Functional local prototype controls: tamper simulation, wallet/deployment simulation, milestone state transitions, profile editing, notification preferences, settings save states, and mobile navigation.
- Source map and security boundary documented in `docs/`.

## Architecture

```mermaid
flowchart LR
  A[Landing page] --> B[Workspace shell]
  B --> C[Agreement creator]
  C --> D[Contract IR]
  D --> E[Human-readable agreement]
  D --> F[Smart contract config]
  E --> G[Parity engine]
  F --> G
  G -->|pass| H[Sepolia escrow deployment]
  G -->|mismatch| I[Deployment blocked]
  H --> J[Milestones and evidence]
  B --> K[Profile, notifications, settings]
  K -. future .-> L[(Supabase)
  K -. future .-> M[Gemini API]
  F -. future .-> N[Wallet + RPC]
  E -. future .-> O[Supabase Storage]
```

## Run locally

```bash
pnpm install
pnpm dev
```

Open `http://localhost:3000`.

## Production integration checklist

The current UI is intentionally safe and local-only. Before enabling real users or funds, connect:

1. Next.js frontend hosting on Vercel.
2. Supabase project for Auth, Postgres, Row Level Security, and Storage.
3. Gemini API for server-side extraction and clarification, never from the browser.
4. Authentication with email/password, verified sessions, role checks, and protected routes.
5. Contract IR schema and migrations for agreements, versions, fields, parity reports, wallets, deployments, milestones, and audit events.
6. Sepolia RPC endpoint and a funded test wallet held in server-side deployment infrastructure.
7. OpenZeppelin escrow contract deployment with tests, reentrancy protection, pull-based releases, dispute pause, and event indexing.
8. Wallet integration using a supported connector and explicit chain/network checks.
9. File storage with private buckets, signed URLs, malware scanning, document versioning, and retention policy.
10. Environment variables from `.env.example`; never commit `.env` files, credentials, private keys, or service-role keys.

See `docs/SETUP.md`, `docs/ARCHITECTURE.md`, `docs/SECURITY.md`, and `docs/TESTING.md` for the implementation boundary and next steps.

## Verification

The prototype can be tested without external credentials:

- Launch application or Explore the demo from the landing page.
- Navigate to Parity verification and use **Simulate tampering** to confirm deployment is blocked.
- Restore approved parameters, open Smart contracts, connect the demo wallet, and simulate deployment.
- Open Milestones and move each milestone through Pending → Submitted → Released.
- Open Notifications, Profile, and Settings; change controls and verify the saved state.
- Resize to a mobile portrait viewport to verify the responsive sidebar and stacked cards.
