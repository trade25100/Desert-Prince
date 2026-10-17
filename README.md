# Desert Prince Coordinates — GitHub Pages + Firebase

64 fixed coordinates for **World → United Arab Emirates**, with 31 initially found. The page works locally even when Firebase is not configured.

## Deploy

1. Upload `index.html`, `style.css`, `app.js`, and `firebase-config.js` to the root of your GitHub repository.
2. GitHub → Settings → Pages → Deploy from a branch → `main` → `/ (root)` → Save.
3. For shared edits: create a Firebase project, register a **Web app**, and paste its web configuration into `firebase-config.js`.
4. Firebase Console → Build → Authentication → Sign-in method → enable **Anonymous**.
5. Firebase Console → Build → Firestore Database → create database; Rules → paste the contents of `firestore.rules` and publish.
6. Reload GitHub Pages. The connection badge should say **Live sync connected**.

**Important:** The Firebase web config is public by design; never put admin/service-account keys in this repository. Anonymous sign-in allows *any visitor* to change coordinate statuses and dates. The provided rules validate shape and limit document paths but do not prevent vandalism. For a trusted editor-only tracker, use restricted authentication/authorization and consider Firebase App Check.

Changes are stored in browser localStorage when offline. Existing offline changes are **not automatically merged** into Firestore on reconnect, to avoid overwriting shared data. The first shared edit creates that coordinate's Firestore document; other coordinates use the built-in initial statuses until edited remotely.
