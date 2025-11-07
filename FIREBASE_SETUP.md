# 🔥 Firebase Setup Guide for Kutumbh

## Step 1: Create Firebase Project

1. **Go to Firebase Console**
    - Visit: https://console.firebase.google.com
    - Sign in with your Google account

2. **Create New Project**
    - Click "Add project" or "Create a project"
    - Enter project name: `kutumbh-app` (or any name you prefer)
    - Click "Continue"

3. **Google Analytics** (Optional)
    - Enable or disable Google Analytics
    - If enabled, select or create an analytics account
    - Click "Create project"
    - Wait for project creation (30-60 seconds)

---

## Step 2: Register Web App

1. **Add Web App**
    - In Firebase console, click on "</>" (Web icon)
    - App nickname: `Kutumbh Web App`
    - ✅ Check "Also set up Firebase Hosting"
    - Click "Register app"

2. **Copy Configuration**
    - You'll see a `firebaseConfig` object like this:
   ```javascript
   const firebaseConfig = {
     apiKey: "AIzaSyDxxxxxxxxxxxxxxxxxxxxxxxxxxx",
     authDomain: "your-project-id.firebaseapp.com",
     projectId: "your-project-id",
     storageBucket: "your-project-id.appspot.com",
     messagingSenderId: "123456789012",
     appId: "1:123456789012:web:abcdef1234567890",
     measurementId: "G-XXXXXXXXXX"
   };
   ```
    - **Copy this entire object**

3. **Update Your Config File**
    - Open: `kutumbh-app/src/config/firebase.js`
    - Replace the placeholder values with your actual config
    - Save the file

---

## Step 3: Enable Authentication

1. **Navigate to Authentication**
    - In Firebase Console sidebar: Build → Authentication
    - Click "Get started"

2. **Enable Email/Password**
    - Click on "Sign-in method" tab
    - Click "Email/Password"
    - Toggle to "Enable"
    - Click "Save"

3. **Optional: Add Other Providers**
    - Google Sign-in
    - Facebook Login
    - Phone Authentication

---

## Step 4: Create Firestore Database

1. **Navigate to Firestore**
    - Sidebar: Build → Firestore Database
    - Click "Create database"

2. **Select Mode**
    - Choose: **"Start in test mode"** (for development)
    - Click "Next"

3. **Choose Location**
    - Select closest region (e.g., `asia-south1` for India)
    - cd kutumbh-app
      npm run dev
      Click "Enable"
    - Wait for database creation

4. **Set Security Rules**
    - Go to "Rules" tab
    - Replace with these rules:
   ```javascript
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       // Users collection
       match /users/{userId} {
         allow read: if request.auth != null;
         allow create: if request.auth != null;
         allow update: if request.auth != null && request.auth.uid == userId;
       }
       
       // Posts collection
       match /posts/{postId} {
         allow read: if request.auth != null;
         allow create: if request.auth != null;
         allow update, delete: if request.auth != null && 
           resource.data.authorId == request.auth.uid;
       }
       
       // Alerts collection
       match /alerts/{alertId} {
         allow read: if request.auth != null;
         allow create: if request.auth != null;
         allow update: if request.auth != null;
       }
     }
   }
   ```
    - Click "Publish"

---

## Step 5: Enable Cloud Storage

1. **Navigate to Storage**
    - Sidebar: Build → Storage
    - Click "Get started"

2. **Security Rules**
    - Choose: **"Start in test mode"**
    - Click "Next"

3. **Location**
    - Use same location as Firestore
    - Click "Done"

4. **Update Storage Rules** (for production)
   ```javascript
   rules_version = '2';
   service firebase.storage {
     match /b/{bucket}/o {
       match /posts/{allPaths=**} {
         allow read: if request.auth != null;
         allow write: if request.auth != null;
       }
     }
   }
   ```

---

## Step 6: Enable Cloud Messaging (Push Notifications)

1. **Navigate to Messaging**
    - Sidebar: Build → Messaging
    - Click "Get started"

2. **Get VAPID Key**
    - Go to Project Settings → Cloud Messaging tab
    - Scroll to "Web Push certificates"
    - Click "Generate key pair"
    - Copy the key

3. **Update Notifications Config**
    - Open: `kutumbh-app/src/utils/notifications.js`
    - Find line: `vapidKey: 'YOUR_VAPID_KEY'`
    - Replace with your actual VAPID key

---

## Step 7: Test Your Configuration

1. **Start Development Server**
   ```bash
   cd kutumbh-app
   npm run dev
   ```

2. **Open Browser**
    - Go to: http://localhost:3000
    - Open Developer Console (F12)

3. **Test Registration**
    - Click "Get Started" or "Sign Up"
    - Fill in registration form
    - Try to create an account

4. **Check for Errors**
    - No errors in console = Success! ✅
    - If errors appear, check:
        - API key is correct
        - Services are enabled
        - Security rules are published

---

## Common Issues & Solutions

### ❌ "Firebase: Error (auth/invalid-api-key)"

**Solution**: Double-check your API key in `firebase.js`

### ❌ "Firebase: Missing or insufficient permissions"

**Solution**:

- Check Firestore security rules
- Make sure you're authenticated
- Ensure rules are published

### ❌ "Firebase: Storage URL is undefined"

**Solution**: Enable Storage service in Firebase Console

### ❌ "Messaging is not supported"

**Solution**:

- Check if browser supports notifications
- HTTPS is required (or localhost for dev)
- Enable Cloud Messaging in console

---

## Production Deployment Checklist

Before deploying to production:

- [ ] Update Firestore rules (remove test mode)
- [ ] Update Storage rules (remove test mode)
- [ ] Add authorized domains in Authentication settings
- [ ] Enable App Check for security
- [ ] Set up Firebase Hosting
- [ ] Enable backup for Firestore
- [ ] Set up monitoring and alerts
- [ ] Configure billing alerts

---

## Security Best Practices

1. **Never commit `firebase.js` with real credentials to public repos**
    - Use environment variables
    - Add `.env` to `.gitignore`

2. **Restrict API Keys**
    - Go to Google Cloud Console
    - Restrict keys to specific domains
    - Limit API access

3. **Update Security Rules**
    - Never use test mode in production
    - Implement proper validation
    - Add rate limiting

4. **Enable App Check**
    - Protects against abuse
    - Verifies requests come from your app

---

## Need Help?

- 📖 [Firebase Documentation](https://firebase.google.com/docs)
- 💬 [Firebase Community](https://firebase.google.com/support)
- 🐛 [Stack Overflow](https://stackoverflow.com/questions/tagged/firebase)

---

**Setup Complete! 🎉**

Your Firebase backend is now ready for Kutumbh!
