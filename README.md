# TutorVerse – CST3144 Full Stack Development

This project is my coursework for **CST3144 – Full Stack Development**.  
It includes a Vue.js frontend and an Express.js backend connected to MongoDB Atlas.  
The frontend is deployed on GitHub Pages and fetches lesson data from my Render backend.

---

## Live Demo (Frontend)

**GitHub Pages:**  
https://godsend07.github.io/tutorverse-frontend/

---

## GitHub Repositories

### Frontend (Vue.js App)

- GitHub Repo:  
  https://github.com/godsend07/tutorverse-frontend  

- GitHub Pages Deployment:  
  https://godsend07.github.io/tutorverse-frontend/

### Backend (Express.js App)

- GitHub Repo:  
  https://github.com/godsend07/tutorverse-backend  

- Render Deployment (API):  
  https://tutorverse-backend-o69h.onrender.com/lessons

---

## Project Structure (ZIP Submission)

```text
CST3144/
  TutorVerse/      ← Vue.js frontend (no node_modules)
  ExpressApp/      ← Express.js backend (no node_modules)
  README.md
Before creating the ZIP file, remove all node_modules folders.

Frontend (Vue.js)
Built with Vue 3 (Composition API)

Features:

Lesson list with search and sort

Shopping cart system

Form validation (name and phone)

Fetches lessons from the live backend

Run frontend locally
bash
Copy code
cd TutorVerse
npm install
npm run dev
Deploy frontend (GitHub Pages)
bash
Copy code
npm run build
npm run deploy
Backend (Express.js)
Node.js + Express

MongoDB Atlas using the MongoDB driver

CORS enabled for GitHub Pages

Main endpoints:

API Endpoints
Get all lessons
http
Copy code
GET /lessons
Returns all lessons from the lessons collection.

Create an order
http
Copy code
POST /orders
Example body:

json
Copy code
{
  "name": "John",
  "phone": "123456",
  "items": [
    { "_id": "lessonIdHere", "qty": 1 }
  ]
}
Run backend locally
bash
Copy code
cd ExpressApp
npm install
node server.js
Example .env file (not included in submission)
env
Copy code
MONGODB_URI=your-mongodb-connection-string
DB_NAME=tutorverse_db
PORT=8080
Hosting Summary
Frontend: GitHub Pages
https://godsend07.github.io/tutorverse-frontend/

Backend: Render
https://tutorverse-backend-o69h.onrender.com/lessons

Coursework Requirements Covered
Separate GitHub repos for frontend and backend

Deployed frontend on GitHub Pages

Frontend fetches data from live backend (Render)

Backend hosted on Render with MongoDB Atlas

ZIP contains both apps and this README