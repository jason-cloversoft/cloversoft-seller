# Cloversoft All-in-one by Jason

E-commerce stock and order portal. Static site (`index.html`) backed by Cloud Firestore.

## Deploy to GitHub Pages
1. Push this folder to a GitHub repository.
2. Settings → Pages → Source: `Deploy from a branch`, branch `main`, folder `/ (root)`.
3. Open the Pages URL.

## Firebase setup (once)
1. **Firestore:** Build → Firestore Database → Create database (region `asia-southeast1`).
2. **Authentication:** Build → Authentication → Sign-in method → enable **Anonymous**.
3. **Rules:** deploy `firestore.rules` (Firestore → Rules, or `firebase deploy --only firestore:rules`).
4. **Authorized domains:** Authentication → Settings → Authorized domains → add your `github.io` domain.
5. **API key:** Google Cloud Console → Credentials → restrict the browser key to your domain.
6. **Create the Key Account first.** Open the site once after deploying. If no Key Account exists, the first-time setup page appears. Do this before you share the link.

## Security notes (read before real use)
- Passwords are stored as salted PBKDF2-SHA256 hashes, never in plain text.
- Firebase keys in `index.html` are public by design. Security comes from the Firestore rules and Authentication.
- **Known limitation:** the app signs in anonymously, so anyone who opens the site gets database access under the rules. Passwords are checked in the browser. For a fully private deployment, move to per-user Firebase Authentication with rules tied to each user.
- Password reset is handled by the Key Account administrator. Nothing is emailed.
