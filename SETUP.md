# Workspace Manager — Setup

1. In Firebase Console, open project `a1business-55e5a` and create a **Cloud Firestore** database.
2. Under **Authentication → Sign-in method**, enable **Google**. Confirm `muzellamedia@gmail.com` is an available Google account.
3. Under **Authentication → Settings → Authorized domains**, add the domain used to open the page. For local use, add `localhost`.
4. In **Firestore → Rules**, paste the contents of [`firestore.rules`](firestore.rules) and publish them. The rules permit only the verified Google account `muzellamedia@gmail.com`, and only that account's own user ID path.
5. Serve `workspace-manager.html` over HTTP (Google sign-in and Firebase module imports do not work reliably from `file://`). For example, from this `outputs` folder run `python -m http.server 8000`, then open `http://localhost:8000/workspace-manager.html`.
6. Click **Login with Google** and select `muzellamedia@gmail.com`. Other accounts are rejected by both the page and Firestore Rules.

The Firebase web config is embedded in the HTML. Firebase web API keys identify the project; Firebase Authentication and Firestore Rules control data access. Keep the rules enabled and do not replace them with public read/write rules. If data was saved under a different Firebase user ID (for example, Anonymous Auth or a separate Email/Password account), it will not appear under the Google sign-in ID.
