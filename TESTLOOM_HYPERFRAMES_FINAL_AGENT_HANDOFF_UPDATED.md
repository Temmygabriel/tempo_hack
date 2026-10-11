# Testloom + HyperFrames — AI Agent Handoff

**Purpose:** Give this file to a GPT/Claude/Gemini/Antigravity/Codex coding agent before asking it to create the Testloom demo video.

**Read this entire file before doing anything. Do not repeat the historical setup investigation.**

---

## 0. NON-NEGOTIABLE SAFETY RULES

The Testloom application has already been submitted to its hackathon. Protect it.

The video-production agent MUST:

- NOT modify the Testloom application source code.
- NOT modify the Testloom GitHub repository.
- NOT create a PR.
- NOT commit or push to the Testloom repository.
- NOT install video-production files into the Testloom application repository.
- Work only inside a separate HyperFrames/video workspace.
- Use the live production site as the source for the product UI when appropriate.

Production Testloom site:
`https://testloom-two.vercel.app/`

Testloom GitHub repository:
`https://github.com/Temmygabriel/testloom`

Treat the GitHub repository as READ-ONLY for video work.

---

## 1. CURRENT WORKING MACHINE

The successful environment is now the user's **local Windows PC**, not the old Codex Cloud Ubuntu environment.

Current known local versions:

- OS: Windows
- Node.js: `v24.14.0`
- npm: `11.9.0`
- HyperFrames: `0.8.80`
- Google Chrome: `153.0.8010.54`
- FFmpeg: `9.0.2-essentials_build-www.gyan.dev`
- FFprobe: `9.0.2-essentials_build-www.gyan.dev`

Chrome path:
`C:\Program Files\Google\Chrome\Application\chrome.exe`

FFmpeg/FFprobe bin directory:
`C:\Users\USER\ffmpeg\ffmpeg-9.0.2-essentials_build\bin`

That FFmpeg bin directory is already on the user's **User PATH** and was confirmed to work in a freshly restarted Antigravity terminal.

Do not reinstall FFmpeg or Chrome unless a new, concrete failure proves that they are missing/corrupt.

---

## 2. IMPORTANT HISTORICAL LESSONS FROM CODEX CLOUD

These are historical facts from a previous cloud run. Do NOT attempt to reproduce the cloud paths on Windows.

### 2.1 Old cloud environment

The old Codex Cloud environment was Ubuntu 24.04.4 with Node `24.15.0`.

HyperFrames initially had network/proxy issues because Node's native `fetch()` ignored the configured proxy. HyperFrames itself reported:

`Proxy variables are set but ignored by Node fetch; if this network requires them, retry with NODE_USE_ENV_PROXY=1`

In that cloud environment, this worked:

```bash
export NODE_USE_ENV_PROXY=1
```

This is a historical cloud workaround. **Do not blindly set Linux-specific paths on Windows.**

### 2.2 Old cloud browser setup

The cloud environment required manually installing Chrome Headless Shell and missing Linux libraries. Those paths are obsolete for this local Windows workflow.

DO NOT use:

```text
/opt/codex/...
```

on the current Windows machine.

### 2.3 What was successfully proven in cloud

Before moving local, the following were proven:

- HyperFrames installed and ran.
- HyperFrames skills were readable.
- FFmpeg/FFprobe worked.
- A HyperFrames local preview worked.
- HyperFrames public publishing worked after `NODE_USE_ENV_PROXY=1`.
- The real Testloom website was successfully captured.

The cloud capture used the real production URL and completed with `ok: true`, HTTP 200, 0 unavailable assets, and extracted screenshots/DOM/design tokens.

### 2.4 Why we moved local

The cloud session consumed substantial agent usage debugging environment details. The local Windows machine is now the working environment and has already proven the core HyperFrames pipeline.

---

## 3. CURRENT LOCAL HYPERFRAMES STATE — PROVEN WORKING

HyperFrames `0.8.80` is installed globally.

This command succeeded:

```powershell
hyperframes --version
```

Result:

```text
0.8.80
```

### FFmpeg

This works in a new Antigravity terminal:

```powershell
ffmpeg -version
ffprobe -version
```

### Chrome

Chrome launches headlessly successfully with:

```powershell
& "C:\Program Files\Google\Chrome\Application\chrome.exe" `
  --headless=new `
  --disable-gpu `
  --dump-dom `
  "about:blank"
```

The command returned valid HTML and then returned to the PowerShell prompt. A GPU warning appeared, but it did not prevent headless launch.

### HyperFrames doctor

`hyperframes doctor --json` confirmed:

- Node: PASS
- FFmpeg: PASS
- FFprobe: PASS
- Disk: PASS
- Memory: PASS
- Archive extractor: PASS
- Chrome path was detected, although the standard GUI Chrome executable timed out in the Doctor's `--version` check.

The direct headless Chrome smoke test proved Chrome itself can launch.

### Local smoke test

A 5-second local HyperFrames smoke project was created and verified:

`C:\Users\USER\Documents\HACKATHONS BUILDS\BOB_IDE\TESTLOOM\TESTLOOM VIDEO\hyperframes-smoke-test`

It passed:

```text
hyperframes lint
0 errors, 0 warnings
```

and:

```text
hyperframes check
Check passed
```

The smoke preview was also successfully served locally on port 3002.

### Real Testloom capture

A real production Testloom capture was successfully created:

`C:\Users\USER\Documents\HACKATHONS BUILDS\BOB_IDE\TESTLOOM\TESTLOOM VIDEO\testloom-capture`

Capture facts:

- URL: `https://testloom-two.vercel.app/`
- HTTP: 200
- Page title: `Testloom`
- Capture `ok`: true
- Phase: complete
- Screenshots: 2 plus generated contact sheet
- Dropped/unavailable assets: 0
- Extracted DOM: `extracted/page.html`
- Design/style files: `tokens.json`, `design-styles.json`, `fonts-manifest.json`
- Fonts: Geist / Geist Mono

**The capture is real and should not be repeated unless the agent has a concrete reason.**

### Real Testloom intro composition

A 10-second product-intro project was successfully created:

`C:\Users\USER\Documents\HACKATHONS BUILDS\BOB_IDE\TESTLOOM\TESTLOOM VIDEO\testloom-product-intro`

Composition:

`testloom-product-intro\index.html`

Real UI asset:

`testloom-product-intro\assets\testloom-ui.png`

Verified:

- 1920x1080
- 30 fps
- 10 seconds
- Real captured Testloom UI
- `hyperframes lint`: 0 errors, 0 warnings
- `hyperframes check`: passed
- Local preview: HTTP 200 / running

The user viewed the intro and said the visual result was **very good**, but it had no voiceover or sound.

---

## 4. HYPERFRAMES WORKFLOW TO USE NOW

HyperFrames is designed as an agent-driven HTML-to-video framework. `/hyperframes` is the entry/router skill. For a product website or product promo, the appropriate workflow is `/product-launch-video`. The official workflow supports roughly 30–90 second videos as its sweet spot and can start from a product URL or supplied script/brief.

Official references:

- HyperFrames repository: https://github.com/heygen-com/hyperframes
- Product launch workflow: https://github.com/heygen-com/hyperframes/blob/main/skills/product-launch-video/SKILL.md
- CLI docs: https://github.com/heygen-com/hyperframes/blob/main/docs/packages/cli.mdx
- Quickstart: https://github.com/heygen-com/hyperframes/blob/main/docs/quickstart.mdx
- HyperFrames launch examples: https://github.com/heygen-com/hyperframes-launches

### Expected production sequence

```text
Read brief/script
    ↓
Inspect product/site and/or existing capture
    ↓
Choose visual identity
    ↓
Storyboard
    ↓
Narration + audio timing
    ↓
Build frame-by-frame HTML compositions
    ↓
Lint
    ↓
Check
    ↓
Preview
    ↓
User review
    ↓
Render final MP4
```

Do not jump directly to rendering a full video before a preview has been checked.

---

## 5. VOICEOVER / AUDIO

The previous 10-second intro was silent. The actual 60-second Testloom demo MUST include narration and appropriate sound unless the user explicitly requests otherwise.

Current HyperFrames CLI documentation supports local TTS through:

```powershell
hyperframes tts "Your narration here"
```

or:

```powershell
hyperframes tts script.txt
```

It supports voice selection with:

```powershell
hyperframes tts --list
```

HyperFrames documents Kokoro local TTS as a no-API-key option, with voice IDs such as `af_*`, `am_*`, etc. The product-launch workflow also supports a full audio step for narration, word timings, BGM and metadata when configured.

### Important audio rule

Before generating audio, the agent should:

1. Read the current HyperFrames audio/TTS instructions.
2. Choose an appropriate English voice.
3. Keep the narration natural and professional.
4. Sync visual changes to narration beats.
5. Use subtle BGM/SFX only where they improve the demo.
6. Avoid cheesy, generic "AI voice" delivery.

The voice should sound like a serious developer-product launch/demo, not an advertisement voiceover.

---

## 6. TESTLOOM PRODUCT FACTS — DO NOT INVENT

Testloom's core story:

> A feature request should not be trusted just because the AI-generated code looks correct. Test it in a real browser.

The demo feature request is:

> **Keep users logged in after refreshing the page.**

Production demo credentials:

```text
Username: demo
Password: demo123
```

### Working implementation

- Login works.
- Dashboard is reached.
- Session survives a browser refresh.
- Result: **PASS**
- 2/2 checks passed.

### Broken implementation

- Login works.
- Dashboard is reached.
- Refresh loses the session.
- Result: **FAIL**
- 1/2 checks passed.

### Core product pipeline

```text
Feature request
→ AI-generated acceptance checks
→ Human review
→ Real Playwright browser execution
→ Evidence capture
→ Deterministic PASS / FAIL / INCONCLUSIVE
```

Important product principle:

> The LLM generates the test plan; it does not decide whether the software passed. Real browser execution and observed behavior determine the result.

Do not invent database integrations, GitHub OAuth, autonomous coding, production monitoring, security scanning, or other capabilities that are not part of the submitted demo.

---

## 7. ONE-MINUTE TESTLOOM DEMO — TARGET STRUCTURE

Target duration: **~60 seconds**.

Format:

- 1920x1080
- 30 fps
- clean, premium developer-tool aesthetic
- dark, technical, human-readable
- restrained motion
- real Testloom UI as the visual anchor
- narration + subtle sound

### Suggested 60-second narrative

**0–6s — Hook**

Visual: fast but restrained opening from the real Testloom capture, with a clear problem statement.

Narration:

> "AI-generated software can look correct without actually working."

On-screen text:

> Looks correct. Not necessarily verified.

**6–14s — Introduce Testloom**

Visual: reveal the actual Testloom landing/product UI.

Narration:

> "Testloom turns a plain-English feature request into real browser acceptance checks."

**14–25s — Feature request**

Visual: show the request:

> "Keep users logged in after refreshing the page."

Then transition into generated acceptance checks.

Narration:

> "Start with a simple request. Testloom turns it into a concrete plan you can review before execution."

**25–37s — Working implementation**

Visual sequence:

```text
Login
→ Dashboard
→ Refresh
→ Dashboard
→ PASS
```

Narration:

> "Testloom runs the approved checks in a real browser. On the working implementation, the user reaches the dashboard and stays logged in after refresh."

Show the real result:

> **PASS — 2/2 checks passed**

Then show evidence briefly.

**37–49s — Broken implementation**

Visual sequence:

```text
Login
→ Dashboard
→ Refresh
→ Session lost
→ FAIL
```

Narration:

> "Now run the intentionally broken implementation. The refresh loses the session, and the browser catches it."

Show the real result:

> **FAIL — 1/2 checks passed**

**49–56s — Why it matters**

Visual: montage of evidence/results.

Narration:

> "The important part is simple: the browser observed what actually happened."

**56–60s — Close**

Visual: Testloom logo/product view + strong final title.

Narration:

> "Don't trust that the feature works. Verify it in a real browser."

End card:

> **Testloom**
> Verify software in a real browser.

---

## 8. VISUAL DIRECTION

The existing 10-second intro established a good visual baseline:

- dark canvas
- clean typography
- real product UI
- subtle depth/shadow
- restrained scaling/motion
- high readability

Keep that quality, but make the full demo feel like a serious product film rather than a collection of title cards.

The real Testloom UI should be shown prominently.

Avoid:

- generic AI brains
- glowing robot imagery
- meaningless particles
- excessive gradients
- constant zooming
- fake dashboards
- giant paragraphs
- overuse of kinetic text
- flashy effects that obscure the product
- "AI slop" visual clichés

Use motion to clarify the workflow:

```text
request → plan → execute → evidence → verdict
```

---

## 9. YOUTUBE / REFERENCE-VIDEO WORKFLOW FOR FUTURE PROJECTS

For serious demo videos, the agent should be encouraged to study **real reference videos before designing**, rather than inventing a style from scratch.

When the user supplies a reference, use it as a pacing/composition reference, not as a source for copying copyrighted visuals or narration.

Useful YouTube searches:

```text
SaaS product launch demo cinematic UI
developer tool product demo
startup product demo video
software launch product video
developer platform demo
AI developer tool product launch
Vercel product launch video
Stripe product launch video
Linear product demo
Raycast product demo
```

The agent should extract design principles from references:

- opening hook length
- product reveal timing
- amount of narration
- transitions
- use of UI close-ups
- text density
- music intensity
- ending CTA

Do not copy another product's branding, script, or distinctive sequence.

HyperFrames itself publishes production examples and working source compositions that are useful references, including product launches and tooling demos:
https://github.com/heygen-com/hyperframes-launches

---

## 10. AGENT OPERATING RULES — AVOID TOKEN / TIME WASTE

The previous cloud setup consumed too much agent usage because the agent repeatedly investigated the environment.

For future runs:

### Do not repeat known setup

Do NOT automatically:

- reinstall Node
- reinstall FFmpeg
- reinstall Chrome
- install Docker
- recreate Linux paths
- repeat the old Codex Cloud dependency hunt
- repeat the full HyperFrames installation investigation

### First inspect the handoff

Before running expensive commands, verify the current local state with a minimal set of commands.

### Work in one dedicated folder

Use:

`C:\Users\USER\Documents\HACKATHONS BUILDS\BOB_IDE\TESTLOOM\TESTLOOM VIDEO`

Create separate subfolders for each production attempt.

Examples:

```text
hyperframes-smoke-test/
testloom-capture/
testloom-product-intro/
testloom-60s-demo/
```

### Keep original capture safe

Never overwrite `testloom-capture`.

### Do not ask the user for approvals on every harmless terminal command

When the user has enabled appropriate Antigravity automatic terminal execution, perform the workflow continuously, but obey the repository safety rules above.

### Stop on real blockers

If a command genuinely fails, report:

- exact command
- exact error
- what the failure means
- one next action

Do not launch a long chain of speculative fixes.

---

## 11. CURRENT IMMEDIATE OBJECTIVE

The next serious objective is:

> **Create a polished ~60-second Testloom demo with real product UI, narration, appropriate BGM/SFX, and a professional HyperFrames visual treatment.**

Before rendering the final video:

1. Build the composition.
2. Generate/sync narration.
3. Add restrained sound.
4. Run `hyperframes lint`.
5. Run `hyperframes check`.
6. Preview it.
7. Inspect the preview/contact sheet.
8. Only after it looks correct, render the final MP4.

Do NOT settle for a silent 10-second title-card demo. The 10-second composition was only the proof that the visual pipeline works.

---

## 12. RECOMMENDED MASTER PROMPT FOR THE NEXT AI AGENT

Paste this **after** giving the agent this file:

```text
Read TESTLOOM_HYPERFRAMES_AGENT_HANDOFF.md completely before doing anything.

This is a video-production task for the already-submitted Testloom project.

IMPORTANT:
- Do NOT modify the Testloom application source code.
- Do NOT modify the Testloom GitHub repository.
- Do NOT create a PR.
- Do NOT commit or push to Testloom.
- Work only inside the dedicated TESTLOOM VIDEO workspace.
- Do not repeat the historical Codex Cloud setup investigation.

Your job is to create a serious ~60-second Testloom product demo using HyperFrames.

Use:
https://testloom-two.vercel.app/

Use the existing real capture when appropriate:
testloom-capture

Use the existing 10-second intro as a visual-quality reference:
testloom-product-intro

The video must include:
- real Testloom UI
- the feature request “Keep users logged in after refreshing the page.”
- reviewed acceptance checks
- working implementation → PASS 2/2
- evidence
- broken implementation → FAIL 1/2
- professional narration
- subtle appropriate BGM/SFX
- 1920x1080
- 30 fps
- approximately 60 seconds

Use the /hyperframes router and the product-launch-video workflow where appropriate.

Before designing, inspect the current HyperFrames audio/TTS documentation and use the supported local/cloud option that is actually available on this machine. Do not guess about voices or providers.

Also look for 2–3 relevant professional product-demo references on YouTube before final visual direction. Extract pacing, UI emphasis, typography/motion principles, and narration style. Do not copy their branding or script.

Create:
- SCRIPT.md
- STORYBOARD.md
- the HyperFrames project/compositions
- final rendered MP4

Production order:

1. Review the handoff.
2. Inspect existing Testloom capture and intro.
3. Study reference videos.
4. Write/refine SCRIPT.md and STORYBOARD.md.
5. Generate narration and audio timing.
6. Build the composition.
7. Run lint.
8. Run check.
9. Preview.
10. Inspect the result.
11. Make only necessary visual fixes.
12. Render the final MP4.

Do not render a full MP4 until lint/check have passed and the preview has been inspected.

At the end report:
- project path
- SCRIPT.md path
- STORYBOARD.md path
- narration provider/voice
- BGM/SFX used
- final MP4 path
- duration
- resolution
- FPS
- file size
- lint result
- check result
- render result
- whether Testloom source/repository was untouched
```

---

## 13. VERIFIED FACTS / OFFICIAL HYPERFRAMES REFERENCES

HyperFrames is an HTML-to-video framework and its official docs describe an agent-driven workflow in which an AI agent creates editable HTML/CSS/JS video compositions. Local rendering does not consume HeyGen credits; hosted/voice/media services may have separate costs.

Official sources:

1. HyperFrames introduction:
https://github.com/heygen-com/hyperframes/blob/main/docs/introduction.mdx

2. HyperFrames quickstart:
https://github.com/heygen-com/hyperframes/blob/main/docs/quickstart.mdx

3. HyperFrames CLI:
https://github.com/heygen-com/hyperframes/blob/main/docs/packages/cli.mdx

4. Product launch workflow:
https://github.com/heygen-com/hyperframes/blob/main/skills/product-launch-video/SKILL.md

5. HyperFrames skill router:
https://github.com/heygen-com/hyperframes/blob/main/skills/hyperframes/SKILL.md

6. HyperFrames production examples:
https://github.com/heygen-com/hyperframes-launches

---

## 14. FINAL PRINCIPLE

The goal is not to prove that HyperFrames can make *a* video.

The goal is to make the Testloom product understandable and credible in about one minute by showing:

```text
Problem
→ Request
→ Reviewable test plan
→ Real browser execution
→ Evidence
→ PASS
→ Broken implementation
→ FAIL
→ Why verification matters
```

The product itself should remain the hero.


---

# 15. FRESH-AGENT START HERE — DO NOT REPEAT SETUP

This section is for a NEW AI account/agent (Antigravity, GPT, Claude, Gemini, etc.).

## The setup is already complete

The Windows machine has already been prepared and the HyperFrames pipeline has already been tested.

**Do not restart setup from zero.**

Do NOT automatically:

- reinstall Node
- reinstall npm
- reinstall HyperFrames
- reinstall FFmpeg
- reinstall FFprobe
- reinstall Chrome
- install Docker
- create WSL/Linux environments
- run broad environment diagnostics
- repeat the old Codex Cloud debugging
- spend time proving the same prerequisites again

Only diagnose a dependency if a CURRENT production command actually fails because of it.

## Current machine

Windows local machine:

```text
Node.js: 24.14.0
npm: 11.9.0
HyperFrames: 0.8.80
Chrome: 153.0.8010.54
FFmpeg: 9.0.2-essentials_build-www.gyan.dev
FFprobe: 9.0.2-essentials_build-www.gyan.dev
```

Known executable locations:

```text
Chrome:
C:\Program Files\Google\Chrome\Application\chrome.exe

FFmpeg/FFprobe:
C:\Users\USER\ffmpeg\ffmpeg-9.0.2-essentials_build\bin
```

The FFmpeg bin directory is already on the user's Windows PATH and was confirmed to work in a freshly restarted Antigravity terminal.

## Proven local HyperFrames capabilities

Already proven on this Windows machine:

1. `hyperframes --version` → `0.8.80`
2. `hyperframes lint` works
3. `hyperframes check` works
4. HyperFrames can start a local background preview
5. Chrome can launch headlessly
6. Real production Testloom website capture works
7. A 10-second real Testloom composition works
8. HyperFrames public publishing worked in the earlier cloud environment

## Existing real Testloom assets — DO NOT RECREATE

Existing folders:

```text
C:\Users\USER\Documents\HACKATHONS BUILDS\BOB_IDE\TESTLOOM\TESTLOOM VIDEO\testloom-capture

C:\Users\USER\Documents\HACKATHONS BUILDS\BOB_IDE\TESTLOOM\TESTLOOM VIDEO\testloom-product-intro

C:\Users\USER\Documents\HACKATHONS BUILDS\BOB_IDE\TESTLOOM\TESTLOOM VIDEO\hyperframes-smoke-test
```

### `testloom-capture` is a REAL production capture

It was captured from:

```text
https://testloom-two.vercel.app/
```

It completed successfully with:

- HTTP 200
- `ok: true`
- complete capture phase
- real Testloom UI
- screenshots
- extracted DOM
- design tokens/styles
- fonts
- 0 dropped/unavailable assets

**Do not recapture unless the existing capture is genuinely unusable.**

### `testloom-product-intro` is already a working real-UI composition

It contains a 10-second real Testloom intro using the actual captured UI.

It passed:

```text
hyperframes lint
0 errors, 0 warnings
```

and:

```text
hyperframes check
Check passed
```

The user has already reviewed it and said the visual quality was very good.

The only major thing missing from that 10-second intro was:

- voiceover
- music/SFX

That project is only a visual baseline. It is NOT the final demo.

---

# 16. THE REAL TASK NOW

The task is no longer setup.

The task is:

> Create the serious ~60-second Testloom product demo.

Required:

- real Testloom UI
- real browser-verification story
- professional voiceover
- appropriate subtle BGM/SFX
- polished motion
- approximately 60 seconds
- 1920x1080
- 30 fps
- final MP4

## The story

Feature request:

```text
Keep users logged in after refreshing the page.
```

Workflow:

```text
Plain-English request
→ acceptance checks
→ human review
→ Playwright browser execution
→ evidence
→ PASS 2/2

Then:

Broken implementation
→ refresh loses session
→ FAIL 1/2
```

The key product principle:

```text
The LLM generates the test plan.
The browser determines what actually happened.
```

## Do not invent capabilities

Do not invent:

- GitHub OAuth
- databases
- autonomous coding
- CI/CD integrations
- production monitoring
- security scanning
- cloud browser fleets
- claims not visible in the real product

---

# 17. REFERENCE VIDEO RESEARCH IS NOW ENCOURAGED

For the final production video, reference research is useful.

The agent should find 2–3 professional software/product-demo references, preferably YouTube examples, and study:

- hook duration
- narration density
- UI reveal timing
- typography
- motion language
- music intensity
- transitions
- end card treatment

Recommended searches:

```text
developer tool product demo
SaaS product launch demo
software product cinematic demo
developer platform demo
AI developer tool product demo
Vercel product launch video
Linear product demo
Stripe product launch video
Raycast product demo
```

Use references as design research only.

Do not copy:

- branding
- scripts
- logos
- distinctive graphics
- exact shot sequences

---

# 18. AUDIO IS A FIRST-CLASS REQUIREMENT

The previous 10-second test proves visual HyperFrames works.

The final video MUST now treat audio as part of production, not an afterthought.

Before generating audio, the agent should:

1. Read the currently installed HyperFrames audio/TTS instructions.
2. Identify which TTS route is actually available on this machine.
3. Prefer a natural professional English voice.
4. Generate timing information where possible.
5. Build the visual pacing around the narration.
6. Add subtle music and restrained SFX.
7. Keep narration intelligible over the music.

Do not fake a voiceover with captions.

Do not use a cheesy advertising narrator.

---

# 19. PRODUCTION GATE — SAVE AGENT USAGE

Do not immediately render a 60-second MP4.

First make a preview.

Required sequence:

```text
plan
→ script
→ storyboard
→ audio
→ composition
→ lint
→ check
→ preview
→ inspect
→ fix only real problems
→ final render
```

The first preview should be the point where the user is invited to judge:

- narration
- pacing
- UI readability
- transitions
- BGM volume
- overall seriousness

Only then render the final MP4.

---

# 20. IMPORTANT NETWORK NOTE

In the old Codex Cloud environment, Node `fetch()` needed:

```bash
NODE_USE_ENV_PROXY=1
```

because the cloud container used a proxy.

That was a **cloud-environment-specific workaround**.

Do NOT blindly add Linux/cloud proxy settings to the current Windows workflow unless a current command proves they are needed.

The current production work is on Windows.

---

# 21. IMPORTANT CHROME NOTE

The old Codex Cloud environment had a missing Linux library:

```text
libatk-1.0.so.0
```

That was a Linux-only issue.

Do NOT try to install Ubuntu packages on Windows.

The current Windows Chrome path is:

```text
C:\Program Files\Google\Chrome\Application\chrome.exe
```

A direct headless Chrome smoke test already succeeded.

The real Testloom capture also succeeded locally, proving that HyperFrames was able to use the browser for the capture workflow.

---

# 22. DO NOT BURN QUOTA ON REPEATED QUESTIONS

The previous cloud run burned substantial agent usage because the agent:

- rechecked the same prerequisites
- tried multiple installation routes
- fought proxy behavior
- retried browser downloads
- repeated diagnostics that had already been answered

A fresh agent MUST:

1. read this file
2. trust the proven facts unless a CURRENT command contradicts them
3. inspect existing project/capture files
4. move directly into video production

If something fails, give:

```text
exact command
exact error
what it means
single next action
```

Do not start a speculative chain of five fixes.

---

# 23. FRESH-ACCOUNT MASTER PROMPT

After uploading this Markdown file to a new AI agent/project, use this prompt.

```text
Read TESTLOOM_HYPERFRAMES_AGENT_HANDOFF.md completely before doing anything.

CRITICAL:
This is NOT a setup task.

The HyperFrames environment is already installed and proven on this Windows machine.

Do NOT:
- reinstall Node
- reinstall FFmpeg
- reinstall FFprobe
- reinstall Chrome
- reinstall HyperFrames
- install Docker
- create WSL
- repeat environment diagnostics
- modify the submitted Testloom repository
- create a PR
- commit or push Testloom

The only task now is to create the REAL Testloom product demo.

WORKSPACE:
C:\Users\USER\Documents\HACKATHONS BUILDS\BOB_IDE\TESTLOOM\TESTLOOM VIDEO

REAL PRODUCT:
https://testloom-two.vercel.app/

EXISTING REAL CAPTURE:
testloom-capture

EXISTING VISUAL BASELINE:
testloom-product-intro

Read those before deciding to capture anything again.

GOAL:
Create a serious approximately 60-second product demo for Testloom using HyperFrames.

The story is:

Feature request:
"Keep users logged in after refreshing the page."

Then:
plain-English request
→ acceptance checks
→ review
→ real browser execution
→ evidence
→ PASS 2/2

Then:
broken implementation
→ refresh loses session
→ FAIL 1/2

The central message is:

"The LLM creates the test plan. The browser proves what actually happened."

REQUIRED:
- real Testloom UI
- 1920x1080
- 30fps
- approximately 60 seconds
- professional narration
- appropriate subtle BGM
- restrained SFX
- polished transitions
- readable typography
- serious developer-tool aesthetic
- no generic AI imagery
- no fake UI
- no invented capabilities
- no cheesy marketing language

REFERENCE RESEARCH:
Before final design, find 2–3 professional software/product demo references on YouTube and extract:
- hook pacing
- narration density
- UI reveal timing
- typography
- motion
- audio treatment
- ending treatment

Do not copy their branding, script, or distinctive graphics.

AUDIO:
Read the currently installed HyperFrames audio/TTS instructions first.
Determine the TTS option that actually works on this Windows machine.
Choose a natural professional English voice.
Build visual timing around the narration.
Use subtle music and sound effects only where useful.

PRODUCTION:
1. Inspect the handoff file.
2. Inspect testloom-capture.
3. Inspect testloom-product-intro.
4. Create/refine SCRIPT.md.
5. Create STORYBOARD.md.
6. Create the full HyperFrames project.
7. Generate/sync narration.
8. Add BGM/SFX.
9. Run hyperframes lint.
10. Run hyperframes check.
11. Start preview.
12. Inspect the preview carefully.
13. Fix only actual problems.
14. Render the final MP4.

IMPORTANT:
Do NOT render the final MP4 until lint/check pass and the preview has been inspected.

When complete, report:
- project path
- SCRIPT.md path
- STORYBOARD.md path
- narration provider/voice
- music/SFX used
- final MP4 path
- duration
- resolution
- FPS
- file size
- lint result
- check result
- render result
- confirmation that Testloom source/repository was untouched
```

# 24. FINAL HANDOFF PRINCIPLE

The new agent should start from:

```text
SETUP DONE
↓
REAL CAPTURE DONE
↓
10-SECOND VISUAL BASELINE DONE
↓
MAKE THE REAL 60-SECOND FILM
```

NOT:

```text
START OVER
→ install everything
→ debug environment
→ waste quota
```

The next meaningful output we want is a serious narrated product demo, not another setup report.


# 25. UPDATED AUDIO WORKFLOW — GOOGLE AI STUDIO + CAPCUT

The previous plan considered installing local Kokoro TTS inside HyperFrames.

DO NOT make Kokoro a required dependency for this Testloom demo.

For this project, use a split workflow:

```text
HyperFrames
→ creates the polished visual video
→ creates/uses timed scene structure

Google AI Studio / Gemini TTS
→ creates the professional voiceover audio

CapCut
→ final assembly
→ voice/music/SFX mixing
→ final export
```

This is intentional. It avoids spending time and RAM installing local TTS when the user can generate the voice separately.

## Important distinction: production timing vs TTS transcript

Create TWO related script files.

### A. SCRIPT.md — production script with timestamps

This is for the human/agent/video-editing workflow.

Example:

```text
00:00–00:05
VOICE: "AI-generated software can look correct without actually working."
VISUAL: Problem hook over Testloom visual language.
MOTION: restrained reveal.

00:05–00:11
VOICE: "Testloom turns a plain-English feature request into a real browser test."
VISUAL: real Testloom UI.

00:11–00:20
VOICE: "Start with a simple request: keep users logged in after refreshing the page."
VISUAL: feature request / acceptance-check creation.

...
```

The timestamps are planning/editing metadata. They are NOT automatically pasted into Google TTS as spoken text.

### B. GOOGLE_TTS.md — clean TTS prompt

This is for Google AI Studio / Gemini TTS.

The spoken transcript must NOT contain production labels such as:

```text
00:00–00:05
VOICE:
VISUAL:
SCENE:
```

Those would risk becoming part of the spoken content.

Instead, create a clean TTS input containing:

1. a short voice/director brief
2. the actual transcript
3. optional inline audio tags only where appropriate

Google's current Gemini TTS documentation says Gemini 3.8 TTS treats transcript text as the text to be spoken. Sustained delivery direction should be supplied as speech metadata/style, while point-in-time pauses/vocal events can be expressed inline. ([Google AI](https://ai.google.dev/gemini-api/docs/speech-generation))

For manual AI Studio use, structure the prompt roughly like:

```text
AUDIO PROFILE
Professional product-demo narrator. Calm, confident, technically fluent, natural conversational delivery. Not an advertisement announcer.

SCENE
A polished developer-tool product demonstration. The viewer is seeing a real software verification workflow.

DIRECTOR'S NOTES
Speak clearly and naturally.
Moderate pace.
Confident but understated.
Slight emphasis on "real browser", "PASS", and "FAIL".
Use short pauses at major transitions.
Avoid hype, sales language, and dramatic trailer delivery.

TRANSCRIPT
AI-generated software can look correct without actually working.

Testloom turns a plain-English feature request into a real browser test.

Start with a simple request:
Keep users logged in after refreshing the page.

Testloom turns that request into acceptance checks that can be reviewed before execution.

Then it runs those checks in a real browser and captures what actually happened.

The working implementation passes.
Two out of two checks passed.

Now test the broken implementation.
The login still works, but the session disappears after refresh.

One out of two checks passed.
That's a real failure.

The LLM creates the test plan.
The browser proves what actually happened.

Testloom.
Don't assume it works. Verify it.
```

The exact final wording must be based on the final `SCRIPT.md` and the actual visuals, not copied blindly from this example.

## Google Gemini TTS formatting guidance

Current Gemini TTS documentation says:

- `speech_metadata.style` is for sustained delivery instructions such as emotion, prosody, pacing and tone.
- Inline angle-bracket tags such as `<short pause>` can mark momentary pauses or vocal events.
- Punctuation, dashes and ellipses can also help control rhythm.
- Gemini 3.8 TTS returns WAV audio by default for unary requests. ([Google AI](https://ai.google.dev/gemini-api/docs/speech-generation))

Therefore:

### GOOD

```text
Style:
Calm, confident, technically fluent product-demo narration. Moderate pace, clear articulation, understated confidence.

Transcript:
AI-generated software can look correct without actually working... <short pause> Testloom turns a plain-English feature request into a real browser test.
```

### BAD

```text
00:00–00:05 [serious voice]
VISUAL: dashboard
SAY:
AI-generated software...
```

Do not include editing instructions in the spoken transcript.

## Audio timing target

A ~60-second English narration commonly needs roughly 120–150 spoken words depending on delivery speed and pauses.

Treat 60 seconds as a target, NOT a rigid rule.

The final narration must be timed against the actual HyperFrames visuals.

If the voiceover is longer than the intended video:

- shorten wording first
- remove filler
- tighten pauses
- do not simply speed the voice unnaturally

If the voiceover is much shorter:

- allow intentional visual breathing room
- do not pad the narration with generic marketing language

## BGM / SFX

Do not make HyperFrames local TTS, local BGM, or local SFX a hard requirement.

Use CapCut for final audio mixing if that is simpler.

Desired audio:

- understated technical/product-demo music
- narration clearly dominant
- subtle UI interaction sounds only when they help comprehension
- no cinematic trailer booms
- no distracting AI-generated ambient noise

The final CapCut mix should make the voice easy to understand on laptop speakers.

---

# 26. REVISED FINAL PRODUCTION PIPELINE

Use this workflow for the serious Testloom demo:

```text
1. Inspect existing real Testloom capture
2. Inspect existing 10-second visual baseline
3. Research 2–3 professional product-demo references
4. Write SCRIPT.md with scene timestamps
5. Write STORYBOARD.md
6. Write GOOGLE_TTS.md
7. Build/refine HyperFrames visuals
8. Run lint
9. Run check
10. Preview and visually inspect
11. Generate the narration separately in Google AI Studio / Gemini TTS
12. Export the voiceover audio
13. Assemble visual + voice + BGM/SFX in CapCut
14. Adjust cuts to narration
15. Export final MP4
```

HyperFrames remains the main visual-generation engine.

Google AI Studio/Gemini TTS is the narration engine.

CapCut is the final editor/mixer.

This is the preferred workflow for Testloom.

---

# 27. YOUTUBE REFERENCE POLICY

Use references before final visual decisions.

The agent should search YouTube for high-quality software/product demonstration videos and collect 2–3 useful references.

For each reference, record:

```text
Reference:
URL:
Why it is useful:
Hook timing:
Narration pace:
UI reveal:
Typography:
Motion:
Audio:
Ending:
```

The purpose is to learn production language, not to imitate.

Do NOT reuse:

- exact scripts
- branding
- logos
- signature graphics
- distinctive sequences
- copyrighted footage

---

# 28. FINAL SCRIPT REQUIREMENT

The final script should be written for a viewer who does NOT already know Testloom.

The first ~5 seconds must communicate the problem.

The concrete example should appear early:

```text
"Keep users logged in after refreshing the page."
```

The viewer should understand:

```text
request
→ checks
→ browser test
→ evidence
→ PASS
→ broken version
→ FAIL
```

The final message should emphasize verification, not AI hype.

A useful closing line is:

```text
The LLM creates the test plan.
The browser proves what actually happened.
```

Then:

```text
Don't assume it works. Verify it.
```

Use those only if they fit the final narration naturally.

---

# 29. MASTER PROMPT — UPDATED FOR GOOGLE TTS + CAPCUT

When giving this handoff to a fresh AI agent, use:

```text
Read TESTLOOM_HYPERFRAMES_FRESH_AGENT_HANDOFF.md completely before doing anything.

This is NOT an environment setup task.

The local HyperFrames environment is already installed and proven.
Do not repeat environment setup unless a current production command actually fails.

Do NOT:
- modify the Testloom application
- clone Testloom
- create a PR
- commit or push Testloom
- reinstall Node
- reinstall FFmpeg
- reinstall FFprobe
- reinstall Chrome
- reinstall HyperFrames
- install Docker
- recreate the known working capture without a concrete reason
- waste usage repeating historical diagnostics

WORKSPACE:
C:\Users\USER\Documents\HACKATHONS BUILDS\BOB_IDE\TESTLOOM\TESTLOOM VIDEO

REAL PRODUCT:
https://testloom-two.vercel.app/

KNOWN REAL ASSETS:
testloom-capture
testloom-product-intro
hyperframes-smoke-test

TASK:
Create the serious approximately 60-second Testloom product demo.

Core story:
"Keep users logged in after refreshing the page."

Narrative:
plain-English request
→ acceptance checks
→ review
→ real browser execution
→ evidence
→ PASS 2/2

Then:
broken implementation
→ refresh loses session
→ FAIL 1/2

Core message:
"The LLM creates the test plan. The browser proves what actually happened."

Visual requirements:
- real Testloom UI
- 1920x1080
- 30fps
- approximately 60 seconds
- premium developer-tool aesthetic
- dark
- restrained motion
- polished transitions
- no fake UI
- no invented product capabilities
- no generic AI imagery

REFERENCE RESEARCH:
Find 2–3 professional software/product demo references on YouTube.
Use them only as design research for pacing, motion, UI emphasis, narration and audio.

AUDIO WORKFLOW:
DO NOT make Kokoro TTS a required part of this task.

Instead:
1. Create SCRIPT.md with timestamps.
2. Create GOOGLE_TTS.md containing a clean spoken transcript plus separate voice/director instructions.
3. The timestamps and visual directions must NOT be inserted into the spoken transcript.
4. Use Google AI Studio / Gemini TTS to generate the voiceover.
5. Use CapCut for final voice/BGM/SFX assembly and mixing.

Gemini TTS formatting:
- sustained delivery instructions belong in the voice/style/director section
- spoken transcript contains only what should be spoken
- use natural punctuation for pacing
- optional inline pause tags such as <short pause> may be used
- do not put VISUAL, SCENE, TIMESTAMP or EDITOR instructions into the spoken transcript

Do not invent Google TTS syntax. Follow the current Google Gemini TTS documentation and use the format appropriate for the currently available model.

PRODUCTION:
1. Read the handoff.
2. Inspect existing real capture.
3. Inspect the 10-second baseline.
4. Research references.
5. Write/refine SCRIPT.md.
6. Write STORYBOARD.md.
7. Write GOOGLE_TTS.md.
8. Build/refine HyperFrames visuals.
9. Run hyperframes lint.
10. Run hyperframes check.
11. Start preview.
12. Inspect visual pacing.
13. Stop and provide the script/TTS package for voice generation if the human still needs to generate the audio externally.
14. Once voiceover audio is available, sync/edit final video.
15. Use CapCut if that is the easiest final audio/mixing path.
16. Render/export the final MP4.

IMPORTANT:
Do not spend large amounts of usage trying to install local TTS when Google AI Studio + CapCut is the chosen workflow.

Do not render the final MP4 until the visual preview looks correct.

FINAL OUTPUT:
- SCRIPT.md
- STORYBOARD.md
- GOOGLE_TTS.md
- final HyperFrames project
- final MP4 when the voiceover/audio is available

Report:
- project path
- script path
- storyboard path
- TTS prompt path
- final MP4 path
- duration
- resolution
- FPS
- voice/TTS model used
- music/SFX workflow
- lint result
- check result
- render/export result
- confirmation that Testloom source/repository was untouched
```
---

# 30. CROSS-PROJECT LESSONS LEARNED FROM FACTOR PROVER

This section records lessons learned while producing the Factor Prover HyperFrames demo. These lessons are intentionally project-agnostic where possible so future TestLoom/video agents can avoid the same waste.

## 30.1 Antigravity + HyperFrames mental model

The working model is:

```text
Antigravity
    ↓
AI coding agent + terminal + editor
    ↓
HyperFrames video project
    ↓
HTML/CSS/JS + GSAP
    ↓
lint / check / preview / render
```

HyperFrames is used **inside the Antigravity workflow**. Do not tell the user to open a separate HyperFrames application unless a future tool/environment explicitly provides one.

## 30.2 Separate product repo from video workspace

Keep application source and video production completely separate.

Example:

```text
APPLICATION REPO
C:\...\PROJECT

VIDEO WORKSPACE
C:\...\PROJECT VIDEO\project-video
```

The video agent may inspect the application repo and the live product, but video-production files should live in the dedicated video workspace.

This prevents accidental application changes and makes cleanup/export simpler.

## 30.3 Capture the real site with HyperFrames

The clean working route for a live website capture was:

```powershell
hyperframes capture "https://example.com/" -o ".\capture" --json
```

In the Factor Prover work, this succeeded with:
- HTTP 200
- real page title
- multiple screenshots
- extracted assets
- detected sections
- detected fonts

Manual Chrome `--screenshot` commands were attempted first and failed to produce the PNG even though Chrome launched. We stopped debugging that path and used HyperFrames capture instead.

**General rule:** when HyperFrames already has a successful capture workflow, prefer it over ad-hoc Chrome screenshot debugging.

## 30.4 Do not debug noisy Chrome warnings unless they actually block output

Chrome may print GPU, GCM, updater, TensorFlow Lite, or similar messages.

Do not treat every stderr line as a blocker.

The relevant question is:

> Did the requested artifact actually get created?

If not, use the known HyperFrames capture route rather than starting an open-ended Chrome debugging session.

## 30.5 AI-agent usage: make the prompt do the thinking

A major source of token/time waste was asking the agent to:
- rediscover the environment
- reinterpret an already-finished visual audit
- invent the storyboard
- investigate capture mechanics repeatedly
- decide the video narrative from scratch

A better pattern is:

```text
human completes research
→ exact story / assets / timings are supplied
→ agent implements
→ check
→ preview
```

For expensive agent calls, provide:
- exact project path
- exact assets
- exact story
- exact timing
- exact text
- exact constraints
- exact acceptance criteria

Tell the agent what is already known and explicitly forbid repeated setup investigation.

## 30.6 Build in stages, preview before rendering

The successful Factor Prover workflow was:

```text
Scene 1
→ user reviews

Scene 2
→ user reviews

Scenes 3–7
→ full composition
→ check
→ preview
→ user reviews
```

This is safer than generating an 80-second render before checking the visual result.

For future projects, keep:

```text
plan
→ compose
→ lint
→ check
→ preview
→ review
→ final render
```

## 30.7 Real UI should be the hero

The strongest results came from using real captured product UI as the visual anchor, with HyperFrames used for:
- framing
- crop/reveal
- subtle zoom
- emphasis
- evidence cards
- transitions
- explanatory overlays

Avoid rebuilding an entire fake dashboard when a real product capture is available.

## 30.8 Do not fabricate a UI state just because the script wants one

Factor Prover exposed an important rule:

The real capture did not contain a literal PROMOTE badge for the historical H-0006 event.

The correct solution was to build an **explicit evidence visualization** from verified data rather than pretending the website showed a screenshot that it did not show.

General rule:

> If a desired state is not present in the captured UI, represent it honestly as a presentation/evidence card, or capture the real state if it is genuinely available. Never fake a screenshot.

## 30.9 Visual QA is worth doing separately

When direct screenshot review was difficult in the main chat, a separate visual review using Claude worked well.

A useful pattern is:

```text
HyperFrames capture
→ contact sheet
→ individual frames
→ visual QA report
→ choose exact assets
```

Ask the visual reviewer to:
- identify what is actually visible
- map filenames to sections
- flag demo-undermining content
- recommend clean frames
- avoid redesign suggestions

This is particularly useful when the builder cannot directly inspect every frame in the chat.

## 30.10 Do not use “the whole website” as the demo story

If the product has technically dense screens, the video should not try to explain every page.

Instead:

```text
simple statement
→ one concrete example
→ actual product evidence
→ central proof
→ close
```

The video should carry the comprehension burden.

This was important for Factor Prover because the live Results/Leaderboard contained cryptic identifiers that were not suitable for the main narrative.

## 30.11 Separate visual production from audio production

The successful preferred workflow is:

```text
HyperFrames
→ visual composition

Google AI Studio / Gemini TTS
→ narration

CapCut
→ voice + BGM + SFX + final export
```

This avoids turning local TTS installation into an unnecessary dependency.

Create:
- a timestamped production script
- a clean TTS transcript

Do not put `SCENE:`, `VOICE:`, timestamps, or visual directions into the spoken transcript.

## 30.12 Preview is the real quality gate

A successful `hyperframes check` proves technical validity.

It does NOT prove the video is good.

The user must still watch the preview for:
- pacing
- readability
- composition
- motion quality
- awkward crops
- accidental warnings/errors
- narration fit
- whether the story actually makes sense

So:

```text
check = technical gate
preview = human quality gate
```

Both are required.

## 30.13 Keep agent calls focused

A future expensive call should ideally do one major production unit.

Good examples:

```text
"Build Scene 1."
"Build Scenes 2–3."
"Implement the remaining scenes from this exact storyboard."
"Fix these two preview issues."
```

Bad example:

```text
"Figure out the whole project, research everything, redesign it, and make the video."
```

The second form burns usage on discovery and reinvention.

## 30.14 When the product is already finished, stop coding it

For hackathon demos, once:
- the product works,
- the key facts are verified,
- the UI rescue is finished,

the next bottleneck is usually presentation.

Do not reopen architecture or redesign the application just because the demo is hard to explain.

Move to:

```text
evidence
→ storyboard
→ composition
→ voice
→ final edit
```
