# 🔥 Firebase Setup - Step by Step Guide

## 📋 **What You'll Do (15 minutes total)**

1. ✅ Create Firebase Project (3 min)
2. ✅ Get Configuration Keys (2 min)
3. ✅ Enable Authentication (3 min)
4. ✅ Set Up Firestore Database (3 min)
5. ✅ Enable Cloud Messaging (2 min)
6. ✅ Set Up Storage (2 min)

---

## **STEP 1: Create Firebase Project** (3 minutes)

### 1.1 Go to Firebase Console

- **URL**: https://console.firebase.google.com
- Click **"Add project"** or **"Create a project"**

### 1.2 Name Your Project

- **Project Name**: Type `Kutumbh` (or any name you want)
- Click **Continue**

### 1.3 Google Analytics (Optional)

- You can **disable** Google Analytics for now (toggle it OFF)
- Or leave it ON if you want analytics
- Click **Continue** then **Create project**

### 1.4 Wait for Setup

- Wait 30-60 seconds for Firebase to create your project
- Click **Continue** when ready

✅ **Project Created!**

---

## **STEP 2: Get Your Configuration Keys** (2 minutes)

### 2.1 Add Web App

- In Firebase Console, look for the **</>** icon (Web icon)
- It says **"Add app"** when you hover
- Click the **</>** icon

### 2.2 Register Your App

- **App nickname**: Type `Kutumbh Web`
- ❌ **Don't check** "Also set up Firebase Hosting" (not needed yet)
- Click **Register app**

### 2.3 Copy Configuration

You'll see code like this:

```javascript
const firebaseConfig = {
  apiKey: "AIzaSyXXXXXXXXXXXXXXXXXXXXXXXX",
  authDomain: "kutumbh-xxxxx.firebaseapp.com",
  projectId: "kutumbh-xxxxx",
  storageBucket: "kutumbh-xxxxx.appspot.com",
  messagingSenderId: "123456789012",
  appId: "1:123456789012:web:xxxxxxxxxxxxx"
};
```

### 2.4 Save These Keys

- **Copy this entire firebaseConfig object**
- We'll use it in Step 7
- Click **Continue to console**

✅ **Configuration Keys Retrieved!**

---

## **STEP 3: Enable Authentication** (3 minutes)

### 3.1 Go to Authentication

- In the left sidebar, click **"Build"** dropdown
- Click **"Authentication"**
- Click **"Get started"**

### 3.2 Enable Email/Password

- Click on **"Email/Password"** in the list
- **Toggle ON** the first switch (Email/Password)
- ❌ Leave **"Email link"** OFF
- Click **"Save"**

✅ **Authentication Enabled!**

---

## **STEP 4: Set Up Firestore Database** (3 minutes)

### 4.1 Go to Firestore

- In the left sidebar, click **"Build"** dropdown
- Click **"Firestore Database"**
- Click **"Create database"**

### 4.2 Choose Location

- **Start in**: Select **"Test mode"** (allows read/write for 30 days)
    - ⚠️ We'll add security rules later
- Click **Next**

### 4.3 Select Region

- **Firestore location**: Choose closest to you:
    - 🇺🇸 `us-central1` (Iowa) - Good for US
    - 🇪🇺 `europe-west1` (Belgium) - Good for Europe
    - 🇦🇺 `asia-south1` (Mumbai) - Good for India/Asia
- Click **Enable**

### 4.4 Wait for Creation

- Wait 1-2 minutes for Firestore to initialize

✅ **Firestore Database Created!**

---

## **STEP 5: Enable Cloud Messaging** (2 minutes)

### 5.1 Go to Project Settings

- Click the **⚙️ gear icon** (top left, next to "Project Overview")
- Click **"Project settings"**

### 5.2 Go to Cloud Messaging

- Click the **"Cloud Messaging"** tab at the top
- Scroll down to **"Web Push certificates"**

### 5.3 Generate Key Pair

- Click **"Generate key pair"**
- Copy the **Key** that appears
- Save it (we'll use it later)

✅ **Cloud Messaging Enabled!**

---

## **STEP 6: Set Up Storage** (2 minutes)

### 6.1 Go to Storage

- In the left sidebar, click **"Build"** dropdown
- Click **"Storage"**
- Click **"Get started"**

### 6.2 Choose Security Rules

- Select **"Start in test mode"**
- Click **Next**

### 6.3 Choose Location

- Use the **same location** you chose for Firestore
- Click **Done**

✅ **Storage Set Up!**

---

## **STEP 7: Update Your App Configuration** (3 minutes)

### 7.1 Open Your Config File

In your project, open: `kutumbh-app/src/config/firebase.js`

### 7.2 Find the firebaseConfig Section

Look for this:

```javascript
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_AUTH_DOMAIN",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_STORAGE_BUCKET",
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

### 7.3 Replace with Your Keys

Replace the values with the keys you copied in Step 2:

```javascript
const firebaseConfig = {
  apiKey: "AIzaSyXXXXXXXXXXXXXXXXXXXXXXXX",              // ← Paste yours
  authDomain: "kutumbh-xxxxx.firebaseapp.com",          // ← Paste yours
  projectId: "kutumbh-xxxxx",                           // ← Paste yours
  storageBucket: "kutumbh-xxxxx.appspot.com",          // ← Paste yours
  messagingSenderId: "123456789012",                    // ← Paste yours
  appId: "1:123456789012:web:xxxxxxxxxxxxx"            // ← Paste yours
};
```

### 7.4 Add VAPID Key (Optional - for notifications)

Find this line:

```javascript
const VAPID_KEY = "YOUR_VAPID_KEY_FROM_CLOUD_MESSAGING";
```

Replace with the key you generated in Step 5.3.

### 7.5 Save the File

- Press **Ctrl + S** to save

✅ **Configuration Updated!**

---

## **STEP 8: Set Security Rules** (Optional but Recommended)

### 8.1 Firestore Rules

Go back to Firebase Console → Firestore Database → Rules tab

Replace the rules with:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Users collection
    match /users/{userId} {
      allow read: if request.auth != null;
      allow write: if request.auth != null && request.auth.uid == userId;
    }
    
    // Posts collection
    match /posts/{postId} {
      allow read: if request.auth != null;
      allow create: if request.auth != null;
      allow update, delete: if request.auth != null && 
        request.auth.uid == resource.data.userId;
    }
    
    // Alerts collection
    match /alerts/{alertId} {
      allow read: if request.auth != null;
      allow create: if request.auth != null;
      allow update, delete: if request.auth != null && 
        request.auth.uid == resource.data.createdBy;
    }
    
    // Alert responses
    match /alertResponses/{responseId} {
      allow read: if request.auth != null;
      allow create: if request.auth != null;
      allow update, delete: if request.auth != null && 
        request.auth.uid == resource.data.userId;
    }
  }
}
```

Click **Publish**

### 8.2 Storage Rules

Go to Storage → Rules tab

Replace with:

```javascript
rules_version = '2';
service firebase.storage {
  match /b/{bucket}/o {
    match /{allPaths=**} {
      allow read: if request.auth != null;
      allow write: if request.auth != null && 
        request.resource.size < 5 * 1024 * 1024; // 5MB limit
    }
  }
}
```

Click **Publish**

✅ **Security Rules Set!**

---

## 🎉 **DONE! Now Run Your App**

```bash
cd kutumbh-app
npm run dev
```

Visit: **http://localhost:3000**

---

## 🆘 **Troubleshooting**

### "Firebase: Error (auth/...)"

- Double-check your firebaseConfig keys
- Make sure Authentication is enabled

### "Missing or insufficient permissions"

- Check Firestore Rules (Step 8)
- Make sure you're logged in

### "Failed to register service worker"

- This is OK - notifications will still work
- Service worker is optional

### Can't See the Configuration?

- Go to Firebase Console
- Click ⚙️ gear icon → Project settings
- Scroll down to "Your apps"
- Click on your web app
- Scroll to "SDK setup and configuration"
- Copy the config

---

## 📞 **Need Help?**

If you're stuck on any step, tell me:

1. Which step number you're on
2. What you see on the screen
3. Any error messages

I'll help you through it!

---

**🎊 You're doing great! Take it one step at a time.**
