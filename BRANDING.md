# MW-ID Brand Guide

**Version:** 1.0  
**Status:** Initial project brand standard  
**Tagline:** One identity. A connected universe.

This guide defines how MW-ID presents itself across repository documentation, product interfaces, diagrams, and ecosystem communications. It is a project-level identity guide, not a claim that every planned product capability is implemented.

## 1. Brand foundation

### Purpose
MW-ID is the identity-infrastructure initiative for the MoonWitness Universe and the wider A-L-L-A-H.COM ecosystem.

### Brand promise
Identity is the foundation of trust.

### Brand essence
A dependable identity layer that helps people and services establish identity, understand access boundaries, and connect through explicit, reviewable contracts.

### Positioning statement
For connected digital services that need trustworthy identity and controlled access, MW-ID is an identity-infrastructure project designed around security, interoperability, privacy, and accountability. It is distinct from the human-facing MoonWitness ID experience and from the wider ecosystem's authority and governance components.

## 2. Brand architecture

| Name | Role | Do not imply |
|---|---|---|
| MW-ID | Identity-infrastructure project and repository direction | That this repository is already the ecosystem's canonical identity authority |
| MoonWitness ID | Human-facing sign-in, registration, account, and session experience | That its interface is implemented in this repository unless verified |
| ARSY | Documented ecosystem authority for canonical identity, authentication, sessions, tenant context, and authorization | That MW-ID has delegated or assumed ARSY authority |
| MoonWitness XV | Narrative, knowledge, research, chronicles, and witness context | That narrative content is an authentication or authorization policy |
| A-L-L-A-H.COM | Wider ecosystem and connected digital services | That all ecosystem services are already integrated |

Use these names consistently. A relationship in the architecture does not prove a runtime integration. Every integration claim needs a documented contract and test evidence.

## 3. Messaging

### Primary message
**One identity. A connected universe.**

### Supporting messages
- Identity is the foundation of trust.
- Secure access begins with clear boundaries.
- Connect services without collapsing their responsibilities.
- Make identity and access decisions reviewable and accountable.

### Short description
MW-ID is an identity-infrastructure initiative for the MoonWitness ecosystem, focused on secure identity, authentication, and controlled access across connected services.

### Long description
MW-ID aims to provide a dependable foundation for people and service identities across the MoonWitness ecosystem. Its direction emphasizes secure defaults, least privilege, privacy, interoperability, explicit authority, and evidence-based operations. The current repository is Kanidm-derived; MoonWitness-specific integrations and production capabilities must be verified independently.

### Words to prefer
Identity, authentication, authorization, session, service identity, trust boundary, least privilege, revocation, interoperability, evidence, accountability.

### Words to avoid or qualify
Unhackable, absolute security, universal access, fully integrated, production-ready, canonical authority, seamless SSO. Use these only if a precise, independently verifiable technical basis exists; absolute security claims should not be used.

## 4. Voice and tone

- **Clear:** short sentences and defined technical terms.
- **Calm:** confident without hype, fear, or urgency theatre.
- **Honest:** distinguish current behavior from intended direction.
- **Respectful:** protect user agency, privacy, and accessibility.
- **Accountable:** state ownership, scope, and evidence.

For feature status, use one of these labels consistently:
- **Implemented:** present in this repository and covered by relevant tests.
- **Verified integration:** tested end-to-end with the named external system.
- **Planned:** accepted direction without completed implementation.
- **Not verified:** capability may exist in an upstream dependency or another project, but has not been proven here.

## 5. Visual identity

### Design concept
A calm, precise identity system. Visuals should communicate a person or service identity operating within clear boundaries and connecting to other services through deliberate pathways.

### Color direction
Use the following as a proposed starting palette. Confirm contrast ratios in the actual interface before release.

| Token | Hex | Intended use |
|---|---|---|
| Midnight | `#101B2D` | Primary dark surfaces and wordmark |
| Indigo | `#3546A5` | Primary brand accent |
| Teal | `#168C8C` | Connection and positive interactive states |
| Ice | `#EAF2F7` | Light surfaces and backgrounds |
| Slate | `#536273` | Secondary text and neutral UI |
| White | `#FFFFFF` | High-contrast content surfaces |

Do not rely on color alone to communicate status. Pair status colors with text, icons, or patterns. Validate text and control contrast against WCAG 2.2 AA before shipping.

### Typography
- Prefer a clear sans-serif family with strong legibility.
- Use regular weights for long-form text and medium/semibold weights for hierarchy.
- Use a consistent monospace family for code, identifiers, and technical values.
- Prefer system font stacks unless the product has a compelling, accessible reason to bundle fonts.

### Shape and imagery
- Favor simple geometry, connected nodes, boundary rings, and clear pathways.
- Keep layouts structured and spacious; avoid decorative complexity.
- Avoid imagery that implies surveillance, militarization, absolute protection, or religious authority.
- Use diagrams to explain trust boundaries and data flow rather than implying that a logo itself guarantees security.

## 6. Logo direction

The preferred direction is a custom MW-ID wordmark with an optional abstract mark. The mark may combine:
- a clear central identity point,
- a protective but open boundary,
- one or more connected pathways.

The symbol must remain recognizable at favicon size and in monochrome. Avoid literal padlocks, shields with checkmarks, eye symbols, and complex network meshes.

Until approved vector and raster assets are committed, use the plain text wordmark **MW-ID**. Do not invent alternate marks or treat generated concepts as approved production artwork.

## 7. Product and security communication

Branding must never blur security boundaries:
- Authentication establishes a verified identity; authorization decides what that identity may do.
- A valid session does not imply access to every service.
- Human and service identities have different lifecycle and ownership requirements.
- Federation requires explicit issuer, audience, redirect, callback, logout, session, and revocation contracts.
- State what is logged, why it is logged, and how long it is retained.
- Never describe an upstream capability as an MW-ID feature without repository-level verification.

## 8. Accessibility and localization

- Meet WCAG 2.2 AA for shipped interface content.
- Support keyboard-only navigation and visible focus.
- Provide accessible names and clear error messages.
- Do not encode meaning only through color, shape, or animation.
- Write in plain language and keep technical terms consistent.
- Localize user-facing content without changing security-critical meanings or protocol terminology.

## 9. Usage checklist

Before publishing a page, interface, diagram, or announcement, verify:

- [ ] MW-ID is named and described consistently.
- [ ] The tagline is used exactly: “One identity. A connected universe.”
- [ ] MW-ID, MoonWitness ID, ARSY, MoonWitness XV, and A-L-L-A-H.COM retain distinct roles.
- [ ] Planned capabilities are not described as shipped.
- [ ] Integration and production claims have evidence.
- [ ] Upstream Kanidm attribution and license notices remain intact.
- [ ] Visual contrast and keyboard accessibility are checked.
- [ ] No language implies absolute security or authority that the system does not possess.

## 10. Governance

This is the initial brand standard. Changes should be made through reviewed documentation updates. Product, legal, security, and accessibility owners should review changes that affect claims, attribution, security messaging, or interface standards.

**MW-ID — Identity is the foundation of trust.**
