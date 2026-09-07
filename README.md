# Gatherly - Fixed Google Login

## Files
- `index.html` - public event discovery and booking page
- `organizer.html` - organizer dashboard with Google login
- `style.css` - shared styling
- `firebase-config.js` - your Firebase web configuration
- `firestore.rules` - recommended Firestore rules

## Firebase setup required
1. Open Firebase Console for project `evently-43c73`.
2. Go to **Authentication → Sign-in method**.
3. Enable **Google** as a provider and save.
4. Go to **Authentication → Settings → Authorized domains**.
5. Add the exact domain where this site will run.
   - For GitHub Pages, add your GitHub Pages hostname, for example `username.github.io`.
   - For local testing, `localhost` is normally already available.
6. Go to **Firestore Database → Rules** and paste the contents of `firestore.rules`, then publish.
7. Make sure Firestore Database has been created.

## Local testing
Do not open `index.html` or `organizer.html` by double-clicking them with a `file://` URL. Use a local web server.

If Python is installed:
`python -m http.server 5500`

Then open:
`http://localhost:5500/organizer.html`

## GitHub Pages
1. Create a GitHub repository.
2. Upload all files from this folder to the repository root.
3. Enable GitHub Pages from the repository settings.
4. Add the resulting `*.github.io` domain to Firebase Authentication → Authorized domains.
5. Open `/organizer.html` and test Google login.

## Important
The Firebase web API key in `firebase-config.js` is not a password. Firebase access is controlled by Authentication and Firestore Security Rules. Never put service-account private keys in this website.
