# Step 2 — Design

*Supporting file for the `hacky-hours` skill. Loaded when the user is at Step 2.*

**Context:** Read `01-ideate/PRODUCT_OVERVIEW.md` under ROOT_PATH — specifically the Constraints & Values section. Also note which design docs already exist.

**Purpose:** Define how the product works in enough detail to build it.

Start by asking which documents this project actually needs:

| Document | Use when... |
|----------|-------------|
| ARCHITECTURE | The product has multiple systems or services |
| DATA_MODEL | The product stores or transforms data of any kind |
| USER_JOURNEYS | You need to map how users move through the product |
| STYLE_GUIDE | The product has a UI |
| ACCESSIBILITY | The product has a UI (almost always) |
| MARKET_FIT | You want to validate who the users are and why they'd choose this |
| BUSINESS_LOGIC | The product has rules, calculations, or domain-specific behavior |
| SECURITY_PRIVACY | The product handles user data, auth, or payments (almost always) |
| LICENSING | Almost always — ask early, before dependencies are chosen |
| TESTING | Almost always — test strategy and definition of done |

**Two-tier design artifacts (v3.0.0):** Each design doc consists of a **summary** (one-screen, diagram-led, what the user signs off on) plus a **deep** technical expansion (for engineers and build-phase AI). The summary is the source of intent — if the deep doc disagrees, the summary wins. Templates live in `${CLAUDE_SKILL_DIR}/templates/design/<DOC>-summary.md` and `<DOC>-deep.md`. Read `${CLAUDE_SKILL_DIR}/templates/design/README.md` for the full pattern before working through any doc.

For each document, work through the summary first — section by section, with questions. Generate Mermaid diagrams proactively and lead the summary with the diagram. Only expand into the deep doc once the summary is signed off.

**When a design decision changes during iteration:** write an Architecture Decision Record (ADR) in `02-design/decisions/` named by date and topic (e.g., `2026-03-20-switch-to-postgres.md`). Update only the affected sections of the original doc — both summary and deep, if relevant — and add a note pointing to the ADR.

**Done when:** A new collaborator could read the summaries and understand how the product is meant to work, with the deep docs available when they need to build. ✅
