# ✅ TODO App — Laravel + Vue.js

This is a simple TODO application built using **Laravel** for the backend and **Vue.js** for the frontend. It allows users to perform **Create, Read, Update, and Delete (CRUD)** operations on a list of tasks, each having a title and a completion status.

---

## 📦 Tech Stack

-   Laravel (Backend API & Blade Template)
-   Vue.js 3 (Frontend via Laravel Vite)
-   Axios (API communication)
-   SQLite (Lightweight DB for quick setup)
-   Vite (Module bundler and dev server)

---

## ⚙️ Setup Instructions

### 1. Clone & Install Laravel Project

```bash
git clone <repo-url>
cd todo-app
composer install
cp .env.example .env
touch database/database.sqlite
php artisan key:generate
```

### 2. Configure `.env` file

Ensure the following values in `.env`:

```
DB_CONNECTION=sqlite
DB_DATABASE=/absolute/path/to/database/database.sqlite
```

### 3. Run Migrations

```bash
php artisan migrate
```

### 4. Install Node Dependencies

```bash
npm install
npm run dev
```

### 5. Serve Laravel App

```bash
php artisan serve
```

Visit: `http://localhost:8000`

---

## 📝 Features

-   ✅ List all tasks
-   ➕ Add new task
-   ✏️ Edit task title
-   ✅ Toggle task completion
-   ❌ Delete task
-   🔃 Instant updates via Vue.js & Axios
-   📦 Lightweight with no CSS frameworks (vanilla styles only)

---

## 📂 Folder Structure Highlights

```
resources/
├— js/
│   └— components/App.vue   # Main Vue.js Component
│   └— app.js               # Vue mount script
└— views/welcome.blade.php  # Blade host for Vue app

routes/
└— api.php                  # Task API Routes

app/
└— Http/
    └— Controllers/TaskController.php
└— Models/Task.php          # Eloquent Model

database/
└— migrations/xxxx_create_tasks_table.php
```

---

## 📌 API Endpoints

| Method | Endpoint          | Description     |
| ------ | ----------------- | --------------- |
| GET    | `/api/tasks`      | List all tasks  |
| POST   | `/api/tasks`      | Create new task |
| PUT    | `/api/tasks/{id}` | Update task     |
| DELETE | `/api/tasks/{id}` | Delete task     |

All responses are in JSON format and follow RESTful standards.

---

## 📘 Validation Rules

| Field     | Rules                 |
| --------- | --------------------- |
| title     | required, string      |
| completed | boolean (update only) |

---

## 👨‍💼 Author

Built with ❤️ by \[Your Name] as part of a technical test challenge.

---

## 📝 License

This project is open-source and free to use for learning and evaluation purposes.
