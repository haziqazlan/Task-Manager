# 📋 Full-Stack Task Manager

A modern, full-featured task management application built with React, Node.js, Express, and MongoDB. Features secure JWT-based authentication, RESTful API design, and a beautiful, responsive UI.

## 🚀 Features

### Authentication & Security
- ✅ User registration and login
- ✅ JWT-based authentication
- ✅ Password hashing with bcrypt
- ✅ Secure session management
- ✅ Protected API routes

### Task Management
- ✅ Create, read, update, and delete tasks
- ✅ Task status tracking (pending/completed)
- ✅ Priority levels (low, medium, high)
- ✅ Due date assignment
- ✅ Task descriptions
- ✅ Real-time filtering by status
- ✅ Task counters and statistics

### User Interface
- ✅ Modern, gradient-based design
- ✅ Fully responsive layout
- ✅ Smooth animations and transitions
- ✅ Intuitive task editing
- ✅ Visual priority indicators
- ✅ Clean, professional styling

## 🛠️ Tech Stack

### Frontend
- **React 18** - UI library
- **Vite** - Build tool and dev server
- **Tailwind CSS** - Utility-first CSS framework
- **Lucide React** - Beautiful icon library

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** - MongoDB object modeling
- **JWT** - Authentication tokens
- **bcryptjs** - Password hashing

## 📦 Installation

### Prerequisites
- Node.js (v16 or higher)
- MongoDB (local or Atlas)
- npm or yarn

### 1. Clone the Repository
```bash
git clone <your-repo-url>
cd task-manager
```

### 2. Backend Setup
```bash
cd server
npm install

# Create .env file
cp .env.example .env

# Edit .env with your configuration
# MONGODB_URI=mongodb://localhost:27017/taskmanager
# JWT_SECRET=your-secret-key
# PORT=5000
```

### 3. Frontend Setup
```bash
cd ../client
npm install
```

### 4. Start MongoDB
If using local MongoDB:
```bash
# macOS/Linux
mongod

# Windows
net start MongoDB
```

Or use MongoDB Atlas (cloud) - update MONGODB_URI in .env

### 5. Run the Application

**Terminal 1 - Backend:**
```bash
cd server
npm run dev
# Server runs on http://localhost:5000
```

**Terminal 2 - Frontend:**
```bash
cd client
npm run dev
# Client runs on http://localhost:3000
```

## 🔐 API Endpoints

### Authentication
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/api/auth/register` | Register new user | No |
| POST | `/api/auth/login` | Login user | No |

### Tasks
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/tasks` | Get all user tasks | Yes |
| GET | `/api/tasks/:id` | Get single task | Yes |
| POST | `/api/tasks` | Create new task | Yes |
| PUT | `/api/tasks/:id` | Update task | Yes |
| DELETE | `/api/tasks/:id` | Delete task | Yes |

### Request/Response Examples

**Register/Login:**
```json
POST /api/auth/register
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "securepassword"
}

Response:
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": {
    "id": "507f1f77bcf86cd799439011",
    "name": "John Doe",
    "email": "john@example.com"
  }
}
```

**Create Task:**
```json
POST /api/tasks
Headers: { "Authorization": "Bearer <token>" }
{
  "title": "Complete project documentation",
  "description": "Write comprehensive README and API docs",
  "priority": "high",
  "dueDate": "2024-12-31"
}

Response:
{
  "_id": "507f1f77bcf86cd799439012",
  "title": "Complete project documentation",
  "description": "Write comprehensive README and API docs",
  "status": "pending",
  "priority": "high",
  "dueDate": "2024-12-31T00:00:00.000Z",
  "userId": "507f1f77bcf86cd799439011",
  "createdAt": "2024-10-15T10:30:00.000Z",
  "updatedAt": "2024-10-15T10:30:00.000Z"
}
```

## 🎨 Features Showcase

### Dashboard
- View all tasks at a glance
- Filter by status (All, Pending, Completed)
- Real-time task counters
- Priority-based visual indicators

### Task Creation
- Simple, intuitive form
- All fields clearly labeled
- Inline validation
- Instant feedback

### Task Management
- One-click status toggle
- Inline editing capabilities
- Confirm-free deletion
- Smooth animations

### Authentication
- Secure login/register flow
- Token-based sessions
- Automatic token refresh
- Logout functionality

## 🔧 Configuration

### Environment Variables

**Server (.env):**
```env
MONGODB_URI=mongodb://localhost:27017/taskmanager
JWT_SECRET=your-super-secret-jwt-key-change-this
PORT=5000
```

**Client (vite.config.js):**
- Proxy configured to forward `/api` requests to backend
- Default port: 3000

## 📱 Responsive Design

The application is fully responsive and works seamlessly on:
- 📱 Mobile devices (320px+)
- 📱 Tablets (768px+)
- 💻 Desktops (1024px+)
- 🖥️ Large screens (1440px+)

## 🚀 Deployment

### Backend (Heroku, Railway, Render)
1. Push code to GitHub
2. Connect repository to platform
3. Set environment variables
4. Deploy

### Frontend (Vercel, Netlify)
1. Push code to GitHub
2. Connect repository
3. Set build command: `npm run build`
4. Set publish directory: `dist`
5. Deploy

### MongoDB Atlas (Production Database)
1. Create free cluster at mongodb.com/cloud/atlas
2. Get connection string
3. Update MONGODB_URI in production env vars

## 🧪 Testing

### Manual Testing Checklist
- ✅ User registration with valid data
- ✅ User login with correct credentials
- ✅ Create task with all fields
- ✅ Update task title and description
- ✅ Toggle task status (pending ↔ completed)
- ✅ Delete task
- ✅ Filter tasks by status
- ✅ Logout and session clearing

### API Testing with Postman/Thunder Client
Import the endpoints and test with proper authorization headers.

## 🐛 Troubleshooting

**MongoDB Connection Error:**
- Ensure MongoDB is running
- Check MONGODB_URI in .env
- Verify network access (for Atlas)

**CORS Error:**
- Verify backend URL in frontend code
- Check CORS configuration in server.js

**Authentication Issues:**
- Clear localStorage
- Check JWT_SECRET consistency
- Verify token expiration (default: 7 days)

**Port Already in Use:**
```bash
# Kill process on port 5000
lsof -ti:5000 | xargs kill -9

# Or change PORT in .env
```

## 📈 Future Enhancements

- 🔔 Task notifications and reminders
- 👥 Task sharing and collaboration
- 📊 Analytics dashboard
- 🏷️ Task categories and tags
- 🔍 Advanced search and filtering
- 📎 File attachments
- 🎨 Theme customization
- 📱 Mobile app (React Native)

## 📄 License

MIT License - feel free to use this project for your portfolio or commercial purposes.

## 👨‍💻 Author

Built with ❤️ as a demonstration of full-stack development skills using modern web technologies.

## 🙏 Acknowledgments

- React team for the amazing library
- Tailwind CSS for the utility-first CSS framework
- MongoDB team for the flexible database
- Express.js community
- Lucide for beautiful icons
