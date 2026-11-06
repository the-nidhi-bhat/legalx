# Setup and integrations

1. Install Node 24 and pnpm 12.
2. Copy `.env.example` to a local environment file; never commit it.
3. Run `pnpm install` and `pnpm dev`.
4. Without credentials, use Explore the demo. It is deterministic and clearly labelled.
5. For production identity and persistence, create a Supabase project, enable Auth and Storage, apply migrations, then configure RLS before exposing real documents.
6. Add `GEMINI_API_KEY` only to server-side environment variables and validate model output before persistence.
7. Configure a Sepolia RPC endpoint and contract address. Use a dedicated test wallet; never put private keys in browser code.
8. Deploy to Vercel with the same environment variables and run migrations before inviting users.

External credentials and deployment approvals are intentionally not included in this repository.
