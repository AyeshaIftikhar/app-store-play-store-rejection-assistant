# Example: Google Play Data Safety Rejection

## Rejection Message

```
Hello Google Play Developer,

Your app "WalletWise" with package ID com.finance.walletwise has been
removed from Google Play due to a policy violation.

Issue: Data Safety

After reviewing your app, we found that the data safety section in your
store listing does not accurately reflect your app's data collection and
sharing practices. Specifically:

- Your app collects financial information but this is not declared in your
  Data Safety form.
- Your app shares data with third-party analytics services (Firebase
  Analytics, Crashlytics) but this data sharing is not declared.
- Your app requests user data (contacts and SMS permissions) but the
  declared data safety section does not include these data types.
- Your privacy policy does not mention the third-party SDKs used by your app.

To resolve this issue:
1. Update your Data Safety form to accurately reflect all data collection
   and sharing
2. Update your privacy policy to include all third-party data sharing
3. Remove any unused permissions from your app manifest
4. Submit an updated version for review

Best regards,
Google Play Review Team
```

## Analysis

```
# Rejection Analysis

## 1. Issue Summary
App removed from Google Play because the Data Safety section in the store
listing does not match the app's actual data collection and sharing practices.
Financial data collection is undeclared, analytics SDK data sharing is
undeclared, and requested permissions (contacts, SMS) are not reflected in
the Data Safety form.

## 2. Platform
Google Play

## 3. Policy Category
Data Safety — Misrepresentation of data collection and sharing

## 4. Severity
Critical — app is removed from the store. Requires correction and appeal.

## 5. Likely Root Cause
The developer filled out the Data Safety form based on an early understanding
of the app's SDK integrations but did not update it as new SDKs or features
were added. The financial data collection (transactions, account balances) and
analytics SDK data sharing were simply omitted from the form. The permissions
declared in the manifest (contacts, SMS) may be left over from a previous
feature that was removed or never implemented.

## 6. Confirmed Facts
- App collects financial information (undeclared in Data Safety form)
- App shares data with Firebase Analytics and Crashlytics (undeclared)
- App declares contacts and SMS permissions in the manifest
- App's privacy policy does not mention third-party SDKs
- App is removed from Google Play

## 7. Assumptions
- Financial data collection might be core functionality (transaction tracking,
  account balances) or accidentally collected via analytics
- Contacts and SMS permissions may be legacy — from a feature that was
  removed but the manifest permission was not cleaned up
- The privacy policy may be a generic template that was never updated to
  reflect the actual SDKs in use
- Firebase Analytics and Crashlytics were added after the initial Data Safety
  submission and the form was never updated

## 8. Required Fixes

### App / Code Changes
- Audit all permissions declared in AndroidManifest.xml:
  - If contacts and SMS permissions are not actively used, remove them
  - If they are used, ensure runtime permission requests include a rationale
    dialog explaining why they are needed
- Audit all SDKs and third-party libraries for data collection:
  - Firebase Analytics (collects: device info, usage stats, events)
  - Crashlytics (collects: crash data, device state)
  - Any ad SDKs, payment SDKs, or utility libraries
- Remove any SDK or permission that is not essential to the app's core
  functionality

### Store Console Changes
- Update the Data Safety form to accurately declare:
  - Financial info: Yes, collected (transactions, account balances)
  - App activity: Yes, collected (analytics)
  - Crash data: Yes, collected (Crashlytics)
  - Device IDs: Yes, collected (analytics + crash reporting)
  - Data shared with third parties: Yes (Firebase)
- Complete ALL sections — do not leave any as "Not collected" without
  verifying
- Submit an appeal explaining every correction made

### Metadata Changes
- No metadata changes required beyond the Data Safety form update

### Privacy / Legal Changes
- Rewrite the privacy policy to include:
  - List of all third-party SDKs used (Firebase Analytics, Crashlytics, etc.)
  - What data each SDK collects
  - Why the data is collected
  - How users can opt out where applicable
  - Contact information for data privacy inquiries
- Ensure privacy policy URL is updated in Play Console and is accessible

### Testing Steps
- Generate a complete data flow map: every SDK, every permission, every
  data type collected
- Verify the app functions correctly after removing unused permissions
- Run Google's internal compliance test (if available) or use a third-party
  privacy scanner
- Verify all runtime permission dialogs work correctly

## 9. Reviewer Response Draft

Dear Google Play Review Team,

We are appealing the removal of WalletWise (com.finance.walletwise). We have
completed a full data practice audit and corrected all issues:

1. Data Safety Form: Completely updated. We now accurately declare:
   - Financial information collection (transaction data, account balances)
   - App activity and crash data collection via Firebase Analytics and
     Crashlytics
   - Data sharing with Firebase (Google LLC)
   - Device ID collection

2. Permissions: SMS and Contacts permissions have been removed from the
   manifest. These were remnants from an earlier feature that has been
   deprecated. The updated build no longer requests these permissions.

3. Privacy Policy: Rewritten to include full disclosure of all third-party
   SDKs (Firebase Analytics, Firebase Crashlytics), data types collected, and
   the purposes of collection. Available at [privacy policy URL].

4. SDK Removal: [Any non-essential SDK that was removed]

An updated build (version 3.2.0) with all changes has been uploaded.

Best regards,
WalletWise Development Team

## 10. Resubmission Checklist

- [ ] Full data collection audit completed
- [ ] AndroidManifest.xml cleaned of unused permissions
- [ ] Contacts permission removed (or rationale added if kept)
- [ ] SMS permission removed (or rationale added if kept)
- [ ] Firebase Analytics declared in Data Safety form
- [ ] Crashlytics declared in Data Safety form
- [ ] Financial info collection declared in Data Safety form
- [ ] Data Safety form submitted and saved
- [ ] Privacy policy rewritten with SDK disclosures
- [ ] Privacy policy URL updated in Play Console
- [ ] Updated APK/AAB uploaded to Play Console
- [ ] Appeal submitted with change descriptions

## 11. Risk Notes
- CRITICAL: This is a removal, not a warning. The app is already off the
  store. Ensure the appeal includes specific details about every correction —
  generic appeals are often rejected.
- If financial data is being shared with any third party beyond Firebase
  (e.g., Plaid, Yodlee, MX), those must also be declared.
- Google may perform a follow-up review of data practices. Consider removing
  any analytics SDK that is not essential to reduce ongoing compliance risk.
- If SMS permission is truly needed, be prepared to justify it with a
  Permissions Declaration Form — SMS is a high-risk permission category.

## 12. Missing Information
- Whether the app also collects location, health, or biometric data
- Which specific financial data points are collected (transaction amounts,
  account numbers, routing numbers)
- Whether Firebase is configured with default event collection or custom events
- Whether any ad SDKs are integrated that also collect data
- Whether the app has a web version with its own data collection
