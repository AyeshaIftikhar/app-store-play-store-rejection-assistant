# App Store & Play Store Rejection Assistant

A reusable AI agent skill that helps coding agents analyze Apple App Store and Google Play rejection messages, identify root causes, plan fixes, draft reviewer responses, and create resubmission checklists.

## Installation

```bash
npx skills add anomalyco/app-store-play-store-rejection-assistant
```

Or clone the repository and link it manually:

```bash
git clone https://github.com/anomalyco/app-store-play-store-rejection-assistant.git
# Then configure your agent to point to skills/app-store-play-store-rejection-assistant/SKILL.md
```

## Usage

1. Receive an app store rejection email or Play Console notice.
2. Activate the skill in your AI coding agent (e.g., Claude Code, Codex, Cursor).
3. Paste the full rejection message.
4. The agent will produce a structured analysis with:
   - Platform identification and policy category
   - Severity assessment
   - Root cause analysis with separated facts vs. assumptions
   - Actionable fix checklist (code, store console, metadata, privacy/legal)
   - Reviewer response draft
   - Resubmission checklist

## Structure

```
skills/
└── app-store-play-store-rejection-assistant/
    ├── SKILL.md                          # Main skill definition
    ├── examples/                         # Realistic rejection scenarios
    │   ├── apple-subscription-rejection.md
    │   ├── apple-information-needed.md
    │   ├── google-child-safety-rejection.md
    │   └── google-data-safety-rejection.md
    ├── templates/                        # Reusable response templates
    │   ├── reviewer-response-template.md
    │   ├── fix-checklist-template.md
    │   └── client-summary-template.md
    └── references/                       # Policy reference summaries
        ├── apple-common-guidelines.md
        └── google-play-common-policies.md
```

## Supported Rejection Patterns

**Apple:**
- Guideline 2.1 — Information Needed
- Guideline 3.1.2 — Subscriptions
- Guideline 5.1.1 — Privacy
- Login / Review Access Issues
- In-App Purchase Issues
- Minimum Functionality Issues

**Google Play:**
- Child Safety Standards / CSAE
- Data Safety Issues
- Ads Declaration Mismatch
- Permissions Declaration Issues
- Account Deletion Issues
- Metadata Issues
- Misleading Claims
- Target Audience Issues

## Example

```markdown
# Rejection Analysis

## 1. Issue Summary
App rejected under Guideline 3.1.2 — auto-renewable subscription
implementation does not clearly disclose subscription terms.

## 2. Platform
Apple App Store

## 3. Policy Category
Guideline 3.1.2 — Subscriptions

## 4. Severity
Blocking — binary rejected, must fix before resubmit
```

## License

MIT
