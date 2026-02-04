# Space Portfolio — Commander's Hub 🚀

A modern, full-featured portfolio platform with user authentication, profiles, and discovery system. Built with React, Vite, and Firebase with a beautiful space-themed glassmorphism UI.

## Features

✨ **Authentication**
- Secure Sign-Up and Login with Firebase Authentication (JWT-based)
- Control Center dashboard for authenticated users
- Protected routes and profile management

👤 **Commander Profiles**
- Create and edit personal profiles with:
  - Profile picture upload to Firebase Storage
  - Bio and professional experience sections
  - Skills listing with tag display
- View other users' profiles by searching
- Profile persistence in Firestore database

🔍 **Commander Registry**
- Search for other users by display name
- Browse and discover community members
- View full profiles with all user information

🎨 **UI/UX**
- Glassmorphism effects (frosted glass) over animated space background
- Orange, purple, and red color theme
- Smooth scroll animations for navigation
- Responsive design for all screen sizes
- Dark theme with subtle star field animation

## Tech Stack

- **Frontend**: React 18.2.0, Vite 5.1.0
- **Routing**: React Router DOM 6.20.0
- **Backend/Auth**: Firebase 10.7.0
  - Authentication (Email/Password)
  - Firestore (Database)
  - Storage (Profile Photos)
- **Build**: Vite with HMR (Hot Module Replacement)

## Setup Instructions

### Prerequisites
- Node.js (v16+)
- npm or yarn
- Firebase account

### Installation

1. **Clone and install dependencies**
   ```bash
   npm install
   ```

2. **Configure Firebase**
   - Create a Firebase project at https://firebase.google.com
   - Get your Firebase config credentials
   - Update `src/config/firebase.js` with your config:
     ```javascript
     const firebaseConfig = {
       apiKey: "YOUR_API_KEY",
       authDomain: "YOUR_AUTH_DOMAIN",
       projectId: "YOUR_PROJECT_ID",
       storageBucket: "YOUR_STORAGE_BUCKET",
       messagingSenderId: "YOUR_MESSAGING_ID",
       appId: "YOUR_APP_ID"
     }
     ```

3. **Setup Firebase Rules** (Firestore & Storage)
   - Enable Email/Password authentication in Firebase Console
   - Set up Firestore security rules:
     ```
     rules_version = '2';
     service cloud.firestore {
       match /databases/{database}/documents {
         match /users/{uid} {
           allow read: if true;
           allow write: if request.auth.uid == uid;
         }
       }
     }
     ```
   - Set up Storage rules:
     ```
     rules_version = '2';
     service firebase.storage {
       match /b/{bucket}/o {
         match /profile-photos/{uid} {
           allow read: if true;
           allow write: if request.auth.uid == uid;
         }
       }
     }
     ```

### Running the App

**Development**
```bash
npm run dev
```
Opens at `http://localhost:5173/`

**Production Build**
```bash
npm run build
```

**Preview Production Build**
```bash
npm run preview
```

## Project Structure

```
src/
├── config/
│   └── firebase.js          # Firebase configuration
├── context/
│   └── AuthContext.jsx      # Auth provider & hooks
├── pages/
│   ├── Home.jsx             # Landing page
│   ├── Signup.jsx           # Registration page
│   ├── Login.jsx            # Login page
│   ├── ControlCenter.jsx    # User dashboard
│   ├── CommanderProfile.jsx # Profile view page
│   └── CommanderRegistry.jsx # User search & discovery
├── components/
│   ├── Header.jsx           # Navigation header
│   ├── Hero.jsx             # Hero section
│   ├── About.jsx            # About section
│   ├── Projects.jsx         # Projects showcase
│   ├── Contact.jsx          # Contact form
│   └── Footer.jsx           # Footer
├── App.jsx                  # Main app with routing
├── main.jsx                 # React DOM render
└── index.css                # Global styles
```

## Key Routes

- `/` — Landing page with portfolio showcase
- `/signup` — Create new account
- `/login` — Login page
- `/dashboard` — Control Center (profile editor, protected route)
- `/registry` — Commander Registry (search users)
- `/commander/:uid` — View user profile

## Features Breakdown

### Smooth Scroll Navigation
- Click navigation links to smoothly scroll to sections
- Uses native `scrollIntoView` with smooth behavior
- Works with `#about`, `#projects`, `#contact` sections

### Profile System
- Upload profile photos directly to Firebase Storage
- Save work experience, skills, and bio
- Public profiles visible to all users
- Search profiles by display name

### Glassmorphism Design
- Frosted glass effect with `backdrop-filter: blur()`
- Semi-transparent backgrounds with RGBA colors
- Space-themed animated starfield background
- Orange/purple/red gradient accents

## Customization

### Change Colors
Edit CSS variables in `src/index.css`:
```css
:root{
  --bg:#05060a;
  --panel:#0f1720;
  --muted:#98a0b3;
  --accent:#ff6b35;        /* Orange */
  --accent-light:#a23b72;  /* Purple */
  --accent-secondary:#f72585; /* Red */
}
```

### Add Background Images
Update body background in `index.css` or modify Hero component to support custom backgrounds per profile.

### Extend Profile Fields
Edit `ControlCenter.jsx` and `CommanderProfile.jsx` to add more fields. Update Firestore document structure accordingly.

## Deployment

### Firebase Hosting (Recommended)
```bash
npm run build
npm install -g firebase-tools
firebase init hosting
firebase deploy
```

### Other Platforms
- Vercel: `npm run build` → Deploy `dist/` folder
- Netlify: `npm run build` → Deploy `dist/` folder

## Environment Variables

Create `.env.local` in the root directory (optional for local Firebase):
```
VITE_FIREBASE_API_KEY=your_key
VITE_FIREBASE_AUTH_DOMAIN=your_domain
VITE_FIREBASE_PROJECT_ID=your_project_id
VITE_FIREBASE_STORAGE_BUCKET=your_bucket
VITE_FIREBASE_MESSAGING_SENDER_ID=your_id
VITE_FIREBASE_APP_ID=your_app_id
```

Then update `firebase.js` to use these:
```javascript
const firebaseConfig = {
  apiKey: import.meta.env.VITE_FIREBASE_API_KEY,
  // ... etc
}
```

## Future Enhancements

- [ ] Social features (follow, message, comments)
- [ ] Rich text editor for bio/experience
- [ ] Advanced search filters
- [ ] Notifications system
- [ ] Dark/Light theme toggle
- [ ] Analytics & activity tracking
- [ ] Export profile as PDF
- [ ] Integrations (GitHub, LinkedIn, etc.)

## License

MIT

## Support

For issues or questions, create an issue in the repository or check Firebase documentation.

---

**Made with ❤️ for Commanders everywhere** 🌌
