![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python)
![Flask](https://img.shields.io/badge/Flask-2.3.3-black?logo=flask)
![React](https://img.shields.io/badge/React-18-blue?logo=react)
![TailwindCSS](https://img.shields.io/badge/TailwindCSS-3.4-teal?logo=tailwindcss)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Database-blue?logo=postgresql)
![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)
![Deployed on Render](https://img.shields.io/badge/Deployed%20on-Railway-3f72af?logo=render)


# Qareeb - Ramadan Companion

A comprehensive full-stack Ramadan companion application with secure authentication and role-based access control.
This is a secure, production-ready architecture. All user credentials are managed server-side with industry-standard password hashing.

## 🏗️ Architecture

### **Backend (Flask + SQLAlchemy + PostgreSQL/SQLite)**
- RESTful API with secure authentication
- Password hashing using `werkzeug.security` (PBKDF2-SHA256)
- PostgreSQL for production / SQLite for development
- User credentials stored encrypted in database
- Role-based access control (RBAC)

### **Frontend (Angular v18)**
- Modern UI with signals and computed properties
- HTTP-only communication with backend
- No credentials stored in frontend code
- LocalStorage for auth state only

## 🔐 Security Features

### ✅ **Implemented**
1. **Password Hashing**: All passwords stored using PBKDF2-SHA256
2. **Backend Authentication**: Login verification happens on server
3. **Secure User Creation**: Auto-generated secure passwords
4. **No Plain-Text Storage**: Passwords never stored in plain text
5. **API-Only User Management**: All user CRUD operations through backend
6. **CORS Protection**: Configured for specific origins

### 🚀 **Production Recommendations**
- Add JWT tokens for stateless authentication
- Implement rate limiting for login endpoints
- Add HTTPS/TLS encryption
- Use environment-based CORS origins
- Implement session timeout
- Add audit logging for security events

## 📁 Project Structure

```
deplyment/
├── backend/
│   ├── app.py                 # Flask app with secure endpoints
│   ├── models.py              # SQLAlchemy models
│   ├── requirements.txt       # Python dependencies
│   ├── .env                   # Environment variables (excluded from git)
│   └── instance/
│       └── qareeb.db          # SQLite database (excluded from git)
├── frontend/
│   ├── src/
│   │   ├── app.component.ts
│   │   ├── components/        # UI components
│   │   ├── services/
│   │   │   ├── data.service.ts    # API communication
│   │   │   └── auth.service.ts    # Secure authentication
│   │   └── environments/
│   │       ├── environment.ts      # Dev config
│   │       └── environment.prod.ts # Prod config
│   ├── angular.json
│   ├── package.json
│   └── tsconfig.json
└── .gitignore

## 🚀 Getting Started

### **Prerequisites**
- Python 3.8+
- Node.js 18+
- PostgreSQL (for production) or SQLite (auto-configured for dev)

### **Backend Setup**

1. **Navigate to backend directory**
   ```bash
   cd backend
   ```

2. **Create virtual environment**
   ```bash
   python -m venv venv
   .\venv\Scripts\activate  # Windows
   # source venv/bin/activate  # Linux/Mac
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment** (Optional - defaults to SQLite)
   ```bash
   # Edit .env file
   DATABASE_URL=postgresql://user:password@localhost:5432/qareeb
   SECRET_KEY=your-secret-key-here
   ```

5. **Run backend server**
   ```bash
   python app.py
   ```
   
   ✅ **Default admin user created automatically**:
   - Username: `qareeb.admin@duck.com`
   - Password: `QareebCommunitySuperAdmin@2026`

### **Frontend Setup**

1. **Navigate to frontend directory**
   ```bash
   cd frontend
   ```

2. **Install dependencies**
   ```bash
   npm install --legacy-peer-deps
   ```

3. **Run development server**
   ```bash
   npm run dev
   ```

4. **Access application**
   - Open browser to: `http://localhost:3000`
   - Admin panel: `http://localhost:3000/#/admin`

## 🔑 API Endpoints

### **Authentication**
- `POST /api/login` - Secure login with password verification

### **User Management (Admin Only)**
- `GET /api/admin/users` - Get all users
- `POST /api/admin/users` - Create new user
- `DELETE /api/admin/users/<id>` - Delete user
- `POST /api/admin/users/<id>/reset-password` - Reset password

### **Events**
- `GET /api/events` - Get all events
- `POST /api/events` - Create event
- `PUT /api/events/<id>` - Update event
- `DELETE /api/events/<id>` - Delete event

### **Catering Services**
- `GET /api/catering` - Get all services
- `POST /api/catering` - Create service
- `PUT /api/catering/<id>` - Update service
- `DELETE /api/catering/<id>` - Delete service

### **Markaz Updates**
- `GET /api/markaz` - Get all updates
- `POST /api/markaz` - Create update
- `PUT /api/markaz/<id>` - Update markaz
- `DELETE /api/markaz/<id>` - Delete markaz

### **Requests**
- `POST /api/requests` - Submit public request
- `GET /api/admin/requests` - Get pending requests (admin)
- `POST /api/admin/approve/<id>` - Approve request (admin)

## 👥 User Roles

- **super**: Full system access
- **event_manager**: Manage events
- **catering_manager**: Manage catering services
- **markaz_manager**: Manage markaz updates
- **alert_viewer**: View alerts/requests

## 🗄️ Database Schema

### **User Table**
- Stores admin users with hashed passwords
- Supports multiple roles per user
- City-level access scoping

### **Schedule Table**
- Religious and community events

### **DeliveryService Table**
- Catering services with tags (JSON)
- City-specific listings

### **Markaz Table**
- Jamaat updates and announcements

### **Request Table**
- Public submissions pending approval

## 📦 Deployment

### **Backend (Production)**
1. Update `DATABASE_URL` to PostgreSQL connection string
2. Set strong `SECRET_KEY`
3. Configure SMTP credentials
4. Enable production mode in Flask
5. Use a WSGI server (Gunicorn/uWSGI)

### **Frontend (Production)**
1. Update `environment.prod.ts` with production API URL
2. Build: `npm run build`
3. Deploy `dist/` folder to static hosting


---

**Developed by Thousif ibrahim
