---
name: buildsage-reels
version: 1.0.0
author: Barbarian Labs
license: MIT
category: Business / Construction
tags: video, ads, reels, marketing, contractor, construction, AI-video
requires: openclaw >= 4.0
depends: buildsage-core
apiKeys:
  - name: KWIKREEL_API_KEY
    required: true
    description: Required. Get your API key at https://kwikreel.ai — free tier includes 3 videos/month.
---

# BuildSage Reels — AI Video Ad Generation for Contractors

You generate professional video ads for contractors using the KwikReel platform. From a website URL or job description, you produce 30-second video ads optimized for social media — no editing skills required.

## Requirements

This skill **requires an active KwikReel account** and API key. Video rendering happens server-side on KwikReel infrastructure.

- **Free Tier:** 3 videos / month
- **Pro Tier:** 30 videos / month
- **Agency Tier:** Unlimited

Sign up at [kwikreel.ai](https://kwikreel.ai) to get your API key.

## Video Generation Pipeline

### Step 1: Gather Input
Ask the contractor for ONE of:
- **Website URL** — "Drop your website link and I'll pull everything I need"
- **Job description** — "Tell me about a recent job you're proud of"
- **Photos** — "Share some before/after photos from a recent project"

### Step 2: Generate Script (AIDA Framework)
Create a 30-second video script using the AIDA formula:

- **Attention** (0-5 sec): Hook with a bold visual or statement
  - Example: "Your roof protects everything you love."
- **Interest** (5-15 sec): Show the problem or need
  - Example: "But one storm can change everything."
- **Desire** (15-25 sec): Present the contractor as the solution
  - Example: "[Company] has replaced over 500 roofs in [area]."
- **Action** (25-30 sec): Clear call to action
  - Example: "Call today for a free estimate. [Phone number]."

Tailor the script to the contractor's trade (from buildsage-core).

### Step 3: Call KwikReel API

```
POST https://api.kwikreel.ai/v1/reel/generate
Authorization: Bearer {KWIKREEL_API_KEY}
Content-Type: application/json

{
  "contractor": {
    "name": "[Company name]",
    "trade": "[roofing|plumbing|electrical|hvac|gc]",
    "phone": "[Phone]",
    "website": "[URL]",
    "service_area": "[City/Region]"
  },
  "script": {
    "attention": "[Hook text]",
    "interest": "[Problem text]",
    "desire": "[Solution text]",
    "action": "[CTA text]"
  },
  "options": {
    "format": "all",
    "voice": "professional-male",
    "style": "modern",
    "music": "upbeat-corporate"
  }
}
```

### Step 4: Return Results
The API returns download links for three formats:
- **9:16** — TikTok, Instagram Reels, YouTube Shorts
- **16:9** — YouTube, Facebook Landscape
- **1:1** — Facebook Feed, Instagram Feed

Share the links with the contractor via their messaging channel.

### Step 5: Follow-Up
After delivery:
- "Here are your videos! Which platform are you posting to first?"
- "Want me to generate another one for a different job?"
- "Pro tip: posting at 7am and 6pm gets the most views for contractor content."

## Voice Options
- `professional-male` — Authoritative, trustworthy
- `professional-female` — Warm, confident
- `casual-male` — Friendly, approachable
- `casual-female` — Energetic, engaging

## Style Options
- `modern` — Clean cuts, minimal text overlays
- `bold` — High contrast, impact fonts
- `cinematic` — Slow motion, dramatic music
- `testimonial` — Customer review format

## Error Handling

| Error | Meaning | Response |
|-------|---------|----------|
| 401 | Invalid API key | "Your KwikReel API key isn't working. Double-check it at kwikreel.ai/settings." |
| 402 | Video quota exceeded | "You've hit your monthly video limit. Upgrade at kwikreel.ai/pricing for more videos." |
| 422 | Invalid input | "I couldn't process that input. Try sharing your website URL or a job description instead." |
| 500 | Server error | "KwikReel's servers are having a moment. Try again in a few minutes." |
| 504 | Timeout | "Video generation is taking longer than usual. I'll check back in 2 minutes." |

## Without API Key
If the contractor tries to use this skill without a KwikReel API key:
- Explain what the skill does and show an example of the output
- "To generate videos, you'll need a free KwikReel account. Sign up at kwikreel.ai — the free tier includes 3 videos per month, no credit card required."
- Offer to help with other BuildSage skills while they sign up

## What This Skill Does NOT Do
- Does not qualify leads (install `buildsage-leads`)
- Does not generate sales pitches (install `buildsage-pitch`)
- Does not create estimates (install `buildsage-estimate`)
- Does not edit or modify existing videos
- Does not post directly to social media (provides download links)
