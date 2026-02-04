# Quick Start Guide 🚀

## What's New

Your portfolio now has a full **multi-user platform** with:

✅ **Smooth scroll navigation** on all buttons (About, Projects, Contact, Get in Touch)
✅ **New color theme**: Orange, purple, and red gradients
✅ **User authentication** (Sign up, Login, Logout)
✅ **Control Center Dashboard** - Edit your profile, upload photos, add skills
✅ **Commander Registry** - Search and discover other users
✅ **Glassmorphism UI** - Frosted glass effects with space background
✅ **Profile Photos** - Upload profile pictures that upload to Firebase Storage

## Quick Setup (5 minutes)

### 1. Get Firebase Credentials
- Go to https://firebase.google.com
- Create a new project (name: "space-portfolio")
- Go to Project Settings → Copy your config
- Enable Email/Password authentication (Build → Authentication → Sign-in method)

### 2. Update Firebase Config
Edit `src/config/firebase.js` and replace the placeholder keys with your Firebase credentials.

### 3. Run It
```bash
npm run dev
```
Visit `http://localhost:5173/`

## Testing the Features

### 1. Test Smooth Scroll
- Click "About" or "Get in Touch" in navigation → Watch it smoothly scroll ✨

### 2. Test Authentication
- Click "Sign Up" (top right)
- Create a new account
- You're redirected to Dashboard

### 3. Test Profile Editor (Dashboard)
- Upload a profile photo
- Add bio, experience, skills
- Click "Save Profile"
- Data saves to Firebase Firestore

### 4. Test Profile Search
- Click "Registry" in navigation
- Search for any user by name
- Click their card to view their full profile

### 5. Test Glassmorphism
- Notice the frosted glass effect on all cards
- See the smooth blur background
- Inspect the orange/purple/red gradient accents

## File Structure Overview

```
src/
├── config/firebase.js          ← Add your Firebase keys here
├── context/AuthContext.jsx     ← Auth logic
├── pages/
│   ├── Home.jsx               ← Landing page
│   ├── Signup.jsx             ← Register
│   ├── Login.jsx              ← Login
│   ├── ControlCenter.jsx      ← Profile editor (PROTECTED)
│   ├── CommanderProfile.jsx   ← View user profile
│   └── CommanderRegistry.jsx  ← Search users
└── index.css                  ← All styles + colors + glassmorphism
```

## Colors & Theme

**Current theme** (in `src/index.css`):
- **Primary Accent** (Orange): `#ff6b35`
- **Secondary** (Purple): `#a23b72`
- **Tertiary** (Pink/Red): `#f72585`

To change colors, update the `:root` variables at the top of `index.css`.

## Adding Backgrounds

You have two options:

**Option A: Add background to entire site**
- Edit `body` styling in `src/index.css`
- Add `background-image: url('...')`

**Option B: Add user profile backgrounds**
- Update `ControlCenter.jsx` to accept a background image upload
- Store URL in Firestore
- Display on user profiles in `CommanderProfile.jsx`

## Next Steps

1. ✅ Add your Firebase credentials
2. ✅ Test sign up → creates account
3. ✅ Test dashboard → upload profile pic
4. ✅ Search for users → view their profiles
5. 🎨 Add backgrounds (as described above)
6. 📱 Deploy to Firebase Hosting (see README_SETUP.md)

## Troubleshooting

**"Cannot find module 'firebase'"**
```bash
npm install firebase
```

**"Firebase config missing"**
- Make sure you updated `src/config/firebase.js` with real keys

**"Smooth scroll not working"**
- Make sure sections have `id="about"`, `id="projects"`, `id="contact"`
- Already in place in current code ✅

**"Photos not uploading"**
- Check Firebase Storage rules are set correctly
- Enable Storage in Firebase console

## Build & Deploy

```bash
# Production build
npm run build

# Deploy to Firebase Hosting
firebase deploy
```

## Questions?

Check `README_SETUP.md` for detailed docs on:
- Firebase setup
- Database rules
- Advanced customization
- Deployment options

---

**Your platform is live!** 🎉
- Local: `http://localhost:5173/`
- Commands: `npm run dev` (dev), `npm run build` (prod)

Enjoy! 🚀
