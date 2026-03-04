# 🏪 TokoPaul Backend API

![Node.js](https://img.shields.io/badge/Node.js-18.x-green)
![Express](https://img.shields.io/badge/Express-4.18.x-blue)
![MySQL](https://img.shields.io/badge/MySQL-8.0-orange)
![JWT](https://img.shields.io/badge/JWT-Auth-purple)
![License](https://img.shields.io/badge/License-MIT-yellow)

Backend API untuk aplikasi e-commerce TokoPaul dengan sistem keamanan tinggi menggunakan Node.js, Express, MySQL, dan JWT.

## ✨ Fitur Unggulan

### 🔐 Keamanan
- ✅ Authentication dengan JWT & Refresh Token
- ✅ Password hashing dengan bcrypt
- ✅ Rate limiting untuk mencegah brute force
- ✅ Account locking setelah 5x gagal login
- ✅ Email verification
- ✅ Session management dengan Redis
- ✅ CSRF protection
- ✅ XSS protection

### 👥 Manajemen User
- ✅ Register & Login
- ✅ Profil management
- ✅ Change password
- ✅ Forgot & reset password
- ✅ Role-based access (User & Admin)

### 🛒 E-commerce
- ✅ Product catalog
- ✅ Shopping cart
- ✅ Order management
- ✅ Stock management
- ✅ Payment integration ready

### 📊 Admin Features
- ✅ User management (CRUD)
- ✅ Product management (CRUD)
- ✅ Order management
- ✅ Dashboard statistics
- ✅ Activity logs

### 🚀 Performance
- ✅ Redis caching
- ✅ Database indexing
- ✅ Pagination
- ✅ Compression
- ✅ Rate limiting

## 🛠️ Tech Stack

| Komponen | Teknologi |
|----------|-----------|
| Runtime | Node.js |
| Framework | Express.js |
| Database | MySQL dengan Sequelize ORM |
| Caching | Redis |
| Authentication | JWT |
| Password Hashing | bcrypt |
| Email | Nodemailer |
| File Upload | Express Fileupload |
| Validation | Express Validator |
| Logging | Winston & Morgan |
| Security | Helmet, CORS |

## 📋 Prasyarat

Sebelum memulai, pastikan Anda telah menginstal:

- [Node.js](https://nodejs.org/) (v14 atau lebih baru)
- [MySQL](https://www.mysql.com/) (v5.7 atau lebih baru)
- [Redis](https://redis.io/) (v6 atau lebih baru)
- [Git](https://git-scm.com/)

## 🚀 Cara Instalasi

### 1. Clone Repository
```bash
git clone https://github.com/username/tokopaul-backend.git
cd tokopaul-backend
