# 🚀 Quick Start Guide

## Get Running in 5 Minutes!

### Step 1: Install Dependencies (2 minutes)

Open two terminal windows:

**Terminal 1 - Backend:**
```bash
cd task-manager/server
npm install
```

**Terminal 2 - Frontend:**
```bash
cd task-manager/client
npm install
```

### Step 2: Configure Environment (1 minute)

**In the server directory:**
```bash
# Create .env file
cp .env.example .env
```

**Edit .env and set:**
```env
MONGODB_URI=mongodb://localhost:27017/taskmanager
JWT_SECRET=my-super-secret-key-123
PORT=5000
```

**Note:** If you don't have MongoDB installed locally, you can:
- Install it: https://www.mongodb.com/try/download/community
- Or use MongoDB Atlas (free cloud): https://www.mongodb.com/cloud/atlas

### Step 3: Start MongoDB (30 seconds)

**If using local MongoDB:**
```bash
# macOS/Linux
mongod

# Windows
net start MongoDB
```

**If using MongoDB Atlas:**
- Sign up at mongodb.com/cloud/atlas
- Create a free cluster
- Get connection string
- Update MONGODB_URI in .env

### Step 4: Run the Application (30 seconds)

**Terminal 1 - Start Backend:**
```bash
cd server
npm run dev
```
You should see: `🚀 Server running on port 5000` and `✅ Connected to MongoDB`

**Terminal 2 - Start Frontend:**
```bash
cd client
npm run dev
```
You should see: `Local: http://localhost:3000`

### Step 5: Open and Test (1 minute)

1. Open browser to **http://localhost:3000**
2. Click "Register" and create an account
3. Start creating tasks!

## 🎉 That's it! You're ready to go!

## Common Issues & Solutions

**"MongoDB connection error"**
→ Make sure MongoDB is running (Step 3)

**"Port 5000 already in use"**
→ Change PORT=5001 in server/.env

**"Cannot find module"**
→ Run `npm install` in both server and client folders

**Frontend won't load**
→ Check that both terminals are running the dev servers

## Need Help?

Check the main README.md for detailed documentation, API endpoints, and troubleshooting guide.
