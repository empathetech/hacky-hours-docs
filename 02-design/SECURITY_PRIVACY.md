# SECURITY_PRIVACY.md

**Level 2 — Design** | Contributed by: Product owner, with Claude facilitation

This document defines how your product handles sensitive data, protects its users, and guards against common threats. It is not optional — if your product touches real users, this document must exist in some form before you write production code.

You don't need to be a security expert to fill this out. You need to think clearly about what you're responsible for.

---

> **Claude Guidance:** This document should be revisited before every implementation task in Level 4. When helping the user fill it out, ask: "What's the most sensitive thing your product stores?" and "What would happen if an attacker got into your database?" Keep the language approachable — no jargon. Flag any gaps (e.g., "you mentioned email addresses but haven't addressed how they're stored") and recommend minimizing data collection where possible. Reference OWASP Top 10 in plain language when relevant. Do not skip this document even for "small" projects — a small project with real users has real responsibilities.

---

## Data Inventory

*What personal or sensitive data does your product collect, store, or transmit? Be exhaustive — include things that feel minor, like email addresses or IP logs.*

| Data Type | Why Collected | Where Stored | Retention Period |
|-----------|--------------|--------------|-----------------|
| | | | |

## Authentication and Access

*How do users prove who they are? How are sessions managed? What happens when a user is locked out or needs to reset credentials?*

## Authorization Rules

*Who is allowed to see or modify what? Cross-reference with `BUSINESS_LOGIC.md` for role definitions.*

## Data in Transit and at Rest

*Is data encrypted when sent over the network? Is it encrypted in storage? What keys or secrets are involved and how are they managed?*

## Third-Party Data Sharing

*What data does your product send to third-party services (analytics, payments, email, etc.)? For each, note what is shared and why.*

## User Rights and Controls

*What can users do with their own data? Can they export it, delete it, or correct it? How do you handle deletion requests?*

## Known Threat Vectors

*The most likely ways your product could be attacked or misused. For each, describe the mitigation.*

| Threat | Mitigation |
|--------|-----------|
| Unauthorized access to user accounts | |
| Injection attacks (SQL, command, etc.) | |
| Cross-site scripting (XSS) | |
| Exposed secrets in code or logs | |

## Compliance Considerations

*Any legal or regulatory requirements that apply — GDPR, CCPA, HIPAA, COPPA, etc. Note what applies and the key obligations.*

## Pre-Launch Security Checklist

*A list of security conditions that must be verified before going live. Claude should check these before marking any implementation task as complete.*

- [ ] No secrets or API keys in version control
- [ ] All user input is validated and sanitized
- [ ] Authentication tokens expire appropriately
- [ ] Error messages do not expose internal state
- [ ] Dependencies are reviewed for known vulnerabilities
- [ ] User data deletion flow is tested

---

## Related

- [Design README](./README.md)
- [DATA_MODEL.md](./DATA_MODEL.md)
- [BUSINESS_LOGIC.md](./BUSINESS_LOGIC.md)
- [build/BACKLOG.md](../04-build/BACKLOG.md)
