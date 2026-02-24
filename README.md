<p align="center">
  <h1 align="center">🩺 HealthDesk</h1>
  <p align="center">
    A full-stack Doctor Appointment Booking System built with the MERN Stack
    <br />
    <strong>Book appointments · Manage doctors · Track schedules</strong>
  </p>
</p>

---

## 📋 Table of Contents

- [About the Project](#-about-the-project)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Environment Variables](#environment-variables)
  - [Installation](#installation)
- [API Reference](#-api-reference)
- [Deployment](#-deployment)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🏥 About the Project

**HealthDesk** is a comprehensive doctor appointment booking platform that connects patients with healthcare providers. The system features three distinct interfaces:

- **Patient Portal** — Browse doctors by speciality, book appointments with available time slots, manage profile, and track appointment history.
- **Admin Panel** — Dashboard with analytics, manage doctors (add/remove), view all appointments, and control doctor availability.
- **Doctor Panel** — Personal dashboard with earnings overview, manage appointments (complete/cancel), and update profile & availability.

---

## ✨ Features

### 👤 Patient (Client-Side)
- User registration & login with JWT authentication
- Browse doctors by speciality (General Physician, Gynecologist, Dermatologist, Pediatrician, Neurologist, Gastroenterologist)
- View detailed doctor profiles (experience, fees, about, address)
- Book appointments with real-time slot availability
- View and cancel upcoming appointments
- Update personal profile with image upload
- Responsive design with mobile support

### 🔧 Admin Panel
- Secure admin login
- Dashboard with key metrics (total doctors, appointments, patients)
- Add new doctors with image upload to Cloudinary
- View and manage all doctors list
- Toggle doctor availability
- View all appointments and cancel if needed
- Latest appointments overview

### 👨‍⚕️ Doctor Panel
- Secure doctor login
- Dashboard with earnings, appointment count, and patient stats
- View and manage personal appointments
- Mark appointments as completed
- Cancel appointments
- Update profile information (fees, address, availability)

---

## 🛠 Tech Stack

### Frontend
| Technology | Purpose |
|---|---|
| **React 18** | UI library |
| **Vite** | Build tool & dev server |
| **Tailwind CSS** | Utility-first styling |
| **React Router v6** | Client-side routing |
| **Axios** | HTTP client |
| **React Toastify** | Toast notifications |
| **Context API** | State management |

### Backend
| Technology | Purpose |
|---|---|
| **Node.js** | Runtime environment |
| **Express.js** | Web framework |
| **MongoDB + Mongoose** | Database & ODM |
| **JWT** | Authentication tokens |
| **bcrypt** | Password hashing |
| **Cloudinary** | Image storage & CDN |
| **Multer** | File upload handling |
| **Validator** | Input validation |

---

## 📁 Project Structure

```
prescripto/
├── backend/                    # Express.js REST API
│   ├── config/
│   │   ├── cloudinary.js       # Cloudinary configuration
│   │   └── mongodb.js          # MongoDB connection
│   ├── controllers/
│   │   ├── adminController.js  # Admin logic (add doctor, dashboard, etc.)
│   │   ├── doctorController.js # Doctor logic (profile, appointments, etc.)
│   │   └── userController.js   # User logic (auth, booking, profile, etc.)
│   ├── middlewares/
│   │   ├── authAdmin.js        # Admin JWT auth middleware
│   │   ├── authDoctor.js       # Doctor JWT auth middleware
│   │   ├── authUser.js         # User JWT auth middleware
│   │   └── multer.js           # File upload config
│   ├── models/
│   │   ├── appointmentModel.js # Appointment schema
│   │   ├── doctorModel.js      # Doctor schema
│   │   └── userModel.js        # User schema
│   ├── routes/
│   │   ├── adminRoute.js       # /api/admin/* routes
│   │   ├── doctorRoute.js      # /api/doctor/* routes
│   │   └── userRoute.js        # /api/user/* routes
│   ├── server.js               # App entry point
│   └── vercel.json             # Vercel deployment config
│
├── clientside/                 # Patient-facing React app
│   ├── src/
│   │   ├── assets/             # Images & static assets
│   │   ├── components/         # Reusable UI components
│   │   │   ├── Banner.jsx      # Promotional banner
│   │   │   ├── Footer.jsx      # Site footer
│   │   │   ├── Header.jsx      # Hero header section
│   │   │   ├── Navbar.jsx      # Navigation bar
│   │   │   ├── RelatedDoctors.jsx
│   │   │   ├── SpecialityMenu.jsx
│   │   │   └── TopDoctors.jsx
│   │   ├── context/
│   │   │   └── AppContext.jsx  # Global state (auth, doctors, user data)
│   │   └── pages/
│   │       ├── Home.jsx        # Landing page
│   │       ├── Doctors.jsx     # Browse doctors by speciality
│   │       ├── Appointment.jsx # Book appointment with a doctor
│   │       ├── Login.jsx       # User login / registration
│   │       ├── MyProfile.jsx   # User profile management
│   │       ├── MyAppointments.jsx
│   │       ├── About.jsx
│   │       └── Contact.jsx
│   └── vercel.json             # Vercel deployment config
│
└── admin/                      # Admin & Doctor panel React app
    ├── src/
    │   ├── assets/             # Images & static assets
    │   ├── components/
    │   │   ├── Navbar.jsx      # Admin panel navbar
    │   │   └── Sidebar.jsx     # Admin panel sidebar navigation
    │   ├── context/
    │   │   ├── AdminContext.jsx # Admin state management
    │   │   ├── AppContext.jsx   # Shared app state
    │   │   └── DoctorContext.jsx# Doctor state management
    │   └── pages/
    │       ├── Login.jsx       # Admin & Doctor login
    │       ├── Admin/
    │       │   ├── Dashboard.jsx
    │       │   ├── AddDoctor.jsx
    │       │   ├── AllAppointments.jsx
    │       │   └── DoctorsList.jsx
    │       └── Doctor/
    │           ├── DoctorDashboard.jsx
    │           ├── DoctorAppointments.jsx
    │           └── DoctorProfile.jsx
    └── vercel.json             # Vercel deployment config
```

---

## 🚀 Getting Started

### Prerequisites

- **Node.js** (v18 or higher recommended)
- **npm** or **yarn**
- **MongoDB** (local instance or [MongoDB Atlas](https://www.mongodb.com/atlas) cloud)
- **Cloudinary** account (for image uploads) — [Sign up free](https://cloudinary.com/)

### Environment Variables

#### Backend (`backend/.env`)

```env
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret_key
ADMIN_EMAIL=admin@example.com
ADMIN_PASSWORD=your_admin_password
CLOUDINARY_NAME=your_cloudinary_cloud_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_SECRET_KEY=your_cloudinary_api_secret
```

#### Client-Side (`clientside/.env`)

```env
VITE_BACKEND_URL=http://localhost:4000
```

#### Admin Panel (`admin/.env`)

```env
VITE_BACKEND_URL=http://localhost:4000
```

### Installation

**1. Clone the repository**
```bash
git clone https://github.com/elyse502/prescripto.git
cd prescripto
```

**2. Install dependencies & run the Backend**
```bash
cd backend
npm install
npm run server    # Starts with nodemon on port 4000
```

**3. Install dependencies & run the Client-Side**
```bash
cd clientside
npm install
npm run dev       # Starts Vite dev server (default: http://localhost:5173)
```

**4. Install dependencies & run the Admin Panel**
```bash
cd admin
npm install
npm run dev       # Starts Vite dev server (default: http://localhost:5174)
```

> **Tip:** Run all three servers simultaneously in separate terminal windows for full functionality.

---

## 📡 API Reference

### Base URL: `http://localhost:4000`

### User Routes (`/api/user`)

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| `POST` | `/register` | ❌ | Register a new user |
| `POST` | `/login` | ❌ | Login user |
| `GET` | `/get-profile` | ✅ User | Get user profile |
| `POST` | `/update-profile` | ✅ User | Update user profile (with image) |
| `POST` | `/book-appointment` | ✅ User | Book an appointment |
| `GET` | `/appointments` | ✅ User | List user's appointments |
| `POST` | `/cancel-appointment` | ✅ User | Cancel an appointment |

### Admin Routes (`/api/admin`)

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| `POST` | `/login` | ❌ | Admin login |
| `POST` | `/add-doctor` | ✅ Admin | Add a new doctor (with image) |
| `POST` | `/all-doctors` | ✅ Admin | Get all doctors |
| `POST` | `/change-availability` | ✅ Admin | Toggle doctor availability |
| `GET` | `/appointments` | ✅ Admin | Get all appointments |
| `POST` | `/cancel-appointment` | ✅ Admin | Cancel an appointment |
| `GET` | `/dashboard` | ✅ Admin | Get dashboard analytics |

### Doctor Routes (`/api/doctor`)

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| `GET` | `/list` | ❌ | Get all doctors (public) |
| `POST` | `/login` | ❌ | Doctor login |
| `GET` | `/appointments` | ✅ Doctor | Get doctor's appointments |
| `POST` | `/complete-appointment` | ✅ Doctor | Mark appointment complete |
| `POST` | `/cancel-appointment` | ✅ Doctor | Cancel an appointment |
| `GET` | `/dashboard` | ✅ Doctor | Get doctor dashboard data |
| `GET` | `/profile` | ✅ Doctor | Get doctor profile |
| `POST` | `/update-profile` | ✅ Doctor | Update doctor profile |

---

## 🌐 Deployment

The project is pre-configured for **Vercel** deployment with `vercel.json` files in each module.

### Deploy Backend
```bash
cd backend
vercel --prod
```

### Deploy Client-Side
```bash
cd clientside
vercel --prod
```

### Deploy Admin Panel
```bash
cd admin
vercel --prod
```

> **Note:** Update the `VITE_BACKEND_URL` environment variable in both frontend apps to point to your deployed backend URL.

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-feature`)
5. **Open** a Pull Request

---

## 📄 License

This project is licensed under the **ISC License**.

---

<p align="center">
  Made with ❤️ using the MERN Stack
</p>
