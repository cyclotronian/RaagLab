# RaagLab v7 — mobile, PIN unlock, private link sync

## Setup
1. Create free Firebase project at https://console.firebase.google.com (Spark plan).
2. Under **Firestore Database**, create a database in production mode. Paste `firestore.rules` into the Rules editor and Publish. **No Firebase Authentication provider is needed.**
3. Under Project Settings > Your apps, register a Web app and copy config into `firebase-config.js`.
4. Create a public GitHub repository and upload all website files. Under Settings > Pages, Deploy from `main` / `(root)`.
5. Open the deployed URL. Choose a 4-digit PIN and press **Create private sync space**.
6. Click **Link iPhone / laptop**, copy the private setup URL and open it on the other device. Choose a PIN for that device. Progress will sync.
7. On iPhone, in Safari use Share > Add to Home Screen.

## Security / limitations
- A **4-digit PIN is only a local convenience lock**. It is **not cloud authentication**. The random 192-bit sync key embedded in the pairing link is the cloud access credential. Anyone with that secret URL can read/change progress. Do not share or publish the link.
- Progress is not sensitive financial/medical data. This lightweight capability-based design is *not* suitable for private/sensitive data. For stronger access control use Firebase Auth.
- PIN is locally stored and is not encrypted; clearing browser storage resets the local lock. Sharing or reusing a device can expose locally cached progress.
- Cloud progress uses a whole-document update, so simultaneous answers on two devices can occasionally overwrite one another. Use one device at a time for training.
- Old v5 local progress is browser-origin-specific; you may export/import progress using the supplied buttons.
- Gayan samay time windows are broad approximations for visual orientation; the sheet's exact labels remain shown.
- Firestore read/write quotas and GitHub Pages restrictions apply; hosting typically fits free tiers for personal use.
