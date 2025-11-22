TutorVerse – CST3144 Full Stack Development Coursework

This project was created for CST3144 – Full Stack Development.
It has two parts:

A Vue.js frontend (lesson browsing + booking/cart system)

An Express.js backend connected to MongoDB Atlas

The frontend is hosted on GitHub Pages and it fetches data from the backend deployed on Render.

Live Demo

Frontend (GitHub Pages):
https://godsend07.github.io/tutorverse-frontend/

GitHub Repositories
Frontend (Vue.js)

Repo:
https://github.com/godsend07/tutorverse-frontend

Live Deployment:
https://godsend07.github.io/tutorverse-frontend/

Backend (Express.js)

Repo:
https://github.com/godsend07/tutorverse-backend

Live API (Render):
https://tutorverse-backend-o69h.onrender.com/lessons

Project Structure (For ZIP Submission)
CST3144/
  TutorVerse/        ← Vue.js frontend (without node_modules)
  ExpressApp/        ← Express.js backend (without node_modules)
  README.md


Before zipping, remove all node_modules folders.

Frontend (Vue.js)

Built using Vue 3 – Composition API.

Main Features

Lesson list with search and sort

Simple shopping-cart style booking

Form validation (name + phone)

Fetches lessons from the live backend

Clean, easy UI layout

Run the Frontend Locally
cd TutorVerse
npm install
npm run dev

Deploy to GitHub Pages
npm run build
npm run deploy

Backend (Express.js)

Backend built with Node.js + Express.

Key Points

MongoDB Atlas database

Uses the MongoDB native driver

CORS enabled for GitHub Pages

Clean and simple routing

API Endpoints
Get all lessons
GET /lessons


Returns all lessons from the database.

Create an order
POST /orders


Example request body:

{
  "name": "John",
  "phone": "123456",
  "items": [
    { "_id": "lessonIdHere", "qty": 1 }
  ]
}

Run the Backend Locally
cd ExpressApp
npm install
node server.js

Example .env (Not included in submission)
MONGODB_URI= mongodb+srv://tutorverse_user:Tutor12345@tutorverse.mugyogj.mongodb.net/?retryWrites=true&w=majority
DB_NAME=tutorverse_db
PORT=8080

Hosting Summary

Frontend (GitHub Pages):
https://godsend07.github.io/tutorverse-frontend/

Backend (Render):
https://tutorverse-backend-o69h.onrender.com/lessons

Coursework Requirements Covered

Separate GitHub repos for frontend & backend

Frontend hosted on GitHub Pages

Backend hosted on Render

Both apps communicate over a live API

MongoDB Atlas database connected

ZIP submission contains both apps + README