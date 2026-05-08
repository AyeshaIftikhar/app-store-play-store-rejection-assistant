# Example: Apple Information Needed Rejection

## Rejection Message

```
Dear Developer,

We need additional information to complete the review of your app, "SocialChef".

Guideline 2.1 - Information Needed

We have started the review of your app, but we are unable to continue because
we need additional information about your app.

Please provide us with the following information in the Resolution Center:

1. A valid demo account with full access to all features of the app.
2. A short video or screen recording demonstrating the recipe sharing and
   social feed features, as these require other users to be present to
   demonstrate fully.
3. Details about how user-generated content is moderated in the app.

Since your app requires account creation, we need a demo account to fully
evaluate the app.

To provide this information, please reply directly to this message in the
App Store Connect Resolution Center.

Best regards,
App Store Review
```

## Analysis

```
# Rejection Analysis

## 1. Issue Summary
Review paused under Guideline 2.1 — Apple cannot complete the review because
the reviewer needs a demo account, a video demonstration, and moderation details.

## 2. Platform
Apple App Store

## 3. Policy Category
Guideline 2.1 — Information Needed (App Completeness)

## 4. Severity
Info — not a rejection, but a request for information. The review clock is
paused until the information is provided.

## 5. Likely Root Cause
The app requires account creation but no demo credentials were provided in the
review notes. The social feed features require multiple users to demonstrate,
which is not possible with a single demo account. Apple's review guidelines
require them to fully evaluate all features, including moderation flows.

## 6. Confirmed Facts
- The reviewer started the review but could not continue
- A demo account with full access is required
- A video showing recipe sharing and social feed is needed
- Apple is asking about user-generated content moderation
- The reviewer has not rejected the binary — the review is in a paused state

## 7. Assumptions
- The app likely has a login/registration screen as the initial entry point
- No demo account credentials were included in the App Store Connect review
  information field
- The social feed may appear empty with only one demo account
- Moderation may be manual, automated, or not yet implemented

## 8. Required Fixes

### App / Code Changes
- No code changes required at this stage — this is an information request
- If moderation is not yet implemented, a basic moderation system should be
  built before resubmission (Apple may reject later under Guideline 5.2 or 5.3)

### Store Console Changes
- Reply in App Store Connect Resolution Center with:
  1. Demo account credentials (email: reviewer@socialchef.demo / password: Review2024!)
  2. A link to a video screen recording showing the recipe sharing flow and
     social feed with seeded content
  3. A written explanation of the moderation process

### Metadata Changes
- Add demo account credentials to the App Review Information section in App
  Store Connect for future submissions

### Privacy / Legal Changes
- If moderation disclosure is needed, ensure it is covered in the privacy policy

### Testing Steps
- Before replying, log in with the demo account to verify it works
- Record the screen recording showing all requested features
- Verify the demo account has access to every feature, not just a subset

## 9. Reviewer Response Draft

Dear App Store Review Team,

Thank you for reviewing SocialChef. Below is the requested information:

1. Demo Account Credentials:
   - Email: reviewer@socialchef.demo
   - Password: Review2024!
   This account has full access to all features including recipe creation,
   social feed, and messaging.

2. Screen Recording: [Link to video]
   The recording demonstrates:
   - Login with the demo account
   - Creating and publishing a new recipe
   - Browsing the social feed with seeded content from other users
   - Interacting with posts (liking, commenting, sharing)

3. Content Moderation:
   User-generated content (recipes, comments, and messages) is moderated
   through a combination of automated filtering and manual review. All
   content is scanned for prohibited content before publishing. Users can
   also report inappropriate content, which is reviewed within 24 hours.

Please let us know if any additional information is needed to continue the review.

Best regards,
SocialChef Development Team

## 10. Resubmission Checklist

- [ ] Demo account created and verified (all features accessible)
- [ ] Screen recording prepared and uploaded to a shareable link
- [ ] Moderation process documented in Resolution Center reply
- [ ] Demo credentials added to App Review Information for future submissions
- [ ] Reply sent in App Store Connect Resolution Center

## 11. Risk Notes
- The review is paused, not rejected — respond promptly to avoid delays
- Once information is provided, the review will resume from where it left off
- If moderation is not yet implemented, be honest about the current state.
  Apple may still require it before approval.
- If the app crashes or has issues during the reviewer's resumed test, it
  will be rejected — pre-test with the same account the reviewer will use

## 12. Missing Information
- Whether the app has any age restrictions or geo-restrictions
- Whether the app uses push notifications or other services that
  require special setup for the demo account
- The exact scope of features the reviewer expects to see
