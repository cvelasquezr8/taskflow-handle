# TaskFlow – Handle Repository

This is the handle repository for the TaskFlow application. It includes both the frontend and backend as Git submodules, allowing unified development and deployment using Docker Compose.

---

## 🔧 Requirements

Before running the application, make sure you have the following tools installed on your system:

- Node.js – v18+ (for frontend development if needed)
- Docker – for containerizing backend, frontend, and PostgresSQL
- Docker Compose – for orchestrating multi-container Docker applications
- Git – to clone the repository and initialize submodules

📝 You do **not** need to install Postgres SQL Server or Node modules globally – Docker handles everything during build time.

---

## 📦 Repository Structure

```
taskflow-handle/
│
├── backend/        # Backend API (ASP.NET Core, Entity Framework, SQL Server)
├── frontend/       # Frontend app (React, Vite, Tailwind CSS)
└── docker-compose.yml
```

```
backend/
├── Controllers/            		# HTTP request handlers
├── Data/                   		# Database context and seed data
├── Dtos/                   		# Data Transfer Objects
├── Models/                 		# Entity models
├── Services/               		# Application logic and services
├── Migrations/             		# EF Core database migrations
├── Program.cs              		# Main entry point
├── appsettings.json        		# Configuration settings
├── Dockerfile              		# Backend container definition
├── task-management-backend.csproj  	# Project file
```

```
frontend/
├── src/
│ ├── components/           # Reusable UI components
│ ├── pages/                # Route-level pages (e.g. Login, Register, Tasks)
│ ├── context/              # Global state and Auth context
│ ├── services/             # API calls
│ ├── App.tsx               # Root component
│ └── main.tsx              # Entry point
├── Dockerfile              # Frontend container definition
├── vite.config.ts          # Vite configuration
├── package.json
├── tailwind.config.js
├── tsconfig.json
```

---

## 🚀 Quick Start (Local Development)

### 1. Clone the repository with submodules

```bash
git clone --recurse-submodules https://github.com/cvelasquezr8/taskflow-handle.git
cd taskflow-handle
```

If you already cloned without submodules:

```bash
git submodule update --init --recursive
```

---

### 2. Create the `.env` file in the root

Create a `.env` file with the following content:

```env
# Backend
#Backend
PORT=5297
DATABASE_NAME=TaskManagerDB
DATABASE_USERNAME=postgres
DATABASE_PASSWORD=postgres
DATABASE_HOST=postgres-db
DATABASE_PORT=5432
JWT_SECRET=este_es_un_secreto_super_secreto_para_firmar_tokens
CORS_URL=http://localhost:5174,http://localhost:5297


# Frontend
VITE_API_URL=http://localhost:5297
```

---

### 3. Start the application using Docker Compose

```bash
docker-compose up --build -d
```

This will:

- Start Postgres SQL Server
- Build and run the .NET backend
- Build and serve the React frontend (on port 5174)

🧪 Accessing the App:

- Frontend: [http://localhost:5174](http://localhost:5174)
- Backend API: [http://localhost:5297](http://localhost:5297)


---
## 🔐 Default Admin User
When the system starts for the first time, a default root user is created automatically. You can use this account to log in as an administrator.

```
email: root@taskflow.com
password: Admin123!
```
---

## 🆕 Temporary Passwords
Each new user is created with a temporary password

```
password: Temp1234!
```
---

## 📄 API Docs (Swagger)

Once the backend is running, access API docs at:

```
http://localhost:5297/swagger
```

---

### 🐳 Notes

To reset containers and remove volumes:

```bash
docker-compose down -v
```

Then start again:

```bash
docker-compose up --build -d
```

---

### 👨‍💻 Technologies Used

- **Frontend:** React, Vite, Tailwind CSS
- **Backend:** ASP.NET Core, Entity Framework Core, JWT
- **Database:** PostgresSQL
- **Containerization:** Docker, Docker Compose

---

### 📂 Related Repositories

- [taskflow-frontend](https://github.com/cvelasquezr8/taskflow-frontend)
- [taskflow-backend](https://github.com/cvelasquezr8/taskflow-backend)

---

