# Kutumbh - Complete Setup Guide

## ✅ Issue Fixed!

The syntax error in `Profile.jsx` has been resolved. The app should now run without errors.

---

## 🚀 Quick Start (3 Steps)

```bash
# Step 1: Navigate to the project folder
cd kutumbh-app

# Step 2: Install all dependencies
npm install

# Step 3: Start the development server
npm run dev
```

**🎉 Your app will be live at: http://localhost:3000**

---

## 📋 All Available Commands

### Development

```bash
npm run dev          # Start dev server (http://localhost:3000)
npm run build        # Create production build
npm run preview      # Preview production build
npm run lint         # Check code quality
```

### Troubleshooting

```bash
# If port 3000 is in use
npx kill-port 3000
npm run dev

# If dependencies have issues
rm -rf node_modules package-lock.json
npm install

# Clear npm cache (if needed)
npm cache clean --force
npm install
```

---

## ⚙️ Configuration Steps

### 1. Firebase Setup (Required)

1. **Create Firebase Project**
    - Go to: https://console.firebase.google.com
    - Click "Add Project"
    - Follow the wizard

2. **Enable Required Services**
    - **Authentication**:
        - Go to Build → Authentication
        - Click "Get Started"
        - Enable "Email/Password" sign-in method

    - **Firestore Database**:
        - Go to Build → Firestore Database
        - Click "Create database"
        - Start in **test mode** (for development)
        - Choose a location

    - **Storage**:
        - Go to Build → Storage
        - Click "Get Started"
        - Start in test mode

    - **Cloud Messaging**:
        - Go to Build → Messaging
        - Click "Get Started"

3. **Get Your Config**
    - Go to Project Settings (gear icon)
    - Scroll to "Your apps" section
    - Click the web icon `</>`
    - Register your app
    - Copy the configuration code

4. **Update Firebase Config**
    - Open `kutumbh-app/src/config/firebase.js`
    - Replace the placeholder config:

```javascript
const firebaseConfig = {
  apiKey: "YOUR_API_KEY_HERE",
  authDomain: "your-project.firebaseapp.com",
  projectId: "your-project-id",
  storageBucket: "your-project.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abcdef",
  measurementId: "G-XXXXXXXXXX"
};
```

### 2. Firestore Security Rules

Go to Firestore Database → Rules tab and paste:

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

### 3. Google Maps Setup (Optional)

1. **Get API Key**
    - Go to: https://console.cloud.google.com
    - Create/select a project
    - Go to "APIs & Services" → "Credentials"
    - Click "Create Credentials" → "API Key"

2. **Enable Required APIs**
    - Go to "APIs & Services" → "Library"
    - Search and enable:
        - Maps JavaScript API
        - Places API
        - Geolocation API

3. **Update Config**
    - Open `kutumbh-app/src/config/googleMaps.js`
    - Replace the API key:

```javascript
export const GOOGLE_MAPS_API_KEY = "YOUR_ACTUAL_GOOGLE_MAPS_API_KEY";
```

---

## 🌐 Deployment Options

### Option 1: Firebase Hosting (Recommended)

```bash
# Install Firebase CLI
npm install -g firebase-tools

# Login to Firebase
firebase login

# Initialize hosting
firebase init hosting
# Select: 
# - Use existing project
# - Public directory: dist
# - Single-page app: Yes
# - GitHub deploys: No (or Yes if you want)

# Build and deploy
npm run build
firebase deploy

# Your app will be live at:
# https://your-project.firebaseapp.com
```

### Option 2: Vercel

```bash
# Install Vercel CLI
npm install -g vercel

# Deploy (run from project root)
vercel

# Follow prompts - it's automatic!
```

### Option 3: Netlify

```bash
# Install Netlify CLI
npm install -g netlify-cli

# Build first
npm run build

# Deploy
netlify deploy --prod --dir=dist

# Follow prompts
```

---

## 📱 Build Android App (Optional)

### Using Capacitor

```bash
# 1. Install Capacitor
npm install @capacitor/core @capacitor/cli
npm install @capacitor/android

# 2. Initialize Capacitor
npx cap init
# App name: Kutumbh
# Package ID: com.kutumbh.app

# 3. Build web assets
npm run build

# 4. Add Android platform
npx cap add android

# 5. Sync web assets to Android
npx cap sync

# 6. Open in Android Studio
npx cap open android

# 7. In Android Studio:
#    - Build → Build Bundle(s) / APK(s) → Build APK(s)
#    - APK will be in: app/build/outputs/apk/debug/
```

### Requirements for Android Build:

- Android Studio installed
- Java JDK 11 or higher
- Android SDK (installed via Android Studio)

---

## 🎨 Project Structure

```
kutumbh-app/
├── public/                 # Static files
├── src/
│   ├── components/        # Reusable components
│   │   ├── EmergencyButton.jsx
│   │   ├── Layout.jsx
│   │   └── Navbar.jsx
│   ├── config/           # Configuration
│   │   ├── firebase.js    # 🔧 Update this!
│   │   └── googleMaps.js  # 🔧 Update this!
│   ├── pages/            # Page components
│   │   ├── Dashboard.jsx
│   │   ├── CommunityWall.jsx
│   │   ├── AlertsPage.jsx
│   │   ├── MapView.jsx
│   │   ├── Profile.jsx
│   │   ├── Login.jsx
│   │   ├── Register.jsx
│   │   └── Landing.jsx
│   ├── services/         # Firebase services
│   ├── store/            # State management
│   ├── styles/           # Global styles
│   ├── utils/            # Helper functions
│   ├── App.jsx
│   └── main.jsx
├── index.html
├── package.json
├── vite.config.js
└── README.md
```

---

## 🐛 Common Issues & Solutions

### Issue: `Firebase not initialized`

**Solution**: Update your Firebase config in `src/config/firebase.js`

### Issue: `Port 3000 already in use`

```bash
npx kill-port 3000
npm run dev
```

### Issue: `Module not found errors`

```bash
rm -rf node_modules package-lock.json
npm install
```

### Issue: `Vite error or build fails`

```bash
npm cache clean --force
rm -rf node_modules package-lock.json dist
npm install
npm run dev
```

### Issue: `Google Maps not showing`

- Verify API key is correct
- Check that APIs are enabled in Google Cloud Console
- Ensure billing is enabled (Google requires it, but won't charge for low usage)

---

## 📚 Additional Resources

- **Firebase Documentation**: https://firebase.google.com/docs
- **React Documentation**: https://react.dev
- **Vite Documentation**: https://vitejs.dev
- **Google Maps API**: https://developers.google.com/maps

---

## ✨ Features Included

✅ User Authentication (Login/Register)
✅ Multiple User Roles (Individual, Family, NGO, Volunteer)
✅ Emergency Alert System
✅ Community Wall / Social Feed
✅ Nearby Support Map
✅ User Profiles with Editing
✅ Responsive Design (Mobile & Desktop)
✅ Modern UI with Orange & Blue Theme
✅ Real-time Updates (Firebase)
✅ Push Notifications (FCM ready)
✅ Geolocation Support

---

## 🎯 Next Steps

1. ✅ Run `npm install`
2. ✅ Update Firebase config
3. ✅ Run `npm run dev`
4. 🎨 Customize theme colors (optional)
5. 🚀 Deploy to Firebase Hosting
6. 📱 Build Android app (optional)

---

## 💡 Tips

- **Development**: Use `npm run dev` for hot reload
- **Testing**: Test on mobile viewport in browser DevTools
- **Production**: Always run `npm run build` before deploying
- **Git**: Add `.env` files to `.gitignore` if using environment variables

---

## 📞 Need Help?

- Check the main `README.md` for detailed documentation
- Review Firebase console for any service errors
- Check browser console for errors (F12)

---

**🏠💙 Kutumbh - Together for Good**

Made with ❤️ for communities everywhere!
