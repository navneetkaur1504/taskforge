TASKFORGE — Team Task Manager
==============================

GitHub: [My repository link here]

OVERVIEW
--------
Taskforge is a full-stack team task management application built with vanilla HTML/CSS/JavaScript.
It includes authentication, project management, task tracking, role-based access control,
a Kanban board, and a real-time activity log — all persisted via localStorage.

FEATURES
--------
✅ Authentication (Signup / Login with validation)
✅ Role-Based Access Control (Admin / Member)
✅ Project Management (Create, Edit, Delete projects with color coding)
✅ Task Management (Create, Edit, Delete, Assign tasks)
✅ Task Status Tracking (To Do → In Progress → Done)
✅ Priority Levels (High / Medium / Low)
✅ Due Dates with Overdue Detection
✅ Kanban Board View (drag & drop between columns)
✅ Dashboard with stats and charts
✅ Team Member Management (invite, promote, remove)
✅ Activity Log (full audit trail)
✅ Search & Filter (by status, priority, project)
✅ Task Detail Side Panel
✅ Persistent storage (localStorage)
✅ Responsive design

DEMO CREDENTIALS
----------------
Admin Account:
  Email:    admin@demo.com
  Password: password123

Member Account:
  Email:    member@demo.com
  Password: password123

ROLE PERMISSIONS
----------------
Admin:
  - Create, edit, delete projects
  - Create, edit, delete any task
  - Invite and remove team members
  - Change member roles (Admin ↔ Member)
  - Full access to all features

Member:
  - View all projects and tasks
  - Create new tasks
  - Edit tasks assigned to them or created by them
  - Update task status (via board drag-drop or detail panel)
  - View team members and activity log

TECH STACK
----------
Frontend:  HTML5, CSS3, Vanilla JavaScript (ES6+)
Storage:   localStorage (browser-based persistence)
Fonts:     DM Sans, Syne, DM Mono (Google Fonts)
No external frameworks or build tools required.

PROJECT STRUCTURE
-----------------
team-task-manager.html
  ├── CSS (embedded <style>) — Dark theme with CSS variables
  ├── HTML — Auth screen + App screen with sidebar & pages
  │   ├── Auth (Login / Signup)
  │   ├── Dashboard (stats, charts, overdue, recent tasks)
  │   ├── Projects (grid view with progress bars)
  │   ├── Tasks (filterable table view)
  │   ├── Board (Kanban drag-and-drop)
  │   ├── Members (team management)
  │   └── Activity (audit log)
  └── JavaScript (embedded <script>)
      ├── Data Store (localStorage CRUD)
      ├── Auth Logic
      ├── RBAC (role-based rendering)
      ├── Render Functions (dashboard, projects, tasks, board)
      └── Modal / UI Helpers

DATA MODEL
----------
Users:    { id, name, email, password, role, color, createdAt }
Projects: { id, name, description, color, due, createdAt, createdBy }
Tasks:    { id, title, description, projectId, assigneeId, status, priority, due, createdAt, createdBy }
Activity: { id, userId, action, target, ts }

API DESIGN (REST — ready for backend integration)
-------------------------------------------------
POST   /api/auth/login
POST   /api/auth/signup
GET    /api/projects
POST   /api/projects
PUT    /api/projects/:id
DELETE /api/projects/:id
GET    /api/tasks
POST   /api/tasks
PUT    /api/tasks/:id
DELETE /api/tasks/:id
GET    /api/users
POST   /api/users/invite
PUT    /api/users/:id/role
DELETE /api/users/:id
GET    /api/activity

KNOWN LIMITATIONS
-----------------
- Data is stored in browser localStorage (not a remote database)
- Passwords are stored in plain text in localStorage (demo only — use bcrypt in production)
- No real email sending for invites (shows temp password in toast)
- Single-user session per browser tab

PRODUCTION UPGRADE PATH
-----------------------
To convert to a full backend-powered app:
1. Add Node.js/Express or FastAPI backend
2. Replace localStorage with PostgreSQL or MongoDB
3. Add JWT authentication with bcrypt password hashing
4. Implement WebSocket for real-time updates
5. Add email service (SendGrid) for invites
