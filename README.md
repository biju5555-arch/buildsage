# BuildSage 🏗️

**The AI Skill Family for Construction — Built for the Building Trades**

BuildSage is a modular set of [OpenClaw](https://openclaw.ai) skills designed specifically for contractors in the construction industry. Each skill solves a specific pain point — from lead qualification to video ad generation — and they work best together.

## The Skills

| Skill | What It Does | Tier |
|-------|-------------|------|
| **[buildsage-core](./buildsage-core)** | Construction-aware base layer. Trade detection, contractor persona, safety guardrails. | Free |
| **[buildsage-leads](./buildsage-leads)** | AI-powered lead qualification. Three-question flow, Hot/Warm/Cold scoring, follow-up drafts. | Free |
| **[buildsage-pitch](./buildsage-pitch)** | Trade-specific sales messaging. Objection handling, pricing anchors, adaptive tone. | Free |
| **[buildsage-estimate](./buildsage-estimate)** | Job scoping and rough estimates. National averages free, hyper-local with KwikReel. | Freemium |
| **[buildsage-reels](./buildsage-reels)** | AI video ad generation. Website-to-video pipeline via KwikReel API. | Premium |

## Quick Install

\`\`\`bash
# Install the free skills
openclaw skill install buildsage-core
openclaw skill install buildsage-leads
openclaw skill install buildsage-pitch

# Install freemium (premium features optional)
openclaw skill install buildsage-estimate

# Install premium (requires KwikReel API key)
openclaw skill install buildsage-reels
\`\`\`

## Supported Trades

- 🏠 **Roofing** — Shingle replacement, metal roofing, repairs, inspections
- 🔧 **Plumbing** — Residential & commercial, new construction, remodels
- ⚡ **Electrical** — Panel upgrades, rewiring, new construction, service calls
- ❄️ **HVAC** — Installation, replacement, repair, maintenance contracts
- 🏗️ **General Contractor** — Remodels, additions, new builds, project management

## How It Works

1. **Install buildsage-core** — gives your OpenClaw agent construction industry knowledge
2. **Add buildsage-leads** — incoming messages get automatically qualified and scored
3. **Add buildsage-pitch** — trade-specific pitches and objection handling activate
4. **Add buildsage-estimate** — scope jobs and generate rough estimates on the fly
5. **Add buildsage-reels** — generate 30-second video ads from your website or job descriptions

Each skill is independently useful, but the real power comes from running them together. Your OpenClaw agent becomes a full construction sales assistant that works 24/7 through WhatsApp, Telegram, or any channel you use.

## Architecture

\`\`\`
                    BuildSage Core
                         |
          ┌──────────────┼──────────────┐──────────────┐
          |              |              |              |
        Leads          Pitch        Estimate        Reels
       [FREE]         [FREE]      [FREEMIUM]     [PREMIUM]
                                                     |
                                              KwikReel API
                                          (server-side, hosted)
\`\`\`

- **Core** provides trade detection and contractor persona to all other skills
- **Leads, Pitch, Estimate** work entirely locally — no external APIs required
- **Reels** connects to the KwikReel platform for video rendering
- **Estimate** has optional premium features via KwikReel API

## KwikReel Integration

BuildSage Reels and BuildSage Estimate (premium features) connect to [KwikReel](https://kwikreel.ai), a video ad platform for contractors.

- **Free tier:** 3 videos/month, basic estimates
- **Pro tier:** 30 videos/month, hyper-local pricing, branded PDFs
- **Agency tier:** Unlimited videos, multi-contractor support

Sign up at [kwikreel.ai](https://kwikreel.ai) to get your API key.

## Requirements

- [OpenClaw](https://openclaw.ai) >= 4.0
- Node.js >= 22
- Any messaging channel supported by OpenClaw (WhatsApp, Telegram, Slack, Discord, etc.)

## Contributing

BuildSage is built by [Barbarian Labs](https://barbarianlabs.com). We welcome contributions that improve the construction trade experience:

- Bug fixes and improvements to existing skills
- New trade-specific templates and pitch angles
- Regional pricing data contributions
- Language and localization support

Please read our [Contributing Guide](.github/CONTRIBUTING.md) before submitting a PR.

## Security

If you discover a security vulnerability, please report it responsibly. See our [Security Policy](SECURITY.md).

## License

MIT License — see [LICENSE](LICENSE) for details.

---

**Built by [Barbarian Labs](https://barbarianlabs.com) · Powered by [KwikReel](https://kwikreel.ai) · Running on [OpenClaw](https://openclaw.ai)**

*"The AI that speaks contractor."*
