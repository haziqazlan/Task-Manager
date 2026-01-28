# Quick Start

Want to get this running locally? Here's the fastest way:

## Prerequisites

- Node.js (I'm using v20, but v16+ should work)
- MongoDB (either local or Atlas account)
- A terminal

## Setup (5-10 minutes)

**1. Get the code**
```bash
git clone https://github.com/YOUR-USERNAME/task-manager-fullstack.git
cd task-manager-fullstack
```

**2. Backend**
```bash
cd server
npm install
```

Create `.env` file in the server folder:
```
MONGODB_URI=mongodb://localhost:27017/taskmanager
JWT_SECRET=literally-any-random-string-works-here
PORT=5000
```

If you're using MongoDB Atlas instead of local MongoDB, replace the MONGODB_URI with your connection string from Atlas.

**3. Frontend**
```bash
cd ../client
npm install
```

**4. Start it up**

Open two terminal windows.

Terminal 1:
```bash
cd server
npm run dev
```
Wait until you see "Server running on port 5000" and "Connected to MongoDB"

Terminal 2:
```bash
cd client
npm run dev
```

**5. Open the app**

Go to http://localhost:3000 in your browser. Register an account and you're good to go.

## Common Issues

**MongoDB won't connect:**
- If using local MongoDB, make sure it's actually running (`mongod` command)
- If using Atlas, check that you whitelisted all IPs (0.0.0.0/0) in Network Access
- Double-check your connection string in .env

**Port 5000 already in use:**
```bash
lsof -ti:5000 | xargs kill -9
```
Or just change PORT to something else in .env

**npm install errors:**
- Try `npm cache clean --force` then install again
- Make sure you're in the right directory
- Check your Node version

**"Cannot find module":**
- Did you run npm install in BOTH server and client directories?

## Testing the API

If you want to test the API directly, you can use Thunder Client or Postman:

```bash
# Register
POST http://localhost:5000/api/auth/register
{
  "name": "Test User",
  "email": "test@test.com",
  "password": "password123"
}

# Login (copy the token from response)
POST http://localhost:5000/api/auth/login
{
  "email": "test@test.com",
  "password": "password123"
}

# Get tasks (use token from login)
GET http://localhost:5000/api/tasks
Headers: Authorization: Bearer YOUR_TOKEN_HERE
```

## That's It

If you run into any issues not covered here, check the main README or open an issue on GitHub.
