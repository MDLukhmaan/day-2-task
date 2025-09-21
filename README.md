# Day 2 Task – Full Stack App (Express + PostgreSQL + React)

## 📂 Project Structure
```
day-2-task/
├── backend/          # Express server + PostgreSQL
│   ├── controllers/  # API controllers
│   ├── middleware/   # JWT middleware
│   ├── routes/       # API routes
│   ├── db.js         # Database connection
│   ├── server.js     # Entry point
│   ├── .env.example  # Example environment variables
│   ├── package.json
│
├── frontend/         # React application
│   ├── src/
│   │   ├── pages/    # Landing, SignUp, SignIn, Home
│   │   ├── api.js    # Axios instance
│   │   ├── App.js
│   │   └── index.js
│   ├── package.json
│
└── README.md         # This file
```

---

## ⚡ Backend Setup (Express + PostgreSQL)
1. Navigate to backend folder:
   ```bash
   cd backend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Copy `.env.example` to `.env` and update your DB credentials + JWT secret.

4. Create the `users` table in PostgreSQL:
   ```sql
   CREATE TABLE users (
     id SERIAL PRIMARY KEY,
     name VARCHAR(100) NOT NULL,
     phone VARCHAR(20) NOT NULL,
     email VARCHAR(100) UNIQUE NOT NULL,
     password_hash TEXT NOT NULL,
     created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
   );
   ```

5. Start backend server:
   ```bash
   npm run dev
   ```

   Server will run on: `http://localhost:5000`

---

## ⚡ Frontend Setup (React)
1. Navigate to frontend folder:
   ```bash
   cd frontend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start React app:
   ```bash
   npm start
   ```

   Frontend will run on: `http://localhost:3000`

---

## 🚀 Features
- **Sign Up** with name, phone, email, password.
- **Sign In** with email + password.
- **JWT Authentication** with protected route `/me`.
- **Frontend** with Landing, Sign Up, Sign In, Home pages.
- **LocalStorage** for token + user.

---

## ✅ Testing Checklist
- [ ] Sign Up with new email → success.
- [ ] Sign Up with existing email → error.
- [ ] Sign In with correct credentials → success.
- [ ] Sign In with wrong credentials → error.
- [ ] Access `/me` with token → success.
- [ ] Access `/me` without token → unauthorized error.
- [ ] Home page shows Name + Phone after login.

---

## 📸 Screenshots to Provide
1. sign up ![Alt Text](./assets/signup-success.png)
2. sign in ![Alt Text](./assets/signin-success.png)
3.home page ![Alt Text](./assets/homescreen.png)


---

# 🛠 Step-by-Step Run Guide

## 1. Setup PostgreSQL Databasegit
1. Open terminal/command prompt.
2. Login to PostgreSQL:
   ```bash
   psql -U postgres
   ```
3. Create a new database:
   ```sql
   CREATE DATABASE taskdb;
   ```
4. Exit PostgreSQL:
   ```sql
   \q
   ```
5. Import the users table:
   ```bash
   psql -U postgres -d taskdb -f users_table.sql
   ```

---

## 2. Run Backend
1. Navigate to backend folder:
   ```bash
   cd backend
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Copy `.env.example` → `.env` and fill values:
   ```env
   DB_USER=postgres
   DB_PASSWORD=yourpassword
   DB_HOST=localhost
   DB_PORT=5432
   DB_NAME=taskdb
   JWT_SECRET=your_jwt_secret
   JWT_EXPIRES_IN=1d
   ```
4. Start backend:
   ```bash
   npm run dev
   ```
   Runs on → `http://localhost:5000`

---

## 3. Run Frontend
1. Open new terminal and go to frontend:
   ```bash
   cd frontend
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Start React app:
   ```bash
   npm start
   ```
   Runs on → `http://localhost:3000`

---

## 4. Test with Postman
1. Import `Day2Task.postman_collection.json` into Postman.
2. Run **Sign Up** → should create user.
3. Run **Sign In** → get token.
4. Copy token → set it in collection variable `{{token}}`.
5. Run **Get Profile (/me)** → should return user data.

---

## 5. Test in Browser
- Go to `http://localhost:3000`
- Try Sign Up / Sign In from UI
- On success → redirects to Home with user info
