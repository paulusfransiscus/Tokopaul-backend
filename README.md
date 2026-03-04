markdown
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
2. Install Dependencies
bash
npm install
3. Setup Database MySQL
bash
# Login ke MySQL
mysql -u root -p

# Buat database
CREATE DATABASE tokopaul CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

# Buat user (opsional)
CREATE USER 'tokopaul_user'@'localhost' IDENTIFIED BY 'Tokopaul@123456';
GRANT ALL PRIVILEGES ON tokopaul.* TO 'tokopaul_user'@'localhost';
FLUSH PRIVILEGES;
EXIT;
4. Setup Redis
bash
# Ubuntu/Debian
sudo apt-get install redis-server
sudo systemctl start redis

# MacOS
brew install redis
brew services start redis

# Windows
# Download dari https://github.com/microsoftarchive/redis/releases
5. Konfigurasi Environment
bash
# Copy file .env.example
cp .env.example .env

# Edit file .env sesuai konfigurasi Anda
nano .env
Isi file .env Anda:

env
# Server Configuration
NODE_ENV=development
PORT=5000
API_URL=http://localhost:5000
FRONTEND_URL=http://localhost:3000

# Database Configuration
DB_HOST=localhost
DB_PORT=3306
DB_USER=tokopaul_user
DB_PASSWORD=Tokopaul@123456
DB_NAME=tokopaul

# Redis Configuration
REDIS_HOST=localhost
REDIS_PORT=6379

# JWT Configuration
JWT_SECRET=your-super-secret-jwt-key-min-32-chars
JWT_REFRESH_SECRET=your-super-secret-refresh-key-min-32-chars
JWT_EXPIRE=15m
JWT_REFRESH_EXPIRE=7d

# Email Configuration
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USER=your-email@gmail.com
EMAIL_PASS=your-app-password

# Admin Code
ADMIN_SECRET_CODE=tokopaul-admin-2024
6. Jalankan Aplikasi
bash
# Development mode (dengan nodemon)
npm run dev

# Production mode
npm start
7. Test API
bash
# Cek kesehatan server
curl http://localhost:5000/health
📚 Dokumentasi API
🔑 Authentication Endpoints
Register User
http
POST /api/auth/register
Content-Type: application/json

{
  "username": "john_doe",
  "email": "john@example.com",
  "password": "Password123!",
  "full_name": "John Doe",
  "phone": "08123456789"
}
Response Success:

json
{
  "success": true,
  "message": "Registrasi berhasil. Silakan cek email untuk verifikasi.",
  "data": {
    "user": {
      "id": 1,
      "username": "john_doe",
      "email": "john@example.com",
      "full_name": "John Doe",
      "role": "user",
      "is_verified": false
    }
  }
}
Login User
http
POST /api/auth/login
Content-Type: application/json

{
  "email": "john@example.com",
  "password": "Password123!"
}
Response Success:

json
{
  "success": true,
  "message": "Login berhasil",
  "data": {
    "user": {
      "id": 1,
      "username": "john_doe",
      "email": "john@example.com",
      "full_name": "John Doe",
      "role": "user"
    },
    "accessToken": "eyJhbGciOiJIUzI1NiIs...",
    "refreshToken": "eyJhbGciOiJIUzI1NiIs...",
    "expiresIn": 900
  }
}
Get Current User
http
GET /api/auth/me
Authorization: Bearer <access_token>
Update Profile
http
PUT /api/auth/profile
Authorization: Bearer <access_token>
Content-Type: application/json

{
  "full_name": "John Updated",
  "phone": "08123456789",
  "address": "Jl. Sudirman No. 123",
  "city": "Jakarta",
  "province": "DKI Jakarta",
  "postal_code": "12345"
}
Change Password
http
PUT /api/auth/change-password
Authorization: Bearer <access_token>
Content-Type: application/json

{
  "current_password": "Password123!",
  "new_password": "NewPassword123!"
}
Logout
http
POST /api/auth/logout
Authorization: Bearer <access_token>
📦 Product Endpoints
Get All Products
http
GET /api/products?page=1&limit=10&category=elektronik&sort=price_asc
Get Product by ID
http
GET /api/products/1
Create Product (Admin only)
http
POST /api/products
Authorization: Bearer <admin_token>
Content-Type: application/json

{
  "name": "Smartphone XYZ Pro",
  "category": "elektronik",
  "price": 5500000,
  "stock": 15,
  "description": "Smartphone dengan kamera 108MP",
  "image_url": "https://example.com/image.jpg"
}
🛒 Cart Endpoints
Get Cart
http
GET /api/cart
Authorization: Bearer <access_token>
Add to Cart
http
POST /api/cart/add
Authorization: Bearer <access_token>
Content-Type: application/json

{
  "product_id": 1,
  "quantity": 2
}
Update Cart Item
http
PUT /api/cart/update/1
Authorization: Bearer <access_token>
Content-Type: application/json

{
  "quantity": 3
}
Remove from Cart
http
DELETE /api/cart/remove/1
Authorization: Bearer <access_token>
📋 Order Endpoints
Create Order
http
POST /api/orders/create
Authorization: Bearer <access_token>
Content-Type: application/json

{
  "shipping_address": "Jl. Sudirman No. 123",
  "shipping_city": "Jakarta",
  "shipping_province": "DKI Jakarta",
  "shipping_postal": "12345",
  "shipping_courier": "jne",
  "payment_method": "bank_transfer",
  "items": [
    {
      "product_id": 1,
      "quantity": 2
    }
  ]
}
Get User Orders
http
GET /api/orders
Authorization: Bearer <access_token>
👑 Admin Endpoints
Get All Users
http
GET /api/admin/users
Authorization: Bearer <admin_token>
Update User Role
http
PUT /api/admin/users/1/role
Authorization: Bearer <admin_token>
Content-Type: application/json

{
  "role": "admin"
}
Get Dashboard Stats
http
GET /api/admin/stats
Authorization: Bearer <admin_token>
📊 Database Schema
Users Table
sql
CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(50) UNIQUE NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    full_name VARCHAR(100),
    phone VARCHAR(20),
    role ENUM('user', 'admin') DEFAULT 'user',
    is_active BOOLEAN DEFAULT true,
    is_verified BOOLEAN DEFAULT false,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
Products Table
sql
CREATE TABLE products (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(200) NOT NULL,
    slug VARCHAR(200) UNIQUE NOT NULL,
    category VARCHAR(50),
    price DECIMAL(12,2) NOT NULL,
    stock INT DEFAULT 0,
    image_url VARCHAR(500),
    rating DECIMAL(2,1) DEFAULT 0,
    sold INT DEFAULT 0,
    is_active BOOLEAN DEFAULT true,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
Orders Table
sql
CREATE TABLE orders (
    id INT PRIMARY KEY AUTO_INCREMENT,
    order_number VARCHAR(50) UNIQUE NOT NULL,
    user_id INT NOT NULL,
    total DECIMAL(12,2) NOT NULL,
    status ENUM('pending','processing','shipped','delivered','cancelled') DEFAULT 'pending',
    payment_status ENUM('pending','paid','failed') DEFAULT 'pending',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id)
);
🧪 Testing
Unit Test
bash
npm test
API Test dengan Postman
Import file Postman collection: TokoPaul API.postman_collection.json

Set environment variables:

base_url: http://localhost:5000

token: (akan terisi otomatis setelah login)

🚢 Deployment
Deploy ke Railway (Rekomendasi)
Install Railway CLI

bash
npm install -g @railway/cli
Login ke Railway

bash
railway login
Deploy aplikasi

bash
railway init
railway up
Add database

bash
railway add
# Pilih MySQL
# Pilih Redis
Deploy ke Heroku
Install Heroku CLI

bash
curl https://cli-assets.heroku.com/install.sh | sh
Login ke Heroku

bash
heroku login
Buat aplikasi

bash
heroku create tokopaul-api
Add database

bash
heroku addons:create jawsdb
heroku addons:create heroku-redis
Set environment variables

bash
heroku config:set JWT_SECRET=your-secret-key
heroku config:set JWT_REFRESH_SECRET=your-refresh-key
Deploy

bash
git push heroku main
Deploy ke VPS (DigitalOcean/AWS)
Setup server dengan Ubuntu

Install Node.js, MySQL, Redis

Clone repository

Install PM2

bash
npm install -g pm2
pm
