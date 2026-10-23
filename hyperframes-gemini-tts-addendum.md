# Addendum: Using Google Gemini TTS for HyperFrames Demo Narration

**Purpose:** supplement the existing HyperFrames handoff/setup guide with the missing voiceover workflow. This is an addendum, not a replacement for the established HyperFrames workflow. It documents the approach that worked when local TTS was unavailable or sounded robotic.

## The practical path that worked

Use Google Gemini text-to-speech to create a narration audio file, then import that finished audio into the existing HyperFrames composition/render workflow. This avoids installing another local voice model and keeps the build focused on the demo.

Successful working request in the UsageBar demo workflow used:

- REST endpoint: `https://generativelanguage.googleapis.com/v1beta/models/gemini-3.8-flash-tts:generateContent`
- Authentication: `x-goog-api-key: <API_KEY>` request header
- Request modality: `generationConfig.responseModalities: ["AUDIO"]`
- Voice configuration: `generationConfig.speechConfig.voiceConfig.prebuiltVoiceConfig.voiceName: "Kore"`
- Narration text: the approved spoken words only; exclude shot directions, timestamps, and visible on-screen labels

**Model-ID note:** `gemini-3.8-flash-tts` is the model ID that succeeded in this specific workflow. Model names and availability can change; if a new build returns a model-not-found error, check current Google Gemini speech-generation documentation and update the model ID instead of repeating the same request blindly.

## Step 1 — Lock the narration before generating audio

1. Finish and review the script/storyboard first.
2. Keep spoken narration in a separate plain-text or Markdown file.
3. Remove scene headings, timestamps, quoted on-screen text that is not meant to be spoken, and production directions.
4. Read the text aloud or estimate duration before calling TTS. Long text can produce a much longer narration than the storyboard target.
5. Do not ask TTS to rewrite or expand the approved script in the generation prompt. Use delivery instructions for voice style, not content changes.

A useful voice-direction instruction is:

> Read in clear English with a natural, warm, composed documentary-style delivery. Use a measured pace, subtle emphasis, short natural pauses between paragraphs, and no exaggerated promotional enthusiasm. Preserve the supplied words exactly.

## Step 2 — Make one direct REST request

A minimal request body has this shape:

```json
{
  "contents": [{
    "parts": [{ "text": "PASTE APPROVED NARRATION HERE" }]
  }],
  "generationConfig": {
    "responseModalities": ["AUDIO"],
    "speechConfig": {
      "voiceConfig": {
        "prebuiltVoiceConfig": { "voiceName": "Kore" }
      }
    }
  }
}
```

Send it as JSON with the `x-goog-api-key` header. The generated audio is returned in the JSON response under the first candidate's content parts, typically in `inlineData.data` as Base64; the MIME type is in `inlineData.mimeType`.

### Authentication without losing time

- Create/obtain the API key from Google AI Studio, and check the current model's access and free-tier limits before generating.
- Keep the key out of prompts that may be saved, source files, git history, screenshots, logs, and final reports.
- For a one-off Windows terminal request, pass the key to a short-lived process using a temporary environment variable, read it from `process.env`, and clear the variable in the parent PowerShell session afterwards. Never write the actual key into the JavaScript file.
- Avoid `Read-Host -AsSecureString` inside a nested PowerShell subprocess launched with `-NonInteractive`: it has no interactive terminal and cannot receive user input. If a masked prompt is used, run it in a normal, interactive PowerShell window.
- If a key was pasted into a chat, prompt, or log, treat it as exposed and rotate it after the build.
- Make one request and report the actual redacted error if it fails; do not silently retry, enable billing, or switch services.

## Step 3 — Decode the returned audio correctly

Do not assume the Base64 payload is already a WAV file. Check `inlineData.mimeType` first.

The UsageBar run received raw PCM and created a valid WAV with the existing FFmpeg installation. The observed output was:

- signed 16-bit little-endian PCM (`pcm_s16le`)
- 24,000 Hz sample rate
- one channel (mono)

For raw PCM in that format, write the Base64-decoded bytes to a temporary raw file and convert it to a WAV using the already-installed FFmpeg:

```powershell
ffmpeg -y -f s16le -ar 24000 -ac 1 -i "voiceover.raw" "voiceover.wav"
```

This command is correct only when the returned audio really is 24 kHz, mono, signed 16-bit little-endian PCM. Inspect the MIME metadata and Google documentation if the format differs. If the data is already a valid WAV container, do not wrap it again. Delete temporary raw data after successful conversion.

## Step 4 — Validate the file before using it

Use the existing FFprobe installation; do not install another package just to inspect audio:

```powershell
ffprobe -v error -show_entries format=duration,size:stream=codec_name,sample_rate,channels -of default=noprint_wrappers=1 "voiceover.wav"
```

Confirm:

- the audio file exists and is non-empty;
- the file has a valid audio stream and the expected sample rate/channel count;
- actual duration is measured, not assumed from the storyboard;
- the spoken content matches the approved script;
- the narration length matches the planned edit. If it is too long, first shorten the script and regenerate; do not speed up automatically without listening.

In the UsageBar example, the first successful WAV was 65.96 seconds although the storyboard target was 50 seconds. That is why duration verification must be part of the repeatable procedure. A shorter, corrected script was then prepared.

## Step 5 — Import into HyperFrames and render

1. Put the final validated narration file in the dedicated video workspace, outside the application source repo.
2. Reference that audio in the existing HyperFrames composition using the workflow in the primary handoff guide.
3. Time the shots to the actual measured audio duration; don't cut off a sentence to hit an arbitrary target.
4. Use the existing HyperFrames lint/check/preview steps before final rendering.
5. Listen to the full rendered MP4 and use FFprobe to verify that the MP4 contains an audio stream and has the expected duration.
6. Keep voiceover versions (`v1`, `v2`, etc.) until a final one is selected. Do not silently overwrite a known-good render.

## Time-saving checklist for the next agent

- [ ] The storyboard is approved before TTS.
- [ ] Narration-only text is saved separately.
- [ ] One Google Gemini TTS request made; API key not stored in repo.
- [ ] Returned MIME type inspected before decoding/conversion.
- [ ] WAV exists and passes FFprobe.
- [ ] Actual duration checked against the storyboard.
- [ ] Final audio imported into HyperFrames.
- [ ] HyperFrames validation/preview completed.
- [ ] Final MP4 has verified video and audio streams.
- [ ] No secrets, narration scratch files, raw PCM, or renders accidentally committed to the application repository.

## Official reference

Google Gemini speech generation documentation: https://ai.google.dev/gemini-api/docs/speech-generation
