# Immich

## Source development guide

### Product and architecture

Self-hosted photo and video library with uploads, albums, search and mobile backup.

NestJS API/job workers in `server/`, SvelteKit browser client in `web/`, Flutter mobile app, Rust native core and Python machine-learning service. PostgreSQL and background services run via Compose.

### Requirements and local development

Docker Compose for deployment; mise-managed versions and tasks for development (see `mise.toml`).

Run these commands from the repository root unless a `cd` is shown:

```sh
mise install
mise tasks ls --all
```

These are source-defined entry points. Full dependency installation and service startup were not run during the portfolio maintenance audit; successful application deployment is not claimed.

### Environment configuration

Inspect `docker/example.env` and the component-specific environment templates before startup. Supply local database, service URLs and integration credentials through untracked environment files or a secret manager. Do not copy production credentials into tracked files.

### Testing

```sh
mise //server:test
```

The full application suite requires the dependencies and services described above. Shell changes in this maintenance pass were checked separately with syntax and mocked command tests; that does not replace integration testing.

### Deployment and integrations

Start with `docker/docker-compose.yml` and review image versions, persistent data paths, authentication, exposed ports and backups before production use. Integration implementations and configuration are in the source directories described above; generated API clients must stay in sync with server contracts.

### Source provenance and license

Imported from [immich-app/immich](https://github.com/immich-app/immich); upstream functionality and copyright belong to the original contributors. Local Git history begins with a 2026 source snapshot import, not historical authorship. The exact imported upstream revision is unknown. The upstream GitHub repository was created on 2022-02-03; the local year directory is organizational metadata.

Read [LICENSE](LICENSE) and nested license/notice files before redistribution; enterprise and bundled third-party components may use different terms. Restored root license text was retrieved verbatim from the official upstream repository during this maintenance pass.
