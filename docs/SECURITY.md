# Security and trust boundaries

- Keep Supabase service-role credentials and Gemini credentials server-side.
- Use Supabase Row Level Security for every user-owned table and organization membership.
- Store private documents in private buckets and issue short-lived signed URLs.
- Validate MIME type, size, filename and malware scanning status for uploads.
- Re-verify every new agreement version before execution.
- Require wallet confirmation for every write; never request seed phrases or private keys.
- Treat webhook signatures, idempotency keys, rate limits and audit logs as mandatory for production routes.
- Hashing, parity and blockchain execution are technical evidence, not legal advice or a finding of enforceability.

Production blockers are intentionally surfaced in the UI when integrations are not configured.
