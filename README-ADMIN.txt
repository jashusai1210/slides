SLIDEVAULT MODULE DASHBOARD SETUP

PACKAGE LAYOUT
- public/index.html: public website; no login required
- public/admin.html: admin dashboard at /admin
- firebase.json: Hosting + Firestore rules config
- firestore.rules: public module data readable; writes restricted to admin email

SECURITY: Do not put your password into source code. The password you shared is not embedded in these files. Create/reset the admin account through Firebase Authentication.

ONE-TIME SETUP
1. In Firebase Console for project slides10x, open Project settings > General > Your apps. Register a Web app if needed and copy its config.
2. Replace the placeholder firebaseConfig in BOTH public/index.html and public/admin.html: apiKey, authDomain, projectId, storageBucket, messagingSenderId, appId.
3. Firebase Console > Authentication > Sign-in method: enable Email/Password. Create the admin user using the authorized admin email and set the password in Firebase Console.
4. Firebase Console > Firestore Database: create the database if needed. Choose the database location carefully; it cannot be changed after creation.
5. Put public/index.html and public/admin.html inside your existing project's public folder. Keep firebase.json and firestore.rules in the project root.
6. From the project root run: firebase deploy --only hosting,firestore:rules
7. Public site: https://slides10x.web.app/ ; admin dashboard: https://slides10x.web.app/admin

HOW MODULE MANAGEMENT WORKS
When Firebase is connected, documents in the Firestore collection "modules" are the public module list. Deleting a document removes that module from the website; hiding a built-in module in /admin marks it hidden. An empty collection shows no modules. The eight built-in modules are used only if Firebase is not configured or cannot be reached. Add/edit modules from /admin; URLs should end in slide-1.png, and later slides are expected to follow the slide-2.png, slide-3.png naming pattern.

ADMIN ROUTE NOTE
Firebase Hosting's default domain uses /admin as a path. admin.web.app is a separate domain and is not automatically created by adding an admin route. The admin page is not linked from the public homepage, but authentication and Firestore rules provide the security.
