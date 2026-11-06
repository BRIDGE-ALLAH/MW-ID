# MW-ID ↔ ARSY integration plan

**Status: design gate — not integrated**

This document records the work required before MW-ID can be described as an ARSY-connected identity service. It is deliberately a plan, not a claim that an integration exists.

## Current verified foundation

- The repository contains the Kanidm identity server and its OAuth 2.0 / OpenID Connect provider implementation.
- The inherited server documents OIDC discovery at `/oauth2/openid/<client_id>/.well-known/openid-configuration`, an authorization endpoint, token endpoint, user-info endpoint, JWKS endpoint, token introspection, and token revocation.
- The inherited OIDC guidance calls for Authorization Code flow with PKCE S256 and ES256 ID-token signatures for compatible clients.
- The existing OAuth2 test suite exercises discovery metadata and a basic OIDC authorization flow.

These capabilities provide a possible protocol foundation. They do **not** establish that ARSY is configured as an upstream identity provider, that ARSY trusts MW-ID, or that identity/session state is synchronized between the systems.

## Architecture decision required

Before implementation, the owners of ARSY and MW-ID must decide which service is authoritative for each responsibility:

| Responsibility | Decision required |
|---|---|
| Canonical person / account identifier | Which system issues the immutable subject ID? |
| Authentication and credential lifecycle | Which system verifies credentials, MFA, passkeys, recovery, and account disablement? |
| Session authority | Which system creates, refreshes, expires, and revokes the user session? |
| Tenant context | Which system resolves tenant membership and tenant switching? |
| Authorization | Which system is authoritative for roles, groups, entitlements, and policy decisions? |
| Identity federation | Is MW-ID an OIDC provider for ARSY, an OIDC client of ARSY, or a broker with a clearly defined trust boundary? |

Do not implement bidirectional synchronization or dual-writer identity records. Choose one authoritative owner per field and define a controlled mapping for downstream consumers.

## Required integration contract

The ARSY owner must provide a versioned contract containing:

1. Issuer URL and discovery document, or confirmation that MW-ID is the issuer.
2. Client registration process, client type, exact redirect URIs, allowed grant types, and PKCE requirements.
3. Expected audience values and token signature algorithms.
4. Stable subject identifier and account-linking rules. Email address must not be used as the immutable account key.
5. Required claims and their semantics, including tenant, roles/groups, account status, and authentication context.
6. Token lifetime, refresh-token policy, logout behavior, revocation behavior, and key-rotation procedure.
7. Provisioning/deprovisioning ownership, disabled-account behavior, and incident response contacts.
8. Test issuer, test clients, non-production accounts, and a non-production callback environment.

No production client secret, signing key, TLS private key, or bearer token may be committed to this repository.

## Proposed protocol path (subject to the contract)

If ARSY confirms that it can consume MW-ID as an OIDC provider:

1. Register a distinct confidential OIDC client for each relying application.
2. Use the exact discovery URL published by the deployed issuer; do not hard-code token or JWKS endpoints in application code.
3. Use Authorization Code flow with PKCE S256 and exact HTTPS redirect URI allowlists.
4. Validate issuer, audience, signature, expiry, nonce, state, and PKCE at the relying application.
5. Map the stable subject identifier to the ARSY canonical account ID only through an explicit, audited mapping.
6. Request only the minimum scopes and claims required by each application.
7. Define logout and revocation semantics separately; ending a local application session must not be assumed to revoke every other service session.

If ARSY is instead the upstream OIDC provider, MW-ID needs a separately reviewed broker/federation design. Do not infer that capability or configuration from the existence of Kanidm's outbound OAuth2 client tooling.

## Security and acceptance tests

The integration is not ready for production until all of the following pass in a non-production environment:

- Discovery metadata has the expected issuer and HTTPS endpoints.
- Authorization Code + PKCE S256 succeeds; invalid verifier, state, or nonce is rejected.
- Wrong issuer, audience, signature, expired token, and unknown signing key are rejected.
- JWKS key rotation is handled without accepting untrusted keys.
- Stable subject mapping survives profile/email changes and prevents duplicate-account linking.
- Tenant and authorization claims are least-privilege, correctly scoped, and cannot be escalated by changing client-supplied values.
- Disabled/deprovisioned accounts cannot start new sessions; existing-session revocation behavior is documented and tested.
- Logout, refresh, revocation, and session expiry are tested across all participating services.
- Redirect URI validation rejects wildcard or unregistered destinations.
- Audit events identify authentication, consent, role/tenant changes, revocation, and administrative actions without logging secrets or raw tokens.
- Backup restoration and signing-key recovery have been rehearsed.

## Work sequence

1. **Contract:** obtain the ARSY integration contract and settle the authority table above.
2. **Threat model:** document trust boundaries, token theft/replay, account linking, tenant isolation, and revocation.
3. **Non-production client:** configure one test client and one test relying application.
4. **Adapter:** implement only the agreed protocol adapter and explicit claim mapping; keep it separate from inherited Kanidm core code where practical.
5. **End-to-end tests:** automate the acceptance tests above.
6. **Operational readiness:** configure secrets, TLS, monitoring, backups, key rotation, incident response, and rollback.
7. **Release gate:** security review and owner approval before production.

## Current blockers

- No ARSY issuer/client contract or test credentials are present in this repository.
- No production domain or TLS material has been supplied for the deployment.
- The container build and existing CI checks are still pending.
- No cross-service end-to-end authentication test has been executed.

Until these blockers are resolved, describe the repository as **MW-ID identity infrastructure with a Kanidm-based OIDC foundation**, not as an ARSY-integrated identity platform.
