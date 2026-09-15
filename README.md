# Deploy and Host Umami Analytics with Railway

Privacy-friendly, self-hosted website analytics — PostgreSQL plus the official Umami Docker image.

## About Umami

[Umami](https://umami.is/) is an open-source analytics platform that tracks page views, referrers, and devices without cookies or heavy JavaScript. It is a common Reddit recommendation for hobby sites, portfolios, and MVPs that want real traffic numbers without Google Analytics.

## About Hosting Umami

Self-hosting Umami gives you full control over your analytics data. This template runs Umami from the official container image with PostgreSQL on Railway — no server management, automatic networking between services, and persistent storage via a Postgres volume.

## Environment Variables

| Variable | Description | Secret | Example/Notes |
| --- | --- | --- | --- |
| `DATABASE_URL` | PostgreSQL connection for Umami | Yes | `${{Postgres.DATABASE_URL}}` |
| `DATABASE_TYPE` | Database driver Umami expects | No | `postgresql` |
| `APP_SECRET` | Session encryption secret | Yes | `${{secret(64)}}` |
| `TRACKER_SCRIPT_NAME` | Custom script filename (optional) | No | `umami` |

## Deploy and Host

1. Create a new Railway project.
2. Add **PostgreSQL** and attach a **volume** at `/var/lib/postgresql/data`.
3. Add a **Docker** service with image `ghcr.io/umami-software/umami:postgresql-latest`.
4. Set the environment variables above on the Umami service.
5. Enable **public HTTP** on Umami and deploy.
6. Open the Umami URL and log in with default credentials (`admin` / `umami`), then **change the password immediately**.
7. Register your website in the Umami dashboard and paste the tracking script into your HTML.

## Common Use Cases

- Personal blogs and portfolios that need traffic stats without a cookie banner
- Side projects and MVPs validating which pages get read
- Community sites tracking referrers from newsletters or social posts
- Replacing Google Analytics on small sites where you own the data

## Dependencies for Umami Hosting

The Railway template includes:

- **Umami** — `ghcr.io/umami-software/umami:postgresql-latest`
- **PostgreSQL** — `postgres:17` (or Railway PostgreSQL plugin) with persistent volume

## Deployment Dependencies

- [Umami documentation](https://umami.is/docs)
- [Umami self-hosting guide](https://umami.is/docs/guides/self-host)
- [Railway PostgreSQL docs](https://docs.railway.com/databases/postgresql)

## Why Deploy Umami on Railway?

Railway provisions Postgres, private networking, and public HTTPS in one project. You get a working analytics dashboard in minutes instead of configuring VPSes, reverse proxies, and database backups by hand.

## Template Content

| Service | Source |
| --- | --- |
| Umami | `ghcr.io/umami-software/umami:postgresql-latest` |
| Postgres | `postgres:17` |

## Marketing site

See `website/index.html` for the template landing page.

## Author

romeoxt — herbylegall9@gmail.com

## License

MIT (this template guide). Umami is MIT-licensed separately.
