# AI Cold Email Generator 

A full-stack web application that generates personalized, high-converting cold emails using AI. Built with the MERN stack (MongoDB, Express, React, Node.js) and powered by the Groq AI API.

## Overview

AI Cold Email Generator helps professionals craft compelling cold emails instantly. Simply provide context about your target (recruiter, company, job role, etc.) and let AI generate a personalized, professional email. Perfect for job seekers, freelancers, and sales professionals looking to streamline their outreach.

---

##  Features

- **AI-Powered Email Generation** – Uses Groq API for fast, intelligent email creation
- **User Authentication** – Secure JWT-based authentication with email verification via OTP
- **Email History** – Track all generated emails with timestamps
- **Responsive UI** – Modern, mobile-friendly interface built with React & Tailwind CSS
- **Monorepo Setup** – Easy installation and concurrent development of frontend and backend
- **Environment-based Configuration** – Secure handling of API keys and sensitive data
- **MongoDB Integration** – Persistent storage for user data and email history

---

## Tech Stack

### Frontend
- **React 18** – UI library
- **Vite** – Fast build tool
- **Tailwind CSS** – Utility-first styling
- **React Router** – Client-side routing
- **Axios** – HTTP client
- **React Hot Toast** – Toast notifications
- **Heroicons** – Icon library

### Backend
- **Node.js & Express** – Server framework
- **MongoDB & Mongoose** – Database and ODM
- **JWT** – Secure authentication
- **Bcryptjs** – Password hashing
- **Nodemailer** – Email sending for OTP verification
- **Groq API** – AI email generation
- **CORS** – Cross-origin request handling

---

## 📋 Prerequisites

Ensure you have the following installed:
- **Node.js** (v16 or higher)
- **npm** or **yarn**
- **MongoDB** (local or cloud via MongoDB Atlas)
- **Git**

### Required API Keys
- **Groq API Key** – [Get it here](https://console.groq.com)
- **MongoDB URI** – Local or MongoDB Atlas connection string

---

## ⚙️ Installation & Setup

### 1. Clone the Repository
```bash
git clone https://github.com/shivam2026Er/AI-COLD-MAIL-GENERATOR.git
cd AI-COLD-MAIL-GENERATOR
```

### 2. Install Dependencies
Install dependencies for the root, server, and client in one command:
```bash
npm run install-all
```

This command runs:
- Root dependencies installation
- Server dependencies installation
- Client dependencies installation

### 3. Configure Environment Variables

Create a `.env` file in the `server` directory:
```bash
cd server
touch .env
```

Add the following variables:
```env
# MongoDB Connection
MONGODB_URI=mongodb+srv://<username>:<password>@cluster.mongodb.net/cold-mail-db

# JWT Configuration
JWT_SECRET=your_super_secret_jwt_key_here

# Groq AI API
GROQ_API_KEY=your_groq_api_key_here

# Email Configuration (for OTP)
EMAIL_USER=your_email@gmail.com
EMAIL_PASSWORD=your_app_specific_password

# Frontend URL
FRONTEND_URL=http://localhost:5173

# Server Port
PORT=5000
```

**Note:** For Gmail's `EMAIL_PASSWORD`, use an [App-Specific Password](https://support.google.com/accounts/answer/185833).

---

##  Running the Project

### Development Mode (Concurrent Frontend & Backend)
```bash
npm run dev
```
This starts:
- **Frontend** on `http://localhost:5173`
- **Backend** on `http://localhost:5000`

### Production Build
```bash
npm run build
```

### Start Only Backend
```bash
npm run start:server
```

### Start Only Frontend
```bash
npm run start:client
```

---

##  Project Structure

```
AI-COLD-MAIL-GENERATOR/
├── client/                    # React frontend
│   ├── src/
│   │   ├── App.jsx
│   │   ├── main.jsx
│   │   ├── index.css
│   │   ├── components/
│   │   │   ├── Layout.jsx
│   │   │   ├── Navbar.jsx
│   │   │   └── Sidebar.jsx
│   │   ├── context/
│   │   │   └── AuthContext.jsx
│   │   ├── pages/
│   │   │   ├── Dashboard.jsx
│   │   │   ├── LandingPage.jsx
│   │   │   ├── Login.jsx
│   │   │   ├── Signup.jsx
│   │   │   └── VerifyOtp.jsx
│   │   └── utils/
│   │       └── api.js
│   ├── package.json
│   ├── vite.config.js
│   ├── tailwind.config.js
│   └── postcss.config.js
│
├── server/                    # Express backend
│   ├── config/
│   │   └── db.js             # MongoDB connection
│   ├── controllers/
│   │   ├── aiController.js   # Email generation logic
│   │   └── authController.js # Authentication logic
│   ├── middleware/
│   │   └── authMiddleware.js # JWT verification
│   ├── models/
│   │   ├── User.js           # User schema
│   │   └── EmailHistory.js   # Email history schema
│   ├── routes/
│   │   ├── aiRoutes.js       # AI endpoints
│   │   └── authRoutes.js     # Auth endpoints
│   ├── utils/
│   │   └── sendEmail.js      # Email sending utility
│   ├── server.js
│   └── package.json
│
├── package.json              # Root monorepo config
└── README.md
```

---

##  API Endpoints

### Authentication Routes

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/signup` | Register a new user |
| POST | `/api/auth/login` | Login user |
| POST | `/api/auth/verify-otp` | Verify OTP for email verification |

**Example Signup Request:**
```json
{
  "email": "user@example.com",
  "password": "securePassword123"
}
```

### AI Routes

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/ai/generate` | Generate email using AI |
| GET | `/api/ai/history` | Get user's email generation history |

**Example Generate Email Request:**
```json
{
  "prompt": "Generate a cold email to Google's hiring manager about a Senior Frontend Designer position, mentioning 5 years of experience in UI/UX"
}
```

**Example Response:**
```json
{
  "success": true,
  "email": "Subject: Frontend Design Collaboration Opportunity\n\nDear Hiring Manager,\n\nI hope this message finds you well..."
}
```

---

##  Usage Guide

### 1. Sign Up
- Navigate to `http://localhost:5173`
- Click "Sign Up"
- Enter email and password
- Verify your email with the OTP sent

### 2. Generate Cold Email
- Log in to your account
- Go to Dashboard
- Enter your prompt/context (e.g., "Generate a cold email to TechCorp's HR manager about a Senior Developer position")
- Click "Generate Email"
- Copy the generated email or save it

### 3. View History
- All generated emails are automatically saved to your account
- Access them from the History section

---

##  Security Features

- **JWT Authentication** – Secure, token-based user sessions
- **Password Hashing** – Bcryptjs for secure password storage
- **Email Verification** – OTP-based email verification
- **Environment Variables** – Sensitive data stored securely
- **CORS Protection** – Controlled cross-origin requests
- **Input Validation** – Server-side validation of all inputs

---

## Future Enhancements

- [ ] Email template customization
- [ ] Bulk email generation
- [ ] A/B testing for email variants
- [ ] Advanced analytics and engagement tracking
- [ ] Integration with email clients
- [ ] Support for multiple AI models
- [ ] Scheduled email sending

---

##  Troubleshooting

### MongoDB Connection Error
- Verify `MONGODB_URI` in `.env`
- Ensure MongoDB service is running
- Check IP whitelist in MongoDB Atlas

### Groq API Error
- Verify `GROQ_API_KEY` is valid
- Check Groq API documentation
- Ensure you have remaining API quota

### Port Already in Use
```bash
# Kill process on port 5000 (Windows)
netstat -ano | findstr :5000
taskkill /PID <PID> /F

# Kill process on port 5173 (Windows)
netstat -ano | findstr :5173
taskkill /PID <PID> /F
```

---

##  License

This project is licensed under the **ISC License**.

---

##  Author

**Shivam Kumar Singh**

---

##  Contributing

Contributions are welcome! Feel free to:
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

##  Support

If you encounter any issues or have questions:
- Open an [Issue](https://github.com/shivam2026Er/AI-COLD-MAIL-GENERATOR/issues)
- Check existing documentation
- Review the troubleshooting section

---

## 📖 Resources

- [Groq API Documentation](https://console.groq.com/docs)
- [MongoDB Documentation](https://docs.mongodb.com/)
- [Express.js Documentation](https://expressjs.com/)
- [React Documentation](https://react.dev/)
- [Tailwind CSS Documentation](https://tailwindcss.com/)

---

**Happy cold emailing! 📧**
