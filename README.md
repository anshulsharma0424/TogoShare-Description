# TogoShare – File Sharing SaaS Platform

> **A full-stack SaaS application for secure file uploads, storage, and sharing with a real-world credit and payment system.**

---

## Live Demo
[https://togo-share.vercel.app](https://togo-share.vercel.app)

> **Note:** The source code for this project is maintained in a **private repository** to protect API keys and intellectual property. This document outlines the technical design, implementation, and features.

---

## 📖 About the Project

**TogoShare** is a full-stack web application that enables users to upload, store, and share files securely. Unlike simple file uploaders, this project is designed as a **Software-as-a-Service (SaaS)** platform with a **credit-based usage model**.

Users receive free credits on signup and can purchase additional credits using real payments. Each file upload consumes credits, enforcing business logic at the backend level.

This project was built to deeply understand:

* Integration of a **React frontend** with a **secure Spring Boot backend**
* Handling and streaming **binary file data**
* Designing **credit systems and payment workflows** used in production SaaS products

---

## Screenshots

> <img width="1582" height="987" alt="image" src="https://github.com/user-attachments/assets/4878afec-433c-4537-b7b4-f22ad71019c1" />

---

## ⚡ Key Features

### Secure Authentication
* Custom-built **Login / Register** system using **Spring Security** and **JWT (JSON Web Tokens)**
* No third-party auth providers (e.g., Auth0, Firebase Auth)
* Manual implementation of:

  * Password hashing using **BCrypt**
  * Token generation, validation, and expiration handling

---
### File Storage
* Drag-and-drop file uploads from the frontend
* Backend **streams files directly** to **Cloudinary (Object Storage)**
* Only file metadata (name, size, owner, visibility) is stored in **MongoDB**
---

### Credit-Based System
* Every file upload consumes **1 credit**
* Backend strictly enforces credit validation
* Upload requests are **rejected immediately** when credits are insufficient

---
### Payments Integration
* Integrated **Razorpay** for purchasing credits
* Backend verifies the **payment signature** to prevent tampering or fraud
* Credits are added **only after successful verification**
---

### Public / Private File Sharing
* Users can toggle file visibility
* Public files generate a **shareable link**
* Private files remain accessible only to the owner
---

## 🛠️ Tech Stack

### Backend
* **Java 21**
* **Spring Boot 3** (Web, Security, Data MongoDB)
* **MongoDB Atlas** (Cloud Database)
* **Docker** (Containerization)

### Frontend
* **React.js** (Vite)
* **Tailwind CSS v4** (Styling)
* **Axios** (API requests with interceptors)
* **Context API** (Global state management)

### Infrastructure & Services
* **Render** (Backend Hosting)
* **Vercel** (Frontend Hosting)
* **Cloudinary** (File Storage)
---
## 🧠 What I Learned

### Spring Security Filters
* Intercepting HTTP requests using filters
* Extracting and validating `Bearer` tokens
* Setting authenticated user context before controller execution
---
### Secure Secret Management
* Managing sensitive keys (Cloudinary, Razorpay) using **Environment Variables**
* Handling differences between **local development** and **production environments** (Render / Vercel)
---
### CORS & Deployment Challenges
* Resolving cross-origin issues between:

  * Frontend hosted on **Vercel**
  * Backend hosted on **Render**
