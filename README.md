# pcrai-assayspecs

Single-page assay specification console for PCR.ai with client-scoped test menus and optional Firebase-backed persistence.

## What Changed

- Assays are now grouped under clients.
- Each client stores its own test menu list in the left navigation.
- Local persistence still works in the browser.
- Optional Firebase Firestore sync is built into the app.
- Firebase Hosting scaffolding is included via [firebase.json](/Users/dougbonebrake/Sites/pcrai-assayspecs/firebase.json) and [.firebaserc](/Users/dougbonebrake/Sites/pcrai-assayspecs/.firebaserc).

## Firebase Setup

1. Create or open the Firebase project named `pcrai-assayspecs`.
2. Enable Firestore in that project.
3. Add a Web App in the Firebase console.
4. Copy the Web App config values.
5. Paste those values into [firebase-web-config.js](/Users/dougbonebrake/Sites/pcrai-assayspecs/firebase-web-config.js).
6. Reload the app. The config will be picked up automatically.
7. Optionally use the `Firebase` button in the header to review or override the values in browser storage.

The project name and account email alone are not enough to derive a valid browser config, so the app stores placeholders until you paste the actual Firebase web config.

## Notes

- Firestore rules must allow this app to read and write the selected document path.
- The current implementation is local-first. If Firebase is unavailable, the app continues using browser storage.
