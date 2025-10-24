# 🩺 Pulsetrack Backend

The **Pulsetrack Backend** is a Node.js + Express REST API that powers the Pulsetrack health management platform.  
It handles user authentication, doctor and appointment management, and tracks user activities.

---

## ⚙️ Tech Stack
- Node.js + Express  
- MongoDB + Mongoose  
- JWT Authentication  
- bcrypt, Helmet, CORS  
- Deployment: Render  

---

## 🛠️ Clone and Install

```bash
git clone https://github.com/Devdave-02/Pulsetrack-Backend.git
cd pulsetrack-backend
npm install

| Entity          | Description                                 | Relationships                              |
| --------------- | ------------------------------------------- | ------------------------------------------ |
| **User**        | Stores user info like name, email, password | One-to-Many → `Activities`, `Appointments` |
| **Activity**    | Represents user’s health-related activities | Belongs to a `User`                        |
| **Doctor**      | Represents available doctors                | One-to-Many → `Appointments`               |
| **Appointment** | Booking made by a `User` with a `Doctor`    | Many-to-One → `User`, `Doctor`             |


🔐 Authentication Flow
JWT Access & Refresh Tokens for secure sessions
Access Token is sent in the Authorization header
Refresh Token is stored in cookies and used to reissue access tokens

🚀 API Documentation
🔑 Auth Routes
Method	Endpoint	Description
POST	/api/auth/register	Register a new user
POST	/api/auth/login	Log in and receive tokens
POST	/api/auth/logout	Log out and clear tokens

🏃 Activities Routes
Method	Endpoint	Description
POST	/api/activities	Create new activity
GET	/api/activities/	Get all user activities

🩺 Appointments Routes
Method	Endpoint	Description
POST	/api/appointments	Book an appointment
GET	/api/appointments/	Get user’s appointments

🧰 Environment Variables Overview
Variable	Description
MONGO_URI	MongoDB connection string
PORT	Backend server port
ACCESS_TOKEN_SECRET	JWT secret for access token
REFRESH_TOKEN_SECRET	JWT secret for refresh token
FRONTEND_URL	Allowed frontend origin (CORS)
VITE_API_URL	Frontend base URL for API requests

🌐 Deployment
Backend (Render): https://pulsetrack-backend.onrender.com
Frontend (Vercel): https://pulsetrack-frontend.vercel.app
