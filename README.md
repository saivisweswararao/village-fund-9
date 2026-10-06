# Village Fund — Cloudflare + Supabase

Cloudflare Workers/static hosting + Supabase Auth/Postgres/RLS/Edge Functions.

## Routes
- `/` — active villages
- `/?village=penubaka` — village page
- `/admin/login.html` — admin login
- `/admin/dashboard.html` — dashboard
- `/admin/onboard-village.html` — super-admin onboarding

## Setup
1. Run `database/schema.sql` in Supabase SQL Editor.
2. Create the first Supabase Auth user and insert its `profiles` row as `super_admin`.
3. Set Supabase URL + publishable key in `public/js/config.js`.
4. Deploy the three Edge Functions under `supabase/functions` and configure secrets.
5. `npm install`, `npx wrangler login`, `npx wrangler deploy`.

Never put a Supabase service-role key or PhonePe secret in frontend code.

The PhonePe functions contain an adapter placeholder because the exact PhonePe PG API/authentication/signature flow must match the merchant product/account and current PhonePe documentation; do not deploy the placeholder as a live payment integration.
