# 🎓 EduCore ERP — Enterprise Integrated Student Information & Academic Resource Planning System

[![CI/CD Status](https://img.shields.io/badge/Build-Passing-brightgreen?style=for-the-badge&logo=github-actions)](https://github.com/DivyeBhatnagar/Student-Management_System)
[![React 19](https://img.shields.io/badge/React-19.1-61DAFB?style=for-the-badge&logo=react)](https://react.dev)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.8-3178C6?style=for-the-badge&logo=typescript)](https://www.typescriptlang.org)
[![Vite](https://img.shields.io/badge/Vite-7.1-646CFF?style=for-the-badge&logo=vite)](https://vitejs.dev)
[![Node.js / Express](https://img.shields.io/badge/Backend-Node.js%20%2F%20Express%205-339933?style=for-the-badge&logo=node.js)](https://nodejs.org)
[![PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-4169E1?style=for-the-badge&logo=postgresql)](https://www.postgresql.org/)
[![Tailwind CSS v4](https://img.shields.io/badge/Tailwind-CSS%20v4-06B6D4?style=for-the-badge&logo=tailwind-css)](https://tailwindcss.com)
[![Razorpay](https://img.shields.io/badge/Payments-Razorpay%20SDK-0C2340?style=for-the-badge&logo=razorpay)](https://razorpay.com)
[![Firebase Storage](https://img.shields.io/badge/Storage-Firebase%20Admin-FFCA28?style=for-the-badge&logo=firebase)](https://firebase.google.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

> **Production-Grade Multi-Tenant Higher Education Enterprise Resource Planning (ERP) Platform.**  
> Built with **React 19**, **TypeScript**, **Vite 7**, **Tailwind CSS v4**, **Node.js / Express 5**, **PostgreSQL 16**, **Razorpay Payment Gateway**, and **Firebase Admin SDK**.

---

## 📌 Architecture & System Overview

**EduCore ERP** is a robust, modular institutional management suite engineered to automate the end-to-end student lifecycle—from multi-stage online admissions and biometric attendance to fee billing, hostel allotment, examination grading (GPA/CGPA), and academic transcript generation.

```
                 ┌──────────────────────────────────────────────────────────┐
                 │                REACT 19 + VITE 7 FRONTEND                │
                 │   (TypeScript • Tailwind CSS v4 • Recharts • Lucide)     │
                 └───────────────┬──────────────────────────┬───────────────┘
                                 │                          │
                   REST APIs     │                          │  Document Uploads
                   (Axios / JWT) │                          │  (Multer / Firebase)
                                 ▼                          ▼
     ┌──────────────────────────────────────────────────────────────────────────┐
     │                       EXPRESS 5 REST API BACKEND                         │
     │            (Helmet • Rate Limiter • Express-Validator • Bcrypt)          │
     ├──────────────────────────────────────────────────────────────────────────┤
     │  ┌───────────────────────┐  ┌───────────────────────┐  ┌──────────────┐  │
     │  │ Admission & KYC Engine│  │ Fee Billing & Invoices│  │ Examination  │  │
     │  │ (Auto ID Generation)  │  │ (Razorpay Gateway)    │  │ & CGPA Calc  │  │
     │  └───────────────────────┘  └───────────────────────┘  └──────────────┘  │
     │  ┌───────────────────────┐  ┌───────────────────────┐  ┌──────────────┐  │
     │  │ Hostel & Asset Manager│  │ Attendance Tracker    │  │ RBAC Guard   │  │
     │  │ (Bed/Room Allocation) │  │ (Biometric / RFID)    │  │ (Audit Logs) │  │
     │  └───────────────────────┘  └───────────────────────┘  └──────────────┘  │
     └──────────────────────────────────────┬───────────────────────────────────┘
                                            │ SQL Connection Pool (pg)
                                            ▼
     ┌──────────────────────────────────────────────────────────────────────────┐
     │                  POSTGRESQL RELATIONAL DATABASE (ACID)                   │
     ├──────────────────────────────────────────────────────────────────────────┤
     │ • Strict Relational Constraints & Foreign Key Integrity                  │
     │ • Transactional Fee Ledger (Zero Over-Billing Guarantee)                 │
     │ • Normalized Schema for Students, Courses, Hostels, and Exams            │
     └──────────────────────────────────────────────────────────────────────────┘
```

---

## 🚀 Core Technical Competencies & Skills Matrix

| Domain | Core Skills & Technology Keywords |
| :--- | :--- |
| **Frontend Architecture** | `React 19`, `TypeScript 5.8`, `Vite 7`, `Tailwind CSS v4`, `React Hook Form`, `Recharts Data Visualization`, `Framer Motion`, `Axios Interceptors`, `Role-Based Route Guards`, `Responsive Dashboard Design` |
| **Backend & API Design** | `Node.js`, `Express 5`, `RESTful Architecture`, `PostgreSQL (node-postgres)`, `Database Migrations & Seeders`, `Connection Pooling`, `Express-Validator`, `Error Middleware` |
| **Security & Authentication** | `JSON Web Tokens (JWT)`, `Bcrypt Password Hashing`, `Helmet Security Headers`, `Express-Rate-Limit (DDoS Guard)`, `Role-Based Access Control (RBAC)`, `Audit Logging` |
| **Cloud, Storage & Payments** | `Razorpay Payment API Integration`, `Firebase Admin SDK (Cloud Storage)`, `Nodemailer SMTP Automation`, `Multer File Streaming`, `ACID Transactions` |
| **Testing & Quality Assurance** | `Jest Unit Testing`, `Supertest API Testing`, `ESLint 9 Flat Config`, `TypeScript Strict Mode`, `Git Workflow` |

---

## ⚡ Core Institutional Modules

### 📋 1. Admissions & Automated Enrollment
- **Digital Registration**: Multi-step admission forms with document verification and file validation.
- **Algorithmic Student ID Generation**: Deterministic matriculation numbering based on year, department, and branch codes.
- **Workflow State Engine**: Step-by-step administrative approval pipeline (Pending $\rightarrow$ Verified $\rightarrow$ Enrolled).

### 💳 2. Automated Fee Billing & Razorpay Settlement
- **Flexible Fee Structures**: Custom fee breakdowns categorized by course, semester, quota, and hostel occupancy.
- **Online Checkout Integration**: Seamless Razorpay payment gateway integration with webhook event verification.
- **Automated Invoicing & Receipts**: Instant PDF-ready digital receipt generation and automated SMS/Email reminders for pending dues.

### 🏢 3. Smart Hostel & Resource Allocation
- **Real-Time Occupancy Tracker**: Live room matrix showing vacancy status across blocks, floors, and rooms.
- **Conflict-Free Allotment**: Transaction-locked bed allocation preventing double-booking.
- **Asset Clearance**: Seamless checkout and deposit clearance workflows.

### 📊 4. Academic Evaluation & CGPA Calculation
- **Grade Management**: Multi-tier grading system (Internal Assessments, Mid-Terms, End-Semester Finals).
- **Automated CGPA / SGPA Computation**: Credit-weighted calculation engine following university standards.
- **Digital Transcript Generator**: Comprehensive grade card and attendance report exports.

---

## 🏛️ Fee Payment & Reconciliation Sequence Flow

```mermaid
sequenceDiagram
    autonumber
    actor Student
    participant UI as React 19 Frontend
    participant API as Express 5 Backend
    participant Gateway as Razorpay Payment Gateway
    participant DB as PostgreSQL Database
    participant Mail as Nodemailer SMTP

    Student->>UI: Select Pending Semester Fee & Click Pay
    UI->>API: POST /api/fees/create-order (Amount, FeeType)
    API->>Gateway: Generate Razorpay Order ID
    Gateway-->>API: Return Order Details
    API-->>UI: Launch Razorpay Checkout Modal
    Student->>Gateway: Authorize Payment (UPI / Cards / NetBanking)
    Gateway-->>UI: Return Payment Signature & Transaction ID
    UI->>API: POST /api/fees/verify-payment (Signature, OrderID)
    API->>API: Cryptographically Verify HMAC SHA256 Signature
    API->>DB: Record Payment in Ledger & Mark Fee as PAID (ACID Transaction)
    API->>Mail: Dispatch Formal Payment Receipt Email
    API-->>UI: Payment Success & Return Digital Invoice
    UI-->>Student: Display Confirmed Receipt & Updated Dashboard
```

---

## 📂 Repository Architecture

```
├── backend/                          # Express 5 REST API & PostgreSQL Engine
│   ├── src/
│   │   ├── controllers/             # Request Handlers (Auth, Admissions, Fees, Exams)
│   │   ├── models/                  # PostgreSQL Schema & Query Handlers
│   │   ├── routes/                  # Express Router Endpoints
│   │   ├── middleware/              # JWT Auth, RBAC, Rate Limiting & Validation
│   │   ├── services/                # Razorpay, Nodemailer, Firebase Storage
│   │   ├── utils/                   # Migration & Database Seeding Scripts
│   │   └── server.js                # Application Entrypoint
│   ├── package.json                 # Backend Node Dependencies
│   └── .env.example                 # Environment Configuration
├── frontend/                         # React 19 + TypeScript + Vite Client
│   ├── src/
│   │   ├── components/              # Reusable UI Primitives & Navbars
│   │   ├── pages/                   # Views (Dashboard, Admissions, Fees, Hostel)
│   │   ├── services/                # Axios API Layer & Interceptors
│   │   ├── utils/                   # Formatting & Calculation Helpers
│   │   └── App.tsx                  # Main Router & Route Guards
│   ├── package.json                 # Frontend Dependencies
│   ├── vite.config.ts               # Vite Build Configuration
│   └── tsconfig.json                # TypeScript Config
├── docs/                             # Technical API & Schema Documentation
│   ├── api-documentation.md         # Complete REST API Specifications
│   └── database-schema.md           # PostgreSQL Entity Relationship Details
├── DEPLOYMENT.md                     # Production Hosting Guide
└── README.md                         # Master Documentation
```

---

## 🛠️ Complete Technology Stack

```
Frontend:           React 19.1 • TypeScript 5.8 • Vite 7.1 • Tailwind CSS v4 • Recharts 3.1 • React Hook Form
Backend:            Node.js 20+ • Express 5.1 • PostgreSQL 16 (node-postgres) • Bcrypt • JWT
Security:           Helmet • Express-Rate-Limit • Express-Validator • Role-Based Access Control (RBAC)
Integrations:       Razorpay SDK 2.9 • Firebase Admin 13.5 (Storage) • Nodemailer 7.0 • Multer 2.0
Testing:            Jest 30 • Supertest 7.1 • ESLint 9 Flat Config
```

---

## ⚙️ Quick Start & Installation

### 1. Prerequisites
- **Node.js**: `18.x+` (or `20.x`)
- **PostgreSQL**: `14+` running locally or on cloud (Neon / Supabase / AWS RDS)
- **Git**

### 2. Backend Setup
```bash
cd backend

# Install dependencies
npm install

# Configure environment variables
cp .env.example .env
```

Configure `.env` in `backend`:
```env
PORT=5000
DATABASE_URL=postgresql://postgres:password@localhost:5432/student_erp
JWT_SECRET=your_jwt_super_secret_key
RAZORPAY_KEY_ID=your_razorpay_key
RAZORPAY_KEY_SECRET=your_razorpay_secret
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your_email@institution.edu
SMTP_PASS=your_email_app_password
```

Run database migrations & start the backend:
```bash
npm run db:migrate
npm run db:seed
npm run dev
```
> Server running on: **http://localhost:5000**

### 3. Frontend Setup
```bash
cd ../frontend

# Install dependencies
npm install

# Launch Vite development server
npm run dev
```
> Access application at: **http://localhost:5173**

---

## 📈 Engineering Impact & Resume Highlights

- **Architected an enterprise full-stack Student Management ERP** supporting multi-tenant role-based dashboards across administrators, faculty, and students using **React 19**, **Express 5**, and **PostgreSQL**.
- **Integrated Razorpay payment gateway** with cryptographic signature verification and automated transactional ledger updates ensuring 100% financial reconciliation.
- **Engineered an automated admissions pipeline** with algorithmic student registration ID generation, document upload streaming via **Firebase Storage**, and automated email notifications.
- **Implemented zero-trust security controls** including JWT token rotation, bcrypt password salting, helmet headers, and express rate limiting against brute-force attacks.

---

## 📜 License
Distributed under the **MIT License**. See `LICENSE` for details.

---

<p align="center">
  <b>Enterprise Higher-Education Student Management & ERP Infrastructure.</b>
</p>
