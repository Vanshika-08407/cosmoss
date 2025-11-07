# ✅ Kutumbh Setup Checklist

## Quick Setup (Choose One)

### Option A: Full Setup with Firebase (15 minutes)

Follow this for a fully functional app with data persistence.

### Option B: Quick Demo Mode (2 minutes)

Just want to see the UI? Start the app immediately!

---

## 📋 **OPTION A: Complete Setup Checklist**

### Before You Start

- [ ] You have a Google account
- [ ] You're in the `kutumbh-app` folder
- [ ] You ran `npm install`

### Step 1: Firebase Console (10 minutes)

Open the guide: **`FIREBASE_SETUP_INTERACTIVE.md`**

- [ ] **1.1** Created Firebase project named "Kutumbh"
- [ ] **1.2** Copied Firebase configuration keys
- [ ] **1.3** Enabled Email/Password authentication
- [ ] **1.4** Created Firestore database in test mode
- [ ] **1.5** Generated Cloud Messaging key (optional)
- [ ] **1.6** Enabled Storage

### Step 2: Update Configuration (2 minutes)

- [ ] **2.1** Opened `kutumbh-app/src/config/firebase.js`
- [ ] **2.2** Replaced `apiKey` with your key
- [ ] **2.3** Replaced `authDomain` with your domain
- [ ] **2.4** Replaced `projectId` with your project ID
- [ ] **2.5** Replaced `storageBucket` with your bucket
- [ ] **2.6** Replaced `messagingSenderId` with your ID
- [ ] **2.7** Replaced `appId` with your app ID
- [ ] **2.8** Saved the file (Ctrl + S)

### Step 3: Run the App (1 minute)

```bash
npm run dev
```

- [ ] **3.1** App opened at http://localhost:3000
- [ ] **3.2** No Firebase errors in console
- [ ] **3.3** Can see the landing page

### Step 4: Test Basic Features (2 minutes)

- [ ] **4.1** Clicked "Get Started" button
- [ ] **4.2** Created an account (Register page)
- [ ] **4.3** Logged in successfully
- [ ] **4.4** Can see the Dashboard

### Step 5: Security Rules (Optional, 3 minutes)

- [ ] **5.1** Added Firestore security rules (see FIREBASE_SETUP_INTERACTIVE.md Step 8)
- [ ] **5.2** Added Storage security rules

---

## 🚀 **OPTION B: Quick Demo Mode**

Want to test the UI without Firebase setup?

### Step 1: Run the App

```bash
cd kutumbh-app
npm install
npm run dev
```

### Step 2: Open in Browser

Visit: http://localhost:3000

### ⚠️ Demo Mode Limitations:

- ❌ Can't create accounts
- ❌ Can't save data
- ✅ Can see all UI components
- ✅ Can navigate between pages
- ✅ Perfect for testing design

### To Enable Full Features:

Follow **Option A** above to set up Firebase.

---

## 🆘 **Stuck? Common Issues**

### Issue: "Firebase: Error (auth/invalid-api-key)"

**Solution:**

- Double-check you copied the ENTIRE API key
- Make sure there are no extra spaces
- API key should start with "AIza"

### Issue: "npm run dev" doesn't work

**Solution:**

```bash
# Delete node_modules and reinstall
Remove-Item -Path node_modules -Recurse -Force
npm install
npm run dev
```

### Issue: Can't find the Firebase config

**Solution:**

1. Go to https://console.firebase.google.com
2. Click your project
3. Click ⚙️ gear icon → Project settings
4. Scroll down to "Your apps"
5. Look for "SDK setup and configuration"
6. Copy the firebaseConfig object

### Issue: "Missing or insufficient permissions"

**Solution:**

- Make sure Firestore is in "Test mode"
- Or add security rules (see FIREBASE_SETUP_INTERACTIVE.md Step 8)

### Issue: Browser console shows Firebase errors

**Solution:**

- Open `src/config/firebase.js`
- Check that ALL values are updated (not "YOUR_...")
- Restart the dev server (Ctrl+C, then `npm run dev`)

---

## 📖 **Documentation Files**

| File | Purpose |
|------|---------|
| **FIREBASE_SETUP_INTERACTIVE.md** | 📖 Step-by-step Firebase setup with detailed instructions |
| **OPENSTREETMAP_GUIDE.md** | 🗺️ Map customization guide (optional) |
| **QUICK_START.md** | ⚡ Quick reference for commands |
| **README.md** | 📚 Complete app documentation |

---

## ✅ **Success! You Should See:**

1. **Landing Page** with hero section
2. **Login/Register** pages working
3. **Dashboard** after logging in
4. **Navigation bar** with all sections
5. **Map view** with OpenStreetMap
6. **Emergency button** (red, bottom-right)

---

## 🎉 **Next Steps After Setup**

1. **Customize**: Change colors, logo, text
2. **Add Users**: Create test accounts
3. **Test Features**: Try alerts, posts, map
4. **Deploy**: Host on Firebase, Vercel, or Netlify

---

## 💬 **Need Help?**

Tell me:

1. ✅ Which checklist items you've completed
2. ❌ Where you're stuck
3. 📋 Any error messages you see

I'll guide you through it!

---

**You've got this! 💪 One step at a time.**
