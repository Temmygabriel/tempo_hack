# LICENSEVAULT BUILD SPEC
## BLI Legal Tech Hackathon 2 — Evidence-First MVP

**Project:** LicenseVault  
**Hackathon:** BLI Legal Tech Hackathon 2  
**Organizer:** Blockchain Legal Institute (BLI)  
**Primary technical ecosystem:** Story  
**Core technical path:** Story IP licensing + Confidential Data Rails (CDR)  
**Status:** Pre-build specification  
**Date:** 2026-10-05

---

# 0. BUILD CONTRACT

Build the smallest real product that proves:

> A user cannot read protected digital content without the required Story Protocol license, and can read it after obtaining the correct license.

The product is not a generic IP marketplace, legal AI assistant, document notarization tool, or compliance dashboard.

The core experience is:

```
PROTECTED RESOURCE
        ↓
LICENSE REQUIRED
        ↓
TRY WITHOUT LICENSE
        ↓
READ REJECTED
        ↓
OBTAIN LICENSE
        ↓
TRY AGAIN
        ↓
READ ALLOWED
        ↓
PROTECTED CONTENT DECRYPTED
        ↓
ONCHAIN / PROTOCOL PROOF
```

The protocol is the source of truth.

UI state is never financial, legal, or authorization proof.

---

# 1. NON-NEGOTIABLE RULES

1. Never invent protocol addresses, contract interfaces, network IDs, asset IDs, RPC endpoints, SDK methods, sponsor claims, or transaction hashes.
2. If a critical fact cannot be verified from current official source code/docs or live chain state, mark it UNVERIFIED and stop at the relevant phase.
3. Never replace a failed protocol operation with a mock and call the result real.
4. Never show ACCESS GRANTED unless the real protected-read flow succeeds.
5. Never show a fake transaction or explorer link.
6. Never put a private key, seed phrase, or credential in source control.
7. Never ask the user for a seed phrase or private key.
8. Never expose a server-side private key or internal API credential to browser code.
9. Do not depend on the Story IP Portal as a runtime dependency.
10. Do not claim Story is a BLI 2026 bounty partner until current BLI evidence confirms it.
11. Use Story Aeneid/testnet during development unless current official requirements explicitly require another network.
12. No paid dependency may be mandatory for the core MVP without explicit approval.
13. Do not build extra features before the one complete gated-access flow is proven.
14. The application must distinguish:
   - NO LICENSE
   - VERIFICATION ERROR
   - LICENSE VERIFIED
   - ACCESS GRANTED
15. Legal claims must stay narrow and technically provable.

---

# 2. PRODUCT

## Product name

LicenseVault

Keep the name as the working project/product name unless a later naming review changes it.

## Product category

Licensed digital-asset access.

## One-line product contract

> LicenseVault turns an onchain IP license into a real access permission for protected digital content.

## Human explanation

> A protected digital asset stays locked until the connected wallet has the license required to read it.

---

# 3. MVP USE CASE

Use one simple fictional demonstration resource:

**COMMERCIAL BRAND ASSET PACK**

The resource is protected digital content.

The exact content can be a small demo file or small protected payload.

The product does NOT become a real commercial asset marketplace.

The user journey should be understandable without legal or blockchain knowledge.

---

# 4. TECHNICAL THESIS

The important mechanism is:

```
Story IP Asset
    +
Story license terms
    +
Story license token
    ↓
License-aware read condition
    ↓
Protected encrypted resource
    ↓
READ REJECTED / READ ALLOWED
```

The strongest known current technical path is Story's Confidential Data Rails (CDR) plus its Aeneid-deployed LicenseReadCondition.

The current public CDR SDK repository documents LicenseReadCondition as:

> only Story Protocol license token holders for the specified IP can read.

Its current integration tests demonstrate:
- read without a license fails;
- a Story license token is minted;
- the licensed read succeeds;
- protected data is recovered.

This behavior must be independently reproduced in LicenseVault.

---

# 5. VERIFIED REFERENCE MATERIAL

Treat these as current technical references that must be rechecked before implementation if anything has changed:

## Story / CDR SDK

Repository:
https://github.com/piplabs/cdr-sdk

Current package identified in the repository:
`@piplabs/cdr-sdk`

Current repository package version observed:
`0.2.2`

Current Aeneid/testnet:
- chain ID: 1315
- EVM RPC: `https://aeneid.storyrpc.io`

Current CDR system addresses documented by the SDK:
- DKG: `0xcccccc0000000000000000000000000000000004`
- CDR: `0xcccccc0000000000000000000000000000000005`

Current Aeneid LicenseReadCondition documented by the SDK:
`0xC0640AD4CF2CaA9914C8e5C44234359a9102f7a3`

Current Aeneid OwnerWriteCondition documented by the SDK:
`0x4C9bFC96d7092b590D497A191826C3dA2277c34B`

Current Aeneid Story LicenseToken contract used by the SDK's integration fixture:
`0xFe3838BFb30B34170F00030B52eA4893d8aAC6bC`

IMPORTANT:
These addresses are protocol reference values, not values to fabricate into a production UI.
Before any live transaction, read the current source/docs and verify the network and contract bytecode/state.

---

# 6. CURRENT CDR FLOW TO REPRODUCE

The public CDR integration test currently exercises this general flow:

1. Connect to Aeneid.
2. Fetch the CDR global public key.
3. Allocate a CDR vault.
4. Configure:
   - OwnerWriteCondition for writes;
   - LicenseReadCondition for reads.
5. Store encrypted data.
6. Attempt read with no license token.
7. Assert the read fails.
8. Mint a Story license token for the target IP and terms.
9. Encode the returned license token ID as read auxiliary data.
10. Attempt the read again.
11. Assert the protected data is recovered.
12. Record evidence.

The implementation must verify every step from current source rather than assume the SDK integration test is unchanged.

---

# 7. NETWORK

Development network:

**Story Aeneid testnet**

Current network identifier observed:
- chain ID 1315

Current documented public EVM RPC:
`https://aeneid.storyrpc.io`

The CDR SDK also requires a Story-API REST endpoint for DKG/partial-decryption operations.

The current SDK repository documents:
`http://172.192.41.96:1317`

This endpoint is explicitly documented as plain HTTP.

Rules:
- never hardcode this into browser/client code;
- keep it server-side;
- verify it is reachable and usable before depending on it;
- if it fails, stop and report the blocker;
- do not silently replace it with an invented endpoint.

---

# 8. WALLET MODEL

Preferred browser UX:

- user connects an EVM-compatible wallet;
- wallet owns/receives the Story license token;
- browser signs only user-authorized transactions;
- no seed phrase or private key ever enters the app.

For development-only scripted tests, a disposable test key MAY be used through secure environment variables.

Never commit it.

Never print the raw secret.

Never use Mainnet funds.

---

# 9. ACCESS MODEL

The application must have two distinct concepts:

## A. Eligibility

Does the wallet hold the required license token?

## B. Protected read

Can the wallet actually read/decrypt the protected resource?

The second is the stronger proof.

Do NOT implement:

```
wallet owns token
→ React setAccessGranted(true)
```

as the final authorization mechanism.

The real protected-read operation must succeed.

---

# 10. PRODUCT STATE MACHINE

```
LOCKED
  ↓
CHECKING
  ↓
┌─────────────────────┐
│                     │
NO LICENSE         LICENSE VERIFIED
│                     │
↓                     ↓
LOCKED            ACCESSING
                      ↓
                   UNLOCKED
```

Error branch:

```
CHECKING
   ↓
VERIFICATION ERROR
```

Definitions:

### LOCKED
Protected resource cannot currently be read.

### CHECKING
The app is querying/verifying protocol state.

### NO LICENSE
The real gated-read or license-state verification indicates the wallet does not satisfy the rule.

### LICENSE VERIFIED
The required license relationship has been verified.

### ACCESSING
The real protected-read/decryption operation is executing.

### UNLOCKED
The protected resource has actually been recovered.

### VERIFICATION ERROR
The app could not establish a trustworthy result.

---

# 11. SIGNATURE INTERACTION

Primary interaction:

**VERIFY LICENSE**

Success path:

```
VERIFY LICENSE
     ↓
CHECK LICENSE
     ↓
PROTOCOL READ
     ↓
LICENSE VERIFIED
     ↓
OPEN PROTECTED ASSET
```

The memorable state change is:

**LOCKED → UNLOCKED**

The user should feel the content opening because the underlying authorization changed.

---

# 12. MVP SCREENS

Only four major surfaces:

## 1. Landing

Explain:
- what LicenseVault is;
- protected content;
- license required;
- CTA.

Primary CTA:
`CHECK ACCESS`

## 2. Protected Resource

Show:
- asset name;
- preview;
- required license;
- access state;
- Verify License action.

## 3. Access Result

Show:
- LICENSE VERIFIED;
- ACCESS GRANTED;
- protected content;
- concise reason.

## 4. Proof

Show:
- IP Asset;
- license terms;
- license token;
- wallet;
- network;
- CDR vault identifier;
- read transaction;
- result;
- explorer links where available.

Do not build an admin dashboard unless required later.

---

# 13. LEGAL LANGUAGE

ALWAYS be precise.

Allowed:
- licensed content;
- protected resource;
- license required;
- license verified;
- access granted;
- access restricted;
- onchain licensing state;
- protocol-enforced read condition.

Avoid:
- copyright guaranteed;
- piracy prevented;
- legally compliant;
- ownership proven;
- universal DRM;
- blockchain makes the license legally enforceable everywhere.

LicenseVault controls access to the protected resource inside the application.

It does not control the entire internet and does not guarantee that a legitimate reader cannot copy content after access.

---

# 14. SECURITY INVARIANTS

## INV-01
A wallet without the required license cannot successfully read the protected resource.

## INV-02
A wallet with the correct license can successfully read the intended resource.

## INV-03
A license for the wrong IP does not satisfy the target resource's read condition.

## INV-04
An arbitrary unrelated token cannot satisfy the license condition.

## INV-05
Changing browser state cannot grant access.

## INV-06
A failed protocol transaction cannot become ACCESS GRANTED.

## INV-07
The app does not silently switch networks.

## INV-08
Protected plaintext is not sent to the client before authorized recovery.

## INV-09
Private keys remain server-side or inside the user wallet and never enter public source.

## INV-10
Retry logic checks real chain/protocol state rather than assuming the previous request failed.

---

# 15. EVIDENCE REQUIREMENTS

Canonical run:

`licensevault-aeneid-001`

Record:

```
NETWORK
CHAIN ID
COMMIT
PACKAGE VERSIONS
IP ASSET
LICENSE TERMS
LICENSE TOKEN
VAULT UUID
PAYER / USER WALLET
UNAUTHORIZED READ TX / RESULT
LICENSE MINT TX
AUTHORIZED READ TX / RESULT
DECRYPTION RESULT
EXPLORER LINKS
FINAL RESULT
```

Suggested directory:

```
evidence/
└── licensevault-aeneid-001/
    ├── environment.json
    ├── ip-asset.json
    ├── license-terms.json
    ├── vault.json
    ├── unauthorized-read.json
    ├── license-mint.json
    ├── authorized-read.json
    ├── decrypted-resource.json
    └── verification.json
```

Never create evidence files for events that did not occur.

---

# 16. VERIFIER

Create:

`tools/verify-canonical-run.ts`

It must independently verify as much as practical.

Minimum checks:

```
NETWORK PASS
IP ASSET PASS
LICENSE PASS
LICENSE TOKEN PASS
VAULT PASS
UNAUTHORIZED READ PASS
LICENSED READ PASS
DECRYPTION PASS
RESULT PASS
```

The verifier must not simply trust `evidence/*.json`.

It must query the current network/protocol wherever practical.

---

# 17. CLAIM STATUS

Create:

`docs/CLAIM_STATUS.md`

Initial statuses:

| Claim | Status |
|---|---|
| Story IP licensing exists | PROVEN |
| Aeneid exists | PROVEN |
| CDR exists on Aeneid | PROVEN |
| LicenseReadCondition exists on Aeneid | PROVEN |
| Current SDK integration demonstrates gated read | OBSERVED |
| LicenseVault independently reproduces gated read | UNVERIFIED |
| LicenseVault blocks unauthorized access | UNVERIFIED |
| LicenseVault permits licensed access | UNVERIFIED |
| Story is a confirmed BLI 2026 bounty | UNVERIFIED |
| Universal copyright protection | UNSUPPORTED |

Use:
`PROVEN / OBSERVED / INFERRED / UNVERIFIED / UNSUPPORTED`

---

# 18. TESTING

Test order:

1. unit;
2. protocol integration;
3. adversarial;
4. live canonical E2E.

Unit tests should cover:
- state transitions;
- address/config validation;
- license-token decoding;
- proof formatting;
- error mapping.

Protocol tests should cover:
- vault creation;
- unauthorized read rejection;
- license mint;
- authorized read;
- decryption.

Adversarial tests should cover:
- wrong IP;
- wrong license terms;
- wrong token;
- empty license list;
- malformed auxiliary data;
- wrong chain;
- reverted transaction;
- retry after timeout;
- browser refresh.

---

# 19. COST RULE

Core path should remain $0.

Preferred:
- Aeneid testnet;
- Story faucet/test assets;
- open-source SDK;
- GitHub;
- free hosting if adequate.

Do not add:
- paid database;
- paid RPC;
- paid storage;
- paid AI;
- paid monitoring;
- paid legal API

unless the dependency is genuinely required and explicitly approved.

---

# 20. STORAGE

CDR protects encrypted data.

For MVP, prefer the smallest payload possible.

Do not build a large file-storage platform.

A tiny protected demo resource is enough.

If an offchain storage provider becomes necessary for the actual protected-file path, choose one current open/free provider supported by the SDK and document the cost and limits.

The protected data key and read authorization remain the critical security boundary.

---

# 21. SERVER ARCHITECTURE

Preferred:

```
Browser
   ↓
LicenseVault Next.js app
   ↓
server-side protocol adapter
   ↓
Story RPC + CDR Story-API
   ↓
Story / CDR contracts
```

If a browser wallet must sign a user transaction, the wallet signs it directly.

Server-only secrets:
- test/development private key, if genuinely required;
- internal API configuration;
- any non-public service credential.

Never prefix secrets with `NEXT_PUBLIC_`.

---

# 22. DEPLOYMENT

Target:
Vercel or another free Node-compatible host.

Before calling the app production-ready, verify:

```
Browser
→ hosted app
→ Story RPC
→ CDR API
→ real transaction / read
→ real state
→ browser result
```

No persistent-process assumptions.

Document request duration and timeout behavior.

---

# 23. IMPLEMENTATION PHASES

## Phase 0 — Repo + environment

Output:
- Next.js TypeScript app;
- package setup;
- env validation;
- README skeleton;
- docs structure;
- secure .gitignore.

Gate:
- install;
- lint;
- typecheck;
- no secrets.

## Phase 1 — Protocol spike

Output:
- current SDK installed;
- Aeneid connectivity;
- read chain ID;
- read current CDR/LRT deployment;
- verify LicenseReadCondition code/address.

Gate:
- real protocol connectivity.

## Phase 2 — Protected vault

Output:
- create/prepare one protected CDR resource.

Gate:
- real vault exists.

## Phase 3 — Unauthorized access

Output:
- attempt read without license.

Gate:
- protocol rejects it.

## Phase 4 — Licensed access

Output:
- obtain correct license;
- retry read;
- recover protected data.

Gate:
- protocol allows it and decrypted content is real.

## Phase 5 — Evidence + verifier

Output:
- canonical run;
- verifier;
- claim status;
- security tests.

Gate:
- independent verification.

## Phase 6 — Core application

Output:
- landing;
- protected resource;
- access gate;
- result;
- proof.

Gate:
- end-to-end product flow works.

## Phase 7 — Visual polish

Output:
- final visual system;
- responsive layout;
- motion;
- accessibility.

Gate:
- visual quality target >=20/24.

## Phase 8 — Hardening

Output:
- retries;
- errors;
- deployment checks;
- secret scan;
- regression tests.

Gate:
- no critical unresolved issue.

## Phase 9 — Demo

Output:
- final 60-second sequence;
- screenshots;
- README;
- live link.

Gate:
- judge can understand it quickly and verify it.

---

# 24. PHASE REPORT

Every phase ends with:

```
PHASE:
STATUS: PASS | FAIL | BLOCKED
COMMIT:
FILES CHANGED:
DEPENDENCIES:
TESTS:
LIVE EVIDENCE:
PROTOCOL FACTS:
SECURITY FINDINGS:
KNOWN LIMITATIONS:
BLOCKERS:
NEXT PHASE:
```

If blocked:

```
PHASE:
STATUS: BLOCKED

BLOCKER:
WHAT IS UNKNOWN:
WHY IT MATTERS:
SOURCE CHECKED:
WHAT I NEED:
SAFE NEXT STEP:
```

---

# 25. NO-GO CONDITIONS

Do not continue to UI polish if:

- unauthorized access is only simulated;
- licensed access is only simulated;
- CDR deployment is unavailable;
- LicenseReadCondition cannot be reproduced;
- Story integration is only decorative;
- a fake token is used;
- the app grants access based only on local React state;
- secret is committed;
- protected plaintext is leaked;
- paid infrastructure becomes mandatory without review;
- protocol facts cannot be verified.

---

# 26. FIRST BUILD TASK

Do NOT build the landing page first.

Do NOT build the final branding first.

Do NOT build an admin dashboard.

Do this first:

1. Create a minimal TypeScript/Node test harness.
2. Connect to Story Aeneid.
3. Verify chain ID.
4. Install/use the current `@piplabs/cdr-sdk`.
5. Verify current CDR deployment.
6. Verify current LicenseReadCondition deployment.
7. Reproduce the SDK's unauthorized-read failure.
8. Reproduce the licensed-read success.
9. Save real transaction/state evidence.
10. Stop and report if any part is blocked.

The first success milestone is:

```
AENEID
  ↓
REAL PROTECTED RESOURCE
  ↓
NO LICENSE
  ↓
READ REJECTED
  ↓
REAL LICENSE
  ↓
READ ACCEPTED
  ↓
REAL PROTECTED DATA RECOVERED
```

Only after this passes should the main LicenseVault application be built.

---

# 27. FINAL PRODUCT PRINCIPLE

The product is not:

> a dashboard showing that a wallet owns a license.

The product is:

> **a protected resource whose access actually depends on the licensing state.**

That distinction is the core of LicenseVault.
