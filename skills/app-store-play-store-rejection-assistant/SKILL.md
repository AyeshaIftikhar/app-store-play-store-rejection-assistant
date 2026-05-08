---
name: app-store-play-store-rejection-assistant
description: Use when analyzing Apple App Store or Google Play rejection messages, review guideline issues, policy violations, subscription problems, privacy issues, child safety standards, permissions declarations, data safety problems, or reviewer response drafts for mobile apps.
---

# App Store & Play Store Rejection Assistant

## Purpose

Analyze Apple App Store and Google Play rejection messages to help developers understand the root cause, determine the required fixes, draft a professional reviewer response, and create a resubmission plan. This skill converts vague or alarming rejection messages into actionable engineering tasks.

## When to Use This Skill

- You received an Apple App Store rejection email from App Review
- You received a Google Play rejection or suspension notice from the Play Console
- You need to understand what policy was violated and why
- You need to separate what the reviewer actually said from what you assume
- You need a structured plan to fix the issue and resubmit
- You need to draft a response to the App Review team
- You need to explain the rejection to a non-technical stakeholder
- You are preparing a pre-submission review checklist

## Do Not Use This Skill When

- You need legal advice about app store policies
- You want to guarantee approval — no skill can do that
- You need to bypass or circumvent app store policies
- You are dealing with a legal threat or trademark dispute
- The app has already been removed for fraud or has a terminated developer account
- You are submitting a purely web-based app that wraps a website without native functionality

## Required Input

Provide the **full rejection message** including:
- The platform (Apple App Store or Google Play)
- The exact rejection text (copy-pasted, not paraphrased)
- The app name and bundle ID / package name
- Current app version
- Any previous rejection history (if applicable)

**Optional but helpful:**
- Your app's primary category (e.g., Health, Finance, Social, Dating, Kids)
- Whether you use in-app purchases, subscriptions, or login
- Whether your app handles user-generated content, location, or health data

## Analysis Workflow

### Step 1: Identify Platform

Determine whether the rejection is from Apple App Store or Google Play based on the messaging style, policy references, and terminology used.

**Apple indicators:** "Guideline 2.1", "App Review", "Binary Rejected", "Resolution Center", "Apple Developer Program"
**Google indicators:** "Policy violation", "Play Console", "Compliance notice", "Enforcement action", "Developer Program Policies"

### Step 2: Classify Rejection Category

Map the rejection to a specific policy area. See the Common Apple Rejection Patterns and Common Google Play Rejection Patterns sections below.

### Step 3: Determine Severity

| Severity | Apple | Google Play |
|----------|-------|-------------|
| **Info** | Guideline inquiry, clarification needed | Warning, no enforcement yet |
| **Warning** | Rejected but can resubmit after fix | Warning period before enforcement |
| **Blocking** | Binary rejected, must fix before resubmit | App suspended, must appeal |
| **Critical** | Account flagged, repeated violations | Account terminated, removal from store |

### Step 4: Explain Likely Root Cause

Analyze the rejection text and identify the most probable technical or policy root cause. Consider:
- What specific behavior triggered the review?
- What does the policy actually require?
- What is the gap between the current implementation and the policy requirement?

### Step 5: Separate Confirmed Facts, Assumptions, and Missing Information

Create three clear lists:
- **Confirmed Facts:** Direct statements from the reviewer. Do not paraphrase or infer.
- **Assumptions:** What you believe the reviewer means, but is not explicitly stated.
- **Missing Information:** What you still need to know to fully resolve the issue.

### Step 6: Create Required Fix Plan

Organize fixes into categories:

- **App / Code Changes:** Code modifications needed
- **Store Console Changes:** Configuration changes in App Store Connect or Play Console
- **Metadata Changes:** App description, screenshots, keywords, category changes
- **Privacy / Legal Changes:** Privacy policy updates, terms of service, data handling disclosures
- **Testing Steps:** How to verify the fix works before resubmitting

### Step 7: Draft Reviewer Response

Write a professional, concise response that:
1. Acknowledges the issue
2. Explains what was changed
3. Provides any requested information
4. Avoids arguing with the reviewer
5. Does not make claims that cannot be verified

### Step 8: Create Resubmission Checklist

A step-by-step checklist of everything needed before resubmitting, including both the fix and the response.

### Step 9: Optional Client-Facing Explanation

If requested, draft a plain-language summary of the rejection, its impact, and the resolution timeline for non-technical stakeholders.

## Output Format

```
# Rejection Analysis

## 1. Issue Summary

## 2. Platform

## 3. Policy Category

## 4. Severity

## 5. Likely Root Cause

## 6. Confirmed Facts

## 7. Assumptions

## 8. Required Fixes

### App / Code Changes

### Store Console Changes

### Metadata Changes

### Privacy / Legal Changes

### Testing Steps

## 9. Reviewer Response Draft

## 10. Resubmission Checklist

## 11. Risk Notes

## 12. Missing Information
```

## Reviewer Response Template

```
Dear App Review Team,

Thank you for your review. We have addressed the issue(s) identified:

1. [Issue]: [Brief description of what was changed]
2. [Issue]: [Brief description of what was changed]

We have re-uploaded the updated binary to App Store Connect for re-review.

Please let us know if any additional information is needed.

Best regards,
[Developer Name / Team]
```

## Common Apple Rejection Patterns

### Guideline 2.1 — Information Needed
The reviewer needs more information to complete the review. This often happens when:
- Login credentials are missing or expired
- The app requires a specific environment or setup
- The app's functionality is not clear from the description
- Demo accounts need to be provided or updated

**Fix:** Provide clear, working demo credentials. Add a note explaining any required setup steps. Ensure the reviewer can access all features without external hardware or accounts.

### Guideline 3.1.2 — Subscriptions
Issues with auto-renewable subscription implementation:
- Subscription benefits not clearly communicated to users
- Subscription duration and pricing not properly displayed
- Lack of restore functionality for existing subscribers
- Free trial terms not clearly disclosed
- Subscription cancellation instructions not visible

**Fix:** Ensure subscription terms are displayed prominently before purchase. Implement restore purchases. Provide clear cancellation instructions in the app. Ensure all subscription metadata in App Store Connect matches the in-app experience.

### Guideline 5.1.1 — Privacy
Data collection and privacy concerns:
- App collects data without user consent
- Privacy policy does not list all data collected
- Data is used for purposes not disclosed to the user
- App shares data with third parties without disclosure
- Account deletion or data deletion not supported

**Fix:** Review and update privacy policy. Implement proper consent flows. Add account deletion functionality. Ensure data handling matches privacy policy disclosures.

### Login / Review Access Issues
The reviewer cannot access app features because:
- Demo accounts are not provided
- Provided credentials do not work
- App requires a specific configuration or backend environment
- App requires physical hardware or a specific geographic location

**Fix:** Provide working demo credentials. Set up a review-specific backend environment if needed. Document any special setup instructions.

### In-App Purchase Issues
Problems with IAP implementation:
- IAP items not properly configured in App Store Connect
- IAP not using the correct product type
- Content or features locked behind IAP not matching the product description
- Consumable vs. non-consumable product type mismatch
- Missing restore purchases mechanism

**Fix:** Verify all IAP product IDs match between code and App Store Connect. Implement restore purchases. Ensure product descriptions match the actual content delivered.

### Minimum Functionality Issues
The app does not provide sufficient functionality:
- App is essentially a website wrapper without meaningful native functionality
- App is too simple or does not deliver the promised features
- App crashes or has significant bugs on review devices
- App is a demo, trial, or beta without sufficient content

**Fix:** Add meaningful native functionality. Fix all crashes. Ensure all promised features work. Remove any placeholder or incomplete sections.

## Common Google Play Rejection Patterns

### Child Safety Standards / CSAE
Violation of Google's Child Sexual Abuse and Exploitation (CSAE) policy or child safety requirements:
- App content or features that could enable child exploitation
- App targets children but lacks appropriate safety measures
- User-generated content in children's apps without moderation
- Collection of data from children without proper disclosures

**Fix:** Implement robust content moderation. Add age-gating mechanisms. Ensure compliance with Google's Families Policy. Review all user-generated content flows.

### Data Safety Issue
Problems with Google Play's Data Safety section:
- Data safety declarations do not match actual data collection
- Missing or incomplete data safety disclosures
- Data sharing with third parties not declared
- Data collection categories not properly listed (location, personal info, financial info, etc.)

**Fix:** Audit all SDKs and third-party libraries for data collection. Update Data Safety form in Play Console to accurately reflect all data collection and sharing practices. Ensure privacy policy matches declarations.

### Ads Declaration Mismatch
Issues with advertising declarations:
- Ads SDK integrated but not declared in the Data Safety form
- Ads behavior (e.g., personalized ads) not properly disclosed
- Ad networks not listed in the declaration
- Inappropriate ad content shown in certain categories

**Fix:** Declare all ad SDKs and networks in the Data Safety form. Ensure ads are appropriate for the app's target audience. Verify ad serving complies with Google's ad policies.

### Permissions Declaration Issue
Problems with app permissions:
- Permissions requested without corresponding feature implementation
- High-risk or sensitive permissions (SMS, Call Log, Location) without clear justification
- Permissions declared in manifest but not reflected in the Data Safety form
- Permissions used for purposes not disclosed to users

**Fix:** Remove unused permissions. Implement permission rationale dialogs. Ensure permission usage matches both the manifest declarations and the Data Safety form. For high-risk permissions, submit a Permissions Declaration Form if required.

### Account Deletion Issue
Account and data deletion compliance:
- App supports account creation but does not provide account deletion
- Account deletion process is not easily discoverable
- Data deletion does not cover all user data (including backups, analytics, etc.)
- Account deletion in-app but not available outside the app

**Fix:** Implement in-app account deletion. Provide a web-based account deletion option. Ensure all user data is deleted within the required timeframe. Document the deletion process in the Data Safety form.

### Metadata Issue
Problems with store listing metadata:
- Misleading app description or title
- Inappropriate icons, screenshots, or promotional graphics
- Incorrect category or content rating
- Keywords that imply functionality not present in the app
- Impersonation of other apps or brands

**Fix:** Update app title, description, and screenshots to accurately represent the app. Verify category and content rating are correct. Remove any misleading or keyword-stuffed metadata.

### Misleading Claims
The app makes claims that cannot be verified:
- Health or medical claims without evidence
- Performance claims (e.g., "best battery saver") without substantiation
- Misleading representations of app capabilities
- Fake reviews, ratings, or install counts

**Fix:** Remove unsubstantiated claims from metadata and in-app copy. Provide evidence for any performance or health claims. Ensure the app delivers what it promises.

### Target Audience Issue
Problems with target audience and age rating:
- App targets children but is rated for general audiences
- App contains content unsuitable for the declared target audience
- Families Policy requirements not met for apps targeting children
- Age rating does not match app content

**Fix:** Complete the Target Audience section in Play Console. Update content rating if needed. Implement Families Policy requirements if targeting children. Review all content for age-appropriateness.

## Style Rules

1. Be direct and actionable — every finding should include a "what to do about it" component.
2. Never assume the user has made changes — always use conditional language: "If implemented" or "When configured."
3. Separate facts from interpretation clearly in every analysis.
4. Do not guarantee approval — no outcome can be guaranteed.
5. Be professional and constructive — rejections are frustrating; the tone should be helpful, not critical.
6. Flag high-risk areas explicitly: children, privacy, health, finance, location, subscriptions, dating, and user-generated content.
7. Keep developer-focused — assume the reader knows how to code but may not know store policies.
8. When in doubt about a policy requirement, note it in Missing Information rather than guessing.
9. Avoid legal language — do not provide legal interpretations or guarantees.
10. If the rejection is critical (account-level), recommend escalation or legal review rather than self-help.
