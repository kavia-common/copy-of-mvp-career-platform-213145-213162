# CareerPlatformDatabase

This workspace contains optional database tooling and visualization for the Career Platform. For the current MVP and local development flows, the Backend API persists to a local SQLite file by default (no external DB required).

## Current Usage

- The FastAPI backend uses SQLite via SQLAlchemy by default.
- A PostgreSQL instance is optional and not required for basic CRUD or feature flows.
- SQLite file path is controlled by the backend environment (see backend README).

## Docker Compose (project stack)

The project’s `docker-compose.yml` at the repo root brings up:
- Node RoleMappingService (port 4000)
- FastAPI Backend (port 3001, SQLite)
- React Frontend (port 3000)

A dedicated database container is not included in the compose stack because the MVP runs on SQLite for local development. You can still use the scripts in this workspace (e.g., backups, visualization) if you bring your own database; however, that is outside the default compose workflow.

## Where data lives

- SQLite file (default): created by the backend in its working directory (in compose, `/app/career_platform.db` inside the backend container).
- JSON ingestion files: `./data/imports` at the repository root, mounted into services at `/app/data/imports`.

## Notes

- See the backend README for environment variables that control SQLite path and JSON ingestion (`SQLITE_PATH`, `SEED_FROM_JSON`, `INGESTION_JSON_DIR`).
- See `kavia-docs/06-runbook.md` for Excel-to-JSON conversion and seeding guidance.
