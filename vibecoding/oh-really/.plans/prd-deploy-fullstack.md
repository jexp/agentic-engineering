# PRD: Deploy Oh-Really! as a Full-Stack Web App

## Overview

Deploy the "Oh-Really!" O'Reilly-style meme generator as a publicly accessible full-stack
application. Users authenticate with GitHub OAuth, generate memes (via AI or from the existing
animal library), which are stored in S3 and indexed in Neo4j. A public gallery lets anyone browse
all memes, and each meme gets a shareable permalink.

Current state: static `index.html` + local `/images/` folder.
Target state: FastAPI backend + Next.js (TypeScript) frontend + Neo4j + S3.

## Goals

- Make the app publicly deployable and usable without local setup.
- Persist user accounts and their generated meme history in Neo4j.
- Store all meme images durably in S3.
- Support GitHub OAuth so users don't need a separate account.
- Provide a public gallery with permalinks for social sharing.
- Maintain the existing animal library as an alternative to AI generation.

## Non-Goals

- Multi-tenancy or teams.
- Paid tiers or rate limiting (beyond basic abuse protection).
- Mobile app.
- Social features (likes, comments, follows).
- Deletion / moderation of other users' memes.
- Support for OAuth providers other than GitHub.

## Requirements

### Functional Requirements

- REQ-F-001: Users can sign in via GitHub OAuth (GitHub as the sole OAuth provider).
- REQ-F-002: Authenticated users can generate a meme by selecting one of the pre-existing animal
  images from the library and providing a title / caption.
- REQ-F-003: Authenticated users can generate a meme via AI image generation (DALL-E or Replicate)
  using the existing prompt template from `odd-animals.md`.
- REQ-F-004: Generated meme images (both library-overlay and AI-generated) are uploaded to an S3
  bucket. The S3 key format is `memes/{user_id}/{uuid}.png`.
- REQ-F-005: After upload, the meme's S3 URL and metadata (title, animal concept, creator user_id,
  created_at) are stored as a `(:Meme)` node in Neo4j, linked to the `(:User)` node via
  `[:CREATED]`.
- REQ-F-006: User accounts (GitHub id, username, avatar URL, email, created_at) are stored as
  `(:User)` nodes in Neo4j and upserted on each login.
- REQ-F-007: A public gallery page lists all memes (paginated, most recent first) with thumbnail,
  title, creator username, and a "Copy link" button.
- REQ-F-008: Each meme has a permalink (`/meme/{meme_id}`) viewable without authentication.
- REQ-F-009: Authenticated users have a "My Memes" page showing only their creations.
- REQ-F-010: The frontend is implemented in Next.js with TypeScript (App Router). The current
  `index.html` is replaced; the existing animal images in `/images/` are migrated into
  `public/images/`.

### Non-Functional Requirements

- REQ-NF-001: All secrets (Neo4j URI/user/password, AWS credentials, S3_BUCKET, GitHub OAuth
  client_id/secret, AI API key) are read from `.env` and never committed.
- REQ-NF-002: Backend API is a FastAPI application; endpoints documented via auto-generated OpenAPI
  at `/docs`.
- REQ-NF-003: Integration tests cover all backend API endpoints and run against a real Neo4j
  instance and a real (or localstack) S3 bucket, with credentials from `integration.env`.
- REQ-NF-004: S3 bucket must have public-read enabled for the `memes/` prefix so that generated
  image URLs are directly embeddable.
- REQ-NF-005: Sessions are managed via a signed JWT (stored in an httpOnly cookie); no server-side
  session state.

## Technical Considerations

### Backend (Python / FastAPI)

Directory: `backend/`

- **GitHub OAuth flow**: `GET /auth/github` → redirect to GitHub; `GET /auth/github/callback` →
  exchange code for token, fetch user profile, upsert `(:User)` in Neo4j, issue JWT cookie, redirect
  to frontend.
- **Neo4j**: use the official `neo4j` Python driver (>=6.0). Connection pool via a singleton driver
  instance. Credentials: `NEO4J_URI`, `NEO4J_USER`, `NEO4J_PASSWORD` in `.env`.
- **S3**: use `boto3`. Credentials: `AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`, `AWS_REGION`,
  `S3_BUCKET` in `.env`.
- **AI generation**: call DALL-E (`OPENAI_API_KEY`) or Replicate (`REPLICATE_API_TOKEN`) depending
  on which key is present; result is a PNG bytes blob uploaded directly to S3.
- **Library overlay**: use `Pillow` to composite a title/caption onto one of the existing animal
  images; result uploaded to S3.

Key endpoints:
```
GET  /auth/github              — start OAuth flow
GET  /auth/github/callback     — OAuth callback
GET  /auth/me                  — current user (requires JWT)
POST /memes/generate           — create meme (AI or library overlay)
GET  /memes                    — public gallery (paginated)
GET  /memes/{meme_id}          — single meme
GET  /memes/mine               — current user's memes (requires JWT)
```

### Frontend (Next.js / TypeScript)

Directory: `frontend/`

- App Router (`app/` directory).
- Auth state via a `useSession` hook that reads the JWT cookie (or calls `GET /auth/me`).
- Pages: `/` (gallery), `/generate` (meme creator), `/meme/[id]` (permalink), `/me` (my memes).
- Animal library images migrated to `frontend/public/images/`.
- Tailwind CSS for styling (consistent with existing project aesthetic).

### Integration Tests

Directory: `backend/tests/integration/`

- Framework: `pytest` + `httpx.AsyncClient` (ASGI transport — no real network call needed for
  FastAPI).
- Fixtures: `neo4j_driver` (connects to test Neo4j from `integration.env`), `s3_client` (uses
  localstack or real bucket from `integration.env`), `auth_token` (mocked JWT for authenticated
  routes).
- Test coverage: all 7 endpoints listed above, including error paths (unauthenticated, meme not
  found, missing fields).

### Neo4j Data Model

```cypher
(:User {id, github_id, username, avatar_url, email, created_at})
(:Meme {id, title, concept, s3_url, generation_type, created_at})
(:User)-[:CREATED]->(:Meme)
```

## Acceptance Criteria

- [ ] `GET /auth/github` → `/auth/github/callback` flow completes and sets a JWT cookie.
- [ ] A `(:User)` node is created/updated in Neo4j on login.
- [ ] `POST /memes/generate` with `type=library` uploads a Pillow-composited PNG to S3 and creates
  a `(:Meme)` node linked to the user.
- [ ] `POST /memes/generate` with `type=ai` calls the AI API, uploads result to S3, creates node.
- [ ] `GET /memes` returns paginated meme list without authentication.
- [ ] `GET /memes/{id}` returns a single meme with creator info.
- [ ] Next.js gallery page renders memes from `GET /memes`.
- [ ] `/meme/[id]` page works as a shareable permalink.
- [ ] All integration tests pass against a real Neo4j instance (`pytest backend/tests/integration`).
- [ ] No secrets appear in committed files; `.env.example` documents all required keys.

## Out of Scope

- Deployment infrastructure (CI/CD, Docker, Vercel/Fly.io config) — deferred to a follow-on PRD.
- Admin moderation panel.
- Deleting memes.
- Rate limiting / abuse protection.
- Email notifications.

## Open Questions

- [ ] Which AI provider to prefer when both `OPENAI_API_KEY` and `REPLICATE_API_TOKEN` are set?
      (Suggest: DALL-E as default, Replicate as fallback.)
- [ ] Should the S3 bucket be newly created, or will an existing bucket be used? (Affects IAM
      policy guidance in `.env.example`.)
- [ ] Text overlay on library images: fixed font/position, or user-configurable font size/color?
- [ ] Pagination size for gallery — default 20 per page?
