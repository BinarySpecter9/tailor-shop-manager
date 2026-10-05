# Play Store Launch Pack — Tailor Shop Manager

Pre-submission audit + 14-day closed-testing tracker

| CURRENT POSITION | Working mobile web app with a real backend; no Android package yet. |

| --- | --- |

**FAIL**  Release readiness: blocked until Android packaging and compliance work are complete.

Requirements checked against official Google Play guidance on 5 October 2026.

This pack prepares the launch. It does not create an account, submit the app, or pay any fee.

# Release decision

**Do not submit yet. **The product is a working web app, but Google Play needs an Android release artifact and completed account, policy, listing, and testing gates. The fastest safe path is: package first, document data handling, complete Play Console setup, then start the 14-day closed test.

## How to read the audit

| Status | Meaning |

| --- | --- |

| PASS | Evidence exists in the current materials. |

| FAIL | A required release condition is currently absent or contradicted. |

| NOT STARTED | No completed artifact or Play Console proof was available. |

| NOT APPLICABLE | The requirement does not apply to this phone/tablet business app. |

**Audit basis: **the supplied build description, the existing Play Store kit, and known project notes. Console-only items are marked Not started unless evidence was available; update those rows if the account owner has already completed them.

# Readiness at a glance

| 4 | 4 | 24 | 1 |

| --- | --- | --- | --- |

| PASS | FAIL | NOT STARTED | NOT APPLICABLE |

**Critical path: **Android package → signed AAB targeting API 36 → policy/listing completion → closed test → production-access application → final submission.

A “Pass” on web functionality or a draft asset does not mean the app is publishable; the blocking release gates are shown as Fail or Not started.

# Pre-submission audit

Each check states what is true now, the next action, and the evidence that closes the item. Complete the blocking items before asking Google to review the app.

## A. Android package and product quality

| Working mobile experience | PASS |

| --- | --- |

**Current: **A mobile-first web app is reported working and connected to a real backend.

**Do this: **Keep the web build as the product source for the Android wrapper.

**Done when: **The same core customer, measurement, order, progress, and assistant flows work on Android.

| Real backend and persistence | PASS |

| --- | --- |

**Current: **Server-side persistence exists for customers, garment orders, and progress logs.

**Do this: **Confirm production hosting, access control, backups, encryption in transit, and deletion behavior.

**Done when: **A test shop cannot read another shop’s data, records survive reinstall/sign-in, and deletion works as disclosed.

| Android application package | FAIL |

| --- | --- |

**Current: **The current deliverable is a web app, not an Android application.

**Do this: **Create an Android project, for example with Capacitor, and connect it to the existing web app and backend.

**Done when: **The release build installs and runs on real Android devices without relying on a browser tab.

| Android App Bundle (AAB) | FAIL |

| --- | --- |

**Current: **No .aab release file exists.

**Do this: **Build a release Android App Bundle, not a web zip and not only an APK.

**Done when: **A signed .aab uploads successfully to a Play Console testing track.

| Target Android 16 / API level 36 | FAIL |

| --- | --- |

**Current: **There is no Android project, so targetSdk 36 is not configured.

**Do this: **Set compileSdk and targetSdk to 36 or higher and resolve behavior changes and permission issues.

**Done when: **Play Console accepts the bundle without a target-API warning. From 31 August 2026, new phone/tablet apps and updates must target API 36 or higher.

| Permanent package name and versioning | NOT STARTED |

| --- | --- |

**Current: **The draft suggests com.tailorshop.manager, but uniqueness and final ownership are not confirmed.

**Do this: **Choose a unique package name before creating the Play app. Set versionCode 1 and a user-facing versionName such as 1.0.0.

**Done when: **The package name is final, registered to the developer account, and every later upload uses a higher versionCode.

Package names are permanent and cannot be reused. Do not treat the draft suggestion as reserved.

| Play App Signing and upload key | NOT STARTED |

| --- | --- |

**Current: **No signing setup or protected upload key is evidenced.

**Do this: **Enroll the new app in Play App Signing and create a secure upload key for signing bundles sent to Google.

**Done when: **Play Console shows Play App Signing active and accepts a bundle signed with the registered upload key.

| Android device and release testing | NOT STARTED |

| --- | --- |

**Current: **The web app has not been evidenced as a release Android build tested on real devices.

**Do this: **Test install, login, customer creation, measurements, progress updates, search/assistant, offline/error states, upgrades, and deletion on several Android versions and screen sizes.

**Done when: **The signed release build passes the test script on real devices, with no blocker crashes or data loss.

| Known daily-progress count issue | FAIL |

| --- | --- |

**Current: **A known issue can show one item completed today when zero was logged.

**Do this: **Fix the date/count calculation and add tests for zero, multiple entries, midnight, and time-zone changes.

**Done when: **The dashboard count matches the saved progress log in all tested cases.

## B. Developer account and testing access

| Developer account and account type | NOT STARTED |

| --- | --- |

**Current: **No Play Console account or account type is evidenced in the supplied materials.

**Do this: **The owner chooses personal or organization, creates the account, and completes the information Play Console requests.

**Done when: **The owner can access Play Console and the account has no setup task blocking app creation.

| Developer identity and contact verification | NOT STARTED |

| --- | --- |

**Current: **No completed identity verification is evidenced.

**Do this: **Complete the Play Console identity flow using accurate legal details and required documents; verify developer and contact email details.

**Done when: **Play Console marks identity and required contact details verified.

For a personal account, Google may request an official government identity document. Organization requirements differ.

| Android device verification for a new personal account | NOT STARTED |

| --- | --- |

**Current: **No device-verification proof is available.

**Do this: **If Play Console shows the task, use the Play Console mobile app while signed in as the account owner to verify access to a real Android device.

**Done when: **The device-verification task disappears from the Play Console Home page.

| Package-name registration | NOT STARTED |

| --- | --- |

**Current: **No Android package exists or is registered.

**Do this: **After choosing the permanent package name, register it under the verified developer account as required by Play Console.

**Done when: **Play Console shows the app package registered to the correct developer. The 30 September 2026 package-registration requirement is satisfied.

| Closed-test requirement applies? | NOT STARTED |

| --- | --- |

**Current: **The account creation date and type are not known.

**Do this: **Check the Play Console Dashboard. If this is a personal account created after 13 November 2023, use the closed-test plan in this pack.

**Done when: **Applicability is recorded. If required, the production-access card shows the test requirement; if not, retain testing as a quality step.

| Closed testing: 12 continuous opt-ins | NOT STARTED |

| --- | --- |

**Current: **No closed track, tester list, or opt-in evidence exists.

**Do this: **Upload a release to a closed track and have at least 12 testers opt in and remain opted in continuously.

**Done when: **Play Console shows at least 12 qualifying testers for the same app and track.

| Closed testing: 14 continuous days | NOT STARTED |

| --- | --- |

**Current: **No qualifying test window has started.

**Do this: **Track the cohort daily for at least 14 continuous days. Replace any dropout, but restart the shared qualifying window if the count falls below 12.

**Done when: **At least 12 testers have each remained opted in continuously for 14 days and Play Console allows a production-access application.

| Production-access application | NOT STARTED |

| --- | --- |

**Current: **The testing gate has not been completed.

**Do this: **After eligibility appears, answer Play Console questions accurately about the app, testing, feedback, and production readiness.

**Done when: **Production access is granted. Eligibility to apply is not the same as approval.

## C. Privacy and data handling

| Data inventory for app and third-party code | NOT STARTED |

| --- | --- |

**Current: **The backend stores customer and order data, but no complete inventory of data flows, SDKs, retention, or sharing is documented.

**Do this: **List every data type sent off the device, why it is used, where it is stored, who receives it, retention, security, and whether collection is optional.

**Done when: **The inventory covers the app, backend, hosting, authentication, analytics, crash reporting, AI services, and every bundled SDK.

| Google Play Data safety form | NOT STARTED |

| --- | --- |

**Current: **No submitted Data safety declaration exists.

**Do this: **Complete the form from the verified data inventory. Include collection and sharing by the backend and SDKs, not only data stored on the phone.

**Done when: **The form is submitted, accurate for every distributed version, and consistent with the privacy policy.

| Public privacy policy | NOT STARTED |

| --- | --- |

**Current: **A draft exists, but it is not hosted and incorrectly says data is stored only on the device; the current build uses a real backend.

**Do this: **Rewrite the policy to name the actual backend data handling, purpose, retention, security, deletion method, service providers, and contact. Publish it at a stable public URL.

**Done when: **The URL works without login, the policy matches actual behavior and the Data safety form, and contact details are complete.

| Account and data deletion | NOT STARTED |

| --- | --- |

**Current: **It is not confirmed whether users create app accounts or how backend records are deleted.

**Do this: **If the app lets users create accounts, provide an in-app deletion path and a public web request path. Define what is deleted and retained.

**Done when: **A tester can request deletion in app and on the web, and the backend follows the published policy. If there are no user accounts, record that fact.

## D. App content declarations

| Content rating | NOT STARTED |

| --- | --- |

**Current: **No International Age Rating Coalition questionnaire or rating certificate exists.

**Do this: **Complete the Play Console content-rating questionnaire truthfully for the final app and its content.

**Done when: **A valid rating is applied in every target region and the answers still match the app.

| Target audience and content | NOT STARTED |

| --- | --- |

**Current: **No target-age declaration exists.

**Do this: **Choose the intended age groups based on the real audience. Do not select children unless the app and its data practices meet the Families requirements.

**Done when: **Play Console shows the target-audience section complete and consistent with the listing.

| Ads and other app-content declarations | NOT STARTED |

| --- | --- |

**Current: **The old draft says there are no ads, but the release build and SDK list have not been checked.

**Do this: **Declare ads accurately and complete every App content task shown for the final feature set, including permissions or special-category forms if Play Console requests them.

**Done when: **Every applicable App content item is actioned and matches the release build.

| Reviewer access | NOT STARTED |

| --- | --- |

**Current: **It is not known whether login is required or whether a reviewer account exists.

**Do this: **If any feature is behind login, provide stable reviewer credentials and simple access instructions in App access. Avoid flows that depend on your phone.

**Done when: **A reviewer can reach every important feature without contacting the owner.

| Permissions and sensitive access | NOT STARTED |

| --- | --- |

**Current: **No Android manifest exists, so requested permissions cannot be audited.

**Do this: **Request only permissions needed by the final feature set. Remove unused permissions and complete any declaration Play Console requires.

**Done when: **The release manifest has no unnecessary sensitive permissions and Console declarations match it.

## E. Store listing and final preflight

| App name and listing copy | PASS |

| --- | --- |

**Current: **A draft app name, short description, and full description exist. “Tailor Shop Manager” fits the current 30-character app-name limit.

**Do this: **Proofread the copy against the final app and remove any claim the release build cannot demonstrate.

**Done when: **The Main store listing contains approved text within Play limits and exactly matches available features.

| 512 × 512 app icon | PASS |

| --- | --- |

**Current: **A 512 × 512 PNG icon is present in the existing Play Store kit.

**Do this: **Check the final file in Play Console preview and confirm it has no unintended transparency, clipping, or tiny unreadable detail.

**Done when: **Play Console accepts the icon and the preview is clear at small size.

| Feature graphic | NOT STARTED |

| --- | --- |

**Current: **No 1024 × 500 feature graphic is present in the kit.

**Do this: **Create an accurate 1024 × 500 graphic using the approved app brand and no unsupported claims.

**Done when: **The graphic uploads successfully and remains readable in the listing preview.

| Phone screenshots | NOT STARTED |

| --- | --- |

**Current: **No final Android screenshots are present.

**Do this: **After packaging, capture at least two real phone screenshots from the release build; show core flows with safe test data.

**Done when: **The required screenshot slots are accepted and every image represents the actual release UI.

| Support and store contact details | NOT STARTED |

| --- | --- |

**Current: **The privacy-policy draft still lacks a real contact address and no verified support inbox is recorded.

**Do this: **Choose a monitored support email, add it to the policy, and complete the required store contact details.

**Done when: **The support email is verified, monitored, and visible where Google requires it.

| Listing and release preflight | NOT STARTED |

| --- | --- |

**Current: **There is no complete Play Console draft or processed release bundle.

**Do this: **Preview the listing, resolve all Dashboard and App content warnings, review countries/pricing, and run the pre-launch report on the same release candidate.

**Done when: **The Console shows no blocking task, the processed bundle is correct, and the final review checklist is signed off.

| TV, Wear OS, Automotive, and XR assets | NOT APPLICABLE |

| --- | --- |

**Current: **The planned product is a phone/tablet business app, not an app for these form factors.

**Do this: **Do not add those device types unless the product scope changes.

**Done when: **Not applicable while distribution remains phone/tablet only.

# Launch sequence

| Step | Gate | Action |

| --- | --- | --- |

| 1 | Freeze the release scope | Resolve the known progress-count bug and confirm the exact features, login model, backend services, and data deletion behavior. |

| 2 | Build the Android release | Create the Android project, set the permanent package name, target API 36+, configure versioning, and generate a signed AAB. |

| 3 | Test on Android | Run the full workflow on real phones, check errors and upgrades, and fix blocker issues before recruiting testers. |

| 4 | Complete account verification | Finish the identity, contact, device, and package-registration tasks shown in Play Console. |

| 5 | Finish privacy and listing | Publish the accurate privacy policy, submit Data safety and other App content forms, and upload final graphics and screenshots. |

| 6 | Run the closed test | If required for the account, keep at least 12 testers continuously opted in for at least 14 days and record the evidence below. |

| 7 | Apply for production access | Answer the production-readiness questions only after Play Console shows eligibility. |

| 8 | Final preflight and submit | Review the processed bundle, listing, policy forms, test feedback, and all Console warnings before the owner chooses to submit. |

## Definition of release-ready

- The exact AAB that will be released targets API level 36 or higher and is accepted by Play Console.

- Play App Signing is active; the upload key is protected and recoverable.

- The privacy policy, Data safety answers, account-deletion path, permissions, and actual data flows agree.

- The listing shows real release-build screenshots and makes no unsupported claim.

- All applicable account verification and closed-testing gates are complete.

- The known progress-count issue is fixed and the release candidate passes the core workflow on real Android devices.

# Closed-testing tracker

**Use only if Play Console requires the personal-account testing gate. **At least 12 testers must remain opted in continuously for at least 14 days. The safest operating target is 15 slots so one dropout does not immediately reduce the cohort below 12.

| App package |  | Closed track |  |

| --- | --- | --- | --- |

| Release version/code |  | Opt-in link |  |

| Shared window start |  | Earliest day 14 |  |

| Owner |  | Evidence folder |  |

## Tester roster and opt-in record

| Slot | Tester name | Google account email | Invite sent | Opt-in date | Consent / notes |

| --- | --- | --- | --- | --- | --- |

| 01 |  |  |  |  |  |

| 02 |  |  |  |  |  |

| 03 |  |  |  |  |  |

| 04 |  |  |  |  |  |

| 05 |  |  |  |  |  |

| 06 |  |  |  |  |  |

| 07 |  |  |  |  |  |

| 08 |  |  |  |  |  |

| 09 |  |  |  |  |  |

| 10 |  |  |  |  |  |

| 11 |  |  |  |  |  |

| 12 |  |  |  |  |  |

| 13 |  |  |  |  |  |

| 14 |  |  |  |  |  |

| 15 |  |  |  |  |  |

Privacy note: tester emails are personal information. Keep this document private and share only with people managing the test.

# Continuity summary

Update this from the Play Console tester count. “Days covered” counts only uninterrupted opted-in days for that tester in the current shared window.

| Slot | Continuous start | Last confirmed | Days covered | Still opted in? | Evidence reference | Qualifies? |

| --- | --- | --- | --- | --- | --- | --- |

| 01 |  |  |  |  |  |  |

| 02 |  |  |  |  |  |  |

| 03 |  |  |  |  |  |  |

| 04 |  |  |  |  |  |  |

| 05 |  |  |  |  |  |  |

| 06 |  |  |  |  |  |  |

| 07 |  |  |  |  |  |  |

| 08 |  |  |  |  |  |  |

| 09 |  |  |  |  |  |  |

| 10 |  |  |  |  |  |  |

| 11 |  |  |  |  |  |  |

| 12 |  |  |  |  |  |  |

| 13 |  |  |  |  |  |  |

| 14 |  |  |  |  |  |  |

| 15 |  |  |  |  |  |  |

## Cohort qualification check

| Qualifying testers | Required: 12+ | Continuous days | Required: 14+ |

| --- | --- | --- | --- |

| Lowest count in window | Must be 12+ | Eligible in Console? | Yes / No |

# 14-day continuity evidence grid

Write the calendar date above each day. For each tester, mark the cell only after Play Console confirms the tester is still opted in. Use the result column for “Qualified”, “Dropout”, or “Restarted”.

| Date |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Window |

| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

| Slot | D1 | D2 | D3 | D4 | D5 | D6 | D7 | D8 | D9 | D10 | D11 | D12 | D13 | D14 | Result |

| 01 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

| 02 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

| 03 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

| 04 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

| 05 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

| 06 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

| 07 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

| 08 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

| 09 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

| 10 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

| 11 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

| 12 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

| 13 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

| 14 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

| 15 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

Suggested evidence reference: save a dated Play Console screenshot or export each day and put its filename in the continuity summary. The tracker supports your records; Play Console determines whether the requirement is met.

## Dropout and restart log

| Date/time | Slot | Event | Cohort count | Action | New window start |

| --- | --- | --- | --- | --- | --- |

|  |  |  |  |  |  |

|  |  |  |  |  |  |

|  |  |  |  |  |  |

|  |  |  |  |  |  |

|  |  |  |  |  |  |

|  |  |  |  |  |  |

|  |  |  |  |  |  |

## Feedback and release changes

| Date | Tester slot | Area tested | Finding | Action / fix | Build |

| --- | --- | --- | --- | --- | --- |

|  |  |  |  |  |  |

|  |  |  |  |  |  |

|  |  |  |  |  |  |

|  |  |  |  |  |  |

|  |  |  |  |  |  |

|  |  |  |  |  |  |

|  |  |  |  |  |  |

|  |  |  |  |  |  |

# Official sources

Checked 5 October 2026. Google can change Play requirements; recheck these pages immediately before upload and follow any newer task shown in Play Console.

## Owner sign-off

| Release candidate version |  |

| --- | --- |

| Final audit date |  |

| Account owner |  |

| Decision | Ready / Not ready |

| Signature / approval |  |