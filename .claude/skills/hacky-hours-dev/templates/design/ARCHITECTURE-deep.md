# {{Product Name}} — Architecture (Deep)

**Step 2 — Design** | Companion to [ARCHITECTURE-summary.md](./ARCHITECTURE-summary.md)
**Contributed by:** Product owner + technical collaborators

This document is the full technical expansion of the architecture. The user-facing artifact — the one they sign off on and share — is [ARCHITECTURE-summary.md](./ARCHITECTURE-summary.md). This file exists for engineers and for AI doing the build, where decisions need full context, not just headlines.

If the summary and the deep doc disagree, **the summary is the source of intent.** Update this file to match, not the other way around.

---

> **Claude Guidance:** Start by reading the **Constraints & Values** section of `PRODUCT_OVERVIEW.md` before making any recommendations — the user's licensing intent, privacy stance, and infrastructure preference should shape every architectural suggestion.
>
> **Two-tier discipline:** Every decision documented here must have a corresponding entry in [ARCHITECTURE-summary.md](./ARCHITECTURE-summary.md) — either as one of the three key decisions or rolled into the "what this rules out" paragraph. If a decision is too detailed for the summary, that's fine — but the summary should at minimum acknowledge it exists. Never let the summary fall behind the deep doc.
>
> **Safety-first defaults:** Lead with the simplest, cheapest, least-infrastructure-heavy option that meets the product's needs. Specifically:
> - Prefer **managed/hosted** services (Supabase, Vercel, Netlify, Railway, Neon) over self-hosted infrastructure
> - Prefer **fewer external services** — every third-party integration is a credential to manage, a potential outage, and a data-sharing decision
> - Prefer **established, well-maintained open-source libraries** over newer or proprietary ones — especially for auth
> - Flag **cost implications** clearly: free tiers, pricing cliffs, and what happens when the product scales
> - Flag **data residency and privacy implications** for any service that stores or processes user data
> - For **licensing compatibility**: check the user's chosen license against any dependencies — GPL/AGPL libraries in a closed-source product can be a problem
>
> Help the user think through: Where does the product run? Does it need a backend? A database? Third-party services? Draw out the architecture in Mermaid before filling in prose. When choices involve tradeoffs, explain them in plain language and let the user decide.

---

## System Overview

*A paragraph or two summarizing the overall architecture — what exists, how it fits together, and the key design philosophy. Free to be more detailed than the summary's one-sentence version.*

## Architecture Diagram

*A more detailed Mermaid diagram than the summary's. Include subsystems, data flows, and any external integrations the summary diagram omits for clarity.*

```mermaid
%% Replace this placeholder with your detailed architecture diagram
graph TD
    A[User] --> B[Frontend]
    B --> C[Backend API]
    C --> D[(Database)]
    C --> E[External Service]
```

## Components

*For each major system or service, describe what it is, what it does, and why it exists.*

### Frontend

*What technology, where it runs, what it's responsible for, and any notable libraries or frameworks.*

### Backend / API

*What technology, where it runs, what it exposes, and what it's responsible for.*

### Data Storage

*Where data lives, what kind of store it is (relational, document, etc.), and why that choice fits the product.*

### External Services

*Third-party APIs, platforms, or services the product depends on, and what role each plays.*

## Key Technical Decisions

*The most important architectural choices made, and the reasoning behind them. Future Claude sessions should read this section before making implementation decisions.*

*Each decision should map to either a "Key decision" bullet in the summary, or be acknowledged in the summary's "what this rules out" paragraph.*

## Known Constraints and Tradeoffs

*What this architecture is not optimized for. What would need to change as the product scales.*

## Implementation Notes

*Build-phase guidance that doesn't belong in the summary. File layout conventions, environment variable expectations, deployment specifics, common pitfalls. AI doing the build should read this section before writing code.*

---

## Related

- [ARCHITECTURE-summary.md](./ARCHITECTURE-summary.md) — the human-facing one-screen version (source of intent)
- [Design README](../../README.md)
- [DATA_MODEL-deep.md](./DATA_MODEL-deep.md)
- [SECURITY_PRIVACY-deep.md](./SECURITY_PRIVACY-deep.md)
- [LICENSING.md](../../LICENSING.md)
- [diagrams/](../../diagrams/)
