# Project Structure

This document describes the current repository layout for TikTok Miner.

## Root Directory

- `/app` - Main Next.js application, API routes, CLI, tests, and Prisma schema
- `/infra` - Deployment assets, including Docker, Fly.io, and Nginx config
- `/docs` - Project documentation and reference material
- `/tooling` - Repo-level helper scripts and shared utility types
- `/archive` - Historical notes and saved log output
- `/data` - Local configs, SQL helpers, sample scraped profiles, and exports
- `/specs` - Product and technical specifications

## Application Directory (`/app`)

### Product Surface

- `/app/app` - Next.js routes and server actions
- `/app/components` - Reusable UI and feature components
- `/app/hooks` - React hooks
- `/app/lib` - Core logic, integrations, services, and shared app types
- `/app/cli` - Bun CLI entrypoints and handlers

### Data And Tooling

- `/app/prisma` - Prisma schema and migrations
- `/app/scripts` - App-local scripts and workflow utilities
- `/app/config` - Test and tooling configuration
- `/app/e2e` - Playwright test suites and page objects
- `/app/__tests__` - Jest unit and integration tests

### Key Config Files

- `/app/package.json` - Primary script entrypoints and dependencies
- `/app/.env.example` - Environment template
- `/app/next.config.mjs` - Next.js configuration
- `/app/tsconfig.json` - TypeScript configuration

## Infrastructure Directory (`/infra`)

- `/infra/docker/Dockerfile` - Container build for the app image
- `/infra/docker/docker-compose.yml` - Local multi-service stack
- `/infra/fly/fly.toml` - Fly.io deployment configuration
- `/infra/nginx/nginx.conf` - Reverse proxy configuration

## Tooling Directory (`/tooling`)

- `/tooling/scripts` - Repo-level maintenance and data helper scripts
- `/tooling/types` - Shared utility types that are not part of the app runtime

## Archive Directory (`/archive`)

- `/archive/logs` - Saved troubleshooting logs and one-off outputs
- `/archive/notes` - Historical repo notes that are no longer source-of-truth docs

## Documentation Directory (`/docs`)

- `/docs/project-structure.md` - This structure guide
- `/docs/creator-discovery-architecture.md` - System architecture reference
- `/docs/deployment-guide.md` - Deployment workflows and environment notes
- `/docs/testing-guide.md` - Testing workflows

## Source Of Truth

Some older documents still refer to earlier project names and experiments. For current runtime behavior, prefer:

- `/app/package.json`
- `/app/.env.example`
- `/app/app`
- `/infra/docker/docker-compose.yml`
- `/infra/fly/fly.toml`
