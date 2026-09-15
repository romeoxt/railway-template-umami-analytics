# Railway Template Composer Setup

## Marketplace listing

- **Title:** Deploy and Host Umami Analytics with Railway
- **Short description:** Privacy-friendly, self-hosted website analytics — PostgreSQL plus the official Umami Docker image.
- **Category:** Starters
- **Overview:** paste `README.md`

## Services

| Service | Source | Volume | Public HTTP |
| --- | --- | --- | --- |
| Umami | `ghcr.io/umami-software/umami:postgresql-latest` | — | Yes |
| Postgres | Railway PostgreSQL plugin | `/var/lib/postgresql/data` | No |

## Variables — Umami

| Variable | Value | Secret | Description |
| --- | --- | --- | --- |
| `DATABASE_URL` | `${{Postgres.DATABASE_URL}}` | Yes | Postgres connection |
| `DATABASE_TYPE` | `postgresql` | No | Required by Umami |
| `APP_SECRET` | `${{secret(64)}}` | Yes | Session encryption secret |
| `TRACKER_SCRIPT_NAME` | `umami` | No | Optional custom script name |

## Settings — Umami

- Enable public HTTP
- Tell users to change default login (`admin` / `umami`) after first deploy
