# MONAD METROPOLIS 2026 — FULL HANDOVER / CONTINUATION FILE

## PURPOSE OF THIS FILE

This file is a handover for a NEW CHAT / NEW AGENT taking over the Monad Metropolis hackathon research.

The new agent must behave as if it is continuing the same research process, but it MUST NOT assume anything beyond what is explicitly recorded here.

The most important instruction:

> DO NOT INVENT AN IDEA, DO NOT START CODING, AND DO NOT CREATE A BUILD SPEC UNTIL THE RESEARCH PROCESS PASSES THE REQUIRED IDEA-SELECTION GATES.

The user is specifically trying to avoid hallucination, repeated research, and “cool technology → random app” thinking.

The user’s actual strategic system is in:

https://github.com/Temmygabriel/tempo_hack/blob/main/HACKATHON_WINNING_SYSTEM_IDEA_TO_FULL_BUILD.md

That file is the authoritative strategy document for idea selection and build discipline.

The research phases below were intentionally kept OUT of the repo. They are conversation research only.

---

# 0. USER / WORKING STYLE / HARD CONSTRAINTS

The user is a solo hackathon builder in Nigeria.

Important constraints:

- $0 / free-tier first. The user currently has essentially no budget for paid developer infrastructure.
- Windows PC with 8 GB RAM.
- User says the PC cannot comfortably handle heavy npm builds/tests locally.
- Prefer GitHub Actions / cloud for heavy builds/tests.
- Vercel is preferred for deployment.
- GitHub is source of truth for project code.
- Do not put secrets in public GitHub repos.
- User wants simple wording, roughly “explain it like I am 15.”
- No jargon for the sake of sounding technical.
- No guesswork.
- No hallucinated capabilities.
- Evidence-first research.
- One phase at a time.
- Do NOT save temporary research phases into the project repo.
- Only the FINAL complete build spec should eventually go into the project repo, after an idea is actually selected.
- The user does not want generic “premium Web3 dashboard” UI.
- Product UI must be product-specific and mechanism-driven.
- User values adversarial idea killing more than optimistic brainstorming.

The user explicitly corrected the workflow:

> Research phases are internal to the chat only. Do not save Stage 1/2/3/4/5 research files to the repo. Only the eventual final build spec should be committed to the project repo.

---

# 1. THE USER’S ACTUAL HACKATHON STRATEGY

The exact strategy document is:

HACKATHON_WINNING_SYSTEM_IDEA_TO_FULL_BUILD.md

Core thesis:

> Recognizable product/category + concrete new capability + a demo that produces an obvious visible state change.

The system is NOT:

- “find the biggest problem”
- “find an uncrowded category”
- “build AI”
- “use as many sponsors as possible”
- “make a pretty Web3 dashboard”

The actual operating sequence is:

01 EVENT FORENSICS
02 OPPORTUNITY RESEARCH
03 SPONSOR-CAPABILITY RESEARCH
04 IDEA GENERATION
05 IDEA SELECTION
06 PRODUCT + STATE-MACHINE DESIGN
07 PRODUCT ART DIRECTION + UI/UX
08 EVIDENCE-FIRST ENGINEERING
09 DEMO + JUDGE COMMUNICATION
10 SUBMISSION + FINAL AUDIT

Core strategic equation:

> WINNING POTENTIAL =
> Product Meaning
> × Sponsor Specificity
> × Novel Capability
> × Demo Clarity
> × Proof Density
> × Execution Quality
> × Visual Distinctiveness

---

# 2. KEY RULES FROM THE STRATEGY DOCUMENT

## 2.1 Opportunity research

For every real workflow investigate FIVE signals:

A. Existing behavior
- What do users do today?

B. Friction
- What is slow, risky, confusing, expensive, opaque, or impossible?

C. Existing substitutes
- Who already solves it?

D. Technical opening
- What changed recently that makes a better solution possible?

E. Demoability
- Can the improvement be seen in under 60 seconds?

Important:

> Do not optimize for category rarity alone.

---

## 2.2 Sponsor-capability forensics

For every sponsor capability:

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

Score 0–5:

- Native
- Essential
- Visible
- Provable
- Buildable

Target:

> 20/25 or higher

Critical test:

> What materially changes if this sponsor technology is removed and replaced with a generic equivalent?

If almost nothing changes, sponsor fit is weak.

---

## 2.3 Idea generation

Generate from:

> mechanism × workflow

but only AFTER opportunity and sponsor research.

Good construction:

> recognizable product + unusual capability

or

> familiar analogy + new mechanism

or

> concrete outcome + technical mechanism

or

> normal workflow + sponsor-native infrastructure = new behavior users notice

The blockchain/technology does NOT have to be the hero.

The product behavior is the hero.

---

## 2.4 Idea selection

100-point model:

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
| TOTAL | 100 |

Bands:

85–100 = attack candidate
75–84 = viable
65–74 = strategic only
<65 = discard

Master scorecard from the document is also useful:

- Stranger understands it
- Recognizable product
- New capability is surprising
- Sponsor capability essential
- Blockchain/infrastructure has precise reason
- One strong state transition
- Demo fits 60s
- Live proof realistic
- Competition acceptable
- UI can become distinctive
- Implementation fits available time
- Failure modes handleable
- Evidence reproducible

Suggested threshold:

> 52+/65 = build candidate

---

## 2.5 15-minute stranger test

A stranger should quickly understand:

1. What is this?
2. What does it let me do?
3. What happens that was not possible/easy before?
4. Why does the infrastructure matter?

If 1–3 are not quickly understandable, change product framing.

---

## 2.6 Product requirements after selection

One-sentence product contract:

> [Recognizable product] that [concrete new capability] for [specific user/outcome].

Then define real state machine.

Then identify irreversible moment.

Then define:

TRIGGER
BEFORE
TRANSITION
AFTER
MEANING
PROOF

Core demo pattern:

> before → action → visible state change → proof

---

# 3. MONAD METROPOLIS — EVENT CONTEXT

Fresh current research was required because the current date is 2026-10-05.

The event is a six-week global online hackathon.

Four tracks:

1. Onchain Finance & Trading
2. Consumer Products & Payments
3. Social, Attention & Culture
4. Trust, Identity & AI Infrastructure

Public research indicates:

- $250K+ headline prize pool.
- $30K per track has appeared in current public event research.
- Exact Grand Champion amount has conflicted between public sources. Do NOT claim an exact grand prize without fresh verification.
- Deadline has also conflicted in public sources:
  - some current sources show 2026-10-12
  - current public participant/research repos based on official portal commonly show 2026-10-13 11:59 PM ET, which becomes 2026-10-14 03:59 UTC.
- Internal planning target was Oct 12 to create safety margin.
- Official portal details have not always been directly openable without login.

Therefore:

> Do not state deadline as absolute without a fresh current portal check in the new chat.

Current Monad developer-network facts that were repeatedly confirmed during research:

- Monad testnet Chain ID: 10143
- testnet RPC: rpc.testnet.monad.xyz
- testnet explorer: testnet.monadscan.com
- testnet faucet is publicly available
- Monad is a high-throughput EVM chain
- current public Monad materials report ~300 ms blocks and ~600 ms deterministic finality
- Monad supports EIP-7702
- Monad ecosystem references P256/WebAuthn
- Monad has Execution Events
- Monad / Category Labs is working on encrypted mempool / BTX
- x402 support exists for Monad

Do not confuse:

- official current documentation
- current ecosystem reports
- third-party hackathon repos
- participant research documents

Always label confidence.

Use:
VERIFIED
OBSERVED
INFERRED
UNVERIFIED

---

# 4. IMPORTANT METHODOLOGICAL DRIFT THAT HAPPENED IN THIS CHAT

This is important because the new agent must not repeat it.

At one point, the research drifted into:

> “Monad has encrypted mempool / BTX, so let’s generate private-intent ideas.”

That was WRONG according to the user’s strategy system.

The user called this out.

The correct strategy is:

> opportunity first → sponsor capability → idea

NOT:

> Monad primitive → app idea

That drift was explicitly corrected.

Later research also sometimes leaned too heavily on “what is less crowded?” That is also insufficient.

The strategy says:

> low saturation is only one small part of the score.

The new agent MUST preserve this correction.

---

# 5. MONAD STAGE HISTORY

This is the chronological research record.

---

## STAGE 01 — EVENT FORENSICS

Status:

> PASS / CONDITIONAL

Positive:

- global
- online
- solo-friendly
- free
- public Monad testnet
- faucet
- RPC
- several tracks
- multiple sponsor/technology routes

Still needing fresh verification:

- exact current eligibility/country rules
- exact deadline/time zone
- exact detailed judging rubric
- exact sponsor bounty availability/eligibility
- exact Grand Champion amount

Internal execution cutoff used:

> Oct 12, 2026

This was an internal safety target, NOT a claim about official event deadline.

---

# 6. STAGE 02 / EARLY OPPORTUNITY RESEARCH

Several obvious workflow families were investigated and killed.

### Group gifting / collective contributions

Existing products already provide shared contribution pots and tracking.

Verdict:

> KILL

Reason:
real problem but established product category.

---

### Savings circles / susu / ajo

Existing products already digitize ROSCAs, contributions and payouts.

Verdict:

> KILL

Reason:
real problem but direct substitutes.

---

### Marketplace escrow

Existing escrow providers already handle buyer payment, holding, delivery confirmation and seller release.

Verdict:

> KILL

Reason:
extremely mature product shape; blockchain escrow alone not novel.

---

### Rental deposits

Existing rental platforms already provide deposit holding, inspection windows, damage handling and refunds.

Verdict:

> KILL

---

### Freelancer milestone escrow

Upwork/Freelancer already have milestone/escrow behavior.

Verdict:

> KILL

This taught an important lesson:

> A painful workflow is not automatically an open hackathon opportunity.

---

# 7. FIRST STRONG OPPORTUNITY: MACHINE-PAID DIGITAL SERVICES

This was the first strong-looking opportunity territory.

Conceptual workflow:

machine/agent pays for a service
→ service executes
→ result is checked
→ settlement depends on outcome

Stage 2 signals:

- Existing behavior: machine payments + APIs
- Friction: machine can pay even when service fails / tool quality uncertain
- Existing substitutes: x402, service marketplaces, runtime monitoring
- Technical opening: x402 + external verification
- Demoability: very strong

Sponsor work then found:

### Monad/x402

Strongest capability.

Current Monad docs/ecosystem evidence shows x402 support for programmatic machine payments.

Capability score used:

25/25

But:

> “machine payments on Monad” is NOT itself novel.

Current Monad/x402 marketplace projects already exist.

### Chainlink CRE

CRE can call external APIs, read chains, perform offchain computation, reach consensus and write outcomes back onchain.

Potential role:

payment
→ service execution
→ external result
→ CRE verification/consensus
→ settlement

Score used:

~21/25

Caveat:
production CRE workflow deployment may require approval/access, so it is a technical gate, not guaranteed.

### Envio

Strong indexer/evidence layer.

Score used:

~22/25

Not central innovation.

### Privy / Dynamic

Useful wallet infrastructure.

Not load-bearing.

Counterfactual: replace with another wallet provider and core idea survives.

---

# 8. MACHINE-SERVICE IDEA GENERATION

Generated candidates:

- Data Order
- Restore Drill
- Deploy-to-Verify
- Browser Job Receipt
- Freshness Pass
- Proof-Ready Document
- Workflow Purchase
- SLA Auto-Claim
- Verified Webhook Delivery
- Compute Artifact Purchase

Initial scores ranged roughly 68–84.

Then adversarial Stage 5 killed them.

Important collisions found:

### Data Order
OpenBook is a current product directly combining:
- machine purchase
- freshness
- delivery checking
- refund/settlement

Verdict:

> KILL

### Freshness Pass
Also direct collision with freshness/data products.

Verdict:

> KILL

### Restore Drill
Existing restore verification products already test actual recoverability.

Verdict:

> KILL

### SLA Auto-Claim
Existing SLA-credit products and monitoring systems already occupy this.

Verdict:

> KILL

### Deploy-to-Verify
CI/CD systems already verify successful deployments.

Verdict:

> KILL

### Browser Job Receipt
Current browser automation/payment products already avoid charging on failed tasks.

Verdict:

> KILL

### Workflow Purchase
Too close to machine service procurement/agent-service infrastructure.

Verdict:

> KILL

### Proof-Ready Document
Crowded provenance/verification space.

Verdict:

> KILL

### Compute Artifact Purchase
Existing decentralized compute marketplace and escrow behavior.

Verdict:

> KILL

### Verified Webhook
Weak product recognizability and weak reason for blockchain.

Verdict:

> KILL

Final lesson:

> “payment conditional on verified service outcome” is itself becoming infrastructure.
> Do not build that as the main novelty.

Stage 5 result:

> NO BUILD CANDIDATE.

---

# 9. SECOND OPPORTUNITY: FAST SHARED-STATE APPLICATIONS

Stage 2 was reset.

Idea territory:

> real products where many participants change shared state quickly.

Examples considered:

- inventory stocktake
- package custody
- maintenance handoff
- incident room
- live crowd control
- shared capacity

Most failed.

Why?

Because a normal database is enough.

This is critical.

The correct question is not:

> “Can Monad make this faster?”

It is:

> “Does the fact that this state is public/programmatic/onchain materially change the product?”

If the answer is no, kill it.

---

# 10. STAGE 3 FOR SHARED STATE

Monad’s strongest relevant capabilities:

### Parallel execution

Current Monad architecture supports parallel transaction execution with conflict detection.

### Fast finality

Current public Monad materials report ~300 ms blocks and ~600 ms deterministic finality.

### EIP-7702

Supports smart-account-like capabilities from EOAs, including batching/session-key style behavior.

### Envio

Strong indexing / evidence layer.

Sponsor / capability assessment:

- Monad core: 25/25
- EIP-7702: ~22/25
- Envio: ~22/25
- Mera: useful but not core

But the opportunity family itself mostly failed.

Stage 4 generated:

- Live Stocktake Ledger
- Custody Handoff
- Maintenance Handoff
- Live Incident Room
- Live Crowd Control
- Shared Capacity Board

All failed or were weak.

The key conclusion:

> “fast shared state” is too broad; most ordinary workflows should remain in databases.

Stage 4 result:

> NO ATTACK CANDIDATE.

---

# 11. THIRD OPPORTUNITY: MEDIA PROVENANCE RECOVERY

Fresh Stage 2 research found a real 2026 problem:

Media provenance metadata can be stripped by:
- compression
- cropping
- screenshots
- re-encoding
- reposting

C2PA explicitly discusses soft bindings and recovery of a detached manifest using perceptual fingerprints/invisible watermarks.

OpenAI and Adobe also currently provide provenance-related systems.

Important:

> DO NOT CLAIM WE INVENTED PROVENANCE RECOVERY.

C2PA itself already describes detached-manifest recovery.

The opportunity explored was:

> Build a recognizable product that does something useful once provenance can be recovered.

Sponsor ideas:

- Mera / passkey
- P256/WebAuthn
- Envio
- optionally Chainlink CRE

Strong-looking product candidates:

- Rights Checkout
- Remix Receipt
- UGC Rights Check
- Creator Credit Recovery
- Media Handoff Receipt
- AI Dataset License Receipt
- Marketplace Photo Origin

Then adversarial Stage 5 killed the family.

### Remix Receipt

ERC-5554 covers derivative works, commercial exploitation, attribution, license/royalty semantics.

FreeMix currently has machine-readable remix licensing and royalty concepts.

KAIZORA has downstream royalty/licensing/lineage concepts.

Verdict:

> KILL

### Rights Checkout

Existing rights management / clearance platforms already do similar workflows.

Verdict:

> KILL

### UGC Rights Check

Existing UGC rights management products already handle channel, duration, paid advertising, exclusivity, etc.

Verdict:

> KILL

### Creator Credit Recovery

C2PA/OpenAI already address provenance recovery/verification.

Verdict:

> KILL

### Media Handoff Receipt

Adobe Content Credentials + newsroom provenance systems already occupy the workflow.

Verdict:

> KILL

### AI Dataset License Receipt

Emerging dataset provenance/licensing products and standards already occupy this.

Verdict:

> KILL

Stage 5:

> NO BUILD CANDIDATE.

Lesson:

> Provenance recovery should be treated as existing infrastructure, not as the hackathon’s innovation.

---

# 12. OTHER TECHNICAL BRANCHES ATTACKED

These were considered or mentioned but should not be revived without new evidence.

## Encrypted mempool / BTX / private intent

Interesting Monad/Category Labs research.

Third-party current Metropolis example:
Betex uses BTX-style encrypted orders on Monad testnet.

Problem:

- public application-level API/access remains unclear
- much of evidence is research / third-party
- crypto/infrastructure burden is high
- private auction itself is not novel

Verdict:

> DO NOT CURRENTLY USE AS PRIMARY DEPENDENCY UNLESS FRESH OFFICIAL ACCESS IS PROVEN.

It can still be revisited as a future technical opening.

---

## Private auctions / sealed bids

Previously considered.

Generic private/sealed auctions are too crowded.

Do not return to this unless the workflow itself is unusually strong and clearly distinct.

---

## AI memory

Earlier “Recall” idea was initially an attack candidate.

It was later killed.

Current collisions included:

- Decentrify
- Lethe
- Nimble
- Memobase
- Vertiso Memory
- Dijin
- Engram/LifeContext
- Quarantine

Conclusion:

> cross-app AI memory + Monad/Mera is NOT enough.

The broader permission/memory family was also crowded.

---

## Agent identity / reputation

Extremely crowded in current Metropolis field.

Current public repos include many agent identity/reputation/certification projects.

DO NOT revisit generic:

- agent passport
- ERC-8004 registry
- agent reputation dashboard
- agent certification
- generic trust score

without a very strong consumer product consuming the reputation.

---

## Generic AI agents

Crowded.

Do not build:
- generic trading agent
- agent wallet
- agent passport
- agent procurement
- agent marketplace

unless the product has a much deeper specific workflow.

---

## Per-second / per-block funding

Initially interesting.

Later research found:
- Perennial has every-block funding
- Sidekick (ETHGlobal 2026 winner) already uses continuous/per-block funding

Verdict:

> KILL as a generic novelty.

---

## Onchain credit history

Initially surfaced as whitespace.

Later current research found existing products such as:
- ZentraScore
- ChainScore
- VIZI
- Blocrate
and broader credit scoring products.

Verdict:

> KILL as generic idea.

---

## Passkey wallets / recovery

Mera is a real strong infrastructure capability, but:
- passkey wallets are a mature category
- Coinbase / Argent / Safe / Mixin / others already attack recovery/auth

Verdict:

> Mera should be treated as enabling infrastructure, NOT the product by itself.

---

# 13. CURRENT MONAD ECOSYSTEM / COMPETITIVE FIELD

A current public ecosystem map researched around 2026-09-28 recorded many Monad mainnet apps and current Metropolis builds.

Current ecosystem themes:

## Track 1 — Finance/Trading

Very crowded.

Examples/current products include:
- Kuru
- Perpl
- LeverUp
- Aave
- Euler
- Morpho
- Pendle
- Curvance
- various DEXs and terminals
- many new AI trading agents

Avoid:
- another AMM
- another DEX aggregator
- generic AI trading agent
- generic Perpl risk dashboard

---

## Track 2 — Consumer/Payments

Examples:
- MetaMask Money / mUSD
- Agora / AUSD
- PingMe
- UR
- Abound
- Meru
- Cero
- Mera
- Sablier
- Blink.cash
- Glider
- several current Metropolis remittance/payment projects

Current public participant repos include:
- settle
- Polaris
- Kirogi
- Homeward
- Ping-Pong Pay
- Coffee-by-the-Second
- Accrue
- etc.

Crowded subfamilies:
- remittance
- payment links
- family/shared wallets
- generic subscriptions
- simple stablecoin payments

---

## Track 3 — Social / Attention / Culture

Current ecosystem includes:
- Nad.fun
- CRSH Market
- Kizzy
- Levr Bet
- Blinq
- Hyperstitions
- Trendle
- Farcaster
- The Arena
- Collective Memory
- MUKU
- games and collectible products

This area has fewer serious public Metropolis repos than the other tracks, but “low number of repos” does NOT prove winning potential.

Potential spaces seen:
- beneficiary-paid curation
- person-bound ticketing/access
- cultural outcome markets

BUT:
- generic ticketing is already being built
- prediction/cultural markets are already present
- social-token feeds are crowded

---

## Track 4 — Trust/Identity/AI

Very crowded.

Ecosystem examples:
- ERC-8004 registries
- Mera
- MetaMask Agent Wallet
- BTX encrypted mempool
- Chainlink CRE
- Envio
- Nansen
- Zerion
- Tenderly
- QuickNode
- multiple agent identity/reputation builds

Current public Metropolis repositories include:
- AgentPassport
- agent-pay
- agent-cert
- pod
- agent-jobs
- agentproof
- MonadLens
- Trustset
- etc.

This track should be treated as highly saturated for generic agent ideas.

---

# 14. CURRENT METROPOLIS PUBLIC REPO SIGNALS / EXAMPLES

Current public repositories already observed during research include (not exhaustive):

## Finance
- tima-t/deltamon — delta-neutral vaults
- yigenfeng0707-netizen/metrix-ai — autonomous trading
- vincent-lxc/pulse-on-monad — auditable trading agent
- 0xMigzy/PerpGuard — Perpl risk/liquidation
- DhruPtel/...Alpha-Agents — NFT agents managing portfolios

## Consumer/Payments
- Savitura/settle — Nigerian family wallets + remittance
- icaluwu/Coffee-by-the-Second — per-second payments
- pauleke65/accrue — escrowed job payment
- HYBLOCK-LAB/torna — card refunds
- precious-akpan/monad-metropolis-merchant-rails — merchant/invoice settlement
- nickthelegend/polaris-monad — payment links, pay-in-4, subscriptions
- choiaewoooon/monad-metropolis (Kirogi) — earmarked remittance
- neromtoobad/homeward — passkey AUSD remittance
- mandaputtra/ping-pong-pay — payment links

## Social
- zk1123/Mosaic — address/personality profile
- Turnstile repo exists and explores tickets/access tied to person

## Trust/AI
- Richway17/metropolis-agent-passport
- zuemen/agent-passport
- Cubiczan/aegis-on-monad
- filip-study/agent-pay-monad
- ktb-devteam/agent-cert-monad
- nel349/pod
- grmkris/agent-jobs
- acg0606/agentproof-monad
- ProtocolForge770/monadlens-ai
- Alarm2024/metropolis-desk-sentinel

These are examples of visible current competition, not proof of winning probability.

---

# 15. PUBLIC ECOSYSTEM MAP DATA OBSERVED

A current public ecosystem map based on data pulled around 2026-09-28 reported approximately:

- $1.017B DeFi TVL on Monad
- ~140 listed protocols
- 4.2M+ active wallets (from Monad August 2026 ecosystem highlights)
- 700M+ transactions
- ~$767M+ stablecoin market cap
- 300 ms blocks
- 600 ms finality
- ~10k TPS claim in ecosystem material

The map also noted:
- Kuru was doing a very large share of Monad spot DEX volume
- Monad was strongest in lending/yield by TVL
- consumer/payments/social are present as apps but much smaller in TVL terms
- payments TVL is tiny

Treat these as ecosystem context, not hackathon judging evidence.

---

# 16. CURRENT BEST SPONSOR CAPABILITIES TO KEEP IN MIND

This list is not a list of ideas. It is a capability inventory.

## Monad / x402

Current evidence indicates Monad supports x402 for machine-facing payments.

Strong for:
- per-request payments
- machine commerce
- micro-payments
- usage-based billing

But:
> generic x402 product = crowded

Use only when it materially changes a recognizable workflow.

---

## Mera

Current Category Labs repo describes accounts from passkeys.

Strong for:
- no-seed-phrase onboarding
- passkey native UX
- simple consumer account creation
- multi-key/session patterns

But:
> Mera wallet itself is not a product thesis.

---

## EIP-7702

Useful for:
- batched interactions
- session-like permissions
- smart-account behavior from an EOA
- reduced-signature UX

Again:
> use as a product enabler, not the product.

---

## Envio

Strong for:
- indexing
- real-time/historical chain state
- evidence
- transaction/history views

Current ecosystem evidence also indicates free hosted testing/deployment options.

Do not make “Envio dashboard” the product.

---

## Chainlink CRE

Strong for:
- external API calls
- chain reads
- computations
- decentralized workflow consensus
- writing verified outcomes back onchain

Caveat:
production deployment/access may require approval.

Do not build a core product around CRE without first proving current hackathon access.

---

## Perpl

Useful:
- perps
- market data / APIs
- risk analytics

But finance is highly crowded.

---

## Kuru

Useful:
- onchain order book
- new markets
- trading products

But trading space is crowded.

---

# 17. IMPORTANT CURRENT RESEARCH STATUS

The conversation reached its maximum length before the final idea was selected.

Current exact status BEFORE this handover:

### Monad Stage 1
PASS / CONDITIONAL

### Monad Stage 2
Multiple branches investigated.
Recent strongest surviving opportunity was:

> Open-source software consumption tied to maintainer funding.

### Monad Stage 3
NOT YET COMPLETED FOR THIS LATEST OSS OPPORTUNITY.

### Monad Stage 4
NOT YET RUN FOR THE OSS OPPORTUNITY.

### Monad Stage 5
NOT YET RUN FOR THE OSS OPPORTUNITY.

This is the MOST IMPORTANT POINT TO RESUME FROM.

---

# 18. LATEST ACTIVE OPPORTUNITY: OPEN-SOURCE SOFTWARE CONSUMPTION → MAINTAINER FUNDING

This branch is the current handoff point.

Do NOT assume it is the winner.

It has only passed preliminary Stage 2.

## Workflow

Modern software uses huge dependency trees:

example:

my-app
- React
- Zod
- Playwright
- Axios
- many transitive packages

The software is consumed constantly.

Maintainers are often funded separately through:
- GitHub Sponsors
- subscriptions
- support contracts
- Tidelift
- maintenance-fee initiatives

The opportunity:

> reconnect actual software consumption with automated maintainer funding.

---

# 19. WHY THIS OPPORTUNITY LOOKED REAL

Current 2026 OpenSSF material explicitly discusses sustainable package-ecosystem economics and enterprise funding tied to usage/value.

Open Source Maintenance Fee (OSMF) is an active model where qualifying organizations pay maintenance fees for certain dependency use.

Polly is an example currently introducing a maintenance fee for qualifying organizations.

Tidelift already uses customer dependency/SBOM information to determine which open-source projects a customer depends on and allocate funding.

Royalty.dev is another newer current product exploring contribution/impact-based ongoing funding.

Therefore:

> “fund open source from usage” is NOT new by itself.

That must be respected.

---

# 20. THE POTENTIAL OPENING

Potential product mechanism:

software is built/deployed/consumed
→ dependency usage is measured
→ usage receipt generated
→ small programmable funding allocation
→ multiple maintainers receive their shares
→ allocation history is publicly verifiable

Example conceptual flow:

APP BUILD / DEPLOY
→ dependencies detected
→ usage receipt
→ allocation
→ maintainer distribution

The interesting possible novelty is:

> machine-generated usage event → automatic economic allocation

instead of:
- monthly sponsorship
- centralized subscription
- manually declared support
- SBOM-driven central funding

---

# 21. HUGE UNRESOLVED PROBLEM IN THE OSS OPPORTUNITY

The difficult question is:

> How do we know software usage is real and truthful?

An SBOM says:
“dependency exists.”

It does NOT automatically prove:
“dependency generated X amount of economic value.”

A self-reported usage number is weak.

Tidelift addresses the problem centrally through customer-submitted SBOMs and its own allocation system.

So any serious product needs a credible “usage receipt” or other evidence mechanism.

That is where Monad might potentially matter:

- machine-generated usage/payment event
- programmable distribution
- transparent allocation
- independent auditability

But this has NOT been proven yet.

---

# 22. STAGE 2 SIGNALS FOR OSS OPPORTUNITY

### Existing behavior
PASS

Companies use many open-source dependencies.

### Friction
PASS

Maintainer funding is disconnected from machine-measured usage/value.

### Existing substitutes
PASS WITH CAUTION

Strong substitutes:
- GitHub Sponsors
- Tidelift
- Open Source Maintenance Fee
- Royalty.dev
- other sponsorship/funding systems

Therefore:
> the idea must be more specific than “fund OSS from usage.”

### Technical opening
PLAUSIBLE

Potential:
- x402
- Monad fast/cheap settlement
- Envio
- Mera
- possible automated allocation

But not yet sponsor-proven.

### Demoability
STRONG

Potential demo:

APP BUILD
→ 12 dependencies detected
→ usage receipt
→ $0.037 allocated
→ 12 maintainer distributions
→ public settlement proof

This gives a good visible:
software use → funding
state transition.

---

# 23. CURRENT OSS OPPORTUNITY STATUS

> STAGE 02 = PASS / CONDITIONAL

Not selected.

No Stage 3 sponsor-card work has been completed after this latest branch in the old conversation.

The NEW CHAT should therefore continue:

> STAGE 03 — Sponsor-Capability Forensics for the OSS consumption→funding workflow.

Specifically investigate:

- Monad / x402
- Envio
- Mera
- any other current official Monad sponsor capabilities that materially matter

But only if the capability is:
- native
- essential
- visible
- provable
- buildable

Target >=20/25.

---

# 24. WHAT NOT TO DO NEXT

DO NOT immediately generate ten OSS ideas.

First determine whether:

> software consumption → automatic maintainer funding

has a sufficiently strong sponsor-native wedge.

Then Stage 4 should generate recognizable products from the workflow.

Examples of what NOT to build:
- generic “open-source funding dashboard”
- GitHub Sponsors clone
- generic dependency analytics dashboard
- generic blockchain donation page
- “AI-powered dependency sponsor”
- generic token/DAO for maintainers

Those would likely fail product recognizability and/or novelty.

---

# 25. WHAT THE NEW STAGE 4 SHOULD LOOK FOR

If Stage 3 passes, controlled idea generation should search for:

> recognizable developer/software product + concrete new capability

Possible shapes (NOT YET IDEAS):
- software billing
- package purchasing
- dependency checkout
- enterprise maintenance contracts
- “usage receipt” product
- automated funding obligation
- deploy-time support funding

But these are search directions only.

The new chat must research direct competitors before selecting any.

---

# 26. CURRENT COMPETITIVE WARNING FOR OSS

At minimum remember these existing categories/products:

### GitHub Sponsors
Direct maintainer sponsorship.

### Tidelift
Dependency awareness + enterprise funding allocation.

### Open Source Maintenance Fee
Maintenance fee tied to qualifying dependency use.

### Polly / similar maintainers
Demonstrates maintainers can explicitly charge organizations.

### Royalty.dev
Contribution/impact-based ongoing funding.

Therefore:

> a better “sponsor dashboard” is not sufficient.

Need a new product behavior.

---

# 27. CURRENT STRATEGIC LESSONS LEARNED FROM FAILED BRANCHES

The new chat should retain these exact lessons.

## Lesson A
Painful problem alone is not enough.

## Lesson B
Uncrowded category alone is not enough.

## Lesson C
Monad feature + app is wrong strategy.

## Lesson D
Technical novelty alone is not enough.

## Lesson E
Conditional escrow is becoming infrastructure.

## Lesson F
Provenance recovery is becoming standard infrastructure.

## Lesson G
Fast onchain state is only meaningful where blockchain/public settlement actually changes the product.

## Lesson H
Mera/EIP-7702/passkeys are strong capabilities but should generally enable a product, not BE the product.

## Lesson I
Current Metropolis GitHub competition is real and active. Current public repos should be searched aggressively before selection.

## Lesson J
The adversarial Stage 5 is working. Several attractive ideas that would have looked good on paper were killed by current products/standards.

---

# 28. SOURCE / EVIDENCE HANDLING RULES FOR THE NEW CHAT

Do not treat previous assistant statements as facts just because they are written here.

For any current/technical claim that matters to final selection:
- search current sources again if needed
- prefer official Monad docs
- prefer official sponsor docs
- use current primary project repos for competitor evidence
- distinguish current live product from research/prototype
- label:
  VERIFIED
  OBSERVED
  INFERRED
  UNVERIFIED

No source should be silently upgraded.

For the user’s strategy:
the GitHub strategy document is source of truth.

For event rules:
official current Monad portal/page should be source of truth where possible.

For sponsor capability:
official sponsor documentation is preferred.

For market collisions:
current company/product pages + current repos + standards/EIPs.

---

# 29. DO NOT WRITE RESEARCH INTO THE REPO

This has been explicitly agreed.

The repo:

https://github.com/Temmygabriel/tempo_hack

contains the reusable strategy.

Research phases in this handover are for chat continuity.

Do NOT create:
- STAGE_02.md
- STAGE_03.md
- STAGE_04.md
- STAGE_05.md
- research reports
- temporary idea files

inside the Monad/project repo unless the user explicitly requests it.

When the final winning idea is selected, THEN create the final complete build spec for the actual project.

---

# 30. EXACT TAKEOVER INSTRUCTION FOR THE NEW AGENT

Start by saying internally:

> I have read the Monad handover. I will NOT assume the OSS funding concept is the winner. I will continue from Stage 03 for that opportunity and verify current sponsor capabilities before generating ideas.

Then:

1. Re-open the user’s strategy document:
   https://github.com/Temmygabriel/tempo_hack/blob/main/HACKATHON_WINNING_SYSTEM_IDEA_TO_FULL_BUILD.md

2. Re-verify any current Monad event/sponsor facts that matter.

3. Run Stage 03 sponsor forensics on the OSS usage→funding opportunity.

4. If it fails:
   reset to Stage 02 and search another workflow family.

5. If it passes:
   run controlled Stage 04 idea generation.

6. Do NOT select an idea immediately.

7. Run Stage 05 adversarial attack.

8. A candidate only survives if:
   - recognizable
   - valuable
   - surprising
   - sponsor-load-bearing
   - precise blockchain reason
   - strong state transition
   - 60s demo
   - live proof realistic
   - competition acceptable
   - buildable under the user’s $0 / solo / short-time constraints

9. No coding before selection.

10. No final build spec before selection.

---

# 31. FINAL KNOWN STATE AT HANDOVER

DATE:
2026-10-05

USER LOCAL TIMEZONE:
Africa/Lagos (+01:00)

HACKATHON:
Monad Metropolis 2026

CURRENT RESEARCH PHASE:
Stage 2 passed for:
OPEN-SOURCE SOFTWARE CONSUMPTION → MAINTAINER FUNDING

NEXT REQUIRED PHASE:
Stage 3 sponsor-capability forensics

NO FINAL IDEA SELECTED.

NO MONAD PROJECT REPO CREATED/SELECTED.

NO FINAL BUILD SPEC CREATED.

NO RESEARCH PHASES SAVED TO THE REPO.

---

# 32. ONE-SCREEN SUMMARY

If the new chat only reads one section, read this:

> The user’s strategy is evidence-first and adversarial.
>
> DO NOT start with Monad features.
>
> We previously drifted into “encrypted mempool → private auction” thinking. The user corrected us, and that drift must NOT repeat.
>
> We then ran real workflow opportunity research.
>
> Several families were killed:
> - group money
> - savings circles
> - escrow
> - machine-service conditional payment
> - fast shared-state apps
> - media provenance
> - per-block funding
> - onchain credit
> - generic passkey products
> - generic agent identity/reputation
>
> The latest surviving opportunity is:
>
> **software consumption → maintainer funding**
>
> It passed preliminary Stage 2 because:
> - software dependency consumption is real
> - maintainer funding is disconnected from actual usage
> - OpenSSF/OSMF/Tidelift show active industry movement toward usage/value-based funding
> - a machine-generated usage receipt → programmable funding flow is highly demoable
>
> BUT:
> it is NOT a selected idea.
>
> Stage 3 sponsor forensics has NOT been completed for this branch.
>
> The next action is:
>
> **Stage 03 — test Monad/x402, Envio, Mera and other sponsor capabilities against OSS consumption→funding using the 20/25 rule and counterfactual test.**
>
> If Stage 3 fails, reset Stage 2 again.
>
> If Stage 3 passes, generate product ideas.
>
> Then adversarially attack them.
>
> Do not code.
>
> Do not create a build spec.
>
> Do not save research to the repo.
>
> Keep VERIFIED / OBSERVED / INFERRED / UNVERIFIED labels.
>
> Most important:
>
> **Do not force a winner just because the conversation is long or the deadline is close.**

END OF HANDOVER
