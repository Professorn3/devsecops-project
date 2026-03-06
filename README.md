# 🔐 DevSecOps Project — User Manager API

A beginner DevSecOps project built as part of a school course. A simple User Manager REST API built with C# and .NET, containerized with Docker, version controlled with Git, and secured with an automated CI/CD pipeline using GitHub Actions and CodeQL security scanning.

---

## 🗺️ Project Overview

This project covers all 5 pillars of DevSecOps:

| Stage | What | Tool |
|-------|------|------|
| 1 | REST API | C# / ASP.NET Core |
| 2 | Version Control | Git & GitHub |
| 3 | Containerization | Docker |
| 4 | CI/CD Pipeline | GitHub Actions |
| 5 | Security Scanning | CodeQL (SAST) |

---

## 🚀 What the API does

A User Manager API that handles basic CRUD operations:

| Method | Route | Description |
|--------|-------|-------------|
| GET | `/users` | Get all users |
| GET | `/users/{id}` | Get a specific user |
| POST | `/users` | Create a new user |
| DELETE | `/users/{id}` | Delete a user |

Each user has:
- `Id` — unique identifier
- `Username` — their name
- `Email` — their email address
- `Role` — either `Admin` or `User` (defaults to `User` — least privilege principle)

---

## 🛠️ How to run locally

### Prerequisites
- [.NET 10 SDK](https://dotnet.microsoft.com/download)
- [Docker Desktop](https://www.docker.com/products/docker-desktop)
- Git

### Run with .NET

```bash
git clone https://github.com/Professorn3/devsecops-project.git
cd devsecops-project/taskapi
dotnet run
```

Visit: `http://localhost:YOUR_PORT/users`

### Run with Docker

```bash
docker build -t taskapi .
docker run -p 8080:8080 taskapi
```

Visit: `http://localhost:8080/users`

---

## 🔄 CI/CD Pipeline

Every push to `main` automatically triggers the pipeline:

```
Push code
    ↓
Job 1: Build & Test
    ↓ (only if passed)
Job 2: CodeQL Security Scan
    ↓
Results in GitHub Security tab
```

### Pipeline file
Located at `.github/workflows/pipeline.yml`

---

## 🔐 Security

This project uses **CodeQL** for Static Application Security Testing (SAST).

- Scans every push to `main` automatically
- Checks for common vulnerabilities (SQL injection, hardcoded secrets, etc.)
- Results visible in the GitHub **Security** tab
- Security job only runs if the build passes first

### Security principles applied
- **Least Privilege** — default user role is `User`, not `Admin`
- **Secrets management** — no hardcoded credentials in code
- **Automated scanning** — security is baked into the pipeline, not an afterthought

---

## 🐳 Docker

The app uses a **multi-stage build** for security and efficiency:

- **Stage 1 (build)** — uses the full .NET SDK to compile the app (~700MB)
- **Stage 2 (runtime)** — uses only the lightweight .NET runtime to run it (~200MB)

This means the final container has less attack surface and is smaller.

---

## 📁 Project Structure

```
taskapi/
├── Controllers/
│   └── UsersController.cs    ← handles API requests
├── Models/
│   └── User.cs               ← defines what a User looks like
├── .github/
│   └── workflows/
│       └── pipeline.yml      ← CI/CD + security pipeline
├── Program.cs                ← app entry point
├── Dockerfile                ← container instructions
├── TaskApi.csproj            ← project configuration
└── appsettings.json          ← app settings
```

---

## 📚 Course Context

This project was built as part of a **DevSecOps** program and connects to the following courses:

- ✅ Objektorienterad programmering C# — API built with C#
- ✅ CI/CD — GitHub Actions pipeline
- ✅ Agila metoder — iterative development
- 🔜 Containerteknik — Dockerfile & Docker
- 🔜 CM och Automatisering — pipeline automation
- 🔜 Microsoft Azure — cloud deployment
- 🔜 Molnsäkerhet — cloud security

---

## 👤 Author

**Professorn3** — DevSecOps student