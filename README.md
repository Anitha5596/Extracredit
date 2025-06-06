# Portfolio Backend API

This is the backend for a Portfolio Builder application, developed using the **MEVN Stack** (MongoDB, Express.js, Vue.js, Node.js). It provides portfolio data like projects, skills, education, and certifications to a Vue.js frontend.

---

## Live Links

- **Deployed Backend (Render)**: [https://portfolio-backend-zbe7.onrender.com/api](https://portfolio-backend-zbe7.onrender.com/api)
- **Frontend GitHub Folder**: [`/Vue`](https://github.com/Anitha5596/Extracredit/tree/main/Vue)
- **Backend GitHub Folder**: [`/nodeproject`](https://github.com/Anitha5596/Extracredit/tree/main/nodeproject)
- **Full GitHub Repository**: [https://github.com/Anitha5596/Extracredit](https://github.com/Anitha5596/Extracredit)

---

## API Overview

### `GET /api`

Returns full portfolio data from MongoDB.

**Example response:**
```json
{
  "about": [...],
  "skills": [...],
  "projects": [...],
  "education": [...],
  "experience": [...],
  "certifications": [...],
  "contact": {
    "email": "akona4@unh.newhaven.edu",
    "phone": "203-666-7400"
  }
}
```

---

### `POST /api`

Adds a new project.

**Example request body:**
```json
{
  "name": "Portfolio Website",
  "description": "Built with Vue and hosted on Render",
  "tech": ["Vue.js", "Node.js", "MongoDB"]
}
```

---

## Features Implemented

- Node.js + Express backend
- MongoDB Atlas integration with `ObjectId`
- `GET` and `POST` endpoints for portfolio data
- Vue frontend-ready JSON structure
- Prepared for Render deployment
- Static file serving for `dist/` (optional Vue frontend)

---

## Local Setup (Backend)

### 1. Clone the repository
```bash
git clone https://github.com/Anitha5596/Extracredit.git
cd Extracredit/nodeproject
```

### 2. Install dependencies
```bash
npm install
```

### 3. Create `.env` file
```
PORT=5596
MONGODB_URI=mongodb+srv://anitha:<db_password>@cluster0.szv3odk.mongodb.net/?retryWrites=true&w=majority&appName=Cluster0
```

### 4. Start the server
```bash
node server.js
```

Access it at:
```
http://localhost:5596/api
```

---

## Local Setup (Frontend)

### 1. Navigate to Vue directory
```bash
cd Extracredit/Vue
```

### 2. Install dependencies
```bash
npm install
```

### 3. Run the development server
```bash
npm run serve
```

Open:
```
http://localhost:8080
```

---

## Project Structure

```
Extracredit/
├── Vue/               # Frontend (Vue.js)
│   └── src/, public/, App.vue, components/
├── nodeproject/       # Backend (Node.js + Express)
│   └── server.js, db.json, package.json
├── README.md          # This documentation
```

---

## Author

**Anitha Kona**  
🔗 GitHub: [https://github.com/Anitha5596](https://github.com/Anitha5596)

---
