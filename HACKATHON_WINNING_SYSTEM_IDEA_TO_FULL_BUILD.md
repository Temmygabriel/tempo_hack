# HACKATHON WINNING SYSTEM
## An evidence-led operating system from idea → product → UI/UX → implementation → proof → submission

**Version:** 1.0  
**Purpose:** Build better hackathon entries by combining evidence-led idea selection with sponsor-native product wedges, visible product demonstrations, rigorous proof, disciplined implementation, and product-specific art direction.

---

# 0. EXECUTIVE THESIS

There is no single “winning category”.

The strongest repeatable pattern in the supplied research is a **form**, not a vertical:

> **Recognizable product/category + concrete new capability + a demo that produces an obvious visible state change.**

The research explicitly rejects the old assumption that winners are mainly “frustration-first.” In the verified ETHGlobal New York 2026 finalist set, the dominant pattern was product/outcome-first rather than explicit frustration-first. The research also finds that the clearest commonality across several winning/finalist demos is a visible state transition. See the source research at the end of this document.

The new operating strategy is therefore:

> **Find a real opportunity → find a sponsor-specific capability → turn it into a recognizable product → define one unforgettable state transition → build the smallest real version → prove it with live evidence → make the UI express the product mechanism → package the proof for judges.**

This is not a “make a beautiful website” strategy.

It is not a “build an AI agent” strategy.

It is not a “find an underserved market and hope” strategy.

It is a **selection + product + engineering + design + proof system**.

---

# 1. WHAT WAS WRONG WITH THE OLD STRATEGY

The attached research was already directionally strong. Its most important correction was that it rejected a simple “frustration-first” theory.

Several additional corrections are required before using the research as a future decision system.

## 1.1 Wrong: “frustration-first is the winning formula”

The research itself says this is not supported.

A stronger model is:

> **recognizable thing + concrete capability + specific interaction**

A problem can be frustration-led, but it does not need to be.

### New rule

Do not ask only:

> “What problem annoys people?”

Ask:

> “What recognizable product can I make behave in a way that was previously difficult, costly, opaque, or impossible?”

---

## 1.2 Wrong: “underrepresented = likely winner”

A category being rare among finalists does NOT prove judges prefer it.

The research correctly marks this as uncertain.

For example:
- physical-world interaction appears underrepresented;
- B2B operational workflows appear in the broader submission field but less in the top finalist set;
- non-wallet interaction appears in the broader field;
- evidence/provenance is present but less dominant.

That creates an **opportunity signal**, not a prediction.

### New rule

Treat category rarity as a multiplier, never as the core thesis.

The core thesis must still have:
- a strong user/value proposition;
- a sponsor-native technical wedge;
- a compelling interaction;
- credible execution;
- a provable outcome.

---

## 1.3 Wrong: “find one uncrowded category”

The research does not support a universal next-wave category.

The strategy must therefore avoid category hunting by itself.

### New rule

Do not optimize for “few competitors”.

Optimize for:

> **high product meaning × high sponsor specificity × low idea saturation × high demo clarity × high buildability**

---

## 1.4 Wrong: “technical novelty is enough”

Technology-first projects absolutely can reach finalist status.

But the strongest recurring descriptions in the research are still concrete products with a clear capability.

### New rule

A technical primitive must be wrapped in a product that a non-specialist judge can imagine using.

The technology should produce the **thing the judge sees**, not merely sit underneath it.

---

## 1.5 Wrong: “the sponsor stack is a list of integrations”

A sponsor integration is weak when it is simply:

> “We used Sponsor X for storage.”

A stronger integration is:

> “Without Sponsor X's native capability, this product loses its central mechanic.”

### New rule

For each sponsor, identify the **counterfactual wedge**:

> What materially changes if this technology is removed and replaced with a generic equivalent?

If almost nothing changes, the sponsor integration is weak.

---

## 1.6 Wrong: “build first, make the proof later”

The inspected winsznx repos repeatedly work the opposite way.

Examples:
- phase gates;
- real deployment evidence;
- explicit invariant tables;
- canonical run IDs;
- verifiers;
- live transaction evidence;
- “claim status” fields that can be PROVEN / UNPROVEN;
- source-of-truth order;
- documented limitations.

### New rule

Every important product claim gets an evidence path while it is being designed.

---

# 2. THE WINNING MODEL

The system has ten layers.

```text
01  EVENT FORENSICS
02  OPPORTUNITY RESEARCH
03  SPONSOR-CAPABILITY RESEARCH
04  IDEA GENERATION
05  IDEA SELECTION
06  PRODUCT + STATE-MACHINE DESIGN
07  PRODUCT ART DIRECTION + UI/UX
08  EVIDENCE-FIRST ENGINEERING
09  DEMO + JUDGE COMMUNICATION
10  SUBMISSION + FINAL AUDIT
```

A project advances only when the current stage passes its gate.

---

# 3. STAGE 01 — EVENT FORENSICS

Before generating ideas, study the actual hackathon.

## 3.1 Collect these facts

Create an `EVENT_BRIEF.md` containing:

- submission deadline and timezone;
- judging deadline;
- winner announcement date;
- judging criteria;
- all prize tracks;
- sponsor prizes;
- required chains/ecosystems;
- mandatory technologies;
- optional technologies;
- deployment requirements;
- repository requirements;
- demo/video requirements;
- project-page fields;
- whether judges inspect source;
- whether a live demo is expected;
- whether a testnet or mainnet deployment is required;
- whether grants are separate from prize tracks.

## 3.2 Build a judge model

For each criterion, define:

| Criterion | What the judge must see |
|---|---|
| Product-market fit | obvious user + valuable workflow |
| Innovation | specific mechanism, not a buzzword |
| Real problem solving | outcome is observable |
| Technical quality | real implementation + constraints |
| Sponsor fit | sponsor is load-bearing |
| UX | judge understands the product quickly |
| Evidence | claims can be independently checked |

## 3.3 Build a submission matrix

Do not leave submission requirements until the last day.

Create:

```text
FIELD
SOURCE / REQUIREMENT
VALUE
STATUS
EVIDENCE
FINAL REVIEW
```

---

# 4. STAGE 02 — OPPORTUNITY RESEARCH

The goal is not “find the biggest problem.”

The goal is to locate a problem that has a **strong product shape**.

## 4.1 Search for five signals

For every candidate opportunity, investigate:

### A. Existing behavior
What do users do today?

### B. Friction
What is slow, risky, confusing, expensive, opaque, or impossible?

### C. Existing substitutes
Who already solves it?

### D. Technical opening
What changed recently that makes a better solution possible?

### E. Demoability
Can the change be shown in under 60 seconds?

The fifth signal is the one generic startup research often ignores.

Hackathons are not only judged through documents.

The judge has to **see the mechanism happen**.

---

# 5. STAGE 03 — SPONSOR-CAPABILITY FORENSICS

For every sponsor, create a one-page capability card.

```text
SPONSOR:
NATIVE CAPABILITY:
WHAT IS UNIQUE:
COUNTERFACTUAL WITHOUT SPONSOR:
AVAILABLE APIs/SDKs:
AVAILABLE CONTRACTS:
AVAILABLE TESTNET/MAINNET:
WHAT CAN BE PROVEN LIVE:
LIMITATIONS:
DEMO MOMENT:
```

## 5.1 Sponsor fit scoring

Score each sponsor capability 0–5:

| Dimension | Question |
|---|---|
| Native | Is this actually a first-class sponsor capability? |
| Essential | Does removing it break the core product? |
| Visible | Can the user see its effect? |
| Provable | Can we verify it independently? |
| Buildable | Can we realistically ship it during the event? |

Target:

> **20/25 or higher**

A 7/25 integration should not be marketed as the technical heart of the project.

---

# 6. STAGE 04 — IDEA GENERATION

Generate ideas from **mechanism × workflow**, not from categories alone.

Use these idea forms.

## 6.1 Recognizable thing + unusual capability

```text
Existing product:
market / wallet / insurance / payroll / game / invoice / API / credential

New capability:
privacy / autonomous execution / programmable settlement / physical trigger /
verifiable evidence / cross-chain coordination / conditional payment / etc.
```

Examples found in the supplied finalist research include:
- market + prediction-derived baskets;
- insurance + prediction-market settlement;
- wallet + reduced wallet friction;
- package registry + verifiable security evidence.

---

## 6.2 Familiar analogy + new mechanism

Use:

> “X for Y”

only when the analogy is extremely clean.

Examples from the research:
- Pokémon GO + memecoins;
- Dark Forest + Factorio;
- agar.io-style multiplayer game + onchain/referral mechanics.

The analogy is not the innovation. It is the compression layer.

---

## 6.3 Concrete outcome + technical mechanism

This is particularly strong when the output is proof.

Examples:
- package query → security evidence;
- real-world risk event → insurance settlement;
- physical token → blockchain participation;
- VPN operation → verifiable no-log property.

---

## 6.4 Invisible infrastructure + visible product

This is an especially useful construction pattern:

```text
Normal workflow
      +
sponsor-native infrastructure
      =
new behavior the user actually notices
```

The blockchain does not need to be the hero.

The **behavioral change** can be the hero.

---

# 7. STAGE 05 — IDEA SELECTION

Do not pick the idea that sounds smartest.

Score all serious candidates.

## 7.1 100-point model

| Dimension | Weight |
|---|---:|
| Problem/value clarity | 15 |
| Product recognizability | 10 |
| Sponsor-native wedge | 15 |
| Novel capability | 15 |
| Demo state transition | 15 |
| Technical feasibility | 10 |
| Evidence/provability | 10 |
| Saturation advantage | 5 |
| UX potential | 5 |
| **Total** | **100** |

### Selection bands

**85–100:** attack candidate  
**75–84:** viable  
**65–74:** only with a strong strategic reason  
**<65:** discard

---

# 8. THE 15-MINUTE STRANGER TEST

Before coding, explain the idea to a person who knows nothing about the project.

They should be able to answer:

1. What is this?
2. What does it let me do?
3. What happens that was not possible/easy before?
4. Why does the infrastructure matter?

If they cannot answer #1–3 quickly, change the product framing before writing code.

---

# 9. STAGE 06 — PRODUCT DESIGN

Now turn the idea into a product.

## 9.1 Write the one-sentence product contract

Use:

> **[Recognizable product] that [concrete new capability] for [specific user/outcome].**

Avoid:

> “A decentralized platform powered by AI and blockchain…”

---

## 9.2 Define the product state machine

Write the real states before UI implementation.

Example:

```text
DRAFT
  ↓
FUNDED
  ↓
HELD
  ↓
RELEASED
  OR
EXPIRED
  ↓
CLAIMABLE
  ↓
SETTLED
```

Every state must have:
- what is true;
- who can act;
- what is visible;
- what is impossible;
- what evidence exists.

---

## 9.3 Identify the irreversible moment

Find the moment where the system changes economic or informational reality.

Examples:

- money becomes locked;
- package becomes verified;
- claim becomes settled;
- physical object becomes an onchain state;
- condition becomes executable;
- evidence becomes immutable.

That moment becomes the centre of the demo.

---

# 10. STAGE 07 — PRODUCT ART DIRECTION

This is the design discipline discovered from the recurring winsznx work.

Do not copy his appearance.

Copy the **discipline**.

The inspected projects use very different aesthetics, but repeatedly define:
- a product-specific world;
- detailed visual rules;
- explicit anti-patterns;
- state-aware interactions;
- exact tokens;
- product-specific components;
- technical mechanisms expressed visually.

Examples:
- a “declassified dossier” visual world for confidential prediction;
- “execution narrative” for autonomous trading;
- ledger/gate logic for AI payment verification;
- game/replay/proof as an actual product surface.

The common rule is:

> **The product mechanism determines the visual language.**

---

# 11. THE VISUAL THESIS

Before components, define:

```text
PRODUCT WORLD:
WHY THIS WORLD:
3–5 ADJECTIVES:
PRIMARY VISUAL OBJECT:
SIGNATURE INTERACTION:
MOTION PRINCIPLE:
ANTI-REFERENCES:
```

Examples:

```text
Product:
privacy-sensitive prediction

World:
declassified dossier

Primary object:
redacted market record

Signature interaction:
redacted amount → disclosed amount
```

Another product can be completely different.

The system must NOT force all projects into one visual aesthetic.

---

# 12. DESIGN THE TECHNICAL MECHANISM INTO THE UI

This is the most important UI rule.

Ask:

> “What does the sponsor/technical innovation DO?”

Then represent that action visually.

Examples:

### Privacy
sealed → disclose

### Verification
submitted → gate 1 → gate 2 → verified

### Cross-chain settlement
prepared → remote proof → committed → released

### Autonomous action
mandate → signal → trigger → execution

### Physical interface
object detected → verified → state changes

The goal is not to decorate the technology.

The goal is to **make the mechanism legible**.

---

# 13. THE SIGNATURE INTERACTION TEST

Every serious product should have at least one action where a judge thinks:

> “Ah. THAT is what this product does.”

Define:

```text
TRIGGER
BEFORE
TRANSITION
AFTER
MEANING
PROOF
```

This interaction should be usable in:
- the landing page;
- the live app;
- the demo video.

---

# 14. DESIGN SYSTEM BEFORE UI CODE

Create tokens first.

## Typography

Specify:
- display;
- body;
- data/mono;
- weight;
- scale;
- line height;
- tracking.

## Color

Specify:
- canvas;
- surfaces;
- text levels;
- borders;
- primary accent;
- positive;
- negative;
- warning;
- special product states.

## Geometry

Specify:
- radius;
- border;
- control height;
- layout density;
- shadows/elevation.

## Spacing

Use a coherent scale.

## Motion

Specify:
- duration;
- easing;
- triggers;
- transitions;
- reduced-motion behavior.

---

# 15. NEGATIVE DESIGN RULES

AI defaults are powerful.

Explicitly ban the patterns that make the product generic.

Possible bans:
- purple/blue “AI” gradients;
- random glow;
- glassmorphism;
- giant bento-card layouts;
- fake 3D;
- decorative charts;
- giant rounded cards;
- gradient typography;
- fake metrics;
- meaningless badges;
- generic dashboard sidebars;
- excessive pills;
- generic hero art;
- “Powered by blockchain” decoration.

Do NOT ban something because it is fashionable.

Ban it because it conflicts with the product concept.

---

# 16. COMPONENTS MUST SPEAK THE PRODUCT'S LANGUAGE

Bad visible vocabulary:

```text
Card
FeatureCard
InfoCard
StatCard
DashboardCard
```

Better:

```text
SettlementCertificate
VerificationGate
CommitmentTimeline
DisclosureBar
ExecutionTrace
ProofReceipt
DeadlineState
```

Generic primitives can exist internally.

The visible components should describe the actual product.

---

# 17. BUILD THE JOURNEY BEFORE THE SCREENS

Write:

```text
LAND
→ UNDERSTAND
→ CHOOSE
→ CONFIGURE
→ REVIEW
→ CONFIRM
→ WAIT
→ STATE CHANGE
→ VERIFY
→ SETTLE
```

Then map real screens.

For every screen:

```text
USER GOAL
PRIMARY ACTION
SECONDARY ACTION
INFORMATION
HIDDEN INFORMATION
CURRENT STATE
SUCCESS
FAILURE
EMPTY
LOADING
PROOF
```

---

# 18. STAGE 08 — EVIDENCE-FIRST ENGINEERING

This is one of the strongest lessons from the inspected repos.

## 18.1 Source-of-truth hierarchy

For high-stakes implementation, define an order such as:

```text
1. deployed contract state / verified transaction evidence
2. current official sponsor documentation
3. active product specification
4. accepted architecture decisions
5. code/tests
6. README/marketing material
```

If two sources conflict:

> Stop → document conflict → resolve explicitly.

Do not silently pick whichever is convenient.

---

# 19. PHASE GATES

Build in phases.

A phase is PASS only when the required behavior is proven.

Recommended phases:

### Phase 0 — repository + environment
- repo initialized;
- dependency policy;
- env validation;
- network configuration;
- source-of-truth rules.

### Phase 1 — protocol skeleton
- contracts / core backend interfaces;
- unit tests;
- invariants;
- deployment plan.

### Phase 2 — smallest real flow
Make ONE end-to-end happy path work.

### Phase 3 — live deployment gate
Deploy the minimal product.

Verify:
- chain ID;
- bytecode;
- contract address;
- source verification;
- real interaction.

### Phase 4 — failure paths
Test:
- invalid input;
- expired;
- unauthorized;
- wrong network;
- duplicated action;
- insufficient balance;
- external dependency failure.

### Phase 5 — evidence layer
Create:
- verifier script;
- transaction artifact;
- canonical run;
- proof page or evidence document.

### Phase 6 — product UI
Only after the core behavior is real.

### Phase 7 — polish
Motion, typography, responsiveness, assets, copy.

### Phase 8 — hardening
Security + regressions + deployment checks.

---

# 20. THE “REAL FIRST” RULE

Never create a fake production branch merely so the demo looks complete.

If something cannot be made live:

1. identify the exact blocker;
2. determine whether it is a core requirement;
3. document the limitation;
4. remove the false claim;
5. either replace the dependency or narrow the demo.

The UI must not pretend.

---

# 21. PREREQUISITES ARE PROTOCOL STEPS

A prerequisite transaction is not “setup”.

If the product says:

```text
approve
→ fund
→ reserve
→ commit
→ release
```

then each is a real protocol step.

For each:

1. submit;
2. await receipt;
3. require success;
4. read resulting state;
5. assert expected state/delta;
6. proceed.

This is stronger than “transaction confirmed”.

---

# 22. DO NOT TRUST A RECEIPT ALONE

A receipt proves inclusion.

It does not prove the next read came from a node that has caught up.

Where needed:

```text
receipt block N
→ wait until provider reports latest >= N
→ read expected state
→ assert state
→ continue
```

This matters especially for fast testnets and chained prerequisite transactions.

---

# 23. LIVE RUN OBSERVABILITY

Any end-to-end run that lasts long enough to fail needs:

- timestamp per stage;
- line-buffered output;
- transaction hash printed at broadcast;
- artifact/log written to disk;
- final summary.

A run should be reproducible from an artifact.

---

# 24. TEST PYRAMID

Use:

```text
unit
→ integration
→ contract
→ property/fuzz
→ adversarial
→ live end-to-end
→ deployment verification
```

Do not stop at “npm run build”.

---

# 25. INVARIANT TABLE

For every value-moving contract, define explicit invariants.

Example:

| ID | Invariant | Where proven |
|---|---|---|
| INV-01 | funds cannot exceed reserved amount | contract + fuzz test |
| INV-02 | settlement executes once | unit test |
| INV-03 | cancelled state cannot execute | adversarial test |
| INV-04 | expired state cannot execute | integration test |
| INV-05 | unsupported asset cannot execute | contract test |
| INV-06 | unauthorized actor cannot release | contract test |

The specific invariants change per product.

---

# 26. CANONICAL RUN

Every serious hackathon project should have one canonical end-to-end run.

Record:

```text
CANONICAL RUN ID:
COMMIT:
NETWORK:
CONTRACTS:
WALLETS:
START TIME:
END TIME:
STEPS:
TRANSACTIONS:
EXPECTED:
ACTUAL:
RESULT:
```

The canonical run should be what the demo, README, submission, and judge documentation reference.

---

# 27. CLAIM STATUS MUST BE EXPLICIT

For every important statement:

```text
PROVEN
UNPROVEN
PARTIALLY PROVEN
UNAVAILABLE
```

Never write:

> “mainnet execution is live”

when the canonical mainnet transaction does not exist.

Never write:

> “oracle verified”

when the mechanism is actually operator-attested.

Never write:

> “AI verified the work”

when the contract only stores a milestone.

This protects credibility.

---

# 28. THE LIMITATIONS RULE

A limitation does not automatically weaken a project.

A dishonest limitation does.

Use:

```text
LIMITATION:
WHY:
IMPACT:
CURRENT STATUS:
SAFE DESCRIPTION:
FUTURE PATH:
```

A strong README can say:

> “This source is operator-attested, not oracle-verified.”

That is stronger than pretending the source is trustless.

---

# 29. SECURITY IS A PRODUCT FEATURE

Security controls should become visible where useful.

Examples:

- exact amount ceiling;
- recipient binding;
- allowlist;
- expiry;
- no double release;
- proof consumption;
- state lock;
- isolated custody.

The UI can show the constraint that protects the user.

This turns “security” from a README paragraph into a product behavior.

---

# 30. ASSET PROVENANCE GATE

If you ship:
- images;
- fonts;
- audio;
- generated graphics;
- stock assets;

track provenance.

Create:

```text
ASSET_PROVENANCE.md
```

For each asset:

```text
ASSET
PATH
SOURCE
LICENSE / PROVENANCE
STATUS
ACTION
```

A build check should fail on known prohibited assets where practical.

---

# 31. COPY DISCIPLINE

The product's language must match the actual mechanic.

Create a `COPY_RULES.md` or section in the PRD.

Define:

```text
ALWAYS SAY:
NEVER SAY:
REQUIRED PRODUCT TERM:
LEGAL/TECHNICAL BOUNDARY:
```

This is especially important when:
- finance;
- RWAs;
- identity;
- AI;
- security;
- gambling-adjacent products;
- custody;
- compliance.

---

# 32. STAGE 09 — BUILD THE DEMO AROUND THE STATE TRANSITION

The research's most defensible demo pattern is:

> **Visible state transition.**

Examples from the supplied research:

- friction disappears;
- physical action → digital reward;
- hidden state → verifiable evidence;
- real-world event → automatic settlement;
- impossible interoperability → visible result;
- package query → security evidence.

The strategy is not:

> “show twelve features.”

It is:

> **make one causal chain undeniable.**

---

# 33. 60-SECOND DEMO STRUCTURE

Recommended:

### 0–5s — WHAT
One sentence + product object.

### 5–15s — SETUP
Show the user action.

### 15–35s — MECHANISM
Show the important state transition.

### 35–50s — PROOF
Show the real chain/system evidence.

### 50–60s — WHY IT MATTERS
Close with the product's memorable outcome.

The exact timings can change.

The principle cannot:

> **before → action → after → proof**

---

# 34. DO NOT DEMO THE ARCHITECTURE FIRST

Do not start with:

```text
Frontend
API
Smart contracts
Oracle
Relayer
Indexer
```

Start with the product.

Then reveal the architecture only after the judge understands the behavior.

---

# 35. THE JUDGE LAYER

The product experience should naturally answer:

### “What is this?”
Product category.

### “Why do I care?”
Outcome.

### “What changed?”
Visible state transition.

### “Why blockchain?”
Enforcement, portability, verification, settlement, coordination, or other specific property.

### “What is actually novel?”
Sponsor-native mechanism.

### “Does it work?”
Canonical live evidence.

### “Can I verify it?”
Transaction/proof path.

---

# 36. SUBMISSION PACKAGING

Prepare these before final submission:

```text
1. live URL
2. repository
3. deployed contracts
4. canonical E2E run
5. verifier command
6. demo video
7. pitch copy
8. screenshots
9. technical description
10. limitations / evidence notes
```

Do not make the judge hunt for proof.

---

# 37. README STRUCTURE

Recommended:

```text
# Product

one-line proposition

## 30-second explanation

## Demo

## Live deployment

## What is novel

## Why the sponsor matters

## How it works

## Verified end-to-end

## Architecture

## Security / invariants

## Known limitations

## Reproduction

## Contract addresses

## License
```

Put proof high in the document.

---

# 38. FINAL VISUAL QUALITY GATE

Score 0–2.

| Criterion | 0 | 1 | 2 |
|---|---|---|---|
| Product clarity | unclear | acceptable | immediate |
| Product-specific visual identity | generic | some identity | unmistakable |
| Technical mechanism expressed visually | absent | partial | central |
| Information hierarchy | noisy | okay | excellent |
| Typography | default | coherent | intentional |
| Spacing/density | random | consistent | deliberate |
| Signature interaction | absent | present | memorable |
| State coverage | weak | partial | strong |
| Motion | random | acceptable | purposeful |
| Mobile | broken | responsive | intentional |
| Technical honesty | misleading | mostly accurate | exact |
| Judge proof | hidden | available | immediate |

Target:

> **20/24 minimum**

A 0 in any of these is a redesign trigger:

- product clarity;
- visual identity;
- technical mechanism;
- technical honesty.

---

# 39. ANTI-AI UI TEST

Ask:

> Could I get roughly this interface by prompting an AI to make a premium Web3 dashboard?

If YES:

**FAIL.**

Then ask:

> What three things identify this product if I remove the logo?

Good answers involve:
- product-specific interaction;
- product-specific object;
- product-specific visual system;
- state-machine visualization.

Bad answer:

> “The gradient and font.”

---

# 40. IDEA → BUILD WORKSHEET

Copy this for every new hackathon.

```text
EVENT:
DEADLINE:
JUDGING:
PRIZE TRACK:
MANDATORY TECHNOLOGIES:

PROBLEM:
USER:
CURRENT WORKFLOW:
CURRENT SUBSTITUTE:

RECOGNIZABLE PRODUCT:
NEW CAPABILITY:
SPONSOR:
SPONSOR-NATIVE WEDGE:

WHY THIS NEEDS THE SPONSOR:
COUNTERFACTUAL WITHOUT SPONSOR:

PRODUCT ONE-LINER:

CORE STATE MACHINE:

SIGNATURE INTERACTION:

DEMO BEFORE:
DEMO ACTION:
DEMO AFTER:
DEMO PROOF:

WHY BLOCKCHAIN / WHY INFRASTRUCTURE:

VISUAL WORLD:
VISUAL THESIS:
PRIMARY PRODUCT OBJECT:
DESIGN LANGUAGE:
ANTI-REFERENCES:

LIVE DEPLOYMENT TARGET:
CANONICAL RUN:
EVIDENCE METHOD:

MAIN RISKS:
KNOWN LIMITATIONS:

IDEA SCORE:
PRODUCT SCORE:
SPONSOR SCORE:
DEMO SCORE:
BUILD SCORE:
PROOF SCORE:

FINAL DECISION:
```

---

# 41. MASTER IDEA SCORECARD

Use this after research.

| Test | Score 0–5 |
|---|---:|
| A stranger understands it | |
| Product is recognizable | |
| New capability is surprising | |
| Sponsor capability is essential | |
| Blockchain/infrastructure has a precise reason | |
| One strong state transition exists | |
| Demo fits in 60 seconds | |
| Live proof is realistic | |
| Competition is not overwhelming | |
| UI can become distinctive | |
| Implementation fits available time | |
| Failure modes can be handled | |
| Evidence can be reproduced | |
| **TOTAL / 65** | |

Suggested threshold:

> **52+ = build candidate**

---

# 42. MASTER BUILD GATE

Before adding feature #N, ask:

```text
Does this improve:
[ ] user outcome
[ ] sponsor differentiation
[ ] technical proof
[ ] demo clarity
[ ] judge comprehension

or is it merely:
[ ] extra feature
[ ] extra dashboard
[ ] extra API
[ ] “looks impressive”
[ ] roadmap bait
```

If the second group wins:

> Do not build it.

---

# 43. THE FEATURE FREEZE

When the core demo works:

**freeze new features.**

Spend remaining time on:

- bugs;
- proof;
- UI;
- responsive behavior;
- performance;
- security;
- submission;
- video;
- judge comprehension.

A partially built “bigger” product is usually weaker than a smaller product whose central promise is visibly real.

---

# 44. THE “ONE REAL FLOW” PRIORITY

A hackathon MVP should have:

> **one real, complete, beautiful, provable flow**

before it has:

> five incomplete flows.

Use this order:

```text
one user
one core action
one real state transition
one real settlement/result
one proof
```

Then expand only if time remains.

---

# 45. WHEN TO USE VISUAL REFERENCES

Reference products should be used at the **art-direction stage**, not copied during implementation.

Extract:

- information hierarchy;
- density;
- motion;
- interaction quality;
- composition;
- visual restraint;
- product storytelling.

Do not copy:
- logo;
- branded colors;
- exact screens;
- proprietary assets;
- wording;
- distinctive illustrations.

The output should be original.

---

# 46. HOW TO WORK WITH AN AI CODING AGENT

Give the agent the project specification in this order:

```text
1. event brief
2. product thesis
3. sponsor capability card
4. product state machine
5. evidence requirements
6. visual thesis
7. design system
8. implementation phases
9. test gates
10. submission requirements
```

Do not say only:

> “Build this app.”

Give the agent a **build contract**.

---

# 47. REQUIRED AGENT BEHAVIOR

The agent must:

- read the spec before editing;
- respect the source-of-truth order;
- work one phase at a time;
- make small coherent commits;
- write tests with or before risky behavior;
- inspect changed code after edits;
- run narrow tests proving fixes;
- never silently swallow errors;
- avoid fake external-success branches;
- record divergences;
- record bugs;
- record limitations;
- produce a status report after each phase.

---

# 48. PHASE STATUS TEMPLATE

Every build phase must end with:

```text
PHASE:
STATUS: PASS | FAIL | BLOCKED
COMMIT:
FILES CHANGED:
CONTRACT DEPLOYMENTS:
TEST COUNTS:
LIVE TRANSACTIONS:
EVIDENCE LINKS:
SECURITY FINDINGS:
KNOWN LIMITATIONS:
NEXT PHASE:
```

A phase is not PASS because the code compiles.

It is PASS only when its required product behavior has evidence.

---

# 49. RESEARCH QUALITY RULES

When researching winning projects:

### Separate:
- organizer-confirmed winner/finalist;
- accessible verified evidence;
- inferred pattern;
- unverified claim.

### Never:
- turn a small finalist sample into universal law;
- invent missing finalists;
- assume underrepresentation has a known cause;
- confuse sponsor prize demand with market saturation;
- confuse a good demo with proof of causality;
- treat a winning idea as evidence that its category will win again.

Use labels:

```text
VERIFIED
OBSERVED
INFERRED
UNVERIFIED
```

---

# 50. STRATEGIC MODEL FOR NEW HACKATHONS

The entire system can be compressed to this:

## A. SEARCH

Find:

> **important workflow + new technical opening**

## B. SHARPEN

Turn it into:

> **recognizable product + surprising capability**

## C. SPONSORIZE

Make the sponsor:

> **load-bearing, not decorative**

## D. DESIGN

Turn the mechanism into:

> **product-specific visual identity + signature interaction**

## E. BUILD

Ship:

> **one complete real flow**

## F. PROVE

Produce:

> **canonical run + verifier + transaction/evidence chain**

## G. DEMO

Show:

> **before → action → visible state change → proof**

## H. SUBMIT

Make the judge see:

> **what it is + why it matters + why the technology matters + proof**

---

# 51. THE FINAL “WINNING” EQUATION

This is the strategic equation to optimize:

> **WINNING POTENTIAL =**
>
> **Product Meaning**
> ×
> **Sponsor Specificity**
> ×
> **Novel Capability**
> ×
> **Demo Clarity**
> ×
> **Proof Density**
> ×
> **Execution Quality**
> ×
> **Visual Distinctiveness**

This is multiplicative in practice.

A project with excellent tech but zero demo clarity suffers.

A beautiful interface with no real proof suffers.

A clever idea with weak sponsor fit suffers.

A novel idea with generic UX can be forgotten.

A strong product with dishonest claims destroys judge trust.

---

# 52. THE MOST IMPORTANT LESSON FROM THE RESEARCHED BUILDER

Do not imitate his style.

Imitate the discipline visible across his work:

### He defines the product before the page.

### He gives the coding agent hard constraints.

### He turns the core technical mechanism into a product behavior.

### He specifies the visual language rather than asking for “premium UI.”

### He builds explicit state machines.

### He treats proof as a deliverable.

### He records limitations instead of hiding them.

### He uses phase gates.

### He keeps canonical evidence.

### He freezes scope once the core product is proven.

That is the transferable advantage.

---

# 53. EQUITY BENEFIT WALLET — HOW THIS SYSTEM WOULD HAVE CHANGED IT

The existing EBW build should not be judged by whether it resembles another builder's site.

The stronger conceptual system would have been:

## Recognizable product

A **work-incentive agreement**.

## New capability

A stock-linked incentive can be funded into contract-controlled settlement rather than depending on the employer to remain the sole custodian of the commitment.

## State machine

```text
DRAFT
→ FUNDED
→ HELD BY CONTRACT
→ RELEASED
OR
→ DEADLINE REACHED
→ CLAIMABLE
→ SETTLED
```

## Signature interaction

```text
commitment
→ contract holds it
→ employer releases
OR
→ calendar unlocks claimant path
```

## Visual object

The agreement itself.

## Visual identity

A financial/work agreement instrument.

## Demo

Create → fund → independent recipient view → release or deadline path → proof.

## Important truth boundary

The current MVP does NOT objectively adjudicate whether work is complete.

The employer confirms completion by releasing.

The deadline provides the contractor fallback.

The smart contract enforces settlement permissions and timing.

That is the claim.

---

# 54. DO NOT TURN THIS INTO A TEMPLATE LOOK

This system must produce different products with different visual worlds.

For one project:

> industrial control room

For another:

> editorial dossier

For another:

> consumer utility

For another:

> financial instrument

For another:

> physical game interface

The method is shared.

The appearance is not.

---

# 55. FINAL OPERATING RULE

At the beginning of every hackathon project, ask:

> **What is the smallest real product that can make a judge SEE a capability they did not have before?**

Then:

> **What sponsor-native infrastructure makes that capability credible?**

Then:

> **What visible state transition proves the capability?**

Then:

> **What product-specific visual language makes that mechanism memorable?**

Then:

> **What is the smallest live build that proves it?**

Then:

> **What evidence makes the claim independently checkable?**

Only after those answers exist should implementation begin.

---

# APPENDIX A — EVIDENCE-LED RESEARCH FINDINGS USED BY THIS SYSTEM

The attached research found:

- The strongest verified finalist-form pattern is **recognizable product/category + concrete surprising capability** rather than a pure frustration-first structure.
- Explicit frustration-first descriptions were rare in the verified ETHGlobal New York 2026 top-10 sample.
- AI-agent architecture was a crowded finalist category in the accessible 2026 material.
- Prediction markets were rapidly crowding.
- Agent security / verification was a growing cluster.
- Physical-world interaction, evidence/provenance, operational workflows, non-wallet interaction, and non-English-first products were smaller signals, but the research explicitly warns that underrepresentation does not establish why those areas are underrepresented.
- The most defensible repeated demo commonality was **visible state transition**.
- The research explicitly rejects a universal “next winning category.”
- The research explicitly distinguishes observed finalist composition from judge-causality claims.

These findings are strategy inputs, not guarantees.

---

# APPENDIX B — RESEARCHED BUILDER PATTERN

The public winsznx repositories inspected for this strategy repeatedly show:

## DarkOdds
A strongly specified design thesis, explicit anti-patterns, detailed visual tokens, product-specific primitives, and a privacy interaction that makes redaction/disclosure part of the UI.

## Lictor
A “cinematic execution narrative” approach where the landing page mirrors the actual system stages: signal, debate, consensus, capital, execution, receipts.

## Custos
A gate-based security model where the payment process itself is represented as a chain of independent checks and the AI is explicitly not allowed to become the payment authority.

## Conduit
A strict source-of-truth hierarchy, explicit invariants, phase-by-phase implementation, architecture decisions, real custody seams, and hard stop conditions.

## Bespeak
Canonical run/evidence packaging, explicit proven/unproven claim states, tested invariants, source provenance, asset verification, and honest limitations.

## Bull Rush
The live product behavior is tied to deterministic replay/proof, and asset provenance is treated as a deployment-quality concern rather than an afterthought.

The recurring lesson is not a common color palette or common visual layout.

It is:

> **highly specified product behavior + strong implementation discipline + explicit proof + product-specific visual language.**

---

# APPENDIX C — FINAL PRE-SUBMISSION CHECKLIST

## Product
- [ ] One-sentence proposition is clear
- [ ] Recognizable product/category
- [ ] User is specific
- [ ] Core capability is concrete
- [ ] Why the infrastructure is necessary is explicit

## Sponsor
- [ ] Sponsor capability is native
- [ ] Sponsor is load-bearing
- [ ] Counterfactual without sponsor is documented
- [ ] Live sponsor capability is tested
- [ ] Limits are documented

## UX
- [ ] 5-second comprehension
- [ ] 30-second comprehension
- [ ] Main journey is obvious
- [ ] Signature interaction exists
- [ ] State machine is reflected in UI
- [ ] Error/loading/empty states exist

## Visual
- [ ] Product-specific visual world
- [ ] Design tokens exist
- [ ] Anti-patterns are banned
- [ ] UI does not feel like a generic AI dashboard
- [ ] Technical mechanism is visible through interaction
- [ ] Mobile is intentionally designed
- [ ] Assets have provenance

## Engineering
- [ ] Real deployment
- [ ] Contract/source verification where applicable
- [ ] Unit tests
- [ ] Integration tests
- [ ] Adversarial tests
- [ ] E2E test
- [ ] Invariants documented
- [ ] No fake production success paths

## Proof
- [ ] Canonical run
- [ ] Transaction hashes
- [ ] Verifier
- [ ] Evidence artifact
- [ ] PROVEN / UNPROVEN status for major claims
- [ ] Known limitations

## Demo
- [ ] Before state
- [ ] User action
- [ ] Visible state change
- [ ] Proof
- [ ] Clear closing message

## Submission
- [ ] Live link works
- [ ] Repo works
- [ ] Screenshots are strong
- [ ] Demo video works
- [ ] Sponsor selections are accurate
- [ ] Contract addresses are correct
- [ ] Description is truthful
- [ ] No unsupported claims
- [ ] Final review by a stranger completed

---

# APPENDIX D — THE ONE-PAGE COMMAND TO GIVE THE CODING AGENT

```text
You are implementing a hackathon product under an evidence-led build system.

Before editing code:

1. Read the event brief.
2. Read the product thesis.
3. Read the sponsor capability card.
4. Read the state machine.
5. Read the evidence requirements.
6. Read the visual thesis and design grammar.
7. Read the current implementation status.

Rules:

- Do not invent unsupported capabilities.
- Do not build fake production success states.
- Do not add features outside the current phase.
- Treat prerequisites as real protocol steps.
- Verify state after prerequisite transactions.
- Record bugs and implementation drift.
- Use small coherent commits.
- Build one real end-to-end path before expanding.
- Design the product mechanism into the UI.
- Do not default to generic AI/Web3 visual patterns.
- Keep the visual identity specific to this product.
- Design the signature interaction first.
- Treat evidence as part of the product, not documentation cleanup.

Every phase must finish with:

PHASE:
STATUS:
COMMIT:
FILES CHANGED:
TESTS:
LIVE EVIDENCE:
SECURITY FINDINGS:
KNOWN LIMITATIONS:
NEXT PHASE:

A phase is PASS only when its behavior is proven.
```

---

# FINAL WORD

The point of this document is not to guarantee a win.

No public dataset can justify that guarantee.

The point is to make your process systematically better at the things the evidence actually supports:

> **specific product form, sponsor-native capability, visible state transition, disciplined execution, truthful evidence, and distinctive product-specific design.**

That is a much stronger system than “find a painful problem” or “make a premium UI.”

