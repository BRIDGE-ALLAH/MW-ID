# MW-ID container deployment

This is a **single-node deployment starter** for the MW-ID fork. It builds the server image locally from this repository; it does not depend on a pre-published GHCR image.

> **Important:** this deploys the inherited Kanidm identity server with the MW-ID presentation layer. It does not by itself connect ARSY, implement MoonWitness ecosystem SSO, or establish production readiness. Those require separate integration contracts and end-to-end verification.

## Requirements

- Linux host with Docker Engine and the Docker Compose plugin.
- A DNS name dedicated to the identity service (the example uses `id.example.com`).
- A valid TLS certificate and private key for that exact DNS name.
- A persistent, backed-up storage location for the identity database.

The server uses TLS for its web interface. Keep LDAP disabled unless a reviewed requirement explicitly calls for it.

## 1. Configure the hostname

From this directory:

1. Point the DNS record for your identity hostname to the server.
2. Copy your certificate chain to `tls/fullchain.pem` and the matching private key to `tls/privkey.pem`.
3. Edit `server.toml`: set both `domain` and `origin` to the same real hostname. For example, if the public URL is `https://identity.example.org`, use `identity.example.org` for `domain` and `https://identity.example.org` for `origin`.

Do not deploy with the placeholder `id.example.com`. The hostname is security-sensitive for WebAuthn and registered credentials; changing it later can invalidate credentials and tokens.

## 2. Prepare protected files

The container runs as UID/GID `1000:1000`. Prepare the directories and files on the host:

```sh
mkdir -p data/backups tls
# Place fullchain.pem and privkey.pem in tls/ before continuing.
sudo chown -R 1000:1000 data
sudo chmod 0750 data data/backups
sudo chown root:1000 server.toml tls/fullchain.pem tls/privkey.pem
sudo chmod 0440 server.toml tls/privkey.pem
sudo chmod 0444 tls/fullchain.pem
```

Keep the private key out of Git, backups that are publicly accessible, and container images. The configuration and key should be read-only to the service process.

## 3. Validate and start

```sh
docker compose config
docker compose build --pull
docker compose up -d
docker compose ps
docker compose logs -f identity
```

The service listens on TCP port `8443` with TLS. Restrict inbound access with the host firewall to the intended clients or reverse proxy. If a reverse proxy terminates public TLS, configure the upstream connection securely and review the server's trusted-proxy settings before forwarding client IP headers.

## 4. Verify before onboarding users

- Confirm the container is healthy: `docker compose ps`.
- Open `https://YOUR_REAL_HOSTNAME:8443` and verify the certificate and hostname.
- Complete an administrator bootstrap using the official Kanidm administration guide for the exact server version.
- Test sign-in, sign-out, account recovery, MFA/passkey enrollment, and a backup/restore exercise in a non-production environment.
- Verify that the configured backup directory contains fresh backups and that restore has been rehearsed.

Do not expose this service to production users until those checks, firewall review, backup restoration, and an independent security review are complete.

## Operations

```sh
docker compose logs -f identity
docker compose restart identity
docker compose down
```

The database and backups are stored under `data/`. Preserve this directory during upgrades. Back it up off-host with encryption and test restoration regularly. Never run two writers against the same database directory.

## Upgrade

Rebuild from a reviewed commit, then recreate the service:

```sh
git pull --ff-only
docker compose build --pull
docker compose up -d
```

Review release notes and backup the database before each upgrade. Do not skip supported upgrade steps or assume a rollback is safe after a database migration.

## Architecture boundary

- **MW-ID:** this fork's identity infrastructure direction and presentation layer.
- **MoonWitness ID:** the intended human-facing identity journeys.
- **ARSY:** the separately documented ecosystem authority for canonical identity and authorization.
- **Kanidm:** the inherited identity engine and upstream technical foundation.

A working MW-ID server does not prove ARSY integration or cross-service SSO. Those are separate milestones and must be tested with real issuer, audience, redirect, callback, logout, session, and revocation flows.
