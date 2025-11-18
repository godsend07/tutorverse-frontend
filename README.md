📘 TutorVerse – CST3144 Full Stack Development

This project is my coursework for CST3144 – Full Stack Development.
It includes a Vue.js frontend and an Express.js backend connected to MongoDB Atlas.
The frontend is deployed on GitHub Pages and fetches lesson data live from my Render backend.

🚀 Live Demo (Frontend)

GitHub Pages:
👉 https://godsend07.github.io/tutorverse-frontend/

🗂️ GitHub Repositories
Frontend (Vue.js App)

GitHub Repo:
👉 https://github.com/godsend07/tutorverse-frontend

GitHub Pages Deployment:
👉 https://godsend07.github.io/tutorverse-frontend/

Backend (Express.js App)

GitHub Repo:
👉 https://github.com/godsend07/tutorverse-backend

Render Deployment (API):
👉 https://tutorverse-backend-o69h.onrender.com/lessons

📦 Project Structure (for ZIP submission)
CST3144/
│
├── TutorVerse/        ← Vue.js frontend (no node_modules)
│
├── ExpressApp/        ← Express.js backend (no node_modules)
│
└── README.md


❗ Before creating the ZIP file, both node_modules folders must be deleted to keep the file under 10MB.

🧩 Frontend (Vue.js) Overview

Built with Vue 3

Uses:

Composition API (ref, computed)

Live sorting and filtering

Shopping cart functionality

Form validation (name + phone)

Fetches lessons from live backend using:

GET https://tutorverse-backend-o69h.onrender.com/lessons

How to run locally
cd TutorVerse
npm install
npm run dev

How to deploy
npm run build
npm run deploy

🧩 Backend (Express.js) Overview

Node.js + Express

MongoDB Atlas via mongodb driver

CORS enabled for GitHub Pages

Endpoints:

API Endpoints
✔ Get all lessons
GET /lessons


Returns all lessons from the “lessons” collection in MongoDB.

✔ Create an order
POST /orders
Body:
{
  "name": "John",
  "phone": "123456",
  "items": [
    { "_id": "...", "qty": 1 }
  ]
}

How to run backend locally
cd ExpressApp
npm install
node server.js

.env file (NOT included in submission)
MONGODB_URI=your connection string
DB_NAME=tutorverse_db
PORT=8080

🌐 Backend Hosting (Render)

The backend is hosted on Render at:

👉 https://tutorverse-backend-o69h.onrender.com

This allows GitHub Pages to fetch live lessons using CORS.

🎓 Coursework Requirements Covered

✔ Separate GitHub repos for frontend + backend
✔ 10+ commits (will add before submission)
✔ Frontend deployed on GitHub Pages
✔ Frontend connected to live backend via Fetch
✔ Backend hosted on Render
✔ MongoDB Atlas database
✔ ZIP file includes both project folders + README

🧑‍🎓 Student Notes

This project demonstrates a basic full-stack application with:

CRUD operations (READ lessons, CREATE orders)

Vue.js front-end features with dynamic UI

Express.js API connected to MongoDB

Deployment on GitHub Pages + Render