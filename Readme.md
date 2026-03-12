# Remaster

**Restore and modernize legacy media for digital publishing.**

A browser-based photo restoration tool that converts plain English descriptions into professional enhancement prompts — then applies targeted corrections in real time. No external tools, no manual sliders, no AI-generated look.

**Live app → coming soon**

---

## The Problem

Travel and lifestyle brands often hold large archives of degraded legacy photos — faded colors, film grain, low resolution, poor lighting. Restoring them manually requires either expensive software expertise or outsourcing to post-production studios.

Existing AI tools tend to over-enhance: they produce results that look painted, cinematic, or hyper-stylized — destroying the authentic character of the original photo and making it unusable for editorial or documentary publishing.

---

## Solution

Remaster uses Claude to convert a plain photo description into a precise, technically-grounded restoration prompt — then applies targeted canvas-based corrections that restore quality while preserving the photo's original era, texture, and realism.

The output looks like a well-shot DSLR photograph of the original scene, not an AI-generated image.

---

## How It Works

![Remaster — Before & After](before-after.png)

**4-step workflow:**

**Step 1 — Upload** · Select any degraded or legacy photo. Tag it with photo type, original era, and primary issue (faded colors, film grain, low resolution, etc.)

**Step 2 — Describe** · Describe the photo in plain English. Claude converts the description into a professional restoration prompt — auto-injecting camera specs, lighting style, and negative prompts to prevent the AI-painted look.

**Step 3 — Enhance** · The app applies targeted corrections based on the generated prompt: brightness lift, contrast boost, color restoration, sharpening, grain reduction, and era-accurate warmth — all via canvas-based processing in the browser.

**Step 4 — Compare & Download** · Drag a split-screen slider to compare original vs restored. Download the enhanced photo as a high-quality JPEG.

---

## Tech Stack

| Layer | Technology | Why |
|-------|-----------|-----|
| Frontend | HTML / CSS / JavaScript | Single-file, zero dependencies, runs in any browser |
| Prompt generation | Claude API (Sonnet) | Converts plain descriptions into technically precise restoration prompts |
| Image processing | Canvas API | Client-side pixel manipulation — no image data sent to any server |
| Backend | Vercel Serverless Function | Proxies Claude API calls — keeps API key off the client |
| Hosting | Vercel | Auto-deploy from GitHub, free tier, global CDN |

---

## Prompt Engineering

Every generated prompt auto-injects three layers of technical instruction:

**Camera spec** — Shot on Canon 5D Mark IV, 85mm f/1.4 lens, RAW DSLR photograph

**Style anchors** — Photojournalism realism, natural lighting, authentic textures

**Negative prompts** — No digital painting, no illustration, no CGI, no hyper-detailed, no cinematic color grading

Words like "realistic," "cinematic," and "dramatic lighting" are explicitly excluded — they push enhancement tools toward a painted, artificial output that destroys archival integrity.

---

## Example Output

A travel media client with an archive of legacy destination photos used this workflow to restore images for digital republishing. Source photos ranged from pixelated mobile screenshots to faded film scans from the 1970s–90s.

Results maintained authentic scene composition and era-accurate color — output was publication-ready without post-production review.

Average processing time: under 20 seconds per image.

---

## Architecture

```
User uploads photo
       ↓
Tags era + issue (pre-sets enhancement parameters)
       ↓
Plain description → POST /api/generate
       ↓
Vercel serverless function → Claude API
       ↓
Professional restoration prompt returned
       ↓
Canvas API applies pixel corrections in browser
       ↓
Split-screen compare → Download
```

---

## Security

- API key stored as a Vercel environment variable — never exposed in client code
- Image data processed entirely client-side via Canvas API — no photos sent to any server
- No user data stored or logged

---

## Roadmap

| Status | Item |
|--------|------|
| ✅ Live | Upload, prompt generation, canvas enhancement, compare slider, download |
| 🔜 Next | Batch processing — restore multiple photos in one session |
| 🔜 Next | Preset library — one-click restoration profiles per era and photo type |
| 📋 Later | Integration with Google AI Studio image enhancement API for higher-fidelity output |
| 📋 Later | Export directly to Cloudinary or S3 for media team handoff |

---

## Product Decisions

**Why canvas-based processing over an image enhancement API** — Keeps image data entirely client-side. No photos are uploaded to a third-party server, which matters for clients with unpublished or proprietary media archives.

**Why Claude for prompt generation instead of a fixed template** — A fixed template produces identical prompts regardless of the source photo's specific issues. Claude interprets the description contextually and adjusts emphasis — a pixelated landscape gets different sharpening instructions than a faded portrait.

**Why negative prompts matter** — Most enhancement tools default to an "AI look" when given vague instructions. Explicitly excluding cinematic, painterly, and hyper-detailed keywords anchors the output to photographic realism.

---

## Disclaimer

The example workflow described above is illustrative and does not reference proprietary client data or internal systems.

---

*Built with Claude · Vercel · Canvas API*
