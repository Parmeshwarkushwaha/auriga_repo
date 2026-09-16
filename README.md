# Habit Tracker

A simple and user-friendly Habit Tracker web application that helps users create habits, track daily completion, and monitor their progress through a 75-day challenge.

## Features

* User Registration and Login
* Create and manage habits
* Add habit description
* Select habit frequency
* Select specific weekdays
* Set habit start date
* Track daily habit completion
* 75-day challenge progress tracking
* Day-wise progress percentage
* User-specific habit data
* SQLite database for persistent data storage
* REST API using Node.js and Express
* Responsive and simple user interface

## Tech Stack

### Frontend

* HTML5
* CSS3
* JavaScript

### Backend

* Node.js
* Express.js

### Database

* SQLite

### Other Technologies

* REST API
* CORS
* Git & GitHub
* GitHub Codespaces

## Project Structure

```text
Habit-Tracker/
│
├── index.html
├── style.css
├── script.js
├── server.js
├── database.js
├── habit_tracker.db
├── package.json
├── package-lock.json
└── README.md
```

## Database Structure

The application uses SQLite with three main tables.

### 1. Users

Stores registered user information.

| Column     | Type     | Description           |
| ---------- | -------- | --------------------- |
| id         | INTEGER  | Unique user ID        |
| name       | TEXT     | User name             |
| email      | TEXT     | User email            |
| password   | TEXT     | User password         |
| created_at | DATETIME | Account creation time |

### 2. Habits

Stores habits created by users.

| Column      | Type     | Description                          |
| ----------- | -------- | ------------------------------------ |
| id          | INTEGER  | Unique habit ID                      |
| user_id     | INTEGER  | ID of the user who created the habit |
| name        | TEXT     | Habit name                           |
| description | TEXT     | Habit description                    |
| frequency   | TEXT     | Habit frequency                      |
| weekdays    | TEXT     | Selected weekdays                    |
| start_date  | DATE     | Habit start date                     |
| archived    | INTEGER  | Archive status                       |
| created_at  | DATETIME | Habit creation time                  |
| updated_at  | DATETIME | Last update time                     |

### 3. Habit Logs

Stores daily habit completion.

| Column    | Type    | Description        |
| --------- | ------- | ------------------ |
| id        | INTEGER | Unique log ID      |
| habit_id  | INTEGER | Related habit ID   |
| log_date  | DATE    | Date of completion |
| completed | INTEGER | Completion status  |

A unique constraint is used for each habit and date combination to avoid duplicate daily logs.

## API Endpoints

### Register User

```http
POST /api/register
```

Request:

```json
{
  "name": "John",
  "email": "john@example.com",
  "password": "123456"
}
```

Response:

```json
{
  "message": "Account created successfully.",
  "userId": 1
}
```

### Login User

```http
POST /api/login
```

Request:

```json
{
  "email": "john@example.com",
  "password": "123456"
}
```

### Get User Habits

```http
GET /api/habits/:userId
```

Example:

```http
GET /api/habits/1
```

### Add Habit

```http
POST /api/habits
```

Request:

```json
{
  "userId": 1,
  "name": "Exercise",
  "description": "Daily workout",
  "frequency": "daily",
  "weekdays": [],
  "startDate": "2026-09-16"
}
```

## Installation and Setup

### 1. Clone the Repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
```

Move into the project directory:

```bash
cd Habit-Tracker
```

### 2. Install Dependencies

Run:

```bash
npm install
```

The project uses the following main dependencies:

```bash
npm install express sqlite3 cors
```

### 3. Create the Database

Run:

```bash
node database.js
```

This creates the SQLite database:

```text
habit_tracker.db
```

and creates the required tables.

### 4. Start the Backend Server

Run:

```bash
node server.js
```

You should see:

```text
Database connected successfully!
Server running on http://localhost:3000
```

### 5. Run the Application

If using GitHub Codespaces:

1. Open the **PORTS** tab.
2. Find port **3000**.
3. Open the forwarded port URL in the browser.
4. The Habit Tracker application will open.

The Express server serves the frontend files and API from the same application.

## How the Application Works

The application follows this flow:

```text
User
  ↓
index.html
  ↓
script.js
  ↓
Express REST API
  ↓
SQLite Database
```

### Registration

1. User enters name, email and password.
2. Frontend sends the data to `/api/register`.
3. Express receives the request.
4. User information is stored in the `users` table.
5. Server sends a success response.

### Login

1. User enters email and password.
2. Frontend sends the credentials to `/api/login`.
3. Server checks the `users` table.
4. If credentials are correct, user information is returned.
5. The application opens the habit dashboard.

### Habit Creation

1. User enters habit details.
2. Frontend sends the habit data to `/api/habits`.
3. Server stores the habit in the `habits` table.
4. The habit becomes available for tracking.

### Habit Tracking

Each habit can be marked as completed for a particular date.

The completion information is stored in the `habit_logs` table.

## 75-Day Challenge

The application supports a 75-day challenge.

Example:

```text
Day 1 of 75
1%

Day 2 of 75
2%

Day 3 of 75
3%

...

Day 75 of 75
100%
```

The challenge progress is calculated based on the number of days completed from the challenge start date.

## Reminder Feature

The application is designed to remind users about habits that have not been logged for the current day.

The reminder system can notify users each morning about incomplete habits.

## Error Handling

The backend handles common errors such as:

* Missing registration fields
* Duplicate email registration
* Invalid login credentials
* Missing habit information
* Database errors
* Invalid API requests

Example error response:

```json
{
  "error": "Invalid email or password."
}
```

## Development

Start the server using:

```bash
node server.js
```

For development, make changes to the frontend files and restart the server when backend changes are made.

## Debugging

### Server Not Starting

Check whether Node.js is installed:

```bash
node -v
```

Check npm:

```bash
npm -v
```

Then install dependencies:

```bash
npm install
```

### Database Error

Recreate the database by running:

```bash
node database.js
```

If necessary, remove the existing `habit_tracker.db` file and run:

```bash
node database.js
```

again.

### API Connection Error

Make sure the backend is running:

```bash
node server.js
```

For GitHub Codespaces, make sure port **3000** is forwarded and the application is opened using the forwarded URL.

### Login/Register Not Working

Check:

1. Server is running.
2. Port 3000 is forwarded.
3. Browser is opened using the Codespaces forwarded URL.
4. Browser console for JavaScript errors.
5. Terminal for backend/database errors.

## Future Improvements

The following features can be added in future versions:

* Password hashing using bcrypt
* JWT-based authentication
* Edit and delete habits
* Habit streak tracking
* Calendar-based habit history
* Charts and statistics
* Email/browser notifications
* Morning habit reminders
* Dark mode
* Cloud database
* Deployment to a production server
* User profile management

## Project Goal

The goal of this project is to provide a simple habit tracking system where users can create habits, track their daily progress, and complete a structured 75-day challenge while storing their data persistently in a database.

## Author

**Parmeshwar Kushwaha**

GitHub: `<YOUR_GITHUB_PROFILE_URL>`
