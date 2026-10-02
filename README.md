# 🎓 Placement Management System

<p align="center">
  <img src="https://img.shields.io/badge/React-19-61DAFB?style=for-the-badge&logo=react&logoColor=white" alt="React"/>
  <img src="https://img.shields.io/badge/Vite-8-646CFF?style=for-the-badge&logo=vite&logoColor=white" alt="Vite"/>
  <img src="https://img.shields.io/badge/Node.js-Backend-339933?style=for-the-badge&logo=node.js&logoColor=white" alt="Node.js"/>
  <img src="https://img.shields.io/badge/Express.js-API-000000?style=for-the-badge&logo=express&logoColor=white" alt="Express"/>
  <img src="https://img.shields.io/badge/MongoDB-Database-47A248?style=for-the-badge&logo=mongodb&logoColor=white" alt="MongoDB"/>
  <img src="https://img.shields.io/badge/JWT-Authentication-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white" alt="JWT"/>
  <img src="https://img.shields.io/badge/Cloudinary-File%20Storage-3448C5?style=for-the-badge&logo=cloudinary&logoColor=white" alt="Cloudinary"/>
</p>

<p align="center">
  <b>A full-stack web platform for managing students, companies, placement drives, applications, eligibility, and recruitment workflows.</b>
</p>

<p align="center">
  <a href="https://github.com/prakash-9610/Placement-management-system">
    View Repository
  </a>
</p>

---

## 📌 Overview

**Placement Management System** is a full-stack college placement management platform designed to simplify the interaction between students and placement administrators.

The system provides separate role-based experiences for:

* 🎓 **Students**
* 🛡️ **Admin / TPO**

Students can maintain their academic and professional profiles, upload resumes, discover eligible placement drives, apply for opportunities, and track their applications.

Administrators can manage companies, create and maintain placement drives, view eligible students, monitor applications, and access placement statistics through an administrative dashboard.

The application uses a **React + Vite frontend**, **Node.js + Express backend**, and **MongoDB** for persistent data storage.

---

# ✨ Key Features

## 🎓 Student Portal

### Authentication

* Student registration
* Student login
* JWT-based authentication
* Protected student routes
* Logout functionality
* Persistent login state

### Student Profile

Students can manage:

* Full name
* Email
* Phone number
* Enrollment number
* Branch
* Semester
* Graduation year
* CGPA
* Backlogs
* 10th percentage
* 12th percentage
* Skills
* About / profile description
* Resume

### 📄 Resume Management

Students can:

* Upload their resume
* Replace an existing resume
* Store uploaded resumes through Cloudinary
* Access their uploaded resume from their profile

### 💼 Placement Opportunities

Students can:

* View placement drives
* View eligible placement drives
* Check recruitment opportunities
* Review company and drive information
* Apply for placement drives
* Track submitted applications
* Withdraw applications where applicable

### 📊 Student Dashboard

The dashboard provides information such as:

* Eligible placement drives
* Recent applications
* Application status
* Academic information
* Profile completion
* Resume completion
* Skills profile
* Backlog information
* Recruitment activity

---

# 🛡️ Admin / TPO Portal

The administrator has dedicated protected routes and management tools.

### 📊 Admin Dashboard

Administrators can monitor placement-related information including:

* Student statistics
* Company information
* Placement drive statistics
* Application statistics
* Recruitment activity

### 🏢 Company Management

Admin can:

* Add companies
* View companies
* Update company information
* Upload company logos
* Deactivate companies
* Reactivate companies

### 📅 Placement Drive Management

Admin can:

* Create placement drives
* View placement drives
* Update placement drives
* Deactivate drives
* Reactivate drives
* View students eligible for a particular drive

### 📝 Application Management

Admin can:

* View applications
* Filter applications by placement drive
* View individual application details
* Update application status
* Add application remarks/details
* Monitor the recruitment lifecycle

### 👥 Student Management

Admin can access registered student profiles and review student academic/professional information.

---

# 🔐 Authentication & Authorization

The system implements role-based authentication for both students and administrators.

### Authentication Flow

```text
                ┌──────────────────┐
                │      User        │
                └────────┬─────────┘
                         │
                         ▼
                ┌──────────────────┐
                │   Login / Signup │
                └────────┬─────────┘
                         │
                         ▼
                ┌──────────────────┐
                │ Express API      │
                │ Authentication   │
                └────────┬─────────┘
                         │
                  Validate User
                         │
                         ▼
                ┌──────────────────┐
                │ JWT Access Token │
                │ + Refresh Token  │
                └────────┬─────────┘
                         │
                         ▼
                ┌──────────────────┐
                │ Role Verification│
                └───────┬──────────┘
                        │
              ┌─────────┴─────────┐
              ▼                   ▼
       ┌──────────────┐    ┌──────────────┐
       │   Student    │    │ Admin / TPO  │
       │   Dashboard  │    │   Dashboard  │
       └──────────────┘    └──────────────┘
```

The backend uses:

* JSON Web Tokens
* HTTP-only cookies
* Bearer token authentication
* Role-based authorization
* Password hashing with bcrypt
* Protected API routes

---

# 🏗️ System Architecture

```text
                         ┌─────────────────────┐
                         │       Browser       │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │ React + Vite       │
                         │ Frontend           │
                         └──────────┬──────────┘
                                    │
                              Axios / REST
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │ Express.js API      │
                         │ Node.js Backend     │
                         └──────────┬──────────┘
                                    │
                ┌───────────────────┼───────────────────┐
                │                   │                   │
                ▼                   ▼                   ▼
        ┌──────────────┐    ┌──────────────┐    ┌──────────────┐
        │ Authentication│    │ Controllers  │    │ Middleware   │
        │ & JWT         │    │ & Routes     │    │ Security     │
        └──────────────┘    └──────────────┘    └──────────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │ Mongoose ODM        │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │      MongoDB        │
                         └─────────────────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │     Cloudinary      │
                         │ Resume / Media      │
                         └─────────────────────┘
```

---

# 🧩 Core Modules

```text
Placement Management System
│
├── Authentication
│   ├── Student Registration
│   ├── Student Login
│   ├── Admin Registration
│   ├── Admin Login
│   ├── JWT Authentication
│   └── Logout / Token Refresh
│
├── Student Management
│   ├── Student Profile
│   ├── Academic Details
│   ├── Skills
│   ├── Resume
│   └── Profile Completion
│
├── Company Management
│   ├── Create Company
│   ├── Update Company
│   ├── Company Logo
│   ├── Activate Company
│   └── Deactivate Company
│
├── Placement Drives
│   ├── Create Drive
│   ├── Update Drive
│   ├── Activate / Deactivate
│   ├── Eligibility
│   └── Eligible Students
│
├── Applications
│   ├── Apply
│   ├── View Applications
│   ├── Withdraw Application
│   ├── Update Status
│   └── Application Remarks
│
└── Dashboards
    ├── Student Dashboard
    └── Admin Dashboard
```

---

# 🛠️ Technology Stack

## Frontend

| Technology                          | Purpose                |
| ----------------------------------- | ---------------------- |
| React 19                            | UI development         |
| Vite                                | Frontend build tooling |
| React Router                        | Client-side routing    |
| Axios                               | API communication      |
| React Hot Toast                     | Notifications          |
| Lucide React                        | Interface icons        |
| Tailwind CSS / Tailwind Vite plugin | UI styling             |

## Backend

| Technology    | Purpose                    |
| ------------- | -------------------------- |
| Node.js       | Runtime                    |
| Express.js    | REST API                   |
| Mongoose      | MongoDB ODM                |
| JWT           | Authentication             |
| bcrypt        | Password hashing           |
| Multer        | File upload handling       |
| Cloudinary    | Resume / media storage     |
| CORS          | Cross-origin communication |
| Cookie Parser | Cookie handling            |
| dotenv        | Environment configuration  |
| Nodemon       | Development server         |

---

# 📁 Project Structure

```text
Placement-management-system/
│
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── assets/
│   │   ├── components/
│   │   │   ├── common/
│   │   │   ├── HomePageDashboard/
│   │   │   └── studentDashboard/
│   │   │
│   │   ├── context/
│   │   ├── hooks/
│   │   ├── pages/
│   │   │   ├── admin/
│   │   │   ├── auth/
│   │   │   └── student/
│   │   │
│   │   ├── services/
│   │   │   ├── adminService.js
│   │   │   ├── api.js
│   │   │   ├── authService.js
│   │   │   └── studentService.js
│   │   │
│   │   ├── utils/
│   │   ├── App.jsx
│   │   ├── index.css
│   │   └── main.jsx
│   │
│   ├── package.json
│   ├── vite.config.js
│   └── vercel.json
│
├── major-backend/
│   ├── public/
│   ├── src/
│   │   ├── controllers/
│   │   ├── db/
│   │   ├── middlewares/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── utils/
│   │   ├── app.js
│   │   ├── constants.js
│   │   └── index.js
│   │
│   ├── env.js
│   ├── package.json
│   └── .prettierrc
│
└── .gitignore
```

---

# 🗄️ Database Models

MongoDB is used as the primary database.

The backend contains dedicated Mongoose models for:

* `User`
* `Admin`
* `StudentProfile`
* `Company`
* `PlacementDrive`
* `Application`

### Relationship Overview

```text
User
 │
 ├──────────────► StudentProfile
 │
 └──────────────► Authentication
                        │
                        ▼
                 Student / Admin


Company
   │
   ▼
PlacementDrive
   │
   ▼
Application
   │
   ▼
Student
```

---

# 🔌 REST API Structure

The backend exposes versioned REST endpoints under:

```text
/api/v1
```

### Main API Modules

```text
/api/v1/users
/api/v1/studentprofile
/api/v1/company
/api/v1/admin
/api/v1/placementdrive
/api/v1/application
/api/v1/dashboard
```

### Example Operations

```text
Authentication
POST   /api/v1/users/register
POST   /api/v1/users/login
POST   /api/v1/users/logout

Student Profile
GET    /api/v1/studentprofile/current-student-profile
PATCH  /api/v1/studentprofile/update-profile
PATCH  /api/v1/studentprofile/update-resume

Placement Drives
GET    /api/v1/placementdrive/all-drives
GET    /api/v1/placementdrive/my-eligible-drives
POST   /api/v1/placementdrive/create-placement-drive

Applications
POST   /api/v1/application/:driveId/apply
GET    /api/v1/application/my-applications
PATCH  /api/v1/application/:applicationId/withdraw
PATCH  /api/v1/application/:applicationId/status

Companies
GET    /api/v1/company/all-companies
POST   /api/v1/company/create-company
PATCH  /api/v1/company/:companyId
```

---

# 🔒 Security

The backend includes several security-oriented mechanisms.

### JWT Authentication

Authenticated requests can include:

```http
Authorization: Bearer <access_token>
```

### Password Security

Passwords are hashed using **bcrypt** before being persisted.

### HTTP Security Headers

The backend applies headers including:

```text
X-Content-Type-Options
X-Frame-Options
X-XSS-Protection
Referrer-Policy
```

### CORS Protection

The API uses configured allowed origins and credential-aware CORS handling.

### Rate Limiting

The backend implements in-memory request limiting for:

* General API requests
* Authentication attempts
* Placement application requests

### File Upload Handling

Multer is used for processing uploaded files, with Cloudinary used for remote media storage.

---

# 🚀 Getting Started

## 1. Clone the Repository

```bash
git clone https://github.com/prakash-9610/Placement-management-system.git

cd Placement-management-system
```

---

# 💻 Frontend Setup

Navigate to the frontend:

```bash
cd frontend
```

Install dependencies:

```bash
npm install
```

Create a `.env` file:

```env
VITE_API_URL=http://localhost:8000/api/v1
```

Start the development server:

```bash
npm run dev
```

Frontend will normally be available at:

```text
http://localhost:5173
```

---

# ⚙️ Backend Setup

Open another terminal and navigate to:

```bash
cd major-backend
```

Install dependencies:

```bash
npm install
```

Create a `.env` file.

Example configuration:

```env
PORT=8000

MONGODB_URI=your_mongodb_connection_string

DB_NAME=placement_management

ACCESS_TOKEN_SECRET=your_access_token_secret

ACCESS_TOKEN_EXPIRY=1d

REFRESH_TOKEN_SECRET=your_refresh_token_secret

REFRESH_TOKEN_EXPIRY=7d

CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name

CLOUDINARY_API_KEY=your_cloudinary_api_key

CLOUDINARY_API_SECRET=your_cloudinary_api_secret

CORS_ORIGIN=http://localhost:5173
```

Then start the backend:

### Development

```bash
npm run dev
```

### Production

```bash
npm start
```

The backend defaults to:

```text
http://localhost:8000
```

Health check:

```text
GET /
```

Expected response:

```text
backend is running
```

---

# 🔄 Application Flow

### Student Flow

```text
Landing Page
     │
     ▼
Student Signup / Login
     │
     ▼
Student Dashboard
     │
     ├──► Complete Profile
     │
     ├──► Upload Resume
     │
     ├──► View Eligible Drives
     │
     ├──► Apply
     │
     └──► Track Applications
```

### Admin Flow

```text
Admin Login
     │
     ▼
Admin / TPO Dashboard
     │
     ├──► Manage Companies
     │
     ├──► Create Placement Drive
     │
     ├──► View Eligible Students
     │
     ├──► Manage Applications
     │
     └──► Monitor Placement Statistics
```

---

# 📊 Role-Based Access

| Feature                 | Student | Admin / TPO |
| ----------------------- | :-----: | :---------: |
| Register                |    ✅    |      ✅      |
| Login                   |    ✅    |      ✅      |
| Manage Own Profile      |    ✅    |      —      |
| Upload Resume           |    ✅    |      —      |
| View Placement Drives   |    ✅    |      ✅      |
| View Eligible Drives    |    ✅    |      ✅      |
| Apply to Drive          |    ✅    |      —      |
| Withdraw Application    |    ✅    |      —      |
| View Own Applications   |    ✅    |      —      |
| Manage Companies        |    —    |      ✅      |
| Create Placement Drives |    —    |      ✅      |
| Update Placement Drives |    —    |      ✅      |
| View Eligible Students  |    —    |      ✅      |
| Manage Applications     |    —    |      ✅      |
| View Student Profiles   |    —    |      ✅      |
| Dashboard Statistics    |    ✅    |      ✅      |

---

# 🎨 Frontend Routing

The frontend uses protected React Router routes.

### Public Routes

```text
/
 /login
 /signup
```

### Student Routes

```text
/student-dashboard
/placement-drives
/my-applications
/student-profile
```

### Admin Routes

```text
/admin-dashboard
/admin/drives
/admin/companies
/admin/applications
```

Unauthorized users are prevented from accessing protected role-specific routes.

---

# ☁️ File Storage

The backend integrates **Cloudinary** for file storage.

Uploaded content can include:

* Student profile avatars
* Student resumes
* Company logos

The database stores references such as:

```text
url
publicId
```

This keeps the application database focused on metadata while files are handled by the media storage service.

---

# 🧪 Development

Frontend linting:

```bash
cd frontend
npm run lint
```

Frontend production build:

```bash
npm run build
```

Frontend preview:

```bash
npm run preview
```

Backend development:

```bash
cd major-backend
npm run dev
```

---

# 🌐 Deployment

The frontend contains a `vercel.json` configuration and can be deployed to **Vercel**.

The Express backend can be deployed on Node.js-compatible hosting such as:

* Render
* Railway
* VPS
* Cloud platforms
* Other Node.js hosting services

For production deployment, configure:

```text
VITE_API_URL
MONGODB_URI
ACCESS_TOKEN_SECRET
REFRESH_TOKEN_SECRET
CLOUDINARY credentials
CORS_ORIGIN
```

Make sure the frontend's production origin is included in the backend CORS configuration.

---

# 🧭 Future Enhancements

Potential extensions for the platform include:

* 📧 Email notifications for placement updates
* 🔔 Real-time application notifications
* 📈 Advanced placement analytics
* 📄 Resume parsing and profile auto-generation
* 🤖 AI-assisted resume analysis
* 🎯 Intelligent job/drive recommendations
* 📱 Progressive Web App support
* 📊 Placement reports and export functionality
* 🏫 Multi-college / multi-institute support
* 🔐 Stronger production-grade distributed rate limiting
* 🧪 Automated API and frontend testing

---

# 🤝 Contributing

Contributions are welcome.

```bash
# Fork the repository

# Create a feature branch
git checkout -b feature/your-feature

# Make your changes

# Commit
git commit -m "Add your feature"

# Push
git push origin feature/your-feature
```

Then open a Pull Request.

---

# 📄 License

This project currently does not specify an open-source license in the repository.

Add a `LICENSE` file if you intend to distribute the project under a particular open-source license.

---

.

<p align="center">

**Built for simplifying college placement management.**

</p>
