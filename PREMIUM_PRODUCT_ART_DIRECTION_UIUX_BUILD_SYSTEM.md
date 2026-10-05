# Product Art Direction & UI/UX Build System
## Reverse-engineered from recurring patterns in winsznx projects

**Purpose:** prevent AI coding agents from producing generic “premium Web3” interfaces. The agent must design the product's visual language from its actual mechanism before implementing UI.

---

# 0. NON-NEGOTIABLE RULE

Do NOT start by writing components.

Do NOT start with:
- Navbar
- Hero
- Cards
- Feature grid
- Dashboard
- CTA
- “modern Web3” styling

First understand the product.

The objective is:

> PRODUCT MECHANISM → PRODUCT STORY → VISUAL CONCEPT → SIGNATURE INTERACTION → DESIGN GRAMMAR → SCREEN ARCHITECTURE → COMPONENTS → IMPLEMENTATION → VISUAL QA

A visually polished generic interface is a failure.

A simpler interface with a distinctive product-specific visual language is preferable.

---

# 1. PRODUCT FORENSICS

Before UI implementation, write a one-page Product Forensics brief.

Answer:

### Product
- What does this product actually do?
- Who is the primary user?
- What is the user's highest-value action?
- What problem exists without this product?
- Why does this need the chosen infrastructure/blockchain?
- What does the smart contract actually enforce?
- What does it NOT enforce?
- What changes state?
- What can be independently verified?

### Judge comprehension
- What should a stranger understand in 5 seconds?
- What should they understand in 30 seconds?
- What should a technical judge understand after exploring?
- What single mechanism should they remember?

### Product magic moment
Identify one moment where the technology becomes tangible.

Examples:
- confidential value → redaction → selective disclosure
- invoice → six verification gates → payment
- mandate → signal monitoring → autonomous execution
- commitment → funded → held → settled

The magic moment must influence the UI.

---

# 2. FIND THE PRODUCT'S VISUAL METAPHOR

Do not choose “dark”, “light”, “Web3”, “futuristic”, or “minimal” as the concept.

Choose a PRODUCT WORLD.

Examples from observed winsznx work:
- financial privacy → declassified dossier
- AI payment verification → vault ledger
- autonomous trading → execution/control-room narrative
- competitive game → sports arena / live competition system

The metaphor must answer:

> “If this product were a physical place, instrument, document, machine, or environment, what would it be?”

Then explain WHY.

Bad:
> “Dark futuristic finance.”

Good:
> “A declassified financial dossier, because the product's core interaction is controlled disclosure.”

---

# 3. VISUAL THESIS

Write exactly one sentence:

> This product should feel like ______ because ______.

Then define 3–5 reference adjectives.

Examples:
- institutional / precise / editorial / restrained
- tactical / operational / dense / technical
- documentary / archival / confidential / deliberate
- playful / competitive / kinetic / responsive

Do not mix contradictory aesthetics without a reason.

---

# 4. REFERENCE EXTRACTION

When a reference product/site is supplied:

Do NOT copy its colors, layout, assets, or branding.

Extract:
- information density
- hierarchy
- typography behavior
- spacing rhythm
- surface treatment
- navigation behavior
- interaction language
- motion language
- storytelling structure
- product-state visualization

Then create an ORIGINAL system appropriate to the product.

Reference quality is an input, not a template.

---

# 5. DESIGN THE PRODUCT MECHANISM INTO THE UI

This is mandatory.

Find the core technical/product mechanism and make it visible through interaction.

Ask:

> “If I removed the logo and all explanatory text, could someone still discover what makes this product different?”

The answer should come from interaction, not decoration.

Examples:

### Privacy
Hidden → reveal → disclosed

### Verification
Input → gate 1 → gate 2 → gate 3 → approved

### Autonomous execution
Mandate → monitoring → trigger → execution → receipt

### Escrow
Draft → funded → held → released/claimed

Do NOT merely place “powered by blockchain” somewhere.

---

# 6. SIGNATURE INTERACTION

Every product must have at least one interaction that is strongly associated with the product.

Define:

- Trigger
- Before state
- Transition
- After state
- What the user learns from it

Example:

> Funded agreement → contract-held state → settlement state

The signature interaction should be visible in the hero/demo whenever possible.

---

# 7. INFORMATION ARCHITECTURE BEFORE COMPONENTS

Map the user journey first.

Example:

Landing
→ understand promise
→ choose action
→ configure
→ review
→ confirm
→ onchain state
→ independent view
→ settlement
→ receipt/proof

Then define screens.

For every screen specify:

- User goal
- Primary action
- Secondary action
- Information required
- Information deliberately hidden
- State
- Success state
- Failure state
- Empty state
- Loading state
- Proof/evidence

Only after this is approved should components be created.

---

# 8. DESIGN GRAMMAR

Define tokens BEFORE page styling.

## Typography
Specify:
- display face
- body face
- data/mono face
- weights
- type scale
- line heights
- letter spacing

## Color
Specify named semantic tokens:
- background
- surface
- elevated surface
- text high/mid/low
- border faint/normal/strong
- primary accent
- positive
- negative
- warning
- special product state

## Geometry
Specify:
- corner-radius family
- border thickness
- button geometry
- input geometry
- surface geometry

## Spacing
Create a real spacing scale.

## Density
Explicitly choose:
- airy/editorial
- balanced
- dense/instrument-like

## Motion
Define:
- what moves
- why it moves
- duration
- easing
- entrance behavior
- state-change behavior
- reduced-motion fallback

---

# 9. NEGATIVE DESIGN RULES

Explicitly ban whatever would make the product generic.

Possible bans:
- purple/blue AI gradients
- glassmorphism
- excessive blur
- floating bento grids
- giant rounded cards
- random glowing borders
- gradient text
- meaningless 3D objects
- stock illustrations
- generic dashboard sidebar
- excessive pills
- fake metrics
- unnecessary charts
- “Powered by blockchain” decoration
- generic Web3 copy
- excessive shadows

Do not ban something merely because it is fashionable.

Ban it because it conflicts with the product concept.

---

# 10. COMPONENT VOCABULARY

Create components from product concepts, not generic UI primitives.

Bad:
- Card1
- Card2
- FeatureCard
- InfoCard
- GlassCard

Better:
- CommitmentCertificate
- SettlementTimeline
- VerificationGate
- DisclosureBar
- ExecutionTrace
- PaymentReceipt
- DeadlineIndicator

Generic primitives may still exist underneath, but the visible component language must describe the product.

---

# 11. PAGE COMPOSITION

Do not automatically use:

Hero → Features → Testimonials → CTA.

Instead create a narrative.

Recommended pattern:

01 — Promise
02 — Core product object
03 — How the mechanism works
04 — Live/product state
05 — Proof
06 — Action

The product object should appear early.

The most important mechanism should be demonstrated, not merely described.

---

# 12. PRODUCT STATES

Design the complete state machine.

At minimum consider:

- idle
- draft
- pending
- loading
- confirmed
- active
- completed
- failed
- expired
- cancelled
- empty
- disconnected
- wrong network

For each state define:
- visual treatment
- copy
- available action
- unavailable action
- evidence

Never design only the happy path.

---

# 13. TECHNICAL TRUTH

The UI must never imply capabilities that the backend/contract does not actually provide.

Before writing copy, map:

UI claim → actual implementation → evidence

Example:

Bad:
> “The contract verifies the work.”

If the contract only allows the employer to release and the contractor to claim after deadline, say:

> “The contract enforces the settlement rules.”

Never invent AI verification, oracles, automation, ownership, legal rights, or guarantees.

---

# 14. JUDGE MODE

The interface must answer these questions visually:

1. What is this?
2. Who is it for?
3. What happens?
4. Why blockchain?
5. What is technically special?
6. Is it actually working?
7. Can I verify it?

The answers should be visible through the product experience, not hidden in documentation.

---

# 15. 30-SECOND TEST

Before implementation is considered complete:

### 5 seconds
Can I identify the product category?

### 10 seconds
Can I understand the core promise?

### 20 seconds
Can I understand the main workflow?

### 30 seconds
Can I explain why the technology matters?

If not, revise the composition/copy.

---

# 16. ANTI-AI VISUAL TEST

Ask:

> Could this interface have been generated by “make a premium Web3 dashboard”?

If YES → FAIL.

Ask:

> If I remove the logo, what three visual/interaction characteristics identify this product?

If the answer is only colors/fonts → FAIL.

If the answer includes product-specific mechanisms → PASS.

---

# 17. VISUAL QUALITY GATE

Score 0–2:

| Criterion | 0 | 1 | 2 |
|---|---|---|---|
| Product clarity | unclear | understandable | immediate |
| Distinctiveness | generic | somewhat distinct | unmistakable |
| Product-mechanism expression | absent | partial | central |
| Information hierarchy | noisy | acceptable | excellent |
| Typography | generic | coherent | intentional |
| Spacing/density | random | consistent | deliberate |
| Interaction quality | basic | polished | product-specific |
| State coverage | weak | partial | complete |
| Motion | random/none | acceptable | purposeful |
| Mobile | broken | responsive | intentionally designed |
| Technical honesty | overclaims | mostly accurate | exact |
| Judge proof | weak | some | immediate |

Minimum target: **20/24**.

Any score of 0 in:
- product clarity
- distinctiveness
- product-mechanism expression
- technical honesty

requires redesign.

---

# 18. IMPLEMENTATION ORDER

The coding agent must work in this order:

### Phase A — Product Forensics
No code.

### Phase B — Visual Thesis
No page implementation.

### Phase C — User Journey + State Machine
No page implementation.

### Phase D — Design Grammar
Tokens, typography, color, geometry, spacing, motion.

### Phase E — Signature Interaction
Prototype the most distinctive interaction.

### Phase F — Screen Architecture
Wireframe all important screens.

### Phase G — First Implementation
Build the core product object and primary flow first.

### Phase H — State Completion
Add loading/error/success/empty/expired states.

### Phase I — Responsive
Desktop + mobile intentionally.

### Phase J — Visual QA
Compare implementation against the approved visual thesis.

### Phase K — Anti-AI Audit
Actively remove generic patterns.

### Phase L — Judge Walkthrough
Test the product as a stranger and as a technical judge.

---

# 19. IMPORTANT AGENT BEHAVIOR

The coding agent must NOT ask:

> “What colors would you like?”

unless the user has explicitly left the visual direction undefined after the design phase.

The agent is expected to propose a coherent visual direction from the product.

The agent must not silently substitute:
- generic shadcn layouts
- default Tailwind aesthetics
- common Web3 patterns
- stock landing-page templates

If a component library is used, it is an implementation primitive, NOT the design direction.

---

# 20. CURRENT EQUITY BENEFIT WALLET APPLICATION

For Equity Benefit Wallet:

### Product mechanism
Employer commitment → funding → contract-held bonus → employer release OR deadline claim.

### Visual world
A serious financial/work agreement instrument.

### Core product object
The agreement/certificate.

### Signature interaction
FUNDED → HELD → SETTLED / CLAIMABLE.

### Important visual truth
The contract does not objectively verify whether the work was completed.

Therefore:
- employer release = employer confirms completion
- deadline claim = contractor's fallback path
- blockchain = independently verifiable escrow + settlement rules

### Candidate visual system
Keep the existing “Desk” direction only if it remains coherent.

Do NOT add generic dashboard components just to make the app feel larger.

The certificate, commitment state, deadline, and settlement proof should remain the center of gravity.

---

# 21. FINAL PRINCIPLE

Do not try to reproduce another builder's “look.”

Reproduce the discipline:

> Every strong visual decision must have a product reason.

The goal is not:
> “Make it beautiful.”

The goal is:
> “Make the product's identity visible.”
