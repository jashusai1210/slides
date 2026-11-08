# SlideVault

SlideVault is a static Firebase Hosting site for browsing SQL course modules, viewing slides, and downloading module PDFs individually, separately in bulk, or together in a ZIP file. The admin dashboard at `/admin` manages module data in Cloud Firestore.

## Project files

- `public/index.html` — public module listing, slide viewer, and download tools
- `public/admin.html` — authenticated module administration
- `firebase.json` — Hosting and Firestore deployment configuration
- `firestore.rules` — public module reads and admin-only writes

## Deploy

Install the Firebase CLI, sign in, and deploy from the project root:

```sh
firebase login
firebase deploy --only hosting,firestore:rules --project slides10x
```

The Firebase web configuration is used by the browser app. Admin access is enforced by Firebase Authentication and the Firestore rules; never put an account password in source code.

See [README-ADMIN.txt](./README-ADMIN.txt) for Firebase setup and module management details.
