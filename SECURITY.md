# Security Policy

## Supported Versions

| Version | Supported |
|---------|-----------|
| 1.0.x   | Yes       |

## Reporting a Vulnerability

If you discover a security vulnerability in any BuildSage skill, please report it responsibly:

1. **Do NOT** open a public GitHub issue
2. Email **security@barbarianlabs.com** with details
3. Include: affected skill, description, steps to reproduce
4. We will acknowledge receipt within 48 hours
5. We will provide a fix timeline within 7 days

## Security Considerations

### API Keys
- BuildSage Reels requires a KwikReel API key stored as an environment variable
- Never commit API keys to version control
- Use OpenClaw's built-in secrets management for key storage

### Data Handling
- BuildSage Core, Leads, and Pitch run entirely locally — no data leaves your machine
- BuildSage Estimate (free tier) runs locally; premium features send job scope data to KwikReel API over HTTPS
- BuildSage Reels sends contractor info and scripts to KwikReel API over HTTPS for video rendering
- No data is shared with third parties beyond KwikReel for premium features

### Skill Verification
- All official BuildSage skills are published under the **Barbarian Labs** publisher account on ClawHub
- Verify the publisher before installing any skill claiming to be part of the BuildSage family
- Check VirusTotal reports on ClawHub before installing

## Third-Party Dependencies

BuildSage skills are plain SKILL.md files with no external code dependencies. The only external service connection is the KwikReel API for premium features.
