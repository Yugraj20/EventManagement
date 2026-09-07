# ✦ Gatherly

**Discover events. Connect with people. Create memorable moments.**

Gatherly is a modern, responsive event discovery and booking web application. Users can browse upcoming events, search for events, and reserve their spots. Organizers can sign in with Google and publish new events through a dedicated organizer dashboard.

Built with **HTML, CSS, Vanilla JavaScript, and Firebase**.

---

## ✨ Features

### 🎟️ Event Discovery

* Browse upcoming events
* Event cards with images, dates, titles, and descriptions
* Search events instantly
* Responsive layout for desktop and mobile
* Automatic event count

### 📅 Event Booking

* Book an event directly from the event card
* Enter your name and email
* Booking information is stored in Firebase Firestore
* Confirmation message after successful booking

### 👤 Organizer Panel

* Google Sign-In authentication
* Organizer dashboard
* Create and publish events
* Add event title, date, description, and image URL
* Automatically associate events with the signed-in organizer
* Logout functionality

### 🌓 Theme Support

* Light mode
* Dark mode
* Automatically detects the system color preference
* Saves the selected theme using local storage

### 📱 Responsive Design

* Mobile-friendly interface
* Responsive event grid
* Mobile navigation adjustments
* Accessible form controls and status messages

---

## 🛠️ Technologies Used

* **HTML5**
* **CSS3**
* **Vanilla JavaScript**
* **Firebase v10**

  * Firebase Authentication
  * Google Authentication
  * Cloud Firestore
* **GitHub Pages** for static hosting

The application imports Firebase v10.4.0 directly from Google's CDN.

---

## 📁 Project Structure

```text
Gatherly/
│
├── index.html
├── organizer.html
├── style.css
├── firebase-config.js
├── firestore.rules
└── README.md
```

### File Description

| File                 | Purpose                               |
| -------------------- | ------------------------------------- |
| `index.html`         | Main event discovery and booking page |
| `organizer.html`     | Organizer dashboard and Google login  |
| `style.css`          | Shared application styling            |
| `firebase-config.js` | Firebase project configuration        |
| `firestore.rules`    | Firestore security rules              |
| `README.md`          | Project documentation                 |

The organizer page provides Google authentication and event publishing functionality.

---

# 🔥 Firebase Setup

Before running the project, you need to configure Firebase.

### 1. Create or Open Firebase Project

Open the Firebase Console and create a Firebase project.

Use your Firebase project for the application configuration.

### 2. Enable Google Authentication

Go to:

```text
Firebase Console
→ Authentication
→ Sign-in method
→ Google
```

Enable the **Google** provider.

Gatherly uses Firebase Authentication with Google Sign-In for organizer access.

### 3. Enable Firestore

Go to:

```text
Firebase Console
→ Firestore Database
```

Create a Firestore database.

The application uses two main collections:

```text
events
bookings
```

Events are loaded from the `events` collection, while bookings are stored in the `bookings` collection.

### 4. Configure Authorized Domains

Go to:

```text
Firebase Console
→ Authentication
→ Settings
→ Authorized domains
```

Add the domain where your website will run.

For GitHub Pages, this will normally look like:

```text
yourusername.github.io
```

The organizer page specifically handles Firebase's `auth/unauthorized-domain` error when the current website domain has not been authorized.

---

# 🔐 Firestore Rules

Open:

```text
Firebase Console
→ Firestore Database
→ Rules
```

Copy the contents of:

```text
firestore.rules
```

into the Firebase Rules editor and publish the rules.

**Important:** Do not use unrestricted Firestore rules such as:

```text
allow read, write: if true;
```

Use appropriate security rules to protect your database.

---

# 💻 Running Locally

Do **not** open the HTML files directly using:

```text
file://
```

Use a local web server instead.

### Using Python

If Python is installed:

```bash
python -m http.server 5500
```

Then open:

```text
http://localhost:5500/
```

For the organizer dashboard:

```text
http://localhost:5500/organizer.html
```

---

# 🚀 Deploying to GitHub Pages

### Step 1: Create Repository

Create a new GitHub repository.

Example:

```text
gatherly
```

### Step 2: Upload Files

Upload all project files to the **root** of the repository:

```text
index.html
organizer.html
style.css
firebase-config.js
firestore.rules
README.md
```

### Step 3: Enable GitHub Pages

Go to:

```text
Repository
→ Settings
→ Pages
```

Under **Build and deployment**, select:

```text
Source: Deploy from a branch
Branch: main
Folder: / (root)
```

Save the settings.

### Step 4: Configure Firebase

After GitHub Pages gives you your website address, add the GitHub Pages domain to:

```text
Firebase Console
→ Authentication
→ Settings
→ Authorized domains
```

### Step 5: Test

Open:

```text
https://yourusername.github.io/gatherly/
```

Then test:

* Event loading
* Event search
* Booking
* Google Sign-In
* Event publishing
* Dark/light mode

---

# 📊 Firestore Data Structure

## Events

Events are stored in:

```text
events
```

Example document:

```json
{
  "title": "Creative Morning Meetup",
  "date": "2026-09-20",
  "description": "A morning meetup for creative people.",
  "imageUrl": "https://example.com/event.jpg",
  "organizerUid": "firebase-user-id",
  "organizerEmail": "organizer@example.com",
  "createdAt": "server timestamp"
}
```

The organizer dashboard saves the organizer's Firebase UID and email along with each event.

## Bookings

Bookings are stored in:

```text
bookings
```

Example document:

```json
{
  "eventId": "event-document-id",
  "name": "John Doe",
  "email": "john@example.com",
  "createdAt": "server timestamp"
}
```

---

# 🎨 Design

Gatherly uses a clean, modern interface with:

* Soft rounded cards
* Purple primary accent
* Responsive event grid
* Sticky navigation
* Modal booking form
* Light and dark themes
* Mobile responsive layouts

## The styling defines separate light and dark theme variables and responsive layouts for smaller screens.

# 🔒 Security Notes

The Firebase configuration contains a **Firebase web API key**. This key is intended to be used by client-side Firebase applications and is not a password by itself.

However:

* Never expose Firebase service-account private keys.
* Never put private credentials in frontend files.
* Always configure Firestore Security Rules.
* Restrict authentication domains to trusted domains.
* Review database permissions before deploying publicly.

Your current Firebase configuration is stored in `firebase-config.js`.

---

# 🐛 Troubleshooting

### Google Login Does Not Work

Check:

```text
Firebase Console
→ Authentication
→ Sign-in method
→ Google
```

Make sure Google authentication is enabled.

Then check:

```text
Authentication
→ Settings
→ Authorized domains
```

and make sure your website domain is listed.

---

### Events Are Not Loading

Check:

* Firestore Database has been created
* `events` collection exists
* Firestore rules allow the required read operation
* Firebase configuration is correct
* Browser console for Firebase errors

---

### Bookings Are Not Saving

Check:

* Firestore is enabled
* `bookings` writes are allowed by your Firestore rules
* Browser console for errors
* The user has filled in all required booking fields

---

# 🌐 Deployment

Gatherly is designed as a **static frontend application**, so it can be deployed using services such as:

* GitHub Pages
* Firebase Hosting
* Netlify
* Vercel

No traditional backend server is required for the current implementation because Firebase provides authentication and database functionality.

---

# 📌 Future Improvements

Potential future features include:

* Organizer event management
* Edit and delete events
* Organizer booking dashboard
* Event capacity limits
* Event categories
* Location and maps
* User accounts
* Email confirmations
* Event favorites
* QR-code tickets
* Admin dashboard
* Event analytics
* Pagination
* Image uploads using Firebase Storage

---

# 📄 License

This project is available for educational and personal use.

---

## ⭐ Acknowledgements

Built using:

**HTML • CSS • JavaScript • Firebase**

Made with ✦ for better events and better connections.

---

**Gatherly | Events worth getting together for.**
