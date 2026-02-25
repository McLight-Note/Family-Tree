# 🌳 Family Tree — Setup Guide

## What you get
- Beautiful login page
- Interactive family tree (drag nodes, zoom/pan)
- Add members with photos, relation, birth year, notes
- Only **you (admin)** can edit — others view only
- Create accounts for family members from your admin panel
- Data saved in Firebase (persists across sessions)

---

## Step 1 — Firebase Setup

1. Go to [https://console.firebase.google.com](https://console.firebase.google.com)
2. Click **"Add project"** → give it a name (e.g. `family-tree`)
3. Disable Google Analytics (optional) → **Create project**

### Enable Authentication
1. Go to **Build → Authentication → Get Started**
2. Click **Email/Password** → Enable → Save

### Create your admin account
1. In Authentication → **Add user**
2. Enter your email and a strong password
3. This is YOUR login — the admin

### Enable Firestore
1. Go to **Build → Firestore Database → Create database**
2. Choose **Start in production mode** → pick a region → Enable

### Get your config
1. Go to **Project Settings** (gear icon) → **General**
2. Scroll to "Your apps" → Click **Web** (`</>` icon)
3. Register app → copy the `firebaseConfig` object

---

## Step 2 — Update config in files

Open **both** `index.html` and `tree.html` and replace:

```js
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",           // ← paste yours
  authDomain: "YOUR_PROJECT...",    // ← paste yours
  projectId: "YOUR_PROJECT_ID",     // ← paste yours
  storageBucket: "YOUR_PROJECT...", // ← paste yours
  messagingSenderId: "...",         // ← paste yours
  appId: "..."                      // ← paste yours
};
```

Also replace in **tree.html**:
```js
const ADMIN_EMAIL = "REPLACE_WITH_YOUR_EMAIL@example.com";
```
With your actual email (the one you created in Firebase Auth).

Also update **firestore.rules** — replace the email there too.

---

## Step 3 — Deploy Firestore Rules

1. Install Firebase CLI: `npm install -g firebase-tools`
2. Login: `firebase login`
3. In the project folder: `firebase init firestore`
4. Deploy rules: `firebase deploy --only firestore:rules`

OR paste the rules manually in Firebase Console → Firestore → Rules tab.

---

## Step 4 — Deploy to Vercel

1. Push this folder to a **GitHub repo**
2. Go to [https://vercel.com](https://vercel.com) → New Project
3. Import your repo → Deploy (no build settings needed for plain HTML)
4. Your site is live! 🎉

---

## How to use

### As Admin
- Login with your credentials
- Click **"+ Add Member"** (bottom left) to add yourself first
- On each node click **"+ Add relative"** to add connected members
- Drag nodes to arrange the tree layout
- Click any node to view details or edit
- Use **"Manage Users"** to create accounts for family members

### As a viewer
- Login with the credentials you gave them
- They can see and explore the tree but cannot edit

---

## Tips
- Use a square photo URL for best avatars
- Start with yourself (relation: Me), then add parents, siblings, children
- The tree auto-saves positions when you drag nodes
