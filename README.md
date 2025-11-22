# **TutorVerse – CST3144 Full Stack Development Coursework**

This project was completed for **CST3144 – Full Stack Development**.  
It includes a **Vue.js frontend** and an **Express.js backend**, both connected to **MongoDB Atlas**.  
The frontend is hosted on **GitHub Pages**, while the backend runs on **Render**.

---

## **🔗 Live Demo**
**Frontend (GitHub Pages):**  
https://godsend07.github.io/tutorverse-frontend/

---

## **📦 GitHub Repositories**

### **Frontend (Vue.js)**
- Repo:  
  https://github.com/godsend07/tutorverse-frontend  
- Live Demo:  
  https://godsend07.github.io/tutorverse-frontend/

### **Backend (Express.js)**
- Repo:  
  https://github.com/godsend07/tutorverse-backend  
- Live API (Render):  
  https://tutorverse-backend-o69h.onrender.com/lessons

---

## **📁 Project Structure (ZIP Submission)**

```
CST3144/
  TutorVerse/        ← Vue.js frontend (no node_modules)
  ExpressApp/        ← Express.js backend (no node_modules)
  README.md
```

Before zipping, **delete all node_modules**.

---

# **🎨 Frontend (Vue.js)**

Built using **Vue 3 (Composition API)**.  
Displays lessons, supports search/sort, and includes a simple booking/cart system.

### **Features**
- Lesson list with search and sorting  
- Simple cart/booking workflow  
- Form validation (name & phone)  
- Fetches data from live backend  
- Clean, minimal UI  

### **Run Locally**
```
cd TutorVerse
npm install
npm run dev
```

### **Deploy to GitHub Pages**
```
npm run build
npm run deploy
```

---

# **🛠️ Backend (Express.js)**

Built using **Node.js + Express**.  
Connected to **MongoDB Atlas** using the official MongoDB driver.  
CORS enabled for GitHub Pages.

### **Main API Endpoints**

#### **GET /lessons**
Returns all lessons.

#### **POST /orders**
Creates a new order.

**Example JSON body:**
```json
{
  "name": "John",
  "phone": "123456",
  "items": [
    { "_id": "lessonIdHere", "qty": 1 }
  ]
}
```

### **Run Backend Locally**
```
cd ExpressApp
npm install
node server.js
```

### **Example .env**
(Not included in submission)

```
MONGODB_URI= mongodb+srv://tutorverse_user:Tutor12345@tutorverse.mugyogj.mongodb.net/?retryWrites=true&w=majority
DB_NAME=tutorverse_db
PORT=8080
```

---

# **🌍 Hosting Summary**

- **Frontend:** GitHub Pages  
  https://godsend07.github.io/tutorverse-frontend/

- **Backend:** Render  
  https://tutorverse-backend-o69h.onrender.com/lessons

- **Database:** MongoDB Atlas (Cloud)

---

# **✅ Coursework Requirements Completed**

- Two separate GitHub repositories (frontend + backend)  
- Frontend deployed on GitHub Pages  
- Backend deployed on Render  
- Frontend successfully fetches data from live backend  
- Database connected via MongoDB Atlas  
- ZIP contains both applications (without node_modules)  
- README explains setup, hosting, and project structure  
- Application functionalities:  
  - Lesson display  
  - Search & sort  
  - Booking/cart  
  - Form validation  
  - API communication  
  - Database storage
