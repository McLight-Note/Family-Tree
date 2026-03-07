# 🌳 Family Tree v3 — Setup Guide

## What's new in v3
- **Connection strings** — draw parent→child links between any two people
- **Couple links** — special dashed pink line with a ❤️ floating heart connecting partners
- **Heart badges** — coupled people get a pulsing ❤️ badge on their card + glowing border
- **Upgraded login page** — animated starfield, floating orbs, smooth animations
- **Better cards** — gender-colored borders, photo avatars, polished dark theme
- **Mode banners** — clear on-screen instructions when connecting people
- **Temp draw line** — see a preview line as you drag to connect
- **All v2 features kept** — drag, zoom/pan, Firebase sync, admin/viewer roles

---

## Quick Setup (same as v2)

### Step 1 — Firebase
1. Go to https://console.firebase.google.com
2. Create a project → enable **Email/Password Auth** → enable **Firestore**
3. Add yourself as a user in Authentication

### Step 2 — Paste your config
Open **both** `index.html` and `tree.html` and replace:
```js
const firebaseConfig = {
  apiKey:            "YOUR_API_KEY",         // ← paste yours
  authDomain:        "YOUR_PROJECT...",       // ← paste yours
  projectId:         "YOUR_PROJECT_ID",       // ← paste yours
  storageBucket:     "YOUR_PROJECT...",       // ← paste yours
  messagingSenderId: "...",                   // ← paste yours
  appId:             "..."                    // ← paste yours
};
```

Also replace in **tree.html** and **firestore.rules**:
```js
const ADMIN_EMAIL = "REPLACE_WITH_YOUR_EMAIL@example.com";
```

### Step 3 — Deploy Firestore rules
```bash
npm install -g firebase-tools
firebase login
firebase init firestore
firebase deploy --only firestore:rules
```
Or paste the rules manually in Firebase Console → Firestore → Rules.

### Step 4 — Deploy to Vercel
1. Push this folder to GitHub
2. Go to vercel.com → New Project → Import repo
3. Set **Root Directory** to `family-tree-v3` (or whatever you named this folder)
4. Deploy — done! 🎉

---

## How to use connections

### Linking parent → child
1. Click **🔗 Child Link** in the top bar
2. Click the **parent's card**
3. Click the **child's card**
→ A purple line with an arrow appears

### Linking a couple
1. Click **💑 Couple Link** in the top bar
2. Click **first partner's card**
3. Click **second partner's card**
→ A dashed pink line with ❤ appears; both cards get heart badges

### Removing a link
1. Click **✂ Remove Link**
2. Click any line on the canvas
→ That connection is deleted

Press **Esc** at any time to cancel the current action.
