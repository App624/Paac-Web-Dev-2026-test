# 📚 Documentation Index

## Start Here 👇

### 🚀 [QUICKSTART.md](QUICKSTART.md) — 5 Minute Setup
- What's new and working
- Setup checklist (Firebase in 5 steps)
- Testing guide (verify each feature)
- Quick troubleshooting

### 📖 [README_SETUP.md](README_SETUP.md) — Complete Setup Guide
- Full feature list
- Installation instructions
- Firebase configuration guide
- Security rules for Firestore & Storage
- Project structure
- Deployment options
- Environment variables

### ✨ [FEATURES_SUMMARY.md](FEATURES_SUMMARY.md) — What You Built
- Detailed feature breakdown
- Technical stack
- File structure explanation
- What's ready vs what needs setup
- All commits made

---

## For Developers 👨‍💻

### Source Code Layout

```
src/
├── config/
│   └── firebase.js                    Setup HERE ⭐
├── context/
│   └── AuthContext.jsx                Auth logic
├── pages/
│   ├── Home.jsx                       Landing
│   ├── Signup.jsx                     Register
│   ├── Login.jsx                      Sign in
│   ├── ControlCenter.jsx              Dashboard
│   ├── CommanderProfile.jsx           View profile
│   └── CommanderRegistry.jsx          Search users
├── components/
│   ├── Header.jsx                     Nav (updated)
│   ├── Hero.jsx, About.jsx, etc       Landing sections
├── App.jsx                            Router
├── main.jsx                           Entry point
└── index.css                          All styles + colors
```

### Key Files to Know

| File | Purpose | Edit for |
|------|---------|----------|
| `src/config/firebase.js` | Firebase setup | Add credentials ⭐ |
| `src/context/AuthContext.jsx` | Auth provider | Auth logic changes |
| `src/index.css` | All styles | Colors, spacing, glassmorphism |
| `src/App.jsx` | Routing | Add new routes |
| `src/pages/*` | Page components | UI/feature changes |

---

## Feature Guides 🎨

### Smooth Scroll
**Where**: `src/components/Header.jsx`
```javascript
const scrollToSection = (e, sectionId) => {
  const element = document.getElementById(sectionId)
  element.scrollIntoView({ behavior: 'smooth' })
}
```
Link to: `#about`, `#projects`, `#contact` sections

### Color Theme
**Where**: `src/index.css` (top of file)
```css
:root {
  --accent: #ff6b35;        /* Orange */
  --accent-light: #a23b72;  /* Purple */
  --accent-secondary: #f72585; /* Pink */
}
```
Change here to update all colors

### Glassmorphism
**Where**: Throughout `src/index.css`
```css
background: rgba(15, 23, 32, 0.6);
backdrop-filter: blur(20px);
border: 1px solid rgba(255, 107, 53, 0.15);
```
Applied to: auth pages, dashboard, cards, search results

### Authentication
**Where**: `src/context/AuthContext.jsx` + `src/pages/Signup.jsx` + `src/pages/Login.jsx`
- Uses Firebase Auth
- Protects `/dashboard` route
- Auto-redirects if not logged in

### Profile System
**Edit**: `src/pages/ControlCenter.jsx` (dashboard)
**View**: `src/pages/CommanderProfile.jsx` (view profile)
**Fields**: bio, experience, skills, photoURL, displayName, email
**Storage**: Firestore (`users` collection) + Firebase Storage

### User Search
**Where**: `src/pages/CommanderRegistry.jsx`
- Searches Firestore by display name
- Shows results in grid
- Click to view full profile

---

## Customization Guide 🎯

### Change Colors
Edit `src/index.css`:
```css
:root {
  --accent: #your-color;
  --accent-light: #your-color;
  --accent-secondary: #your-color;
}
```

### Add Background Image
In `src/index.css`, update `body` background:
```css
body {
  background: url('path/to/image.jpg');
  background-size: cover;
  background-attachment: fixed;
}
```

### Add New Routes
In `src/App.jsx`:
```javascript
<Route path="/new-page" element={<YourComponent />} />
```

### Add Profile Fields
1. Edit `ControlCenter.jsx` (add input)
2. Update Firestore save logic
3. Edit `CommanderProfile.jsx` (display)
4. Update Firestore security rules if needed

### Extend Navigation
Edit `src/components/Header.jsx`:
```javascript
<Link to="/new-page">New Link</Link>
```

---

## Firebase Setup Checklist ✅

- [ ] Create Firebase project
- [ ] Enable Email/Password auth
- [ ] Create Firestore database
- [ ] Enable Firebase Storage
- [ ] Copy credentials to `src/config/firebase.js`
- [ ] Set Firestore security rules
- [ ] Set Storage security rules
- [ ] Test signup → dashboard → profile save

---

## Testing Checklist ✅

- [ ] Smooth scroll works on nav links
- [ ] Sign up creates account
- [ ] Login redirects to dashboard
- [ ] Upload profile photo saves
- [ ] Edit bio/experience/skills saves
- [ ] Registry search finds users
- [ ] Clicking user card shows profile
- [ ] Glassmorphism effects visible
- [ ] Color theme is orange/purple/red
- [ ] Responsive on mobile

---

## Deployment Checklist ✅

- [ ] Build: `npm run build`
- [ ] Check `dist/` folder created
- [ ] Set Firebase production credentials
- [ ] Set security rules in Firebase
- [ ] Deploy to Firebase/Vercel/Netlify
- [ ] Test live domain

---

## Git Commands Reference 📝

```bash
# View history
git log --oneline              # All commits
git log -p src/file.jsx        # Changes to specific file
git show abc123                # View specific commit

# Undo changes
git checkout -- src/file.jsx   # Discard changes
git revert abc123              # Undo commit

# Branches (future)
git branch new-feature         # Create branch
git checkout new-feature       # Switch branch
git merge new-feature          # Merge into main
```

---

## Troubleshooting Quick Links 🔧

**Firebase Issues**
→ See "Firebase Setup" in README_SETUP.md

**Smooth Scroll Not Working**
→ Check section IDs in components (should have `id="about"`)

**Colors Not Changing**
→ Check `:root` variables in `src/index.css`

**Auth Not Working**
→ Verify Firebase credentials in `src/config/firebase.js`

**Photos Not Uploading**
→ Check Storage rules in Firebase console

**Search Not Finding Users**
→ Check Firestore data saved correctly
→ Verify search query in `CommanderRegistry.jsx`

---

## Performance Notes ⚡

- Vite HMR enabled (fast hot reload)
- Firebase lazy loads auth state
- Images should be optimized before upload
- Consider code-splitting for large bundles

---

## Security Notes 🔒

- Firebase credentials in `firebase.js` (move to env vars in production)
- Firestore rules enforce user ownership
- Storage rules prevent unauthorized uploads
- JWT tokens from Firebase Auth
- Passwords handled by Firebase (never stored locally)

---

## Next Steps 🚀

1. **Read QUICKSTART.md** (5 min)
2. **Add Firebase credentials** (5 min)
3. **Run `npm run dev`** (2 min)
4. **Test all features** (10 min)
5. **Deploy** (when ready)

---

## Questions? 🤔

- Check QUICKSTART.md for 5-min answers
- Check README_SETUP.md for detailed guides
- Check FEATURES_SUMMARY.md for technical breakdown
- Check source code files for implementation details

---

**Happy coding!** 🎉🚀

Last updated: 2026-02-04
Platform: Space Portfolio — Commander's Hub
