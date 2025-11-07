# Kutumbh - Community Social Welfare Platform

**Tagline:** Together for Good 🏠💙

## Overview

Kutumbh is a comprehensive community-based social welfare and support platform that connects
families, individuals, NGOs, and volunteers. The application strengthens community bonds by enabling
real-time emergency responses, social initiatives coordination, and community engagement.

---

## 🌟 Core Features

### 👥 User Roles

- **Individual/Family Users**: Request help, participate in community activities
- **NGO Representatives**: Create alerts, manage initiatives, coordinate relief efforts
- **Volunteers**: Respond to alerts, offer skills and services

### 🚨 Emergency Alert System

- **Real-time Notifications**: Instant alerts sent to nearby volunteers and NGOs
- **Geolocation-based**: Alerts target responders within configurable radius
- **Multiple Alert Types**:
    - Emergency
    - Disaster Relief
    - Food Drive
    - Blood Donation
    - Missing Person
    - Medical Aid
    - Shelter Requests
- **Response Tracking**: Monitor volunteer responses (Accept/Available/Decline)
- **Priority Levels**: High-priority emergency handling

### 🏠 Community Wall / Feed

- **Social Feed**: Share updates, needs, and thank volunteers
- **Post Types**: Updates, Community Needs, Thank You messages, Events
- **Engagement**: Like, comment, and interact with posts
- **Media Support**: Upload photos with posts
- **Real-time Updates**: Live feed of community activity

### 🗺️ Nearby Support Map

- **Interactive Map**: View NGOs and volunteers on OpenStreetMap
- **Distance Calculation**: Show proximity to user location
- **Filter by Type**: Toggle between NGOs and volunteers
- **Contact Information**: Quick access to phone and email
- **Verified Badges**: Trust indicators for verified NGOs
- **100% Free**: No API keys or billing required!

### 👤 User Profiles

- **Customizable Profiles**: Name, phone, skills, category
- **Role-specific Fields**:
    - Volunteers: Skills selection
    - NGOs: Category and verification status
- **Profile Editing**: Easy in-app profile updates

### ⚡ Quick Emergency Button

- **Floating Action Button**: Always accessible emergency help
- **One-tap Alert**: Fast emergency notification
- **Location Sharing**: Automatic location attachment

---

## 🛠️ Tech Stack

### Frontend

- **React 18.2**: Modern UI library
- **Vite**: Fast build tool and dev server
- **React Router DOM**: Client-side routing
- **Zustand**: Lightweight state management
- **Lucide React**: Beautiful icon library
- **React Hot Toast**: Elegant notifications

### Backend & Services

- **Firebase Authentication**: Secure user authentication
- **Cloud Firestore**: Real-time NoSQL database
- **Firebase Cloud Messaging**: Push notifications
- **Firebase Storage**: Media file storage
- **Firebase Hosting**: Web app deployment

### Maps & Location

- **🗺️ OpenStreetMap**: Free, open-source maps (NO API KEY NEEDED!)
- **Leaflet.js**: Interactive mapping library
- **React Leaflet**: React components for maps
- **Geolocation API**: User location tracking
- **Haversine Formula**: Accurate distance calculations

---

## 📦 Installation & Setup

### Prerequisites

```bash
# Node.js 16+ and npm
node --version  # Should be v16 or higher
npm --version   # Should be 8 or higher
```

### Step 1: Install Dependencies

```bash
cd kutumbh-app
npm install
```

### Step 2: Firebase Configuration

1. Create a Firebase project
   at [https://console.firebase.google.com](https://console.firebase.google.com)
2. Enable the following services:
    - Authentication (Email/Password)
    - Cloud Firestore
    - Cloud Messaging
    - Storage
    - Hosting

3. Get your Firebase config from Project Settings
4. Update `src/config/firebase.js` with your credentials

**See `FIREBASE_SETUP.md` for detailed instructions**

### Step 3: Maps Configuration (Optional)

**Good news!** OpenStreetMap requires **NO API key** and is **completely FREE**!

The map will work immediately after installing dependencies. No configuration needed!

**Want to customize?** See `OPENSTREETMAP_GUIDE.md` for options like:

- Changing default location
- Switching map styles (dark mode, light mode, etc.)
- Customizing marker colors

---

## 🚀 Build and Run Commands

### Development Mode

```bash
# Start development server
npm run dev

# The app will be available at http://localhost:3000
# Hot reload enabled - changes reflect immediately
```

### Production Build

```bash
# Create optimized production build
npm run build

# Output will be in the 'dist' folder
# Ready for deployment
```

### Preview Production Build

```bash
# Build and preview production version locally
npm run build
npm run preview

# Preview server runs on http://localhost:4173
```

### Linting

```bash
# Check for code issues
npm run lint
```

---

## 🌐 Deployment

### Deploy to Firebase Hosting

```bash
# Install Firebase CLI globally
npm install -g firebase-tools

# Login to Firebase
firebase login

# Initialize Firebase in your project
firebase init hosting

# Select options:
# - Use existing project (select your Firebase project)
# - Public directory: dist
# - Configure as single-page app: Yes
# - Set up automatic builds with GitHub: Optional

# Build and deploy
npm run build
firebase deploy

# Your app will be live at https://your-project.firebaseapp.com
```

### Deploy to Vercel

```bash
# Install Vercel CLI
npm install -g vercel

# Deploy
vercel

# Follow prompts to link project and deploy
```

### Deploy to Netlify

```bash
# Install Netlify CLI
npm install -g netlify-cli

# Build
npm run build

# Deploy
netlify deploy --prod --dir=dist
```

---

## 📱 Android App Setup (Optional)

To convert this web app into an Android app, use Capacitor:

```bash
# Install Capacitor
npm install @capacitor/core @capacitor/cli
npm install @capacitor/android

# Initialize Capacitor
npx cap init

# Build web assets
npm run build

# Add Android platform
npx cap add android

# Copy web assets to Android
npx cap sync

# Open in Android Studio
npx cap open android

# Build APK in Android Studio
```

---

## 📂 Project Structure

```
kutumbh-app/
├── public/                 # Static assets
├── src/
│   ├── components/        # Reusable UI components
│   │   ├── EmergencyButton.jsx
│   │   ├── Layout.jsx
│   │   └── Navbar.jsx
│   ├── config/           # Configuration files
│   │   ├── firebase.js
│   │   └── openStreetMap.js
│   ├── pages/            # Page components
│   │   ├── AlertsPage.jsx
│   │   ├── CommunityWall.jsx
│   │   ├── Dashboard.jsx
│   │   ├── Landing.jsx
│   │   ├── Login.jsx
│   │   ├── MapView.jsx
│   │   ├── Profile.jsx
│   │   └── Register.jsx
│   ├── services/         # API and Firebase services
│   │   ├── alertService.js
│   │   ├── authService.js
│   │   ├── postService.js
│   │   └── userService.js
│   ├── store/            # State management
│   │   └── useStore.js
│   ├── styles/           # Global styles
│   │   └── globals.css
│   ├── utils/            # Utility functions
│   │   ├── constants.js
│   │   ├── helpers.js
│   │   └── notifications.js
│   ├── App.jsx           # Main app component
│   └── main.jsx          # Entry point
├── index.html            # HTML template
├── package.json          # Dependencies
├── vite.config.js        # Vite configuration
└── README.md            # This file
```

---

## 🎨 Design System

### Color Palette

- **Primary**: `#FF6B35` (Warm Orange)
- **Secondary**: `#004E89` (Deep Blue)
- **Accent**: `#F77F00` (Bright Orange)
- **Success**: `#06D6A0` (Green)
- **Warning**: `#FFB703` (Yellow)
- **Danger**: `#EF233C` (Red)

### Typography

- **Font Family**: System fonts (-apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto')
- **Headings**: 700 weight
- **Body**: 400 weight
- **Buttons**: 600 weight

---

## 🔒 Security Features

- **Firebase Authentication**: Secure email/password authentication
- **Firestore Security Rules**: Role-based access control
- **Data Validation**: Client and server-side validation
- **Private Data**: User phone numbers and emails protected
- **Verified NGOs**: Badge system for trusted organizations

---

## 📊 Features Roadmap

### Phase 1 (Current)

- ✅ User authentication and profiles
- ✅ Emergency alert system
- ✅ Community wall/feed
- ✅ Nearby support map
- ✅ Profile management

### Phase 2 (Planned)

- [ ] Real-time chat between users
- [ ] Event calendar and scheduling
- [ ] Donation management system
- [ ] Volunteer hour tracking
- [ ] Analytics dashboard for NGOs

### Phase 3 (Future)

- [ ] Mobile app (iOS & Android native)
- [ ] Multi-language support
- [ ] AI-powered need matching
- [ ] Blockchain-based donation tracking
- [ ] Integration with government databases

---

## 🐛 Troubleshooting

### Common Issues

**Issue**: `Firebase not initialized`

- **Solution**: Ensure Firebase config is correctly set in `src/config/firebase.js`

**Issue**: `Geolocation not working`

- **Solution**: Enable location permissions in browser settings

**Issue**: `Build fails`

- **Solution**: Delete `node_modules` and `package-lock.json`, then run `npm install`

**Issue**: `Map not displaying`

- **Solution**: Verify OpenStreetMap is correctly configured

---

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## 👏 Acknowledgments

- Firebase for backend infrastructure
- React community for amazing tools
- Lucide for beautiful icons
- OpenStreetMap contributors for free mapping data
- All contributors and volunteers

---

## 📧 Support & Contact

For issues, questions, or feature requests:

- Create a GitHub issue
- Email: support@kutumbh.app
- Website: https://kutumbh.app

---

**Made with ❤️ for communities everywhere**

**Kutumbh - Together for Good** 🏠💙
