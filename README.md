# 🤖 HireBOT — Automated Recruitment Email & Workflow System

The project HireBOT aims to automate the process of communication between a college placement cell and multiple HR representatives from various companies. 
The system automatically sends invitation mails to companies with final-year student details categorized by department. It monitors email responses, segregates them into replied and unreplied, and sends appropriate follow-up or acknowledgment mails until the company provides a job description (JD). 
By integrating AI with the Model Context Protocol (MCP), HireBOT ensures intelligent mail classification, context-aware responses, and reliable automation, reducing manual workload and increasing placement outreach efficiency.
after human intervention only , it has to send mail.

---

## 🧱 Project Structure

```
HireBOT/
│
├── README.md
├── .env.example
├── deployment/
│   ├── docker-compose.yml
│   ├── Dockerfile
│   ├── ci-cd.yml
│   ├── nginx.conf
│   └── start.sh
│
├── backend/
│   ├── main.py
│   ├── requirements.txt
│   ├── core/
│   ├── models/
│   ├── db/
│   ├── api/
│   ├── services/
│   ├── middleware/
│   ├── tests/
│   └── celery_app.py
│
├── frontend/
│   ├── package.json
│   ├── vite.config.js
│   ├── src/
│   └── public/
│
├── docs/
│   ├── architecture-diagram.png
│   ├── db-schema.sql
│   ├── api-reference.md
│   └── llm-flowchart.png
│
└── .vscode/
```

---

## ⚙️ Backend Setup (FastAPI)

### 1️⃣ Create Virtual Environment
```bash
cd backend
python3 -m venv venv
source venv/bin/activate
```

### 2️⃣ Install Dependencies
```bash
pip install -r requirements.txt
```

### 3️⃣ Configure Environment Variables
Duplicate `.env.example` to `.env` and fill in real credentials:

```ini
DATABASE_URL=postgresql://user:password@localhost:5432/hirebot
SUPABASE_URL=https://your_supabase_url.supabase.co
SUPABASE_SERVICE_KEY=your_supabase_service_key
MAILJET_API_KEY=your_mailjet_api_key
MAILJET_SECRET_KEY=your_mailjet_secret
JWT_SECRET=your_generated_secret
REDIS_URL=redis://localhost:6379/0
MAIL_SENDER_EMAIL=placementcell@college.com
APP_URL=http://localhost:5173
```

### 4️⃣ Initialize Database
```bash
python db/init_db.py
```

### 5️⃣ Run Backend
```bash
uvicorn main:app --reload
```

Visit **http://localhost:8000/docs** for API Swagger UI.

---

## 💅 Frontend Setup (React + Vite)

### 1️⃣ Install Node Dependencies
```bash
cd frontend
npm install
```

### 2️⃣ Run Development Server
```bash
npm run dev
```
Frontend runs on **http://localhost:5173**.

---

## 🐳 Docker Setup (Optional)

### Build and Start All Services
```bash
cd deployment
docker-compose up --build
```
This spins up:
- FastAPI Backend  
- PostgreSQL  
- Redis  
- Nginx Reverse Proxy

---

## 🧠 Background Workers

If using Celery for async tasks:

```bash
celery -A celery_app.celery worker --loglevel=info
```

To run scheduled tasks:
```bash
python services/scheduler.py
```

---

## 🧪 Running Tests

### Backend Tests
```bash
pytest tests/
```

### Frontend Tests
```bash
npm run test
```

---

## 🧩 Tech Stack

| Layer | Technology |
|-------|-------------|
| Backend | FastAPI, SQLAlchemy, PostgreSQL, Redis, Supabase |
| Frontend | React (Vite), Tailwind CSS |
| Async Queue | Celery |
| Email Service | Mailjet API |
| Deployment | Docker, Nginx |
| Auth | JWT, Role-based Middleware |

---

## 📊 Key Features

✅ Automated recruitment email workflows  
✅ Candidate and HR dashboards  
✅ LLM integration for smart replies  
✅ Metrics and logs tracking  
✅ Secure authentication with JWT  
✅ Modular, scalable architecture  

---

## 📜 License

This project is licensed under the **MIT License**.

---

### 🚀 Developed by Boomika S
