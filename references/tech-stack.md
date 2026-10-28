# Tech stack: how bhai recommends one

The user is a full-stack developer, not tied to one framework. bhai gives **2–3 options with trade-offs**, then says which one he leans toward and why. The goal: the simplest stack that ships the MVP fast **and** won't need a rewrite if the product grows.

## Questions that decide the stack

Answer these from the conversation (ask if unknown) before recommending:

- **What does the app mostly do?** Content and SEO pages, a logged-in dashboard, real-time features (chat, live updates), heavy data or file processing, payments, AI features?
- **Who builds and maintains it?** Default: the user alone. Favor tools they know, and managed services over self-run servers.
- **Where are the users?** Affects hosting region, payment providers (e.g. Stripe for Australia; eSewa/Khalti for Nepal; check what's available locally), and language support.
- **Budget:** free tiers vs. paid. Note where costs jump as usage grows.
- **Realistic scale:** users at launch and in a year. Don't over-engineer for millions of users on day one, but avoid choices that block growth.

## Building blocks to choose from

Pick per layer and explain the why. These are common, solid choices, not a fixed list; check current versions and pricing before recommending.

- **Frontend / full-stack framework:** Next.js (React, strong SEO and server rendering), Remix / React Router, SvelteKit, Nuxt (Vue), Astro (content-heavy sites with islands of interactivity).
- **Backend (if separate):** Node.js with Hono, Fastify or NestJS; Python with FastAPI or Django; Go for high-performance services. Often a full-stack framework's server side is enough for an MVP.
- **Database:** PostgreSQL as the safe default (via Supabase, Neon, or a managed provider). Use an ORM like Prisma or Drizzle. Consider Redis for caching/queues only when needed.
- **Auth:** Supabase Auth, Clerk, Auth.js / Better Auth. Don't build auth from scratch for an MVP.
- **Files and media:** S3-compatible storage (AWS S3, Cloudflare R2, Supabase Storage).
- **Payments:** Stripe where available; local gateways where needed.
- **Hosting:** Vercel or Netlify (frontend/full-stack), Railway, Render or Fly.io (servers, background jobs), Cloudflare (edge, CDN).
- **Email:** Resend, Postmark.
- **Observability:** Sentry for errors; simple product analytics (PostHog, Plausible).
- **3D / motion (if used):** Three.js / React Three Fiber, GSAP, Spline. See design-direction.md.

## How to present the options

For each option:

- **Stack:** one line per layer
- **Good for:** when this option shines
- **Trade-offs:** what's harder, slower or more expensive
- **Scaling path:** what changes when users grow (e.g. "add a job queue", "move heavy work to a separate service")
- **Rough running cost:** free-tier friendly or not (no exact prices unless checked)

Then: **"bhai leans toward Option X because…"** in 2–3 sentences tied to this idea.

## Scalability principles to explain to the user

Keep these short and practical:

- Start as one well-organized app (a "modular monolith"). Split into separate services only when there's a clear reason.
- Keep the app stateless so it can run on more servers later; put state in the database, cache or storage.
- Move slow work (emails, file processing, AI calls) to background jobs.
- Add indexes for the queries that matter; measure before optimizing.
- Use managed services so the solo builder isn't running servers at 2 a.m.

## Tech audit (existing products)

Check, biggest risks first:

1. **Security:** auth and permissions, secrets in code, input validation, dependency vulnerabilities.
2. **Data:** backups, database design, migrations, personal data handling.
3. **Performance:** page speed (Core Web Vitals), large bundles, heavy 3D/images, slow queries.
4. **Reliability:** error tracking, logging, what happens when a service fails.
5. **Maintainability:** code structure, tests on critical paths, outdated dependencies, deploy process.

For each finding: what's wrong, why it matters, and the fix.
