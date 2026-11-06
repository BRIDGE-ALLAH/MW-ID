# MW-ID
## Identity Infrastructure for the MoonWitness Universe

**One identity. A connected universe.**

MW-ID is the identity-infrastructure initiative for the MoonWitness Universe and the wider A-L-L-A-H.COM ecosystem. Its purpose is to provide a clear, secure, and interoperable foundation for identity, authentication, and controlled access across connected digital services.

Identity is more than a login screen. It is the trust boundary that helps people and services establish who or what is acting, what access is permitted, and how that access can be reviewed or revoked.

> **Project status:** This repository currently contains a codebase forked from [Kanidm](https://github.com/kanidm/kanidm). The MW-ID branding and product direction described here do not, by themselves, mean that MoonWitness integrations, ARSY authority, or production SSO are implemented. Those capabilities must be verified independently before being claimed.

## Vision

Build a dependable identity foundation that can grow with the MoonWitness ecosystem: secure by design, understandable to people, interoperable across applications, and governed by explicit authority and accountability.

## Mission

- Provide a consistent identity foundation for connected MoonWitness services.
- Support secure authentication and deliberate access management.
- Keep human identities, service identities, credentials, secrets, and authorization policies conceptually and technically distinct.
- Enable integrations through documented contracts and established protocols.
- Protect privacy through least privilege, clear boundaries, and revocable access.
- Make security and operational claims evidence-based and auditable.

## Core principles

### Identity with purpose
Every identity has a defined subject, owner, context, and lifecycle.

### Security by design
Secure defaults, careful boundaries, and explicit authorization are foundational requirements—not optional additions.

### Trust through evidence
Authentication, session state, permissions, and security events must be grounded in verifiable system responses.

### Privacy by default
Personal and sensitive information is exposed only when necessary and authorized.

### Human accountability
Technology supports people and institutions; it does not claim moral, legal, or divine authority.

### One connected ecosystem
Applications may share an identity foundation while retaining separate product responsibilities and authorization decisions.

## Position in the ecosystem

| Component | Responsibility |
|---|---|
| **MW-ID** | Identity-infrastructure project and this repository's product direction |
| **MoonWitness ID** | Human-facing identity experience: sign-in, registration, account and session journeys |
| **ARSY** | The documented ecosystem authority for canonical identity, authentication, sessions, tenant context, and authorization |
| **MoonWitness XV** | Narrative, knowledge, research, chronicles, and witness context |
| **A-L-L-A-H.COM** | The wider ecosystem and its connected digital services |

These names describe distinct responsibilities. Branding alignment does not merge their codebases or transfer authority. Any integration between this repository and ARSY or MoonWitness ID requires an explicit technical design, implementation, and verification.

## Product direction

MW-ID is intended to support an identity foundation that can serve both people and non-human service principals over time. The long-term direction may include:

- Human identity and account lifecycle.
- Service identities for applications, agents, and integrations.
- Credential and key lifecycle with scoped permissions and revocation.
- Session visibility and trust controls.
- Federation and application hand-off through explicit, verified protocol contracts.
- Auditable policy and security events.

These are product-direction statements, not assertions that each capability is implemented in this repository. Feature status must be established from source, tests, integration evidence, and release records.

## Technical foundation and upstream attribution

This repository is a fork of [Kanidm](https://github.com/kanidm/kanidm), an identity-management project. The existing source, architecture, dependencies, license obligations, notices, and upstream attribution must be preserved unless a reviewed technical and legal change explicitly establishes otherwise.

The current codebase should therefore be treated as a Kanidm-derived technical baseline—not as proof that a distinct MW-ID product integration is complete. Consult the [upstream Kanidm documentation](https://kanidm.github.io/kanidm/stable/) for the inherited engine's behavior and capabilities.

MW-ID is an independent project identity and is not an official Kanidm project or endorsed by the Kanidm maintainers.

## Scope boundaries

- MW-ID branding does not make this repository the canonical identity authority for the ecosystem.
- ARSY remains the documented authority for identity and authorization in the wider ecosystem architecture.
- A successful login does not grant access to every connected application.
- Cross-domain SSO must not be claimed until issuer, audience, redirect, cookie, callback, logout, and revocation behavior are verified end to end.
- Never claim passkeys, MFA, recovery, federation, or production readiness solely because an upstream dependency supports a related capability.

## Brand promise

**MW-ID — Identity is the foundation of trust.**

A connected universe begins with identity that is clear, secure, accountable, and worthy of trust.

## Further reading

- [Brand narrative and identity principles](BRANDING.md)
- [MoonWitness ID product definition](https://github.com/bjo163/A-L-L-A-H.COM/blob/main/apps/id/README.md)
- [MoonWitness ID blueprint](https://github.com/bjo163/A-L-L-A-H.COM/blob/main/apps/id/BLUEPRINT.md)
- [MoonWitness XV master vision](https://github.com/bjo163/moonwitnessxv/blob/main/docs/vision/MASTER_VISION_NARRATIVE_XV.md)
- [Kanidm upstream project](https://github.com/kanidm/kanidm)
