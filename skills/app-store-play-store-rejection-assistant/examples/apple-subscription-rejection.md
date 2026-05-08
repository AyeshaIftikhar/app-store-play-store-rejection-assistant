# Example: Apple Subscription Rejection

## Rejection Message

```
Dear Developer,

We identified one or more issues with a recent delivery of your app, "FitTrack Pro".
Please correct the following issues, then upload a new binary to App Store Connect.

Guideline 3.1.2 - Subscriptions

We noticed that your app uses auto-renewable subscriptions but does not clearly
communicate the following:

- The title of each subscription level does not clearly describe the content or
  service being offered.
- The subscription duration and price are not displayed prominently before purchase.
- Your app lacks a "Restore Purchases" mechanism for existing subscribers.
- The cancellation instructions for the subscription are not easily discoverable
  within the app.

Specifically, your "Premium Monthly" subscription is labeled as "Premium Monthly"
without describing what features it unlocks. The subscription detail page only
displays the price without showing the duration or renewal terms. Additionally,
there is no button or option to restore previous purchases, and users cannot
find instructions on how to cancel their subscription within the app.

Next Steps

To resolve this issue, please revise your app to ensure that:

- Each subscription title clearly describes the content or service
- Subscription duration, price, and renewal terms are displayed prominently
- A "Restore Purchases" mechanism is available
- Cancellation instructions are clearly visible in the app

Once these changes are made, upload the updated binary to App Store Connect.

Best regards,
App Store Review
```

## Analysis

```
# Rejection Analysis

## 1. Issue Summary
App rejected under Guideline 3.1.2 — Subscription implementation fails to clearly
communicate subscription terms, lacks restore purchases, and hides cancellation
instructions.

## 2. Platform
Apple App Store

## 3. Policy Category
Guideline 3.1.2 — Subscriptions (Auto-Renewable)

## 4. Severity
Blocking — binary rejected, must fix before resubmit

## 5. Likely Root Cause
The subscription purchase flow was implemented without proper UI disclosure of
terms. The restore purchases mechanism was either omitted entirely or not wired
to StoreKit's restore API. Cancellation instructions were placed in a location
not reachable from the subscription management screen.

## 6. Confirmed Facts
- Subscription title "Premium Monthly" does not describe the service offered
- Subscription detail page shows price but not duration or renewal terms
- No "Restore Purchases" button exists in the app
- Users cannot find cancellation instructions within the app

## 7. Assumptions
- The subscription uses StoreKit's auto-renewable subscription type (SKProduct)
- App Store Connect subscription metadata may also be incomplete
- The app likely has existing subscribers who would need restore functionality
- Cancellation instructions may be in a settings menu or not implemented at all

## 8. Required Fixes

### App / Code Changes
- Update subscription display UI to show title + feature description (e.g.,
  "Premium Monthly — Unlimited Workouts & Custom Plans")
- Add prominent price, duration, and renewal term display before the purchase
  button (e.g., "$9.99/month, renews automatically until cancelled")
- Implement SKReceiptRefreshRequest and restoreCompletedTransactions to add a
  "Restore Purchases" button on the subscription management screen
- Add a "How to Cancel" section on the subscription management screen with
  instructions: Open Settings > [Your Name] > Subscriptions > [App Name] > Cancel
- Localize all subscription UI strings

### Store Console Changes
- Verify subscription product IDs in App Store Connect match the codebase
- Ensure subscription display names in App Store Connect are descriptive
- Confirm that subscription durations (1 month, 1 year, etc.) are correctly set
  in App Store Connect

### Metadata Changes
- Update app description to reference subscription features
- No metadata changes required for the rejection itself

### Privacy / Legal Changes
- Ensure subscription terms are included or linked in the privacy policy
- Add standard subscription terms disclosure if missing

### Testing Steps
- Run the app in sandbox environment with a test account
- Verify subscription terms display before the purchase sheet appears
- Purchase a subscription and confirm the restore button retrieves it
- Navigate to the cancellation instructions section and verify it matches
  Apple's actual cancellation flow
- Test on both iOS and iPadOS if applicable

## 9. Reviewer Response Draft

Dear App Store Review Team,

Thank you for your review of FitTrack Pro. We have addressed all issues
identified under Guideline 3.1.2:

1. Subscription "Premium Monthly" now displays a clear feature description:
   "Unlimited Workouts & Custom Plans" on the purchase screen.
2. Subscription duration ($9.99/month), price, and renewal terms ("renews
   automatically until cancelled") are now displayed prominently before the
   purchase button.
3. A "Restore Purchases" button has been added to the Subscription Management
   screen, wired to StoreKit's restore transactions API.
4. A "How to Cancel My Subscription" section has been added to the Subscription
   Management screen with step-by-step cancellation instructions.

An updated binary reflecting all changes has been uploaded to App Store Connect.

Please let us know if any additional information is needed.

Best regards,
FitTrack Pro Development Team

## 10. Resubmission Checklist

- [ ] Subscription UI displays title + feature description
- [ ] Price, duration, and renewal terms shown before purchase
- [ ] "Restore Purchases" implemented and tested in sandbox
- [ ] Cancellation instructions visible in-app
- [ ] All subscription strings localized
- [ ] App Store Connect subscription metadata verified
- [ ] Sandbox testing complete for purchase, restore, and cancellation flows
- [ ] Updated binary uploaded to App Store Connect
- [ ] Response submitted in App Store Connect Resolution Center

## 11. Risk Notes
- Sandbox testing must use a real test account — simulated purchases do not
  trigger the full StoreKit flow.
- If existing subscribers cannot restore purchases, they may leave negative
  reviews. Ensure restore is tested with edge cases (expired subscriptions,
  multiple subscriptions).
- Ensure localized builds are tested — subscription UI truncation in some
  languages could hide critical terms.

## 12. Missing Information
- Whether the app supports family sharing for subscriptions
- Whether promotional offers or introductory pricing are used
- Which specific locales/localizations are required
