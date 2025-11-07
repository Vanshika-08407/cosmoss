# 📱 Run Kutumbh on Pixel 9 Device

## ✅ **3 Methods to Run on Your Pixel 9**

---

## 🚀 **METHOD 1: Local Network Access** (Easiest - 2 mins)

### **Step 1: Start Dev Server**

On your PC:

```bash
cd kutumbh-app
npm run dev
```

You'll see something like:

```
  VITE v5.0.0  ready in 500 ms

  ➜  Local:   http://localhost:3000/
  ➜  Network: http://192.168.1.100:3000/  ← Use this IP!
```

### **Step 2: Get Your PC's IP Address**

#### On Windows:

```powershell
ipconfig
```

Look for "IPv4 Address" under your WiFi adapter (e.g., `192.168.1.100`)

#### On Mac/Linux:

```bash
ifconfig | grep "inet "
```

### **Step 3: Connect from Pixel 9**

1. **Make sure Pixel 9 is on the SAME WiFi** as your PC
2. Open Chrome on Pixel 9
3. Go to: `http://YOUR_PC_IP:3000`
    - Example: `http://192.168.1.100:3000`
4. **Done!** App should load on your phone

### **Troubleshooting:**

**Can't connect?**

- Check both devices on same WiFi
- Turn off Windows Firewall temporarily
- Check if port 3000 is open

**To allow port 3000 in Windows Firewall:**

```powershell
netsh advfirewall firewall add rule name="Vite Dev Server" dir=in action=allow protocol=TCP localport=3000
```

---

## 📦 **METHOD 2: Build and Deploy to Firebase Hosting** (5 mins)

### **Step 1: Build the App**

```bash
cd kutumbh-app
npm run build
```

This creates an optimized production build in the `dist` folder.

### **Step 2: Install Firebase CLI**

```bash
npm install -g firebase-tools
```

### **Step 3: Login to Firebase**

```bash
firebase login
```

### **Step 4: Initialize Firebase Hosting**

```bash
firebase init hosting
```

Choose:

- Select your existing Firebase project: `kutumbh-app-bb85e`
- Public directory: `dist` (not `public`)
- Single-page app: `Yes`
- Overwrite index.html: `No`

### **Step 5: Deploy**

```bash
firebase deploy --only hosting
```

You'll get a URL like:

```
✔  Deploy complete!

Hosting URL: https://kutumbh-app-bb85e.web.app
```

### **Step 6: Access on Pixel 9**

1. Open Chrome on your Pixel 9
2. Go to: `https://kutumbh-app-bb85e.web.app`
3. **Bookmark it!**
4. Use "Add to Home Screen" for app-like experience

---

## 📲 **METHOD 3: Install as PWA** (Progressive Web App)

### **Step 1: Deploy Using Method 2**

First deploy to Firebase Hosting (see above).

### **Step 2: Install on Pixel 9**

1. Open `https://kutumbh-app-bb85e.web.app` in Chrome
2. Chrome will show **"Add Kutumbh to Home screen"** banner
3. Or tap **Menu (⋮)** → **"Add to Home screen"**
4. Name it "Kutumbh"
5. Tap "Add"

### **Step 3: Use Like a Native App**

- Find "Kutumbh" icon on your home screen
- Tap to open (opens in full screen, no browser UI)
- Works offline!
- Receives push notifications (if enabled)

---

## 🎯 **Quick Start (Recommended)**

### **For Testing/Development:**

Use **Method 1** (Local Network)

- ✅ Fastest to set up
- ✅ See changes instantly
- ✅ No deployment needed
- ❌ Only works on same WiFi

### **For Permanent Access:**

Use **Method 2** (Firebase Hosting)

- ✅ Access from anywhere
- ✅ HTTPS enabled
- ✅ Fast CDN delivery
- ✅ Custom domain support

### **For App-Like Experience:**

Use **Method 3** (PWA)

- ✅ Home screen icon
- ✅ Full screen mode
- ✅ Offline support
- ✅ Push notifications

---

## 🔥 **Complete Firebase Deployment Steps**

### **1. Prepare Your App**

```bash
cd kutumbh-app

# Make sure Firebase config is set
# Check src/config/firebase.js has your credentials

# Build the app
npm run build
```

### **2. Install Firebase Tools**

```bash
npm install -g firebase-tools
```

### **3. Login**

```bash
firebase login
```

### **4. Initialize**

```bash
firebase init
```

Select:

- ☑ Hosting
- Use existing project: `kutumbh-app-bb85e`
- Public directory: **`dist`** (important!)
- Single-page app: **Yes**
- Set up automatic builds: No (for now)
- Overwrites: No

### **5. Deploy**

```bash
firebase deploy
```

### **6. Access**

Your app is now live at:

```
https://kutumbh-app-bb85e.web.app
```

---

## 📱 **Testing on Pixel 9**

### **Features to Test:**

1. **Registration & Login**
    - Create account
    - Login with credentials

2. **Dashboard**
    - View statistics
    - Check if numbers update

3. **IVR Demo**
    - Click "IVR Helpline Demo"
    - Allow microphone permission
    - Test voice recognition

4. **Community Feed**
    - Create a post
    - Like posts
    - Comment

5. **Map View**
    - Check if map loads
    - View markers

6. **Emergency Button**
    - Click red emergency button (bottom-right)
    - Fill emergency form
    - Submit

7. **Responsive Design**
    - Check if UI adapts to phone screen
    - Test navigation
    - Check if buttons are touch-friendly

---

## 🔧 **Firewall Configuration (If Can't Connect)**

### **Windows Firewall:**

```powershell
# Allow Vite dev server
netsh advfirewall firewall add rule name="Vite Dev Server" dir=in action=allow protocol=TCP localport=3000

# Allow Node.js
netsh advfirewall firewall add rule name="Node.js" dir=in action=allow program="C:\Program Files\nodejs\node.exe"
```

### **Alternative - Turn Off Firewall Temporarily:**

1. Windows Search → "Firewall"
2. Windows Defender Firewall
3. Turn Windows Defender Firewall on or off
4. Turn off for Private network
5. **Remember to turn it back on after testing!**

---

## 📊 **Performance on Pixel 9**

Expected performance:

- **Load Time**: 2-3 seconds (first load)
- **Navigation**: Instant
- **Animations**: Smooth 60 FPS
- **Voice Recognition**: 2-3 seconds
- **Map Loading**: 1-2 seconds

---

## 🆘 **Common Issues**

### **Issue 1: Can't Access via Local IP**

**Solutions:**

1. Check both devices on same WiFi
2. Check Windows Firewall settings
3. Try phone's mobile hotspot
4. Restart dev server: `Ctrl+C` then `npm run dev`

### **Issue 2: "This site can't be reached"**

**Solutions:**

1. Verify IP address is correct
2. Make sure dev server is running
3. Try `http://` not `https://`
4. Check port 3000 is not blocked

### **Issue 3: App Loads but Firebase Errors**

**Solutions:**

1. Check Firebase config in `src/config/firebase.js`
2. Ensure Firestore & Authentication are enabled
3. Check security rules are set
4. Verify internet connection

### **Issue 4: Voice Recognition Doesn't Work**

**Solutions:**

1. HTTPS required (use Firebase Hosting)
2. Allow microphone permission
3. Chrome browser recommended
4. Speak clearly and slowly

---

## 🎨 **PWA Features on Pixel 9**

When installed as PWA:

- ✅ Home screen icon with your logo
- ✅ Splash screen on launch
- ✅ Runs in full screen (no browser bars)
- ✅ Works offline (with cached data)
- ✅ Fast loading (service worker)
- ✅ Push notifications (future)
- ✅ Can be found in app drawer
- ✅ Appears in recent apps

---

## 🚀 **Quick Commands Reference**

```bash
# Start dev server (Method 1)
cd kutumbh-app
npm run dev

# Build for production
npm run build

# Preview production build locally
npm run preview

# Deploy to Firebase (Method 2)
firebase deploy

# Deploy only hosting
firebase deploy --only hosting

# Check Firebase login
firebase login:list

# Get your PC's IP (Windows)
ipconfig

# Allow firewall (Windows)
netsh advfirewall firewall add rule name="Vite" dir=in action=allow protocol=TCP localport=3000
```

---

## 📱 **Step-by-Step: Quick Test on Pixel 9**

### **Fastest Way (5 minutes):**

**On Your PC:**

```bash
# 1. Navigate to project
cd C:\Users\Vanshika\Apps\Hackss\kutumbh-app

# 2. Start server
npm run dev

# 3. Note the Network IP shown (e.g., 192.168.1.100:3000)
```

**On Your Pixel 9:**

```
1. Connect to SAME WiFi as PC
2. Open Chrome
3. Type: http://192.168.1.100:3000
   (Use YOUR PC's IP from step 3 above)
4. App loads!
5. Test all features
```

---

## 💡 **Pro Tips**

1. **Bookmark on Phone**: Add to Chrome bookmarks for easy access
2. **Add to Home Screen**: For app-like experience
3. **Use Chrome**: Best compatibility for all features
4. **Enable Location**: For map features
5. **Allow Notifications**: For emergency alerts
6. **Test Voice**: IVR feature needs microphone permission

---

## 🎯 **Which Method Should You Use?**

| Scenario | Best Method | Why |
|----------|-------------|-----|
| Quick testing | Method 1 (Local) | Instant, no deployment |
| Showing to others | Method 2 (Firebase) | Share URL, works anywhere |
| Demo/Presentation | Method 3 (PWA) | Professional, app-like |
| Development | Method 1 (Local) | Live reload, instant changes |
| Production | Method 2+3 (Firebase+PWA) | Reliable, scalable |

---

## ✅ **Success Checklist**

- [ ] Dev server running on PC
- [ ] PC and Pixel 9 on same WiFi
- [ ] Can access via IP on phone
- [ ] App loads correctly
- [ ] Firebase features working
- [ ] Can register/login
- [ ] IVR demo accessible
- [ ] Voice recognition working
- [ ] Map loads properly
- [ ] Responsive on mobile

---

**🎉 Your Kutumbh app is ready to run on Pixel 9!** 📱✨
