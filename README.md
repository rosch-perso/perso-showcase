# Perso

Sales automation for personalized cold outreach. Perso pulls prospect data from a CRM, enriches it, and drafts individual outreach messages that a salesperson reviews before anything goes out.

Built solo by Robin Scheiwiller, a B2B sales professional, as a working tool for his own outbound process.

## What it does

- **CRM enrichment:** syncs prospects and accounts from the CRM and fills gaps in the data
- **AI drafting:** writes first-touch and follow-up messages per prospect, using web research and a library of past outreach with known outcomes (signed, meeting, replied, no response)
- **Trigger layer (in development):** multi-channel outreach across email and LinkedIn, with more channels planned
- **Human in the loop:** messages go into a manual send queue. Nothing is sent automatically.

## Design decisions

- Per-user funnels instead of one workspace-wide funnel, so each seller works their own pipeline
- No automated LinkedIn actions yet, only a manual task queue
- Email sending sits behind an `EmailSender` interface, so the provider can be swapped without touching the rest of the app
- The background worker runs as a Vercel route, triggered on a schedule by GitHub Actions that holds only a single secret

## Stack

- Next.js and TypeScript, deployed on Vercel
- Claude API for drafting and reasoning
- Neon Postgres with pgvector for prospect data and retrieval over past outreach
- GitHub Actions for scheduled jobs
- Unit-tested core logic (163 tests)

## Status

Working prototype, being prepared for a first internal test with real users. Roadmap: finish CRM sync, then the multi-channel trigger layer.

## Contact

Robin Scheiwiller, Zurich, Switzerland
