TutorVerse – CST3144 Full Stack Development Coursework

This project was created for CST3144 – Full Stack Development.
It includes a Vue.js frontend and an Express.js backend, both connected to MongoDB Atlas.
The frontend is hosted on GitHub Pages, and it communicates with the backend deployed on Render.

Live Demo

Frontend (GitHub Pages):
https://godsend07.github.io/tutorverse-frontend/

GitHub Repositories
Frontend (Vue.js)

Repo: https://github.com/godsend07/tutorverse-frontend

Live Deployment: https://godsend07.github.io/tutorverse-frontend/

Backend (Express.js)

Repo: https://github.com/godsend07/tutorverse-backend

Live API (Render): https://tutorverse-backend-o69h.onrender.com/lessons

Project Structure (ZIP Submission)
CST3144/
  TutorVerse/        ← Vue.js frontend (without node_modules)
  ExpressApp/        ← Express.js backend (without node_modules)
  README.md


Note: Remove all node_modules before creating the ZIP file.

Frontend (Vue.js)

Built using Vue 3 (Composition API).
The frontend handles lesson display, searching, sorting, and a simple cart-style booking system.

Key Features

Lesson list with search and sorting

Basic shopping cart behaviour

Form validation (name, phone)

Fetches live data from the Render backend

Simple, clean UI layout

Run Locally
cd TutorVerse
npm install
npm run dev

Deploy to GitHub Pages
npm run build
npm run deploy

Backend (Express.js)

The backend handles API routes, database communication, and booking creation.
It uses the MongoDB native driver, CORS, and a clean folder structure.

API Endpoints
GET /lessons

Fetches all lessons from MongoDB.

POST /orders

Creates a new order.

Example body:

{
  "name": "John",
  "phone": "123456",
  "items": [
    { "_id": "lessonIdHere", "qty": 1 }
  ]
}

Run Backend Locally
cd ExpressApp
npm install
node server.js

Example .env (Not included in ZIP)
MONGODB_URI=your-mongodb-connection-string
DB_NAME=tutorverse_db
PORT=8080

Hosting Summary

Frontend: GitHub Pages
https://godsend07.github.io/tutorverse-frontend/

Backend: Render (Public API)
https://tutorverse-backend-o69h.onrender.com/lessons

Database: MongoDB Atlas (Cloud)

Coursework Requirements (Completed)

This project meets all CST3144 requirements:

1. Separate Frontend & Backend Repositories

Both parts have their own public GitHub repos

Code is structured and easy to navigate

2. Fully Deployed Application

Frontend deployed on GitHub Pages

Backend deployed on Render

Frontend communicates with the live backend successfully

3. Database Integration

MongoDB Atlas used for lessons and orders

Backend connects using environment variables

API returns JSON data for the frontend

4. Submission-Ready ZIP

Contains both applications

No node_modules included

Includes this README for guidance

5. Functional Frontend Features

Search, sort, booking/cart logic, form validation

Clean and simple UI appropriate for coursework

6. Functional Backend Features

API routes implemented

Data fetched from MongoDB

Orders stored correctly