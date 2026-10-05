# Deploy Guide — Tailor Shop Manager to Google Play

This repo contains everything a developer needs to turn the Tailor Shop Manager web app into a Play Store release.

## What's in this repo

| Path | What it is |
|------|------------|
| `www/index.html` | The app itself (single-file web build) — this is what gets wrapped |
| `capacitor.config.json` | Capacitor config (app id: `com.tailorshop.manager`) |
| `package.json` | Capacitor dependencies |
| `LAUNCH_PACK.md` | Full pre-submission audit + 14-day testing tracker |
| `README.md` | Project overview |

> **Important:** `www/index.html` is the UI prototype with demo data (in-memory). Before release, the developer must connect a real backend (e.g. Firebase Firestore) so tailor shops keep their data permanently. See "Backend" below.

## Developer steps

### 1. Prerequisites
- Node.js 18+
- Android Studio (with Android SDK 36) + Java 17
- A Google Play developer account ($25 one-time) — the app owner creates this

### 2. Set up the Android project
```bash
npm install
npx cap add android
npx cap sync
npx cap open android
```

### 3. Backend (required before release)
The bundled `www/index.html` uses demo data. Wire up Firebase:
1. Create a Firebase project, add an Android app with package `com.tailorshop.manager`
2. Add Firestore collections: `customers`, `measurements`, `progress_logs`
3. Replace the demo data layer in `www/index.html` with Firestore reads/writes
4. Set Firestore security rules so each shop only sees its own data

### 4. Configure the release build
- In `android/app/build.gradle`: set `targetSdk 36`, `versionCode 1`, `versionName "1.0.0"`
- Generate an upload keystore; **enable Play App Signing** in Play Console (recommended — Google manages the final signing key)

### 5. Build the App Bundle
In Android Studio: **Build → Generate Signed Bundle / APK → Android App Bundle**. This produces the `.aab` file.

### 6. Play Console
1. Create the app, fill the store listing (copy from the submission kit), upload the 512×512 icon, feature graphic, and screenshots
2. Complete **App content**: data safety form, privacy policy URL, content rating, target audience
3. Upload the `.aab` to a **closed testing** track
4. Recruit **12 testers**, keep them opted in for **14 continuous days** (log them in `LAUNCH_PACK.md`)
5. Apply for production access, then roll out

## Checklist status
See `LAUNCH_PACK.md` for the full 33-item audit. As of October 2026: app and docs ready; Android packaging, developer account, and closed testing still to do.
