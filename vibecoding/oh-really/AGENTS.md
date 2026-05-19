# AGENTS.md — Oh-Really! Full-Stack Meme Generator

## Project Overview
FastAPI backend + Next.js frontend meme generator. Users authenticate via GitHub OAuth,
generate O'Reilly-style memes (from animal library or AI), stored in S3, indexed in Neo4j.

## Feedback Instructions

### TEST COMMANDS
```bash
# Unit / integration tests (backend)
cd backend && python -m pytest tests/ -v

# Integration tests (require integration.env)
cd backend && python -m pytest tests/integration/ -v --env-file integration.env

# TypeScript type check (frontend)
cd frontend && npm run typecheck
# or: cd frontend && npx tsc --noEmit

# Frontend unit tests
cd frontend && npm test
```

### BUILD COMMANDS
```bash
# Backend: verify imports + startup
cd backend && python -c "from app.main import app; print('OK')"

# Frontend build
cd frontend && npm run build
```

### LINT COMMANDS
```bash
cd backend && python -m py_compile app/main.py app/db.py app/storage.py app/memes.py
cd frontend && npm run lint
```

### FORMAT COMMANDS
```bash
cd backend && python -m black app/ tests/
cd frontend && npm run format
```

## Architecture

```
backend/          FastAPI (Python 3.10+)
  app/
    main.py       FastAPI app, CORS, /health
    db.py         Neo4j singleton driver + Cypher helpers (task-002)
    storage.py    S3 upload helper (task-003)
    auth.py       GitHub OAuth + JWT (task-004)
    memes.py      Meme generation logic (task-005, 006)
    routes/       Endpoint routers (task-007)
  tests/
    integration/  pytest + httpx.AsyncClient; credentials from integration.env

frontend/         Next.js + TypeScript + Tailwind (App Router)
  src/
    app/          Pages: / /generate /meme/[id] /me
    hooks/        useSession.ts
    lib/api.ts    Typed fetch wrappers
  public/images/  Animal images (migrated from /images/)
```

## Conventions
- All secrets read from `.env` (never committed); `.env.example` documents keys
- load_dotenv() called at startup in backend/app/main.py
- Neo4j: neo4j>=6.0.0 package (not neo4j-driver); execute_query() API
- JWT: python-jose; httpOnly cookie; 7-day expiry
- S3 bucket must have public-read on memes/ prefix
- DALL-E preferred when OPENAI_API_KEY set; Replicate fallback when REPLICATE_API_TOKEN set

## Gotchas
- pyproject.toml build-backend must be "setuptools.build_meta" (not "setuptools.backends.legacy:build")
- backend/.gitignore excludes __pycache__ and .env — keep it
- load_dotenv() must run before any os.getenv() calls at module level
- fastclient (TestClient) can test FastAPI without a running server; use for unit tests
- .env.example write: use Python script (Write tool blocks dotenv-like patterns with real secret formats)
