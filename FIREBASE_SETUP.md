# 🔥 Firebase Setup for Real-Time Poker Tournament Manager

## Overview
This guide will help you set up Firebase to enable real-time synchronization across multiple devices for your poker tournament manager.

## Step 1: Create Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click "Create a project" or "Add project"
3. Enter a project name (e.g., "poker-tournament-manager")
4. Choose whether to enable Google Analytics (optional)
5. Click "Create project"

## Step 2: Enable Realtime Database

1. In your Firebase project, click on "Realtime Database" in the left sidebar
2. Click "Create database"
3. Choose a location (pick the closest to your users)
4. Start in test mode (we'll secure it later)
5. Click "Enable"

## Step 3: Get Configuration

1. Click the gear icon (⚙️) next to "Project Overview"
2. Select "Project settings"
3. Scroll down to "Your apps" section
4. Click the web icon (</>)
5. Register your app with a nickname (e.g., "poker-web-app")
6. Copy the configuration object

## Step 4: Update Your Code

Replace the placeholder Firebase configuration in your `index.html` file:

```javascript
const firebaseConfig = {
  apiKey: "YOUR_ACTUAL_API_KEY",
  authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
  databaseURL: "https://YOUR_PROJECT_ID-default-rtdb.firebaseio.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT_ID.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

## Step 5: Security Rules (Optional but Recommended)

In your Realtime Database, go to "Rules" tab and update the rules:

```json
{
  "rules": {
    "rooms": {
      "$roomId": {
        ".read": true,
        ".write": true
      }
    }
  }
}
```

## How It Works

1. **Room System**: Each game session gets a unique 6-character room ID
2. **Real-Time Sync**: All game state changes are automatically synced to Firebase
3. **Multi-Device Support**: Multiple players can join the same room using the room code
4. **Automatic Updates**: Changes appear instantly on all connected devices

## Features

✅ **Real-time player management** - See eliminations and rebuys instantly  
✅ **Live timer synchronization** - All devices show the same countdown  
✅ **Spotify music sync** - Music plays on all devices  
✅ **Break timer sync** - Break status synchronized across devices  
✅ **Connection status** - See if you're connected to Firebase  
✅ **Room sharing** - Share room code with other players  

## Troubleshooting

### Connection Issues
- Check if Firebase project is active
- Verify database rules allow read/write
- Check browser console for errors

### Sync Issues
- Ensure all devices are in the same room
- Check if Firebase configuration is correct
- Verify database URL is correct

### Performance
- Game state syncs every 10 seconds during active play
- Immediate sync on important actions (player elimination, rebuys, etc.)
- Break timers sync in real-time

## Cost

- **Free Tier**: 1GB storage, 10GB/month transfer
- **Paid Plans**: Start at $25/month for higher limits
- **Typical Usage**: Free tier should handle most poker tournaments

## Next Steps

1. Test with 2 devices in the same room
2. Share room code with other players
3. Enjoy real-time synchronized poker tournaments! 🎉

---

**Need Help?** Check the Firebase documentation or create an issue in your repository.
