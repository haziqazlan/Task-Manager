# Project Structure

Here's how the code is organized:

```
task-manager/
├── client/                 # React frontend
│   ├── src/
│   │   ├── App.jsx        # Main component (~600 lines - most of the app logic)
│   │   ├── main.jsx       # React entry point
│   │   └── index.css      # Tailwind imports and global styles
│   ├── index.html
│   ├── package.json
│   ├── vite.config.js     # Dev server config
│   ├── tailwind.config.js
│   └── postcss.config.js
│
├── server/                 # Node.js backend
│   ├── server.js          # Everything backend (~200 lines)
│   ├── package.json
│   └── .env.example       # Template for environment variables
│
├── README.md
├── QUICK_START.md
└── .gitignore
```

## Frontend (`client/`)

### `src/App.jsx`
This is where most of the action happens. It's a single-component React app that handles:

- Authentication state (login/register forms, password visibility toggle, validation)
- All the task CRUD operations
- Search and filter logic
- Sorting
- Statistics calculations
- UI state management (editing mode, success/error messages)

I kept it all in one file because the app isn't that complex yet. If it grows, I'd probably split it into:
- A `components/` folder (AuthForm, TaskList, TaskForm, StatsCard)
- A `hooks/` folder (useAuth, useTasks)
- Maybe context for sharing auth state

### `src/index.css`
Just Tailwind imports plus a few global resets. Nothing fancy.

### `vite.config.js`
Pretty standard Vite setup. Has a proxy configured so API calls to `/api` get forwarded to `localhost:5000` during development.

## Backend (`server/`)

### `server.js`
The entire backend is in this one file. It includes:

**Database Schemas:**
- User (name, email, hashed password)
- Task (title, description, status, priority, dueDate, userId)

**Routes:**
- Auth routes (register, login)
- Task routes (CRUD operations)
- Health check endpoint

**Middleware:**
- JWT verification
- CORS (configured for production URLs)
- JSON body parsing

I structured it this way because it's small enough that splitting it into separate route files felt like overkill. If I add more features (like task sharing or categories), I'd refactor into:
```
server/
├── models/
│   ├── User.js
│   └── Task.js
├── routes/
│   ├── auth.js
│   └── tasks.js
├── middleware/
│   └── auth.js
└── server.js
```

### `.env.example`
Template showing what environment variables you need. Never commit the actual `.env` file.

## Key Features by File

**App.jsx handles:**
- All React state (user, tasks, filters, search query, etc.)
- Form submissions (login, register, create task)
- API calls to backend
- Input validation
- Success/error message display
- Statistics calculations (completion rate, overdue count)
- Search filtering and sorting logic
- Responsive UI rendering

**server.js handles:**
- Database connection
- User authentication (password hashing, JWT generation)
- Protecting routes with JWT middleware
- Task CRUD with user isolation (users can only access their own tasks)
- Input validation
- Error handling

## Dependencies

**Frontend:**
- react & react-dom (UI)
- lucide-react (icons - much lighter than font-awesome)
- Vite (dev server & bundler - way faster than webpack)
- Tailwind & PostCSS (styling)

**Backend:**
- express (web framework)
- mongoose (MongoDB ORM)
- jsonwebtoken (for JWTs)
- bcryptjs (password hashing)
- cors (cross-origin requests)
- dotenv (environment variables)

**Dev Dependencies:**
- nodemon (auto-restart server on changes)
- Some Tailwind plugins

## File Sizes

App.jsx is definitely the biggest file (~600 lines). I could probably break it up, but honestly it's still pretty readable. Everything is organized into logical sections:

1. State declarations
2. Effects (auto-login, message auto-dismiss)
3. API functions (auth, tasks)
4. Helper functions (filtering, sorting, stats)
5. Render (auth screen vs main app)

## Design Decisions

**Why one big App.jsx?**
- The app isn't complex enough to warrant dozens of tiny files
- State is mostly related (tasks affect stats, search affects filters, etc.)
- Makes it easier to understand the flow
- Can always refactor later if needed

**Why no TypeScript?**
- Wanted to focus on learning the full-stack flow first
- Might add it later for better IDE autocomplete

**Why Vite instead of Create React App?**
- Much faster hot reload
- Smaller bundle size
- CRA is basically deprecated at this point

**Why MongoDB?**
- Good for this type of unstructured data
- Easy to change schema as I add features
- Free tier on Atlas is generous

## What I'd Refactor

If I were to continue building this:

1. Split App.jsx into smaller components
2. Add a proper folder structure (components, hooks, utils)
3. Extract API calls to a separate service file
4. Add TypeScript
5. Split backend into MVC pattern
6. Add tests (I know, I know)
7. Set up proper logging instead of console.log

But for now, it works and the code is maintainable. That's good enough for a learning project.
