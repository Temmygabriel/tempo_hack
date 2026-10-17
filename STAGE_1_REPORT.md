# STAGE 1 REPORT — LICENSEVAULT DEMO AUDIT, SCRIPT & STORYBOARD

**Date:** 2026-10-17  
**Project:** LicenseVault (Story Aeneid Testnet · Chain ID 1315)  
**Hackathon:** BLI Legal Tech Hackathon 2  
**Production Workspace:** `C:\Users\USER\Documents\HACKATHONS BUILDS\BLI_LEGALTECH_HACK\LICENSEVAULT VIDEO\`  
**Target Video Profile:** 1920 × 1080 | 30 fps | ~60 seconds | The Licensed Archive Visual Style  

---

## 1. Executive Summary (In Plain English for a 15-Year-Old)

Imagine buying a concert ticket online. On most websites, you just see a picture of a ticket, while the actual backstage door is locked with a separate padlock. If someone steals the padlock key or copies a link, the website cannot stop them.

**LicenseVault fixes this by turning the blockchain ticket directly into the key that opens the lock.**

Here is what really happens:
1. A digital file (a brand package delivery manifest) is encrypted and sealed on the **Story Aeneid** blockchain.
2. If someone connects a digital wallet without the required **Commercial Use license**, the smart contract directly checks the token register on-chain and says **"No"**. The file remains completely locked.
3. When an authorized wallet with the license checks in, the user signs a real read request.
4. Independent network computers (validators) release pieces of the decryption key.
5. The browser puts the key together, opens the sealed 804-byte file, checks that its unique digital fingerprint (SHA-256 hash) matches the original file exactly, and displays the unlocked content.
6. The app gives you an undeniable audit receipt proving that the blockchain itself granted access.

Our walkthrough video demonstrates this honest story in 60 seconds without exaggerations or fake animations.

---

## 2. Authoritative Source of Truth & Repository Audit

### GitHub Repository & Inspected Commit
* **Repository URL:** [https://github.com/Temmygabriel/LicenseVault](https://github.com/Temmygabriel/LicenseVault)
* **Authoritative Remote Revision:** `origin/main`
* **Inspected Commit SHA:** `ad62898ea581eb07b91a524fb691145ec9f9e084`
* **Commit Date:** `Fri Oct 16 11:51:53 2026 +0100`
* **Commit Message:** `chore: remove internal development artifact LICENSEVAULT_BUILD_SPEC.md`
* **Safety Rule Honored:** The local LicenseVault application repository was treated as strictly read-only. Zero files were added, edited, committed, or pushed to the product repository. All video assets live in the dedicated external workspace.

### Inspection of Repository Files

| File Inspected | Key Findings & Evidence Extracted |
|---|---|
| `README.md` | Documents the core workflow, live Vercel URL, demo addresses (license holder `0x226e...A863` and unlicensed owner `0x75D9...aCa9`), verified contracts on Aeneid (Chain 1315), 5 access checkpoints, and the explicit distinction that the payload is an 804-byte JSON manifest (not individual media binaries). |
| `PROGRESS.md` | Updated on 2026-10-16. Confirms successful browser demo execution: wallet connection, license verification, signed CDR read, data-key recovery (32 bytes), browser AES-256-GCM decryption, and SHA-256 digest match against `46cab4a8...64cd7`. Clarifies that token #73228 was used for the live browser run and notes the open plain-HTTP keeper transport risk. |
| `docs/CLAIM_STATUS.md` | Register of claims: Ecosystem claims (Story programmable IP, Aeneid availability, CDR contracts, LicenseReadCondition `0xC064...f7a3`) are PROVEN. LicenseVault gated read is OBSERVED. Unauthorized blocking is PROVEN (via on-chain condition probe). Explicitly UNSUPPORTED: Universal DRM, piracy prevention, legal advice. |
| `docs/EVIDENCE.md` | Documents the canonical run `licensevault-aeneid-001`, verification procedure, condition encoding (`conditionData` pins IP and LicenseToken; `accessAuxData` passes token ID), and 41 verified claims. |
| `docs/LIMITATIONS.md` | Defines scope boundaries: Story Aeneid testnet only; fictional resource; payload is strictly the 804-byte manifest; five listed files are metadata only; keeper proxy leg is plain HTTP; third-party replay is pending. |
| `docs/ASSET_PROVENANCE.md` | Plaintext is an 804-byte JSON manifest authored deterministically. Sealed ciphertext is 832 bytes (12-byte IV + ciphertext + 16-byte GCM tag). All interface artwork consists of hand-authored inline SVGs; no third-party copyrighted or generative art used. |
| `docs/SECURITY.md` | Evaluates adversarial tests. Details §5 open risk: upstream keeper proxy leg is plain HTTP. Explains AES-256-GCM authenticated decryption failing closed upon corruption. Documents credential redaction controls in API routes. |
| `docs/PROTOCOL_DECISION.md` | Explains architectural decisions: published `@piplabs/cdr-sdk@0.2.2` pinned for vaults; `@story-protocol/core-sdk@1.4.4` for minting; viem ABI parameter encoding for condition checks; authority lives strictly on-chain. |
| `docs/VISUAL_QA.md` | Design scoring report (22/24 score). Explains layout rules across 6 viewports, contrast compliance, and self-hosted fonts (`IBMPlexSans`, `IBMPlexMono`, `Newsreader`). |
| `docs/UX_TEST.md` | Formulates the three comprehension questions required for external user testing. |
| `app/page.tsx` | Main landing surface assembling `AccessProvider`, `VaultMark`, `HeroActions`, `AccessPanel`, `ProofReceipt`, and contextual footer. |
| `components/AccessPanel.tsx` | Implements the Access Docket, token ID input (`#73227`), 5-checkpoint journey list, error alerts, fee sheet, optional locked-read test, recovered manifest viewer, and session proof receipt. |
| `components/AccessProvider.tsx` | Implements the reducer state machine: `connectWallet`, `switchToAeneid`, `verifyLicense`, `mintDemoLicense`, `tryLockedRead`, and `unlockProtectedContent`. |
| `lib/protocol/cdr-browser.ts` | Browser protocol adapter handling viem clients, Story Core SDK license minting, CDR SDK wasm initialization, same-origin proxy requests, threshold partial reconstruction, and AES-GCM decryption. |
| `evidence/licensevault-aeneid-001/` | Contains committed JSON artifacts: `decrypted-resource.json` (matching hash), `gate-probes.json` (on-chain probes for holder and non-holder), `protected-content-manifest.json`, and `protected-content.bin`. |
| `qa-screens/` | Committed real-state screenshots captured via Chrome DevTools Protocol: `desktop-locked.png`, `desktop-no-license.png`, `desktop-verified.png`, `desktop-proof.png`, `desktop-verification-error.png`. |

---

## 3. Live Deployed Production Site Inspection

* **Production URL:** [https://licensevault.vercel.app/](https://licensevault.vercel.app/)
* **HTTP Response:** `200 OK` (Served via Vercel Edge / Turbopack build)
* **Observed UI & Components:**
  * **Brand Identity:** Warm paper background (`#F4F1E8`), fine archival document rules (`#D4D0C5`), dark carbon ink (`#1C1D1B`), and warm copper accent (`#A7613C`).
  * **Hero Header:** `VaultMark` SVG shield with copper keyhole, navigation links (`How it works`, `Proof`), and interactive `Connect wallet` button.
  * **Hero Section:** Eyebrow *"Onchain rights. Real access."*, Newsreader display headline *"A license should open the door."*, supporting explanation, and 3 principles.
  * **Access Docket (`#access-docket`):**
    * Protected Resource: *Commercial Brand Asset Pack* (Fictional demonstration resource) with original archival book-well illustration.
    * License Required: *Commercial Use*.
    * Access Status: Initial state is `Locked`.
    * License Token ID Input: Initialized to demo token `#73227`.
    * Journey Checkpoints: 5-step sequence (`01 Connect wallet`, `02 Verify license`, `03 Sign CDR read`, `04 Recover & decrypt`, `05 Verify content`).
  * **Proof Receipt Section:**
    * Displays canonical run `licensevault-aeneid-001` on Story Aeneid.
    * Lists rights identifiers, sealed record attributes, cipher specifications (AES-256-GCM), 832-byte ciphertext, and plaintext SHA-256 digest `46cab4a8...64cd7`.
    * Links 6 on-chain transactions directly to the Story Aeneid explorer (`https://aeneid.datanetscan.io`).
    * Displays independent verification tally: 41 verified, 0 refuted, 1 unverified.

---

## 4. What the Deployed Product Genuinely Demonstrates

1. **On-Chain Refusal via `checkReadCondition`:**
   * Calling the live condition contract (`0xC0640AD4CF2CaA9914C8e5C44234359a9102f7a3`) on Story Aeneid (Chain 1315) with an address that does not own token #73227 (`0x75D900D18866D8aA416CCEFD9e85D2C61dB0aCa9`) returns `false`. The UI updates to `NO LICENSE` / `LOCKED`.
2. **In-Browser Wallet Connection:**
   * Connects via injected browser wallet (e.g., MetaMask, Rabby). Zero signatures or gas are requested upon connection.
3. **Demo License Acquisition:**
   * Allows minting a fresh Commercial Use license token on Story Aeneid using the Story Core SDK (`mintLicenseToken`), updating the active token ID to the newly minted token (e.g., #73228).
4. **Wallet-Signed Protected CDR Read Transaction:**
   * Authorized connected wallet submits the state-changing read transaction to contract `0xcccccc0000000000000000000000000000000005`.
5. **Threshold Validator Decryption & Key Recovery:**
   * SDK queries validator nodes through the same-origin `/api/cdr` proxy, receives ECIES-encrypted threshold partials, and recovers the 32-byte AES data key.
6. **In-Browser Decryption & SHA-256 Verification:**
   * Browser decrypts the 832-byte ciphertext with AES-256-GCM, yielding the 804-byte JSON manifest.
   * Browser computes the SHA-256 hash and confirms an exact match with the pre-seal digest `46cab4a8232e4eea226500b424416a353618c8606008d374dbb15f56bc864cd7` (`"matches": true`).
7. **Session Proof Receipt:**
   * Renders the user's live mint transaction, read transaction, and content digest confirmation, clearly distinct from the historical canonical run.

---

## 5. Deliberately Excluded Claims & Technical Limitations

To guarantee complete intellectual honesty:
* **Payload Boundary:** The protected payload is strictly an **804-byte JSON delivery manifest**. The 5 brand assets listed inside it (`brand-mark-primary.svg`, `brand-mark-inverse.svg`, `wordmark-horizontal.eps`, `palette.coco`, `usage-guidelines.pdf`) are **metadata entries**, not delivered binaries. We do NOT claim the image or PDF binaries were decrypted.
* **Condition Probes vs. Transactions:** Committed gate probes in `evidence/` represent read-only `eth_call` queries, not failed state-changing signed transactions.
* **Open Keeper Transport Risk:** The server-to-keeper proxy leg operates over plain HTTP to a raw IP address (`172.192.41.96`). We do NOT claim end-to-end TLS security for keeper communication.
* **Observed Run vs. Replay:** The documented successful browser run is an observed demonstration. A fresh independent third-party replay is not claimed.
* **Scope Exclusions:** We do NOT claim universal DRM, piracy prevention, copyright compliance guarantees, or legal advice.
* **Resolution of Document Contradiction:** Older paragraphs in `LIMITATIONS.md` (dated 2026-10-05) stated the browser flow was not yet demonstrated. However, `PROGRESS.md` (2026-10-16), updated sections of `LIMITATIONS.md`, and application code confirm that the complete browser read flow was implemented and observed. Our walkthrough accurately reflects the proven, observed browser flow.

---

## 6. Video Production Deliverables

All video production files have been created in the dedicated external video workspace:
`C:\Users\USER\Documents\HACKATHONS BUILDS\BLI_LEGALTECH_HACK\LICENSEVAULT VIDEO\`

### Deliverable 1: `SCRIPT.md`
* **File Location:** `LICENSEVAULT VIDEO\SCRIPT.md`
* **Word Count:** 132 words
* **Estimated Duration:** ~60.0 seconds at ~130 wpm
* **Tone:** Composed, warm, editorial documentary delivery.
* **Spoken Text:**
  > "In digital media, ownership is usually just a receipt on a website—completely detached from the files themselves. Anyone with a link can read them.  
  > 
  > LicenseVault changes that. Here, an on-chain intellectual property license becomes the actual cryptographic keyhole.  
  > 
  > In the Access Docket, a fictional Commercial Brand Asset Pack requires a commercial license. When an unlicensed wallet checks access, the on-chain condition inspects the token registry and firmly refuses entry.  
  > 
  > Once the correct license is verified on Story Aeneid, the connected wallet signs a real protected read. Validator nodes release decryption partials, and the browser recovers the sealed data key.  
  > 
  > The browser decrypts the delivery manifest, confirms the SHA-256 digest byte-for-byte, and logs the on-chain proof.  
  > 
  > The license isn't a promise. It's the condition that opens the door."

### Deliverable 2: `STORYBOARD.md`
* **File Location:** `LICENSEVAULT VIDEO\STORYBOARD.md`
* **Format:** 1920 × 1080 | 30 fps | 1,800 frames total
* **Visual Structure (6 Scenes):**
  1. **Scene 1 (00:00–00:11.5 | 345f):** The Problem — Archival canvas, visual contrast between unsealed web files and off-chain receipts.
  2. **Scene 2 (00:11.5–00:19.0 | 225f):** The Thesis — Hero reveal, `VaultMark` emblem, headline *"A license should open the door."*, 3 core principles.
  3. **Scene 3 (00:19.0–00:33.5 | 435f):** Access Docket & Refusal — Access Docket close-up, demo token `#73227`, unlicensed check → `NO LICENSE / LOCKED`, condition `0xC064...f7a3` returning false.
  4. **Scene 4 (00:33.5–00:47.5 | 420f):** Verified License & CDR Read — Status flips to `LICENSE VERIFIED`, 5-checkpoint sequence (01–04), wallet signs CDR read, validator partials collected.
  5. **Scene 5 (00:47.5–00:55.5 | 240f):** Decrypted Manifest & Proof — Status updates to `UNLOCKED`, recovered delivery manifest displays 5 metadata entries, SHA-256 digest match (`46cab4a8...64cd7`), session proof receipt.
  6. **Scene 6 (00:55.5–01:00.0 | 135f):** Resolution & Close — Centered `VaultMark` emblem, Story Aeneid Chain 1315 badge, and production URL `licensevault.vercel.app`.

### Deliverable 3: `GOOGLE_TTS.md`
* **File Location:** `LICENSEVAULT VIDEO\GOOGLE_TTS.md`
* **Workflow:** Based on `hyperframes-gemini-tts-addendum.md`.
* **Model ID:** `gemini-3.8-flash-tts`
* **Voice Selected:** `Kore`
* **Conversion Pipeline:** Direct REST request with API key via environment variable → Base64 decode to raw PCM (24kHz, 16-bit LE, mono) → FFmpeg conversion to `licensevault-voiceover-v1.wav` → FFprobe validation of audio stream and duration.

---

## 7. Reference-Video Analysis & Production Takeaways

Three reference styles informed the pacing, typography, and motion design:
1. **Linear Launch Demos:** Measured documentary pacing (~125–130 wpm); restrained 2D zooms into actual UI cards; clean monospaced font accents; quiet sound design.
2. **Stripe Verification Demos:** Clear visual contrast between user interaction and cryptographic/contract verification; authentic interface states over marketing hype.
3. **Vercel Feature Walkthroughs:** Hero focus on real interface mechanisms, verifiable proof receipts, and honest error handling.

---

## 8. Stage 1 Completion Gate Summary

| Requirement | Result | Verified Artifact / Evidence |
|---|---|---|
| Authoritative GitHub Commit | Recorded | `ad62898ea581eb07b91a524fb691145ec9f9e084` (`origin/main`, Oct 16 2026) |
| Repository Documentation Audit | Complete | `README`, `PROGRESS`, `CLAIM_STATUS`, `EVIDENCE`, `LIMITATIONS`, `ASSET_PROVENANCE`, `SECURITY` |
| Live Production UI Audit | Verified | `https://licensevault.vercel.app/` (HTTP 200, Licensed Archive theme confirmed) |
| Repository Protection | 100% Intact | Zero edits, commits, or pushes to the application repository |
| External Video Workspace | Created | `C:\Users\USER\Documents\HACKATHONS BUILDS\BLI_LEGALTECH_HACK\LICENSEVAULT VIDEO\` |
| Spoken Narration Script | Complete | `LICENSEVAULT VIDEO\SCRIPT.md` (132 words, ~60s estimated duration) |
| Detailed Storyboard | Complete | `LICENSEVAULT VIDEO\STORYBOARD.md` (6 scenes, 1,800 frames at 30 fps) |
| Google Gemini TTS Addendum Plan | Complete | `LICENSEVAULT VIDEO\GOOGLE_TTS.md` (`gemini-3.8-flash-tts`, voice `Kore`) |
| Local Stage 1 Report File | Created | `LICENSEVAULT VIDEO\STAGE_1_REPORT.md` |
| Audio Generation & Video Rendering | Withheld | Paused for user approval before Stage 2 |

---

*Report prepared and locked in the dedicated video workspace. Awaiting user approval to proceed to Stage 2.*
