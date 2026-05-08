# Example: Google Play Child Safety Rejection

## Rejection Message

```
Hello Google Play Developer,

Your app "KiddyLearn" with package ID com.kiddev.kiddylearn has been
suspended and removed from Google Play due to a violation of the Child
Safety Standard policy.

Issue: Child Safety Standard

We found that your app does not comply with the Google Play Families Policy
requirements for apps that target children. Specifically:

- Your app targets children under 13, but you have not completed the Target
  Audience section in Play Console.
- The app collects personal and device information (including advertising ID,
  device model, and usage analytics) but does not disclose this in a child-
  appropriate privacy policy.
- Your app integrates third-party SDKs (AdMob, Firebase Analytics) that
  collect data, but you have not ensured these SDKs are configured to comply
  with COPPA and the Families Policy.
- The app does not provide an in-app disclosure about data collection practices.

Your app must be compliant with the Families Policy to be reinstated.

To appeal this decision, you need to:
1. Complete the Target Audience section in Play Console
2. Update your privacy policy to be child-appropriate
3. Configure all SDKs to disable personalized advertising for child users
4. Add in-app disclosures about data collection
5. Submit an appeal through Play Console

Best regards,
Google Play Review Team
```

## Analysis

```
# Rejection Analysis

## 1. Issue Summary
App suspended from Google Play for violating the Child Safety Standard /
Families Policy — missing target audience declaration, improper data collection
from children, non-compliant SDK configuration, and missing privacy disclosures.

## 2. Platform
Google Play

## 3. Policy Category
Child Safety Standards / Families Policy / COPPA

## 4. Severity
Critical — app is suspended and removed from the store. Requires an appeal
process for reinstatement.

## 5. Likely Root Cause
The app was built with standard SDK configurations (AdMob with personalized ads,
Firebase Analytics default collection) without adapting for child users. The
Target Audience section was not completed in Play Console, so Google's automated
systems likely detected the app's content as child-directed and flagged the
missing compliance measures.

## 6. Confirmed Facts
- App "KiddyLearn" has been suspended and removed from Google Play
- Target Audience section in Play Console is not completed
- App collects advertising ID, device model, and usage analytics
- Privacy policy is not child-appropriate
- AdMob and Firebase Analytics SDKs are not configured for child-directed use
- No in-app data collection disclosure exists

## 7. Assumptions
- The app contains content, design, or themes that appeal to children under 13
- The app may be using default AdMob settings (personalized ads enabled)
- Firebase Analytics is collecting data with default settings
- The privacy policy is a standard adult-oriented policy
- The developer did not intend to target children but Google determined the
  app does based on its content

## 8. Required Fixes

### App / Code Changes
- Add age-gating mechanism to restrict features for users under 13
- Implement a child-specific consent flow for data collection
- Configure AdMob to serve only non-personalized ads when child users are
  detected (set tagForChildDirectedTreatment to YES)
- Configure Firebase Analytics to disable data collection for child users
  (set analytics collection disabled for child-identified sessions)
- Add an in-app privacy disclosure screen for child users explaining what
  data is collected (or that no data is collected)

### Store Console Changes
- Complete the Target Audience section in Play Console:
  - Declare that the app is designed for children (if it is)
  - OR declare it is NOT designed for children but may appeal to them
- Update app content rating if needed
- Submit an appeal through Play Console after all changes are made
  (include a detailed explanation of every change made)

### Metadata Changes
- Update app description to clarify target age range
- Review screenshots and graphics — ensure they do not appeal to children if
  the app is not intended for them

### Privacy / Legal Changes
- Rewrite privacy policy in child-appropriate language if targeting children
- OR update privacy policy to clearly state no data is collected from children
- Ensure the privacy policy is linked from the app's store listing and is
  accessible within the app

### Testing Steps
- Create a test child profile and verify:
  - No personalized ads are shown
  - Analytics data is not sent for child sessions
  - Age gate appears if implemented
  - In-app disclosure is displayed
- Verify the privacy policy link works from all supported devices
- Test on multiple Android versions (API 26+ recommended)

## 9. Reviewer Response Draft

Dear Google Play Review Team,

We are appealing the suspension of KiddyLearn (com.kiddev.kiddylearn). We have
fully addressed the Child Safety Standard violations:

1. Target Audience: The Target Audience section is now completed in Play
   Console, declaring the app is designed for children ages 5-12.

2. SDK Configuration:
   - AdMob: tagForChildDirectedTreatment set to YES for all ad requests.
     Personalized advertising is disabled.
   - Firebase Analytics: Data collection is disabled for child user sessions.
     Analytics is only collected for parent/guardian flows.

3. Privacy Policy: A new child-appropriate privacy policy has been published
   at [privacy policy URL] and linked in the store listing and within the app.

4. In-App Disclosure: A data collection disclosure screen has been added that
   appears on first launch for child users, explaining data practices in
   age-appropriate language.

All changes have been tested and verified. We are committed to maintaining
compliance with Google's Families Policy.

An updated build (version 2.1.0) has been uploaded to the Play Console.

Best regards,
KiddyLearn Development Team

## 10. Resubmission Checklist

- [ ] Target Audience section completed in Play Console
- [ ] AdMob configured for child-directed treatment (tagForChildDirectedTreatment)
- [ ] Firebase Analytics data collection disabled for child sessions
- [ ] All other SDKs audited for child data collection compliance
- [ ] Child-appropriate privacy policy written and published
- [ ] In-app data disclosure screen implemented
- [ ] Age-gating mechanism implemented (if applicable)
- [ ] App content rating verified and updated
- [ ] Privacy policy link added to store listing and in-app
- [ ] Appeal submitted through Play Console with detailed change description
- [ ] App re-uploaded with updated version code
- [ ] Tested with child profile — no personalized ads, no analytics

## 11. Risk Notes
- CRITICAL: This is a suspension, not a simple rejection. The app is already
  removed from the store. Every user-facing change must be complete before
  appealing — Google may not allow a second appeal.
- If the app was NOT intended for children, consider restructuring the app
  to clearly target a general audience and remove child-directed content
  rather than adding child safety measures.
- COPPA compliance is a legal requirement, not just a store policy — ensure
  legal counsel reviews the privacy policy.
- Any third-party SDK that collects data must be compliant. Remove any SDK
  that cannot be configured for child users.
- If the appeal is rejected, the developer account may be at risk.

## 12. Missing Information
- Whether the app is intentionally targeting children or was classified as
  doing so by Google's automated systems
- Which specific third-party SDKs are integrated beyond AdMob and Firebase
- Whether in-app purchases are used and if they require parental consent
- The exact content rating currently assigned to the app
- Whether the app uses any web views or third-party content that could
  link to non-child-safe content
