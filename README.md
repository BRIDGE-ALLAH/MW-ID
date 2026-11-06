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

## Brand identity

### Brand essence
**Identity is the foundation of trust.**

MW-ID stands for a dependable identity layer: clear enough to understand, disciplined enough to secure, and open enough to connect services without erasing their boundaries.

### Brand attributes
- **Trustworthy:** precise, transparent, and evidence-led.
- **Calm:** confident without alarmism or exaggerated promises.
- **Human-centred:** respectful of people, privacy, and agency.
- **Connected:** designed for interoperability and clear service boundaries.
- **Accountable:** explicit about ownership, permissions, and limitations.

### Voice and writing
Use direct, plain, technically accurate language. Prefer “supports,” “is designed to,” and “verified” over absolute claims. Explain security decisions and limitations. Avoid mystical or authoritarian language in technical product copy, and never imply that software has divine, legal, or moral authority.

### Visual direction
The visual system should feel like a trustworthy identity infrastructure product rather than a generic consumer social network.

- **Primary palette:** midnight navy for stability; deep indigo for the identity layer; restrained cyan or teal for connection and active states; warm off-white for readable surfaces.
- **Neutral palette:** slate and graphite for body text, borders, and secondary surfaces.
- **Accent discipline:** use bright accents sparingly for links, focus, and meaningful status—not for decoration.
- **Typography:** use a highly legible sans-serif for interface and body text; reserve a restrained display weight for the MW-ID wordmark and major headings. Prefer system fonts where possible for performance and consistency.
- **Graphic language:** simple connected nodes, protected boundaries, rings, and pathways may communicate identity and trust. Avoid padlock clichés, surveillance imagery, religious symbols, and visual claims of absolute security.
- **Accessibility:** maintain WCAG-conscious contrast, visible keyboard focus, scalable text, and meaning that is never conveyed by color alone.

### Logo direction and usage
The preferred logo direction is a distinctive **MW-ID wordmark** paired, when useful, with a compact abstract mark suggesting a verified identity within a connected network. The mark should remain legible at small sizes and work in monochrome. Do not distort, rotate, add effects to, or place the logo on low-contrast backgrounds. Until an approved logo asset is committed, use the plain text wordmark **MW-ID**; do not treat an improvised icon as the official logo.

### Tagline
**One identity. A connected universe.**

Supporting brand promise: **Identity is the foundation of trust.**

## Product direction

MW-ID is intended to support an identity foundation that can serve both people and non-human service principals over time. The long-term direction may include:

- Human identity and account lifecycle.
- Service identities for applications, agents, and integrations.
- Credential and key lifecycle with scoped permissions and revocation.
- Session visibility and trust controls.
- Federation and application hand-off through explicit, verified protocol contracts.
- Auditable policy and security events.

These are product-direction statements, not assertions that each capability is implemented in this repository. Feature status must be established from source, tests, integration evidence, and release records.

## Scope boundaries

- MW-ID branding does not make this repository the canonical identity authority for the ecosystem.
- ARSY remains the documented authority for identity and authorization in the wider ecosystem architecture.
- A successful login does not grant access to every connected application.
- Cross-domain SSO must not be claimed until issuer, audience, redirect, cookie, callback, logout, and revocation behavior are verified end to end.
- Never claim passkeys, MFA, recovery, federation, or production readiness solely because an upstream dependency supports a related capability.

## Delivery roadmap

| Stage | Outcome | Completion evidence |
|---|---|---|
| **1. Brand foundation** | Consistent name, promise, voice, and ecosystem positioning | This README and approved brand assets |
| **2. Repository clarity** | Clear upstream attribution, scope, status, and contribution boundaries | Reviewed repository docs and license notices |
| **3. Product contract** | Defined identity, session, tenant, and authorization responsibilities | Versioned architecture and API specifications |
| **4. Integration proof** | Verified interaction with MoonWitness ID and ARSY | Automated end-to-end tests and deployment evidence |
| **5. Operational readiness** | Security, recovery, observability, and release processes | Security review, runbooks, backups, and release checklist |

A stage is complete only when its evidence exists. A roadmap item is not a shipped feature.

## Technical foundation and upstream attribution

This repository is a fork of [Kanidm](https://github.com/kanidm/kanidm), an identity-management project. The existing source, architecture, dependencies, license obligations, notices, and upstream attribution must be preserved unless a reviewed technical and legal change explicitly establishes otherwise.

The current codebase should therefore be treated as a Kanidm-derived technical baseline—not as proof that a distinct MW-ID product integration is complete. Consult the [upstream Kanidm documentation](https://kanidm.github.io/kanidm/stable/) for the inherited engine's behavior and capabilities.

MW-ID is an independent project identity and is not an official Kanidm project or endorsed by the Kanidm maintainers.

## Contribution and change policy

- Keep branding and product documentation separate from changes to authentication, authorization, cryptography, and other security-sensitive behavior.
- Preserve upstream copyright notices, license files, and attribution.
- Every implementation claim must point to code, tests, or operational evidence.
- Security-sensitive changes require focused review and tests; do not infer safety from a successful build alone.
- Record deviations from upstream clearly so future maintainers can distinguish inherited behavior from MW-ID changes.

## Further reading

- [MoonWitness ID product definition](https://github.com/bjo163/A-L-L-A-H.COM/blob/main/apps/id/README.md)
- [MoonWitness ID blueprint](https://github.com/bjo163/A-L-L-A-H.COM/blob/main/apps/id/BLUEPRINT.md)
- [MoonWitness XV master vision](https://github.com/bjo163/moonwitnessxv/blob/main/docs/vision/MASTER_VISION_NARRATIVE_XV.md)
- [Legacy reconciliation](https://github.com/bjo163/A-L-L-A-H.COM/blob/main/LEGACY_RECONCILIATION.md)
- [Kanidm upstream project](https://github.com/kanidm/kanidm)

---

**MW-ID — One identity. A connected universe.**
