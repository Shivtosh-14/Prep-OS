# Firebase Setup Guide for Prep OS

## 🔥 Firebase Configuration

To complete the Firebase integration, you need to:

### 1. Create a Firebase Project
1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click "Create a project" or "Add project"
3. Enter project name: `prep-os` (or your preferred name)
4. Enable Google Analytics (optional)
5. Click "Create project"

### 2. Enable Authentication
1. In your Firebase project, go to "Authentication" in the left sidebar
2. Click "Get started"
3. Go to "Sign-in method" tab
4. Enable "Google" provider
5. Add your domain to authorized domains (for production)

### 3. Enable Firestore Database
1. Go to "Firestore Database" in the left sidebar
2. Click "Create database"
3. Choose "Start in test mode" (for development)
4. Select a location for your database

### 4. Get Your Configuration
1. Go to Project Settings (gear icon)
2. Scroll down to "Your apps" section
3. Click "Add app" and select Web (</>) icon
4. Register your app with a nickname
5. Copy the Firebase configuration object

### 5. Update Configuration in All Files
Replace the placeholder configuration in these files:
- `prototype.html`
- `login.html`
- `sat.html`
- `jee.html`
- `neet.html`
- `cuet.html`
- `esat.html`
- `lsat.html`

**Find this section in each file:**
```javascript
const firebaseConfig = {
    apiKey: "AIzaSyBXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX", // Replace with your API key
    authDomain: "prep-os-XXXXX.firebaseapp.com", // Replace with your domain
    projectId: "prep-os-XXXXX", // Replace with your project ID
    storageBucket: "prep-os-XXXXX.appspot.com", // Replace with your bucket
    messagingSenderId: "123456789012", // Replace with your sender ID
    appId: "1:123456789012:web:abcdefghijklmnop" // Replace with your app ID
};
```

**Replace with your actual configuration:**
```javascript
const firebaseConfig = {
    apiKey: "your-actual-api-key",
    authDomain: "your-project-id.firebaseapp.com",
    projectId: "your-project-id",
    storageBucket: "your-project-id.appspot.com",
    messagingSenderId: "your-sender-id",
    appId: "your-app-id"
};
```

## 🚀 Features Implemented

### ✅ Google Authentication
- Users can sign in with their Google account
- No passwords required
- Secure OAuth2 flow

### ✅ Custom Username Setup
- After Google login, users set a custom username
- Username uniqueness validation
- Stored in Firestore database

### ✅ User Profile Management
- User data stored in Firestore `users` collection
- Profile includes: uid, email, displayName, photoURL, username
- Automatic login state persistence

### ✅ Cross-Page Authentication
- Login state shared across all pages
- Automatic logout on all pages when signed out
- User avatar and username display

## 📁 Database Structure

### Firestore Collection: `users`
Each document contains:
```javascript
{
    uid: "firebase-user-id",
    email: "user@example.com",
    displayName: "User Name",
    photoURL: "https://lh3.googleusercontent.com/...",
    username: "custom_username",
    createdAt: timestamp,
    lastLogin: timestamp
}
```

## 🔧 Security Rules (Optional)

For production, update your Firestore security rules:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

## 🎯 Next Steps

1. Complete Firebase project setup
2. Update configuration in all files
3. Test Google sign-in functionality
4. Verify username creation works
5. Test logout functionality
6. Deploy to production domain

## 🐛 Troubleshooting

- **Authentication not working**: Check if Google provider is enabled
- **Database errors**: Verify Firestore is enabled and rules allow access
- **Configuration errors**: Double-check all config values are correct
- **CORS issues**: Add your domain to Firebase authorized domains

## 📞 Support

If you encounter issues:
1. Check browser console for errors
2. Verify Firebase project settings
3. Ensure all configuration values are correct
4. Test in incognito mode to avoid cache issues

