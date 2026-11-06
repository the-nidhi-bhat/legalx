# Testing checklist

Run `pnpm exec tsc --noEmit` for the TypeScript baseline and `pnpm build` for the production build.

Manual critical path:

- Landing page to Explore demo.
- Create agreement stepper from description to verification.
- Parity verification success.
- Simulate tampering and confirm Continue to execution is disabled.
- Restore approved parameters and confirm execution unlocks.
- Simulate wallet/deployment and progress milestones.
- Open every sidebar route, including settings, profile, notifications and activity.
- Check mobile layout at 311px and desktop layout at 1280px.

Supabase, Gemini, Sepolia and smart-contract tests remain unverified until their credentials and deployment artifacts are configured.
