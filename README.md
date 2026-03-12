# TikTok Miner

TikTok Miner is a creator discovery and analytics application. The active codebase is a Next.js app in `app/` with a web UI, API routes, Prisma-backed persistence, and a Bun-powered CLI.

## What It Does

- discovers creator profiles from keyword-based search workflows
- stores and browses creators in a dashboard at `/creators`
- runs scraping and pipeline-style discovery flows from `/scraper`
- supports analytics, filtering, export-oriented workflows, and automated tests

## Repo Layout

```text
tiktok-minor/
├── app/                  # Main Next.js application and CLI
├── infra/                # Deployment, container, and platform config
├── docs/                 # Project documentation and reference guides
├── tooling/              # Repo-level helper scripts and shared types
├── archive/              # Historical notes and log captures
├── data/                 # Local fixtures, configs, and sample outputs
└── specs/                # Product and technical specs
```

Key app directories:

```text
app/
├── app/                  # Next.js routes and API endpoints
├── cli/                  # Bun CLI commands
├── components/           # React components
├── lib/                  # Business logic, integrations, utilities
├── prisma/               # Prisma schema and migrations
├── config/               # Tooling config, including Playwright
└── .env.example          # Environment template
```

Infrastructure directories:

```text
infra/
├── docker/               # Dockerfile and compose stack
├── fly/                  # Fly.io deployment config
└── nginx/                # Reverse proxy config and TLS mounts
```

## Prerequisites

- Bun 1.2+
- Node.js 20+
- PostgreSQL or Supabase Postgres

## Getting Started

```bash
git clone https://github.com/aquaright1/tiktok-minor.git
cd tiktok-minor/app
bun install
cp .env.example .env.local
```

Update `.env.local` with the values your environment needs. The application expects database and Supabase settings at minimum:

```bash
DATABASE_URL=postgresql://...
DIRECT_URL=postgresql://...
NEXT_PUBLIC_SUPABASE_URL=https://...
NEXT_PUBLIC_SUPABASE_ANON_KEY=...
NEXT_PUBLIC_APP_URL=http://localhost:3000
```

Optional integrations already wired in the template include:

- `OPENAI_API_KEY`
- `GITHUB_TOKEN`
- `AZURE_EMAIL_CONNECTION_STRING`
- SMTP settings

## Run The App

From `app/`:

```bash
bun x prisma generate
bun run dev
```

The web app runs on [http://localhost:3000](http://localhost:3000). The root route redirects to `/creators`.

## Useful Commands

Run these from `app/`:

```bash
# Web app
bun run dev
bun run build
bun run start

# CLI
bun run cli

# Database
bun run prisma:generate
bun run prisma:migrate:deploy

# Tests
bun run test
bun run test:integration
bun run test:e2e
bun run test:coverage
```

## Docker

The repo keeps container and deployment config under `infra/`:

```bash
docker compose -f infra/docker/docker-compose.yml up -d
docker compose -f infra/docker/docker-compose.yml logs -f
docker compose -f infra/docker/docker-compose.yml down
```

Check the compose file before first run and make sure the required environment variables are available to the app container. Fly.io configuration now lives at `infra/fly/fly.toml`.

## Documentation

- [App README](./app/README.md)
- [API setup guide](./docs/API_SETUP_GUIDE.md)
- [Project structure](./docs/project-structure.md)
- [Creator discovery architecture](./docs/creator-discovery-architecture.md)
- [Deployment guide](./docs/deployment-guide.md)
- [Testing guide](./docs/testing-guide.md)

## Notes

Some older documentation in this repository still refers to earlier project names and adjacent experiments. When in doubt, treat `app/package.json`, `app/.env.example`, and the live route structure under `app/app/` as the source of truth.
