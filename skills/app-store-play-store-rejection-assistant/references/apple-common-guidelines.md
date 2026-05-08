# Apple App Store — Common Rejection Guidelines

This reference summarizes the most frequently encountered Apple App Store Review
guidelines. Use this to quickly map rejection messages to policy areas.

---

## 1. Safety (Guidelines 1.1 — 1.6)

| Guideline | Topic | Common Triggers |
|-----------|-------|-----------------|
| 1.1 | Objectionable Content | Hate speech, violence, pornography, defamation |
| 1.2 | User-Generated Content | No content moderation, no reporting mechanism, no blocking |
| 1.3 | Kids | Missing Kids Privacy Policy, no COPPA compliance, inappropriate ads |
| 1.4 | Physical Harm | Health/medical apps making unsubstantiated claims, no disclaimer |
| 1.5 | Legal | Gambling without license, prescription drug sales, illegal content |
| 1.6 | VPN / Security | VPN apps outside China without required approvals |

## 2. Performance (Guidelines 2.1 — 2.5)

| Guideline | Topic | Common Triggers |
|-----------|-------|-----------------|
| 2.1 | App Completeness | Binary rejected, crashes on review, placeholders, demo/beta content |
| 2.1 | Information Needed | Login required but no demo account, features unclear |
| 2.2 | Beta / Unfinished | App is not fully functional, contains bugs, or is clearly incomplete |
| 2.3 | Accurate Metadata | Misleading screenshots, keywords stuffed with unrelated terms |
| 2.4 | Hardware Compatibility | Requires specific accessory not available to reviewer |
| 2.5 | Software Requirements | Uses private APIs, non-public frameworks, or deprecated technologies |

## 3. Business (Guidelines 3.1 — 3.2)

| Guideline | Topic | Common Triggers |
|-----------|-------|-----------------|
| 3.1.1 | In-App Purchase | Digital goods/services not using IAP, missing restore purchases |
| 3.1.2 | Subscriptions | Unclear subscription terms, no cancellation instructions |
| 3.1.3 | Multiplatform | Apps available on other platforms not linking to purchase page |
| 3.1.4 | Content Codes | Content codes (e.g., gift cards) used for digital content |
| 3.2 | Other Business Models | Rentals, donations, or other models not compliant with IAP rules |

## 4. Design (Guidelines 4.0 — 4.9)

| Guideline | Topic | Common Triggers |
|-----------|-------|-----------------|
| 4.0 | Copycats | Imitating other apps, brand impersonation |
| 4.1 | Minimum Functionality | Website wrapper, no native functionality |
| 4.2 | Minimum Functionality | Buggy, crashes, poor user experience |
| 4.3 | Spam | Multiple apps with similar content, template-based apps |
| 4.5 | Apple Sites / Services | Using Apple logos or marketing materials without permission |
| 4.6 | Alternative Storefronts | Mail-order, item sales, not using proper commerce framework |
| 4.7 | Developer Information | Missing or inaccurate support URL, contact info |
| 4.8 | Sign in with Apple | Apps using third-party login not implementing Sign in with Apple |
| 4.9 | ARKit / Crypto | AR experiences, cryptocurrency wallets/trading without proper disclosures |

## 5. Privacy (Guidelines 5.1 — 5.2)

| Guideline | Topic | Common Triggers |
|-----------|-------|-----------------|
| 5.1.1 | Data Collection | No privacy policy, collecting data without consent |
| 5.1.1 | Account Deletion | No account deletion mechanism, deletion does not fully delete data |
| 5.1.2 | Location | Location data collected without clear purpose, no consent |
| 5.1.3 | Health / HealthKit | Health data used outside HealthKit, sold, or used for advertising |
| 5.1.4 | Apple Pay / Wallet | Storing payment data, using Apple Pay without proper implementation |
| 5.1.5 | Data Use / Sharing | Sharing data with third parties without disclosure |
| 5.1.6 | Face ID / Touch ID | Using biometric auth without proper purpose and disclosure |
| 5.2 | Intellectual Property | Copyright infringement, trademark violation |

---

## Reviewer Access Issues

Common reasons the reviewer cannot log in or test the app:

- Demo account credentials were not provided in App Review Information
- Demo account credentials are expired or locked
- App requires a specific network environment (VPN, internal server)
- App requires 2FA that the reviewer cannot bypass
- App requires a physical device (Bluetooth peripheral, credit card reader)
- App requires a specific geographic location
- App requires another app or service to be installed

**Fix:** Always provide a demo account in App Store Connect > App Review Information.
If the app requires specific setup, document it clearly. Set up a review-specific
backend environment that does not require VPN access.

---

## Common Rejection Phrases and What They Mean

| Phrase | Likely Meaning |
|--------|----------------|
| "We noticed your app uses..." | Automated scan detected something |
| "We need additional information" | Review is paused, not rejected |
| "Please revise your app" | Must fix before resubmit |
| "We found that your app does not comply" | Confirmed violation |
| "This is a repeated issue" | Risk of account termination |

---

## Re-Review Typical Timelines

- Standard re-review: 24-48 hours
- Expedited re-review: 1-6 hours (if available)
- Major revision (new binary): 24-48 hours
- After appeal: 1-7 days
