# AI Logs

## Project

Habit Tracker – 75 Day Habit Tracking Application

## Purpose of Using AI

AI was used as a development assistant during the implementation of the Habit Tracker application. The main purpose was to understand technical requirements, plan the application structure, debug issues, and improve the implementation.

AI was used for guidance and problem-solving rather than blindly copying complete solutions.

## Areas Where AI Was Used

### 1. Requirement Understanding

AI was used to break down the project requirements into smaller development tasks.

The main requirements identified were:

* User registration and login
* Habit creation
* Habit tracking
* Daily completion logs
* 75-day challenge progress
* Database storage
* Backend API
* Morning reminders for incomplete habits
* GitHub repository documentation

### 2. Project Architecture

AI helped decide a simple architecture for the application:

```text
Frontend
HTML + CSS + JavaScript
        ↓
REST API
        ↓
Node.js + Express
        ↓
SQLite Database
```

This structure keeps the frontend, backend and database responsibilities separated.

### 3. Database Design

AI was used to design the database structure.

Three main tables were created:

* `users`
* `habits`
* `habit_logs`

Relationships were designed so that:

```text
User
 ↓
Habits
 ↓
Habit Logs
```

A user can have multiple habits, and each habit can have multiple daily logs.

### 4. Backend Development

AI was used for guidance while implementing REST API endpoints such as:

```text
POST /api/register
POST /api/login
GET  /api/habits/:userId
POST /api/habits
```

The API handles communication between the frontend and SQLite database.

### 5. Debugging

AI was used to identify and troubleshoot errors during development.

One important issue was:

```text
ERR_CONNECTION_REFUSED
```

The frontend was trying to access:

```text
http://localhost:3000
```

while the application was running inside GitHub Codespaces.

The issue was resolved by serving the frontend through the Express server and using relative API paths such as:

```javascript
fetch("/api/register")
```

and:

```javascript
fetch("/api/login")
```

### 6. Database Testing

AI guidance was used to test database creation and API requests.

The database was initialized using:

```bash
node database.js
```

The backend was started using:

```bash
node server.js
```

### 7. Documentation

AI was also used to structure the project documentation, including:

* README.md
* REASONING.md
* AI_LOGS.md

## Example AI-Assisted Tasks

### Task 1

**Requirement:** Create a database for the Habit Tracker.

**AI assistance:** Suggested using SQLite with Node.js and Express and separating users, habits and daily logs into different tables.

### Task 2

**Requirement:** Connect the frontend login/register forms with the backend.

**AI assistance:** Suggested using JavaScript `fetch()` requests to communicate with the REST API.

### Task 3

**Problem:** Browser showed `ERR_CONNECTION_REFUSED`.

**AI assistance:** Helped identify the difference between the local browser environment and the GitHub Codespaces server environment and suggested serving the frontend from Express.

### Task 4

**Requirement:** Track progress for a 75-day challenge.

**AI assistance:** Helped structure the day and percentage calculation so that the challenge can display progress from Day 1 through Day 75.

## Human Contribution

The project implementation, testing, configuration and final decisions were performed by the developer.

AI was used as a supporting tool for:

* Understanding requirements
* Technical guidance
* Debugging
* Database planning
* API planning
* Documentation structure

All AI-assisted suggestions were reviewed and adapted according to the project requirements.

## Important Note

AI-generated suggestions were not treated as automatically correct. Errors were tested and corrected during development, and the final implementation was adjusted based on actual application behavior.
