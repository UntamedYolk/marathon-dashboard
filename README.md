# Marathon Dashboard

Private-data running dashboard (React + Vite + Supabase Auth), hosted as a PWA on GitHub Pages.

## Setup

1. Set GitHub Actions repository variables **VITE_SUPABASE_URL** and **VITE_SUPABASE_PUBLISHABLE_KEY** (Supabase project Settings → API Keys). The publishable key is browser-safe; never use service_role/secret keys.
2. In GitHub repository Settings → Pages, choose **GitHub Actions** as Build and deployment source.
3. In Supabase Authentication, create your user and disable public signups. Authorize the user's UUID in dashboard_private.allowed_users. No user is allowed by default.
4. Push to main; the GitHub Actions workflow builds and deploys to https://untamedyolk.github.io/marathon-dashboard/.

The app uses read-only public.dashboard_activities and public.dashboard_training_notes views with security_invoker and RLS on the underlying running schema. A login alone is not sufficient: the UUID must be allowlisted.

Local development: copy .env.example to .env.local, supply public credentials, run npm install and npm run dev.

Deployment triggered after repository variables were configured.
