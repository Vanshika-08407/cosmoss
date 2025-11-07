# 🚀 Kutumbh - Quick Start Guide

## **3-Step Setup (5 minutes!)**

### Step 1: Install Dependencies

```bash
cd kutumbh-app
npm install
```

### Step 2: Configure Firebase

1. Go to https://console.firebase.google.com
2. Create a project
3. Copy your config
4. Update `src/config/firebase.js`

**Detailed guide**: See `FIREBASE_SETUP.md`

### Step 3: Run the App!

```bash
npm run dev
```

**Open**: http://localhost:3000

---

## ✨ What Makes Kutumbh Special

### 🗺️ FREE Interactive Maps - NO API KEY!

Unlike most apps that require Google Maps ($$$), Kutumbh uses:

- ✅ **OpenStreetMap** - 100% Free forever
- ✅ **No API key** required
- ✅ **No billing** or credit card
- ✅ **No setup** - works immediately!

### 🔥 Firebase Backend

- ✅ **Free tier** is generous
- ✅ Perfect for small/medium apps
- ⚠️ Only needs Firebase config (see FIREBASE_SETUP.md)

---

## Key Commands

```bash
# Development
npm run dev              # Start dev server (port 3000)

# Production
npm run build           # Create production build
npm run preview         # Preview production build

# Deploy
firebase deploy         # Deploy to Firebase Hosting
```

---

## What's Already Built

### ✅ Complete Features:

- **Authentication**: Login, Register, Password Reset
- **User Roles**: Individual, Family, NGO, Volunteer
- **Emergency Alerts**: Create & respond to alerts
- **Community Wall**: Post, like, comment
- **Interactive Map**: View nearby NGOs/volunteers
- **Profiles**: View & edit user profiles
- **Responsive UI**: Works on all devices
- **Real-time Updates**: Firebase sync

### 💰 Zero Cost Features:

- **Maps**: OpenStreetMap (FREE!)
- **Backend**: Firebase free tier
- **Hosting**: Firebase Hosting included
- **All libraries**: Open source

---

## Project Structure

```
kutumbh-app/
├── src/
│   ├── pages/           # Main pages
│   │   ├── Landing.jsx      # Homepage
│   │   ├── Login.jsx        # Login page
│   │   ├── Register.jsx     # Registration
│   │   ├── Dashboard.jsx    # User dashboard
│   │   ├── CommunityWall.jsx  # Social feed
│   │   ├── AlertsPage.jsx   # Emergency alerts
│   │   ├── MapView.jsx      # Interactive map 🗺️
│   │   └── Profile.jsx      # User profile
│   │
│   ├── components/      # Reusable components
│   │   ├── Navbar.jsx       # Navigation bar
│   │   ├── EmergencyButton.jsx  # Floating help button
│   │   └── Layout.jsx       # Page layout
│   │
│   ├── config/          # Configuration
│   │   ├── firebase.js      ← Update with your Firebase config
│   │   └── openStreetMap.js ← Maps config (no API key!)
│   │
│   ├── services/        # Firebase services
│   │   ├── authService.js
│   │   ├── alertService.js
│   │   ├── postService.js
│   │   └── userService.js
│   │
│   └── utils/           # Helper functions
│       ├── constants.js
│       ├── helpers.js
│       └── notifications.js
│
├── FIREBASE_SETUP.md       ← Step-by-step Firebase guide
├── OPENSTREETMAP_GUIDE.md  ← Map customization guide
└── README.md               ← Full documentation
```

---

## Configuration Files

### 🔥 Firebase (REQUIRED)

**File**: `src/config/firebase.js`

```javascript
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "your-project.firebaseapp.com",
  projectId: "your-project-id",
  storageBucket: "your-project.appspot.com",
  messagingSenderId: "123456789",
  appId: "YOUR_APP_ID"
};
```

**Guide**: See `FIREBASE_SETUP.md`

### 🗺️ OpenStreetMap (Optional)

**File**: `src/config/openStreetMap.js`

**Already configured!** No API key needed.

**Want to customize?**

- Change default location
- Switch map style (dark/light mode)
- Adjust zoom levels

**Guide**: See `OPENSTREETMAP_GUIDE.md`

---

## Testing the App

### 1. Start Development Server

```bash
npm run dev
```

### 2. Test Features

#### ✅ Registration

1. Go to http://localhost:3000
2. Click "Get Started"
3. Fill registration form
4. Choose role (Individual/NGO/Volunteer)
5. Submit

#### ✅ Login

1. Use credentials you created
2. Login

#### ✅ Dashboard

- View stats
- See recent alerts
- See community posts

#### ✅ Community Wall

- Create a post
- Like a post
- Comment on posts

#### ✅ Alerts

- View active alerts
- Respond to alerts (if volunteer)
- Create alert (use emergency button)

#### ✅ Map View

- See interactive map (OpenStreetMap)
- View nearby NGOs
- View nearby volunteers
- Click markers for details

#### ✅ Profile

- View your profile
- Edit profile information
- Update skills (if volunteer)
- Update location

---

## Common Issues

### ❌ "Firebase: Error (auth/invalid-api-key)"

**Fix**: Update Firebase config in `src/config/firebase.js`

### ❌ Map not loading

**Fix**: Check internet connection (tiles load from OSM servers)

### ❌ Port 3000 already in use

```bash
# Kill process on port 3000
npx kill-port 3000
npm run dev
```

### ❌ Dependencies issues

```bash
rm -rf node_modules package-lock.json
npm install
```

---

## Deployment Checklist

Before deploying to production:

- [ ] Firebase config is updated
- [ ] Firestore security rules are set
- [ ] Storage rules are configured
- [ ] Test all features
- [ ] Build passes (`npm run build`)
- [ ] Firebase CLI is installed
- [ ] Deploy with `firebase deploy`

---

## Next Steps

### 📚 Learn More

- **Full docs**: See `README.md`
- **Firebase setup**: See `FIREBASE_SETUP.md`
- **Map customization**: See `OPENSTREETMAP_GUIDE.md`

### 🎨 Customize

- Change theme colors in `src/styles/globals.css`
- Modify default location in `src/config/openStreetMap.js`
- Add your logo to `public/`

### 🚀 Deploy

```bash
npm run build
firebase deploy
```

### 🤝 Contribute

- Report issues
- Suggest features
- Submit pull requests

---

## Key Advantages

### 💰 Cost-Effective

| Feature | Cost |
|---------|------|
| Maps (OpenStreetMap) | ✅ $0/month |
| Firebase (small app) | ✅ $0/month |
| Hosting | ✅ $0/month |
| **Total** | **$0/month** |

Compare to Google Maps:

- Google Maps requires API key + billing
- Costs money after $200 free credit
- Kutumbh uses OpenStreetMap = FREE!

### 🚀 Quick to Deploy

- No complex API setups
- Only Firebase needs config
- Deploy in minutes

### 🎯 Full-Featured

- All core features included
- Professional UI/UX
- Production-ready code

---

## Support

**Need help?**

- Check documentation files
- Review code comments
- Test with sample data
- Check Firebase console for errors

**Resources:**

- [Firebase Docs](https://firebase.google.com/docs)
- [Leaflet Docs](https://leafletjs.com/)
- [React Docs](https://react.dev)

---

**Ready to start building? Run `npm install && npm run dev`**

**Kutumbh - Together for Good** 🌟
