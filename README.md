# 🛒 Online Shopping Database

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)
![Version](https://img.shields.io/badge/Version-1.0-blue.svg)

A complete **PostgreSQL** database schema for a full-featured **Online Shopping / E-commerce** system.

## ✨ Features

- Customer & Admin management
- Product catalog with categories
- Shopping Cart system
- Order processing & Order details
- Payment tracking
- Automatic stock reduction using **Triggers**
- Stored **Functions** and **Views** for easy reporting

## 📋 Table of Contents

- [Overview](#-overview)
- [Database Schema](#-database-schema)
- [Setup Instructions](#-setup-instructions)
- [Usage Examples](#-usage-examples)
- [Database Objects](#-database-objects)
- [Project Structure](#-project-structure)
- [Notes](#-notes)
- [Contributing](#-contributing)
- [License](#-license)

## 📊 Overview

**Database Name:** `online_shopping_db`  
**Type:** PostgreSQL  
**Purpose:** Backend for online shopping websites, learning projects, or full-stack e-commerce applications.

## 🗃️ Database Schema

### Tables

| Table            | Description                                      |
|------------------|--------------------------------------------------|
| `customer`       | Customer accounts and details                    |
| `admin`          | Admin users                                      |
| `category`       | Product categories                               |
| `product`        | Products with price, stock & images              |
| `cart`           | Shopping carts (one per customer)                |
| `cartitem`       | Items in the cart                                |
| `orders`         | Customer orders                                  |
| `orderdetails`   | Line items of each order                         |
| `payment`        | Payment records                                  |

### Relationships

- One-to-Many: `customer` → `orders`, `cart`
- One-to-Many: `category` → `product`
- One-to-Many: `orders` → `orderdetails`, `payment`
- Many-to-One: `cartitem` → `cart`, `product`

### Special Objects

- **Trigger**: `trg_update_stock` → Auto-reduces stock on purchase
- **Functions**:
  - `getcustomerorders(customer_id)`
  - `gettotalsales()`
- **Views**:
  - `customerordersview`
  - `productcategoryview`

## 🚀 Setup Instructions

### 1. Create Database

```sql
CREATE DATABASE online_shopping_db;
### 2. Import Schema
Bashpsql -U your_username -d online_shopping_db -f online_shopping_Database.sql
### 3. Connect
SQL\c online_shopping_db
Example
-- Category
INSERT INTO category (categoryname, description) 
VALUES ('Electronics', 'Smartphones, laptops & accessories');

-- Product
INSERT INTO product (categoryid, productname, price, stockquantity, imageurl)
VALUES (1, 'iPhone 15', 999.99, 50, 'https://example.com/iphone.jpg');

-- Customer
INSERT INTO customer (name, email, password, phone, address)
VALUES ('John Doe', 'john@example.com', 'hashed_password_here', '+1234567890', '123 Main Street');
