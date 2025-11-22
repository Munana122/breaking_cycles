# Breaking Cycles - Setup Guide

## Step 1: Firebase Project Setup (5 minutes)

### 1.1 Create Firebase Project
1. Go to https://console.firebase.google.com/
2. Click "Add project"
3. Name: `breaking-cycles`
4. Disable Google Analytics (optional)
5. Click "Create project"

### 1.2 Enable Authentication
1. Click "Authentication" in sidebar
2. Click "Get started"
3. Go to "Sign-in method" tab
4. Enable "Email/Password"
5. Click "Save"

### 1.3 Create Firestore Database
1. Click "Firestore Database" in sidebar
2. Click "Create database"
3. Select "Start in test mode"
4. Choose location: `europe-west` (closest to Rwanda)
5. Click "Enable"

### 1.4 Get Firebase Config
1. Click gear icon ⚙️ → "Project settings"
2. Scroll to "Your apps"
3. Click web icon `</>`
4. Register app: `breaking-cycles-web`
5. Copy the `firebaseConfig` object

## Step 2: Configure Application (2 minutes)

1. Open `index.html` in your editor
2. Find the Firebase config section (around line 850)
3. Replace the placeholder config:
```javascript
const firebaseConfig = {
    apiKey: "PASTE_YOUR_API_KEY",
    authDomain: "your-project.firebaseapp.com",
    projectId: "your-project-id",
    storageBucket: "your-project.appspot.com",
    messagingSenderId: "123456789",
    appId: "your-app-id"
};
```

4. Save the file

## Step 3: Test Locally (2 minutes)

### Option A: Direct File
- Double-click `index.html` to open in browser

### Option B: Local Server (Recommended)
```bash
# Python
python -m http.server 8000

# Node.js
npx http-server
```

Navigate to: `http://localhost:8000`

## Step 4: Create Test Accounts

1. Click "Sign Up"
2. Create regular user: `test@example.com`
3. Create admin user: `m.munana@alustudent.com`

## Step 5: Deploy to Production

### Firebase Hosting
```bash
npm install -g firebase-tools
firebase login
firebase init hosting
# Select your project
# Set public directory to: .
# Configure as SPA: Yes
firebase deploy
```

### Netlify (Easiest)
1. Go to https://app.netlify.com/drop
2. Drag `index.html` into the upload area
3. Done! Get your live URL

### GitHub Pages
```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/yourusername/breaking-cycles.git
git push -u origin main
```
Then enable Pages in repo settings.

## Troubleshooting

### Issue: Firebase not initialized
- ✅ Check that you replaced the config
- ✅ Verify API key is correct
- ✅ Check browser console for errors

### Issue: Authentication not working
- ✅ Ensure Email/Password is enabled in Firebase Console
- ✅ Check that auth domain matches config

### Issue: Chat messages not appearing
- ✅ Verify Firestore is in test mode
- ✅ Check browser console for permission errors
- ✅ Try logging out and back in

### Issue: Can't mark courses complete
- ✅ Ensure you're logged in
- ✅ Check Firestore rules allow writes

## Security Notes

**Before going to production:**
1. Update Firestore rules from test mode to:
```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId} {
      allow read: if request.auth != null;
      allow write: if request.auth.uid == userId;
    }
    
    match /chatRooms/{room}/messages/{message} {
      allow read: if request.auth != null;
      allow create: if request.auth != null;
    }
    
    match /stories/{story} {
      allow read: if true;
      allow create: if request.auth != null;
      allow update: if request.auth.token.email == 'm.munana@alustudent.com';
    }
    
    match /contactSubmissions/{submission} {
      allow create: if true;
      allow read: if request.auth.token.email == 'm.munana@alustudent.com';
    }
  }
}
```

2. Enable HTTPS only
3. Set up proper CORS policies
4. Add reCAPTCHA to forms

## Next Steps

✅ Test all features
✅ Take screenshots for documentation
✅ Invite beta testers
✅ Gather feedback
✅ Launch! 🚀
