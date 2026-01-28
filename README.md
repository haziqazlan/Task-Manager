# Task Manager - Full Stack Web App

A task management application I built to learn full-stack development with React, Node.js, and MongoDB. Started as a basic CRUD app and evolved into something with proper authentication, search, statistics, and a bunch of other features I thought would be useful.

**Live Demo:** [https://task-manager-green-beta-19.vercel.app](https://task-manager-green-beta-19.vercel.app)

**Backend:** [https://task-manager-backend-62y6.onrender.com](https://task-manager-backend-62y6.onrender.com)

## What It Does

This is a web app where you can manage your tasks - create them, mark them complete, set priorities and due dates, that kind of thing. I added JWT authentication so each user has their own private task list. The frontend is React with Tailwind for styling, backend is Node/Express, and MongoDB for the database.

Some features I'm particularly happy with:
- Statistics dashboard showing your task completion rate and what's overdue
- Search bar that filters through your tasks in real-time
- Different ways to sort tasks (by date, priority, due date)
- Shows you when tasks are overdue with red highlighting
- Password show/hide toggle (because I always mistype passwords)
- "Forgot password" flow (though the email part isn't wired up yet)

## Tech Stack

**Frontend**
- React 18
- Vite (much faster than Create React App)
- Tailwind CSS
- Lucide for icons

**Backend**
- Node.js & Express
- MongoDB with Mongoose
- JWT for authentication
- bcrypt for password hashing

## Running Locally

You'll need Node.js and either MongoDB installed locally or a MongoDB Atlas account (free tier works fine).

**1. Clone and install:**
```bash
git clone https://github.com/YOUR-USERNAME/task-manager-fullstack.git
cd task-manager-fullstack
```

**2. Backend setup:**
```bash
cd server
npm install
```

Create a `.env` file in the server directory:
```
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=some_random_secret_string
PORT=5000
```

**3. Frontend setup:**
```bash
cd client
npm install
```

**4. Run both servers:**

In one terminal:
```bash
cd server
npm run dev
```

In another terminal:
```bash
cd client
npm run dev
```

Frontend runs on `localhost:3000`, backend on `localhost:5000`.

## API Endpoints

All task endpoints require the `Authorization: Bearer <token>` header.

**Auth:**
- `POST /api/auth/register` - Create account
- `POST /api/auth/login` - Login

**Tasks:**
- `GET /api/tasks` - Get all your tasks
- `GET /api/tasks/:id` - Get one task
- `POST /api/tasks` - Create task
- `PUT /api/tasks/:id` - Update task
- `DELETE /api/tasks/:id` - Delete task

## Features Breakdown

### Authentication
- Register/login with email and password
- Password validation (min 6 characters)
- Show/hide password toggle
- "Forgot password" modal (frontend only for now)
- Better error messages that actually tell you what went wrong
- JWT tokens with 7-day expiration

### Task Management
- Create tasks with title, description, priority, and due date
- Edit everything inline - just click the edit icon
- Mark tasks complete with one click
- Delete with confirmation (learned this the hard way)
- Overdue tasks get highlighted in red
- Search through tasks by title or description
- Sort by newest, oldest, priority, or due date
- Filter by all/pending/completed

### Dashboard
- Stats showing total, pending, completed, overdue, and high priority tasks
- Progress bar with completion percentage
- Motivational message when you finish everything
- All stats update in real-time as you work

### UI/UX
- Responsive design (works on phones, tablets, desktop)
- Success messages that auto-dismiss after 5 seconds
- Loading states on buttons
- Hover effects and smooth transitions
- Sticky navbar so you can always logout
- Empty states with helpful messages

## Deployment

I deployed this using free tiers:
- Frontend on Vercel (auto-deploys from GitHub)
- Backend on Render (also auto-deploys)
- Database on MongoDB Atlas (512MB free tier)

Main gotcha: Make sure to allow all IPs (0.0.0.0/0) in MongoDB Atlas network settings, otherwise Render can't connect.

## Things I'd Add Next

- Email verification and actual password reset emails
- Task categories or tags
- Ability to share tasks with other users
- Dark mode (everyone asks for this)
- Keyboard shortcuts
- Export tasks to CSV
- Drag and drop to reorder
- Mobile app version

## Challenges I Ran Into

The CORS setup took me a while to get right for production. Also spent some time debugging why Render couldn't connect to MongoDB - turned out I needed to whitelist all IPs.

The overdue task detection was trickier than expected because of timezone handling. Had to make sure to compare dates properly.

Getting the search and sort to work together without re-fetching from the API every time was a good learning experience with React state management.

## What I Learned

This was my first real full-stack project with authentication. Learned a lot about:
- JWT tokens and how to handle them securely
- MongoDB schemas and relationships
- React hooks (especially useEffect and useState)
- Deploying separate frontend and backend
- Environment variables and keeping secrets safe
- API design and RESTful principles

## License

MIT - use it for whatever you want.

## Contact

Feel free to reach out if you have questions or want to chat about the code!

- GitHub: [@yourusername](https://github.com/yourusername)
- Email: your.email@example.com
