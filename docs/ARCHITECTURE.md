# LEGALX architecture

LEGALX is a Next.js App Router product prototype with a clear trust boundary between human-readable agreements, structured Contract IR, parity verification, and simulated or real blockchain execution.

## Current implementation

- `app/page.tsx`: interactive landing page and authenticated-style demo workspace.
- Demo state is intentionally local and visibly labelled; no transaction or legal outcome is fabricated.
- The parity gate blocks the execution screen when a critical parameter is tampered with.
- `public/legalx-hero.png` is an original generated visual asset used only for product storytelling.

## Planned production boundary

Supabase Auth/Postgres/Storage should own identity, organization isolation, agreement versions, evidence and audit records. Gemini calls must run in server routes, validate structured output against the existing IR schema, and require human approval. Sepolia transactions must be initiated by a connected wallet and recorded only after chain confirmation.

## Trust model

Hashing proves deterministic content integrity; parity proves supported structural/behavioral correspondence; neither is legal advice or a guarantee of enforceability. Every production verification record should pin agreement version, canonicalization version, IR version, engine version, timestamp, approval evidence and transaction reference.
