# Kutumbh - Quick Start Guide

## 🚀 Essential Commands

### Install & Run (First Time)

```bash
# Navigate to project directory
cd kutumbh-app

# Install all dependencies
npm install

# Start development server
npm run dev
```

**Your app will be running at: http://localhost:3000**

---

## 📋 Common Commands

```bash
# Development
npm run dev              # Start dev server with hot reload

# Production
npm run build           # Create production build
npm run preview         # Preview production build locally

# Code Quality
npm run lint            # Check code for issues
```

---

## ⚙️ Quick Firebase Setup

1. **Create Firebase Project**: https://console.firebase.google.com
2. **Enable Services**:
    - Authentication → Email/Password
    - Firestore Database
    - Storage
    - Cloud Messaging

3. **Get Config**: Project Settings → General → Your apps → Config

4. **Update**: `src/config/firebase.js` with your credentials

---

## 🗺️ Google Maps Setup

1. **Get API Key**: https://console.cloud.google.com
2. **Enable APIs**: Maps JavaScript API
3. **Update**: `src/config/googleMaps.js`

---

## 🌐 Deploy Commands

### Firebase Hosting

```bash
npm install -g firebase-tools
firebase login
firebase init hosting
npm run build
firebase deploy
```

### Vercel

```bash
npm install -g vercel
vercel
```

### Netlify

```bash
npm install -g netlify-cli
npm run build
netlify deploy --prod --dir=dist
```

---

## 📱 Build Android App

```bash
npm install @capacitor/core @capacitor/cli @capacitor/android
npx cap init
npm run build
npx cap add android
npx cap sync
npx cap open android
```

Build APK in Android Studio (Build → Build Bundle(s) / APK(s) → Build APK)

---

## 🔧 Troubleshooting

**Port already in use?**

```bash
# Kill process on port 3000
npx kill-port 3000
npm run dev
```

**Dependencies issue?**

```bash
rm -rf node_modules package-lock.json
npm install
```

**Build errors?**

```bash
npm run build -- --debug
```

---

## 📞 Need Help?

- Check main README.md for detailed documentation
- Open an issue on GitHub
- Email: support@kutumbh.app

---

**Happy Coding! 🏠💙**
