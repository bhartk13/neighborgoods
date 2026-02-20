# 🏡 NeighborGoods

A simple, beautiful neighborhood marketplace web app for buying and selling items locally. Built with vanilla HTML/CSS/JavaScript and Firebase Realtime Database.

## ✨ Features

- **📱 Mobile-First Design** - Beautiful, responsive UI that works great on phones and tablets
- **🖼️ Multi-Image Support** - Upload up to 5 photos per listing with gallery navigation
- **📸 Full-Screen Image Viewer** - Tap any image to view it full-screen
- **💬 Easy Contact** - Buyers can express interest and contact sellers via SMS
- **🔐 Admin Panel** - Secure admin login to manage listings
- **✏️ Edit Listings** - Update title, price, description, and photos anytime
- **✅ Mark as Sold** - Track which items are still available
- **📝 Rich Text Formatting** - Support for bullet points and formatted descriptions
- **📱 SMS Notifications** - Optional Twilio integration for automatic notifications
- **🔔 Push Notifications** - Optional Pushover integration for instant alerts

## 🚀 Quick Start

### 1. Firebase Setup

1. **Create a Firebase Project**
   - Go to [Firebase Console](https://console.firebase.google.com/)
   - Click "Add Project"
   - Follow the setup wizard

2. **Enable Realtime Database**
   - In your Firebase project, go to **Realtime Database**
   - Click **Create Database**
   - Choose your location
   - Start in **test mode** (we'll update rules below)

3. **Configure Database Rules**
   - Go to **Realtime Database** → **Rules**
   - Update rules to allow public read access (buyers need to read listings):
   ```json
   {
     "rules": {
       ".read": true,
       ".write": true
     }
   }
   ```
   ⚠️ **Note**: For production, consider adding authentication and more restrictive write rules.

4. **Get Firebase Config**
   - Go to **Project Settings** (gear icon) → **General**
   - Scroll to "Your apps" → **Web app** (or add one)
   - Copy your Firebase configuration object

5. **Update Firebase Config in index.html**
   - Open `index.html`
   - Find the `firebaseConfig` object (around line 820)
   - Replace with your Firebase credentials:
   ```javascript
   const firebaseConfig = {
     apiKey: "YOUR_API_KEY",
     authDomain: "YOUR_PROJECT.firebaseapp.com",
     databaseURL: "https://YOUR_PROJECT-default-rtdb.firebaseio.com",
     projectId: "YOUR_PROJECT_ID",
     storageBucket: "YOUR_PROJECT.appspot.com",
     messagingSenderId: "YOUR_SENDER_ID",
     appId: "YOUR_APP_ID"
   };
   ```

### 2. Deploy to GitHub Pages

1. **Push to GitHub**
   ```bash
   git add .
   git commit -m "Initial commit"
   git push origin main
   ```

2. **Enable GitHub Pages**
   - Go to your repository on GitHub
   - Settings → **Pages**
   - Source: **Deploy from a branch**
   - Branch: **main** (or your default branch)
   - Folder: **/ (root)**
   - Click **Save**

3. **Access Your Site**
   - Your site will be available at: `https://YOUR_USERNAME.github.io/neighborgoods/`

## 👤 Admin Setup

### First-Time Login

1. **Default Password**: `*****`
2. Click **👤 Admin Login** button
3. Enter the default password
4. **⚠️ IMPORTANT**: Change your password immediately in **Security Settings**

### Admin Features

Once logged in, you can:

- **📤 Post New Items** - Add listings with title, price, description, and photos
- **✏️ Edit Listings** - Update any listing's details
- **✅ Mark as Sold** - Toggle sold status
- **🗑️ Delete Listings** - Remove items from the marketplace
- **📱 Configure Contact** - Set your phone number for buyer contact
- **🔐 Change Password** - Update admin password

### Forgot Password?

If you forget your admin password:

1. Click **👤 Admin Login**
2. When prompted for password, type **"reset"**
3. Confirm the reset
4. Log in again with default password: `*****`

## 📱 Contact Configuration

### Required: Seller Phone Number

**You must configure your phone number** for buyers to contact you:

1. Log in as admin
2. Go to **📱 Contact Configuration**
3. Enter your phone number with country code (e.g., `+1234567890`)
4. Click **Save Configuration**

This phone number is stored in Firebase so buyers can contact you even if they don't have admin access.

### Optional: Twilio SMS (Automatic Notifications)

Get automatic SMS notifications when buyers express interest:

1. Sign up at [Twilio](https://console.twilio.com) (free trial with $15 credit)
2. Get your **Account SID** and **Auth Token**
3. Get a **Twilio Phone Number** (free in trial)
4. Enter these in the admin panel under **📲 Twilio SMS Notifications**
5. Click **Save Twilio Settings**
6. Test with **📱 Test SMS** button

**Cost**: ~$0.01 per SMS notification

### Optional: Pushover Notifications

Get push notifications instead of SMS:

1. Sign up at [Pushover](https://pushover.net) (free for 30 days, then $5 one-time)
2. Get your **User Key**
3. Create an app at [pushover.net/apps/build](https://pushover.net/apps/build)
4. Get your **App Token**
5. Enter these in the admin panel under **📬 Pushover Notifications**
6. Click **Save Pushover Settings**
7. Test with **🔔 Test Notification** button

## 📝 Using the App

### For Sellers (Admin)

1. **Post an Item**
   - Log in as admin
   - Fill out the form: Title, Price, Description, Photos
   - Click **📤 Post Item**

2. **Format Descriptions**
   - Use bullet points by starting lines with `-`, `*`, or `•`
   - Example:
     ```
     Great condition
     - Barely used
     - Includes original box
     - All accessories included
     ```

3. **Manage Listings**
   - Click **✏️ Edit Listing** to update details
   - Click **✅ Mark as SOLD** when item is sold
   - Click **🗑️ Delete** to remove listings

### For Buyers

1. **Browse Listings**
   - View all available items on the homepage
   - Tap images to view full-screen
   - Swipe/click through multiple photos

2. **Express Interest**
   - Click **💬 I'm Interested** on any item
   - Enter your name (optional message)
   - Click **Send Message**
   - Your phone's SMS app will open with a pre-filled message to the seller

## 🛠️ Technical Details

### Tech Stack

- **Frontend**: Vanilla HTML, CSS, JavaScript
- **Backend**: Firebase Realtime Database
- **Image Conversion**: HEIC2Any library for iPhone photo support
- **Hosting**: GitHub Pages (or any static hosting)

### Browser Support

- ✅ Chrome/Edge (latest)
- ✅ Safari (latest)
- ✅ Firefox (latest)
- ✅ Mobile browsers (iOS Safari, Chrome Mobile)

### File Structure

```
neighborgoods/
├── index.html          # Main application file
├── firebase-config.js  # Firebase configuration template
├── .gitignore         # Git ignore rules
└── README.md          # This file
```

## 🔧 Troubleshooting

### "Firebase Not Configured" Warning

- Make sure you've updated the `firebaseConfig` object in `index.html`
- Verify your Firebase project has Realtime Database enabled
- Check that database rules allow read access

### "Contact information not configured" Error

- **Admin**: Make sure you've saved your phone number in **📱 Contact Configuration**
- **Buyers**: This means the seller hasn't configured their phone number yet
- Check Firebase console to verify `config/adminPhone` exists

### Can't Save Listings (PERMISSION_DENIED)

- Check Firebase Realtime Database rules
- Rules must allow `.write: true` for admin operations
- See "Configure Database Rules" section above

### Images Not Uploading

- Check file size (large images may fail)
- Try converting HEIC photos to JPEG first
- Ensure Firebase Storage is configured (if using Storage instead of base64)

### Admin Password Reset Not Working

- Clear browser localStorage manually:
  1. Open browser DevTools (F12)
  2. Go to **Application** → **Local Storage**
  3. Delete `adminPassword` key
  4. Refresh page

## 📄 License

This project is open source and available for personal use.

## 🤝 Contributing

Feel free to fork this project and customize it for your neighborhood!

## 📞 Support

For issues or questions:
- Check the troubleshooting section above
- Review Firebase console for database errors
- Check browser console (F12) for JavaScript errors

---

**Made with ❤️ for neighborhoods everywhere**
