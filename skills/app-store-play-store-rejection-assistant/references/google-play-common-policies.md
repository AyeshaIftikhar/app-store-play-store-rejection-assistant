# Google Play — Common Policy Violations

This reference summarizes the most frequently encountered Google Play policy
violations. Use this to quickly map rejection/suspension messages to policy areas.

---

## 1. Deceptive Behavior

| Policy | Description | Common Triggers |
|--------|-------------|-----------------|
| Device and Network Abuse | Apps that interfere with network or device functions | SMS/Call log hijacking, VPN misconfiguration |
| Deceptive Behavior | Apps that mislead users or the store | False claims, fake reviews, click injection |
| Malicious Behavior | Malware, trojans, spyware | Code obfuscation hiding malicious functionality |
| Misleading Claims | Unsubstantiated health, performance, or feature claims | "Lose weight fast", "Best battery saver" without evidence |
| Metadata Issues | Store listing does not match the app | Misleading title, irrelevant keywords, wrong category |
| Impersonation | Pretending to be another app or brand | Using similar icon, name, or developer name |

## 2. Store Listing and Ratings

| Policy | Description | Common Triggers |
|--------|-------------|-----------------|
| App Ratings | Manipulating ratings or install counts | Review farms, incentivized ratings |
| Metadata | Inaccurate or misleading store listing | Keyword stuffing, misleading screenshots |
| Target Audience | Wrong age rating or audience designation | Kids content without Families Policy compliance |

## 3. Ads

| Policy | Description | Common Triggers |
|--------|-------------|-----------------|
| Ads Policy | Inappropriate ad content or placement | Full-screen ads at unexpected times, deceptive ad buttons |
| Ads ID | Misuse of Advertising ID | Using AAID for analytics without disclosure |
| Ads Declaration | Not declaring ad SDKs in Data Safety | AdMob, Facebook Audience Network, etc. undeclared |
| Personalized Ads | Serving personalized ads without consent | No consent dialog, no opt-out option |

## 4. Permissions

| Policy | Description | Common Triggers |
|--------|-------------|-----------------|
| Permissions | Requesting unnecessary permissions | SMS, Call Log, Location without core feature need |
| High-Risk Permissions | SMS/Call Log default handler permissions | Requires Permissions Declaration Form |
| Location | Background location without clear need | Location for non-navigation/non-location apps |

## 5. Data Safety

| Policy | Description | Common Triggers |
|--------|-------------|-----------------|
| Data Safety Form | Incomplete or inaccurate declarations | Missing data types, undeclared third-party sharing |
| Privacy Policy | Missing or inadequate privacy policy | Generic policy, no SDK disclosures, no contact info |
| Data Handling | Mishandling user data | Storing data unencrypted, sharing without consent |
| Account Deletion | App creates accounts but no deletion | Missing in-app deletion, no web deletion option |

## 6. Families / Child Safety

| Policy | Description | Common Triggers |
|--------|-------------|-----------------|
| Families Policy | Apps targeting children | Must complete Target Audience section |
| COPPA Compliance | Data collection from children under 13 | No parental consent, no child-appropriate privacy policy |
| CSAE | Child sexual abuse and exploitation | Zero-tolerance — immediate account termination |
| Child Safety Standards | App content or features | UGC moderation, inappropriate content for children |

## 7. Financial and Regulatory

| Policy | Description | Common Triggers |
|--------|-------------|-----------------|
| Financial Services | Loans, budgeting, crypto | Requires regulatory disclosures and licensing |
| Gambling | Real-money gambling | Requires licensing and country-specific approval |
| Health | Health/medical apps | No disclaimers, unsubstantiated claims |
| VPN | VPN services | Requires review and approval from Google |

---

## Enforcement Levels

| Level | Description | User Impact | Fix Path |
|-------|-------------|-------------|----------|
| Warning | Policy violation detected but no enforcement | None | Fix before deadline or next update |
| App Suspended | App removed from store | New users cannot download | Appeal with fixes |
| App Removed | App removed, may be eligible for appeal | New users cannot download | Appeal with fixes + re-upload |
| Account Termination | Developer account terminated | All apps removed | Almost irreversible — legal review needed |

---

## Common Rejection Phrases and What They Mean

| Phrase | Likely Meaning |
|--------|----------------|
| "We found that your app does not comply" | Confirmed violation, action required |
| "Your app has been suspended" | App removed from store |
| "Your developer account has been terminated" | Critical — entire account is closed |
| "Please update your Data Safety form" | Data declarations are incomplete or wrong |
| "Complete the Target Audience section" | Google cannot determine age rating automatically |
| "This is a final notice" | Repeated violation, risk of account termination |
| "Your app appeals to children" | Google's automated systems classified it as child-directed |

---

## Data Safety Form — Data Types to Declare

| Category | Examples |
|----------|----------|
| Location | Approximate, precise GPS |
| Personal Info | Name, email, phone, address, user IDs |
| Financial Info | Payment info, credit score, transactions |
| Health & Fitness | Health data, fitness data, medical records |
| Messages | SMS, MMS, in-app chat, voicemail |
| Photos & Videos | Photos, videos, media files |
| Audio | Voice recordings, music files |
| Contacts | Device contacts, address book |
| App Activity | App usage, search history, installed apps |
| Web Browsing | Browser history, cookies |
| Device IDs | Advertising ID, device model, IMEI |
| Other | Any data not covered above |

---

## Re-Review Typical Timelines

- Standard re-review: 2-5 business days
- Expedited appeal: 1-3 business days
- Appealed suspension: 3-7 business days
- Appealed termination: 7-14 business days
