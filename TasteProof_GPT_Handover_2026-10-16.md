# TasteProof --- GPT Agent Handover / Project Memory

**Prepared:** 16 October 2026\
**Purpose:** A factual handover for another GPT/coding agent. Continue
the existing project without guessing, restarting, or repeating
already-fixed iterations.

## 0. Mandatory instructions for the receiving agent

-   Start by inspecting the live GitHub `main` branch and the latest
    commit. Do not assume a local checkout or branch is current.
-   Technical source of truth: current repo plus current official Qloo
    documentation and actual API responses. This note is a handover, not
    a replacement for source verification.
-   Never invent Qloo behavior, ranks, affinity scores, evidence,
    returned fields, deployment status or successful tests. No rank
    means insufficient evidence, not a mismatch.
-   Keep `QLOO_API_KEY` server-side. Never ask the user to paste it into
    chat, print it in logs, or commit it. Never create
    `NEXT_PUBLIC_QLOO_API_KEY`.
-   User constraints: free tools/services only, no paid APIs or credits;
    PC has 8 GB RAM and limited disk/data, so use GitHub Actions/cloud
    for heavy installs/builds. Be clear and specific, explain technical
    issues plainly, avoid guesswork and generic "AI slop."
-   Preserve the product direction and current editorial UI. Do not
    restart or redesign from scratch. The immediate priority is
    debugging real candidate ranking and entity resolution.
-   Separate facts from hypotheses. If a cause is not confirmed, say so.
-   The original build spec and agent prompt were intentionally excluded
    from the public repo; do not re-add them without the user's request.

## 1. Product, purpose and hackathon

**Product:** TasteProof\
**Positioning:** "A taste QA layer for AI agents."\
**Repo:** https://github.com/Temmygabriel/TasteProof\
**Production homepage listed in GitHub metadata:**
https://taste-proof-lake.vercel.app\
**Hackathon:** Qloo Agentic Hackathon 2026\
**Deadline in original spec:** 30 October 2026, 11:45 PM EDT (recheck
the official event page before relying on this).

TasteProof is **not** a recommendation generator. An external AI agent
produces place recommendations; TasteProof tests whether those
recommendations fit a supplied taste context using Qloo. It resolves
taste anchors and candidate places to Qloo entity IDs, requests Qloo
Insights, applies a transparent deterministic rank-to-verdict rule, and
presents an inspectable receipt.

Core mechanism:

``` text
External agent recommendations
  → user task, location and taste anchors
  → Qloo entity resolution
  → Qloo Insights evidence for submitted candidates
  → deterministic relative verdicts + evidence
  → Anchor Swap: change one anchor and rerun
  → compare actual results, never fabricate a change
```

Signature interaction: **Anchor Swap**. Changing an anchor must not be
represented as having changed results unless the returned evidence
actually changes.

The idea was selected through the user's hackathon research workflow:
research many ideas, reject real access/funding/implementation blockers,
then build a differentiated product with a clear Qloo dependency. The
goal is a QA layer for agent outputs, not another consumer
recommendation app.

The original private docs were
`TASTEPROOF_BUILD_SPEC_FULL_DISCIPLINE.md` and
`HACKATHON_WINNING_SYSTEM_IDEA_TO_FULL_BUILD.md`. The full build spec is
in the user's ChatGPT Library, not intended for the public repo. It
emphasizes official API verification, secure credential handling,
evidence integrity, polished UI, end-to-end tests and submission
readiness.

User's workflow preference: use explicit build/spec Markdown, audit
before coding when asked, keep public repo professional, use Vercel, use
GitHub Actions for heavy checks, remove private prompts from public
repo, and explain in plain language. Free-only constraints are hard
constraints.

## 2. Current repo state (last verified 16 Oct 2026)

-   **Main SHA:** `312707e3e7e217cf18ddb8c06031d2cfac9ec911`
-   **Latest commit:** "Separate candidate and discovery result counts"
-   **Commit URL:**
    https://github.com/Temmygabriel/TasteProof/commit/312707e3e7e217cf18ddb8c06031d2cfac9ec911
-   **Repo homepage metadata:** https://taste-proof-lake.vercel.app
-   **License:** MIT
-   **Repo:** https://github.com/Temmygabriel/TasteProof

Latest workflows for main commit `312707e…` were all completed
successfully: - Live verification:
https://github.com/Temmygabriel/TasteProof/actions/runs/38569226102 -
CI:
https://github.com/Temmygabriel/TasteProof/actions/runs/38569225265 - UI
preview/browser workflow:
https://github.com/Temmygabriel/TasteProof/actions/runs/38569225261

Important qualification: green workflows prove those configured checks
passed, not that all arbitrary candidate lists will be ranked. The
user's real Tokyo Test 2 below returned zero candidates from the
candidate-filtered Insights call.

### Merged PR history

-   **#9 --- Editorial product UI:**
    https://github.com/Temmygabriel/TasteProof/pull/9 (merged 14 Oct
    2026; branch `feat/editorial-product-ui`)
-   **#10 --- User-controlled Qloo entity selection:**
    https://github.com/Temmygabriel/TasteProof/pull/10 (merged 14 Oct
    2026; branch `feat/qloo-entity-selection`)
-   **#11 --- Rank submitted candidates directly:**
    https://github.com/Temmygabriel/TasteProof/pull/11 (merged 14 Oct
    2026; branch `fix/direct-candidate-affinity-ranking`)
-   **#12 --- Separate candidate/discovery counts:**
    https://github.com/Temmygabriel/TasteProof/pull/12 (merged 14 Oct
    2026; branch `fix/result-count-contract`)

Several Dependabot PRs were open at last check. Do not merge major
dependency updates blindly; they are not the immediate product issue.

## 3. UI / product direction

The visual direction is **Test Lab / warm editorial paper**: warm paper,
editorial typography, specimen labels, central Taste Test Card,
inspectable result evidence and a clear candidate leaderboard. It should
not look like a generic admin dashboard or AI-generated template.

Main UI: `src/app/page.tsx`. Public preview assets: -
`public/logo.svg` - `public/tasteproof-preview.png` -
`public/tasteproof-mobile-preview.png`

User flow: 1. Enter 1--5 taste anchors and choose a Qloo category for
each. 2. Enter 1--10 place recommendations from the agent being tested.
3. Use **Find Qloo match** for ambiguous/non-exact names and select the
intended live Qloo entity. 4. Evaluate using selected Qloo IDs. 5. Show
candidate ranks/verdicts/evidence and a separate broad discovery list
for context. 6. Change one anchor and rerun. 7. Show the technical
receipt.

Editorial city imagery is illustrative context only, not a photo of the
exact venue. Do not imply the imagery verifies the place.

## 4. Architecture / key files

Next.js + React + TypeScript. `package.json` records Next `16.4.0`,
React `19.2.0`, TypeScript `5.9.3`, Vitest `5.0.3`, and `tsx`. GitHub
Actions uses Node 22. Prefer cloud checks over heavy local npm
operations.

Important files: - `src/lib/qloo.ts` --- Qloo client, entity search,
broad Insights baseline and candidate ranking. - `src/lib/run-test.ts`
--- orchestration, entity resolution and test-state transitions. -
`src/lib/evaluate.ts` --- rank-to-verdict logic. - `src/lib/types.ts`
--- run/result interfaces and result counts. - `src/lib/test-state.ts`
--- state machine. - `src/app/page.tsx` --- main UI. - API routes
include `/api/test`, compatibility alias `/api/evaluate`,
`/api/qloo/search`, `/api/qloo/insights`, `/api/health`. -
`public/openapi.json` --- agent-callable API docs. - `tests/` --- unit
tests, including candidate filter coverage. - `scripts/verify-demo.ts`
--- live single-anchor test and Anchor Swap. -
`scripts/verify-multi-anchor.ts` --- live mixed-category test and Anchor
Swap. - `.github/workflows/live-verification.yml` and other workflows
for CI/UI browser preview. - `README.md` --- product description, setup,
limits, endpoints and screenshots.

Verify exact paths in current main before editing.

### Current Qloo client behavior

Source `src/lib/qloo.ts`: - Requires `QLOO_API_KEY`. - Defaults
`QLOO_BASE_URL` to `https://hackathon.api.qloo.com`. - Restricts base
URL to approved HTTPS Qloo origins: `hackathon.api.qloo.com`,
`api.qloo.com`, `staging.api.qloo.com`, with no custom path. - Sends
`X-Api-Key`; `cache: no-store`; redirects disabled; 12-second timeout;
bounded retry on 429. - Candidate ranking function:
`getCandidateRanking(anchorEntityIds, candidateEntityIds, location)`. -
It constructs `/v2/insights` with: - `filter.type=urn:entity:place` -
`signal.interests.entities=<comma-separated anchor IDs>` -
`filter.location.query=<location>` -
`filter.results.entities=<comma-separated candidate IDs>` -
`sort_by=affinity` - `take=min(50, unique candidate count)` - It parses
response entities, deduplicates IDs and assigns ranks by returned order.

**Crucial caution:** source currently sends `filter.results.entities`,
but the user's real Test 2 returned zero candidate entities. Do not
assume this parameter is officially supported or behaves as expected
until checking current official docs and the actual response.

Official references used: -
https://github.com/qloo/docs-public/blob/main/reference/insights-api-deep-dive.md -
https://docs.qloo.com/reference/api-overview -
https://docs.qloo.com/reference/api-onboarding -
https://docs.qloo.com/reference/basic-insights-use-case -
https://docs.qloo.com/reference/get-search

The agent-callable tool is `POST /api/test` (also `POST /api/evaluate`).
It accepts a task, location, taste anchors and candidate names and
returns resolutions/ranks/verdicts/evidence. Qloo is the only external
API credential needed for the core flow.

## 5. Important iterations and rationale

### A. Original spec

The private spec locked the product contract, design, API verification,
security, evidence rules, tests and deployment. It explicitly instructed
the coding agent to verify current official Qloo API docs rather than
assume endpoints/parameters.

### B. PR #9 --- editorial redesign

Reworked UI to the Test Lab visual system. Preserve this direction; the
user dislikes generic AI UI and asks for careful UI/UX reviews.

### C. PR #10 --- user-controlled entity resolution

Exact-name matching was too brittle. Users can search Qloo and choose
exact entity IDs for anchors/candidates. The UI should show suggestions
for ambiguous or failed matching rather than guess. Editing an entity
name/category should clear stale selection. Selected IDs are passed into
evaluation.

### D. PR #11 --- remove top-20 intersection flaw

Old behavior intersected user-submitted candidate IDs with a broad
top-20 discovery list. That could make all submitted candidates
unresolved merely because they did not happen to be in that unrelated
list. PR #11 changed the flow to call Qloo Insights with the submitted
IDs via `filter.results.entities`; broad discovery results are separate
context only.

This was the correct product-level concern, but the direct ranking
request has not been proven for every input. Test 2 returned zero, so
the API contract/request construction/parser must now be checked. Do not
revert to using top-20 discovery as candidate ranking.

### E. PR #12 --- distinct counts

The result model/UI previously conflated two counts. Current main has: -
`candidateRankingResultCount`: number of entities returned by
candidate-filtered Insights. - `rankedCandidateCount`: number of
submitted candidates actually assigned a rank. - `baselineResultCount`:
number of entities in the separate broad discovery list. Keep these
distinct in types, UI, scripts and OpenAPI.

## 6. Immediate priority: user's real Test 2 failed to produce ranks

User pasted a receipt from the live app:

-   Run ID: `630B39E2`
-   Timestamp shown: `14/10/2026, 17:58:44`
-   Task: "Recommend places to visit for someone who loves anime,
    Japanese gaming, and pop-culture experiences."
-   Location: Tokyo, Japan
-   Result: **0 of 3 submitted recommendations received a position in
    Qloo's candidate-filtered affinity results (0 candidate entities
    returned)**.
-   All three candidates were unresolved for ranking, even though each
    had an entity ID resolved by Qloo.
-   The separate broad discovery list contained 20 entities, correctly
    labelled context only.

Anchors shown: 1. `brand` --- **Picsart Photo Studio** ---
`D7A9ADF9-C36D-4669-994F-FEF4D527D31A` 2. `brand` --- **Nintendo** ---
`FFD31D42-DF50-4B60-932C-7497C8E73A80` 3. `movie` --- **Pokémon:
Detective Pikachu** --- `8069C6FC-5805-4E10-AF9E-693067633CAD`

Candidates: 1. `Pokémon Center Mega Tokyo & Pikachu Sweets` --- Qloo
resolved ID `F1C14AD4-DDFA-4696-87C7-5ED466BC2D5F` 2.
`Nintendo Tokyo Shibuya Japan` --- Qloo resolved ID
`F64CA0D3-6113-4B23-B839-D02FA9AD8FFC` 3.
`Beer Hall Ginza Lion Akihabara Radio-kaikan` --- Qloo resolved ID
`F16B8DD4-2615-4CDD-BF49-87BF1216AE2D`

The app correctly showed "No rank / Not enough evidence / UNRESOLVED"
and did not fabricate scores. But the product's direct-ranking behavior
is still unproven for this input.

### Separate resolution-quality warning

`Picsart Photo Studio` does not fit an anime/Japanese gaming/pop-culture
taste anchor. It may be a wrong selection for an intended anchor such as
Studio Ghibli, but do not assume what the user originally entered.
Investigate the actual selection flow and result list if available.

The third candidate resolved to
`Beer Hall Ginza Lion Akihabara Radio-kaikan`, a suspicious
composite/unexpected display name. It may be a wrong Qloo match. A
search result being returned does not prove it is the correct real-world
venue. The UI needs to make entity identity obvious and allow
correction/confirmation.

### Required debugging sequence

1.  Inspect technical receipt and server logs for run `630B39E2`, if
    retained. Record safe details only: endpoint, query parameter names
    and values/IDs, HTTP status, response envelope/shape, returned
    entity IDs/names, parsed count and any request ID. Never expose API
    key.
2.  Verify the official current docs for `filter.results.entities`:
    exact spelling, supported value syntax (comma-separated IDs vs
    repeated params/other format), whether it is supported with
    `signal.interests.entities`, and interaction with location filters.
3.  Inspect `parseQlooEntities` and compare the documented response
    schema for broad Insights versus candidate-filtered Insights.
4.  Make a minimal reproducible live test in GitHub Actions or a
    server-side script using the existing secret: one known valid
    anchor + one known place ID, then 2--3 candidate IDs. Log safe,
    sanitized output only.
5.  Compare documented/supported requests: broad Insights,
    candidate-filtered Insights, single ID vs multiple IDs, and
    with/without location only if the docs support it. This can isolate
    filter syntax, ID/type issues, parser issues and location
    interaction.
6.  If direct arbitrary-candidate ranking is not supported by Qloo, do
    not claim it is. Find an evidence-backed alternative using supported
    API behavior, update product limitations and UI copy, and keep
    unresolved cases honest. Never fall back to top-20 intersection
    while describing it as direct ranking.
7.  Investigate why `Picsart Photo Studio` and the composite third
    candidate were selected. Improve resolution confirmation if needed.
8.  Add regression tests based on the confirmed API contract; run CI,
    live verification and browser workflow.
9.  Align README, UI and `public/openapi.json` with verified behavior.
    The current README has a stale-sounding limitation saying candidate
    matching depends on appearing in the broader Insights baseline; this
    conflicts with the intended direct-ranking flow. Reconcile it after
    the API issue is resolved, not by simply asserting success.
10. Rerun the Tokyo scenario using corrected and explicitly selected
    entities. Only report a fix after the evidence proves it.

### Do not do these

-   Do not mark all three candidates FAIL because no ranks returned.
-   Do not fabricate affinity numbers or derive ranks from
    discovery-list order.
-   Do not claim missing means poor taste match.
-   Do not silently change anchors behind the user's back.
-   Do not claim the issue is fixed because CI passes.
-   Do not assume Qloo's "resolved" name is the correct venue.

## 7. Verdict semantics and result counts

Current `src/lib/evaluate.ts`: - `PASS`: top third of the returned
candidate ranking. - `REVIEW`: middle third. - `FAIL`: bottom third. -
`UNRESOLVED`: candidate not resolved/returned, invalid rank, or fewer
than three ranked entities available for a meaningful three-way split.

These are relative QA signals, not probabilities, psychological claims,
or guarantees that a person will like a place. Do not invent a numeric
affinity score if Qloo only returns ordered results.

Keep these counts separate: - `candidateRankingResultCount`: number of
candidate entities returned by candidate-filtered Insights. -
`rankedCandidateCount`: number of submitted candidates actually assigned
a rank. - `baselineResultCount`: number of broad discovery results used
only for context.

A potential semantic choice to review: if fewer than three candidate
entities return, the current evaluator leaves verdicts unresolved
because thirds cannot be calculated reliably. Keep that honesty unless a
defensible alternative is deliberately designed and documented.

## 8. Environment, security and deployment

Environment: - `QLOO_API_KEY` --- required server-side for live
evaluation. - `QLOO_BASE_URL` --- optional; defaults to
`https://hackathon.api.qloo.com`.

The user previously confirmed the GitHub Actions secret is configured.
Vercel should have the server environment variables configured too.
Never ask the user to reveal the key.

Security controls already in the Qloo client: - allowlisted HTTPS Qloo
origins; - redirects disabled; - 12-second timeout; - bounded 429
retry; - configuration/auth/rate-limit errors; - server-side
`X-Api-Key`.

`.env.example` is a blank template and `.gitignore` excludes `.env*`. Do
not add credentials to frontend code, URLs, fixtures, screenshots, tests
or commits.

`GET /api/health` reports whether a key is configured; it does not
validate that the key works. README notes the per-process rate limit is
best-effort, not a distributed quota system.

Deployment caution: GitHub metadata lists
`https://taste-proof-lake.vercel.app`, and the UI workflow passed.
Verify the current Vercel production deployment/revision before claiming
it serves main commit `312707e…`. GitHub green checks alone do not prove
the production app is current.

## 9. Testing workflows

Package scripts: - `npm run dev` - `npm run build` - `npm run start` -
`npm run typecheck` - `npm run test` - `npm run verify-demo` -
`npm run verify-multi-anchor`

Live workflow: `.github/workflows/live-verification.yml`. It uses GitHub
Actions secret `QLOO_API_KEY` and optional variable `QLOO_BASE_URL`,
then runs single-anchor and mixed-category live evaluations with Anchor
Swap. Automatic smoke checks use real Qloo baseline-derived entities.
Manual dispatch accepts three comma-separated candidate names, location
and replacement anchor.

UI/browser workflow captures desktop/mobile renders, builds production
app, runs browser checks through the UI, submits a live evaluation,
changes an anchor, verifies the comparison and checks mobile overflow.
Inspect workflow source before relying on exact behavior.

Latest main workflows were green (links above), but Test 2 still exposed
a product-level gap. Keep these separate: - CI pass = code
compiles/tests/builds. - Live smoke pass = tested scenarios worked. -
Actual user scenario pass = that candidate set was returned and ranked.
Do not conflate them.

## 10. README / public submission status

README covers product purpose, visual identity, flow, endpoints, setup,
env variables, CI/live checks, limitations, MIT license and official
links. Private build spec/prompt are intentionally absent from public
root.

One apparent inconsistency to revisit: README's flow says direct
candidate-specific ranking with a separate discovery list, but a later
limitations paragraph still says matching depends on candidates
appearing in the broader Insights baseline. That may be leftover text
from the old flawed implementation. Update it only after confirming what
the API actually supports.

Before submission, confirm: - public repo and MIT license; - functional
external demo and current deployment; - no secrets/private build docs in
public repo; - at least one reproducible end-to-end run with actual
external-agent candidates; - UI is polished/responsive; - claims
accurately describe Qloo's role and limitations.

## 11. Next actions for the receiving agent

**Priority 1:** Root-cause the Test 2 zero-rank result. Verify Qloo
docs, actual request/response and parser; reproduce safely with existing
Actions secret. Do not ask the user for the key.

**Priority 2:** Fix entity-resolution quality so the user can recognize
a wrong match. Specifically investigate Picsart Photo Studio and the
combined Ginza Lion/Akihabara Radio-kaikan entity.

**Priority 3:** Add regression coverage based on the confirmed API
contract. Run typecheck, unit tests, build, live verification and
browser workflow on the new commit. Test the Tokyo case again.

**Priority 4:** Align README, UI, receipt and OpenAPI docs with the
verified behavior. Keep candidate ranking and broad discovery counts
distinct.

**Priority 5:** Confirm current Vercel deployment and submission
readiness.

## 12. Links to open first

-   Repo: https://github.com/Temmygabriel/TasteProof
-   Homepage in repo metadata: https://taste-proof-lake.vercel.app
-   Latest main commit:
    https://github.com/Temmygabriel/TasteProof/commit/312707e3e7e217cf18ddb8c06031d2cfac9ec911
-   Latest CI:
    https://github.com/Temmygabriel/TasteProof/actions/runs/38569225265
-   Latest live verification:
    https://github.com/Temmygabriel/TasteProof/actions/runs/38569226102
-   Latest UI preview/browser workflow:
    https://github.com/Temmygabriel/TasteProof/actions/runs/38569225261
-   PR #9 UI: https://github.com/Temmygabriel/TasteProof/pull/9
-   PR #10 entity selection:
    https://github.com/Temmygabriel/TasteProof/pull/10
-   PR #11 direct ranking:
    https://github.com/Temmygabriel/TasteProof/pull/11
-   PR #12 separate counts:
    https://github.com/Temmygabriel/TasteProof/pull/12
-   Qloo Insights deep dive:
    https://github.com/qloo/docs-public/blob/main/reference/insights-api-deep-dive.md
-   Qloo overview: https://docs.qloo.com/reference/api-overview
-   Hackathon: https://qloo.devpost.com/

## Final instruction

Continue from actual current `main`. The product and design already
exist; do not rebuild from scratch. First investigate the real Qloo
behavior behind the zero-rank Tokyo result and the questionable entity
matches. Make the smallest evidence-backed fix, add tests, run cloud
checks, verify the live app, and report exactly what was proved. If the
docs/API do not support the assumed behavior, explain the limitation and
adjust the product honestly instead of guessing.
