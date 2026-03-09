# NexaBank — Bank Account Management System

---

## 📌 Project Overview
NexaBank is a full-stack web-based Bank Account Management System built using Java Servlets, JDBC, and MySQL following the MVC (Model-View-Controller) architecture. It provides a modern, responsive user interface for managing bank accounts, performing transactions, and monitoring account status.

---

## 🛠️ Technology Stack

| Layer | Technology |
|-------|-----------|
| Backend | Java Servlets (javax.servlet) |
| Database | MySQL 8.0 |
| Database Connectivity | JDBC |
| Frontend | HTML5, CSS3, JavaScript |
| Architecture | MVC Pattern |
| Server | Apache Tomcat 9 |
| JSON Library | Google Gson 2.10.1 |
| Build | Manual JAR + WAR |

---

## ✨ Features
- ✅ Create new bank accounts (Savings / Current)
- ✅ View and search accounts by name or account number
- ✅ Deposit money into active accounts
- ✅ Withdraw money with minimum balance validation
- ✅ Check account balance instantly
- ✅ Update account status (Active / Inactive / Closed)
- ✅ View transaction history (last 20 transactions)
- ✅ Dashboard with live statistics
- ✅ Responsive modern UI with dark theme

---

## 📁 Project Structure

```
BankingSystem/
│
├── src/
│   └── com/
│       └── bank/
│           ├── util/
│           │   └── DatabaseConnection.java
│           ├── model/
│           │   ├── Account.java
│           │   └── Transaction.java
│           ├── dao/
│           │   └── AccountDAO.java
│           └── servlet/
│               └── AccountServlet.java
│
├── webapp/
│   ├── index.html
│   ├── style.css
│   ├── app.js
│   └── WEB-INF/
│       └── lib/
│           ├── mysql-connector-j-9.6.0.jar
│           └── gson-2.10.1.jar
│
└── sql/
    └── schema.sql
```

---

## ⚙️ Prerequisites

- Java JDK 11 or higher
- MySQL Server 8.0
- Apache Tomcat 9
- MySQL Connector/J JAR
- Google Gson JAR

---

## 🚀 Setup Instructions

### Step 1 — Database Setup
Run the SQL script in MySQL Workbench:
```sql
CREATE DATABASE IF NOT EXISTS banking_system;
USE banking_system;
```
Then run the full schema.sql file to create tables and insert sample data.

---

### Step 2 — Configure Database
Open `DatabaseConnection.java` and update:
```java
private static final String DB_USER     = "root";       // your MySQL username
private static final String DB_PASSWORD = "password";   // your MySQL password
```

---

### Step 3 — Compile Java Files
```powershell
javac -cp "path/to/servlet-api.jar;path/to/mysql-connector.jar;path/to/gson.jar" -d webapp/WEB-INF/classes src/com/bank/util/DatabaseConnection.java src/com/bank/model/Account.java src/com/bank/model/Transaction.java src/com/bank/dao/AccountDAO.java src/com/bank/servlet/AccountServlet.java
```

---

### Step 4 — Build WAR File
```powershell
jar -cvf BankAccountManagement.war -C webapp .
```

---

### Step 5 — Deploy to Tomcat
```powershell
Copy-Item "BankAccountManagement.war" "path/to/tomcat/webapps/"
```

---

### Step 6 — Start Tomcat
```powershell
$env:JAVA_HOME = "C:\Program Files\Java\jdk-xx"
$env:CATALINA_HOME = "path/to/tomcat"
& "$env:CATALINA_HOME\bin\startup.bat"
```

---

### Step 7 — Open Browser
```
http://localhost:8080/BankAccountManagement/
```

---

## 🗄️ Database Schema

### accounts table
| Column | Type | Description |
|--------|------|-------------|
| id | INT | Primary key |
| account_number | VARCHAR(20) | Unique account number |
| customer_name | VARCHAR(100) | Account holder name |
| email | VARCHAR(150) | Email address |
| phone | VARCHAR(20) | Phone number |
| address | TEXT | Full address |
| account_type | ENUM | Savings or Current |
| balance | DECIMAL(15,2) | Account balance |
| status | ENUM | Active, Inactive, Closed |
| created_at | TIMESTAMP | Account creation date |

### transactions table
| Column | Type | Description |
|--------|------|-------------|
| id | INT | Primary key |
| transaction_id | VARCHAR(30) | Unique transaction ID |
| account_number | VARCHAR(20) | Foreign key to accounts |
| transaction_type | ENUM | Deposit, Withdrawal, Account Created |
| amount | DECIMAL(15,2) | Transaction amount |
| balance_after | DECIMAL(15,2) | Balance after transaction |
| description | VARCHAR(255) | Transaction description |
| transaction_date | TIMESTAMP | Transaction date and time |

---

## 💼 Business Rules
- Savings accounts must maintain a minimum balance of ₹500
- Only Active accounts can perform transactions
- Closed accounts cannot be reopened
- Account numbers are auto-generated in format ACC0000000001
- Transaction IDs are auto-generated with timestamp

---

## 👩‍💻 Developer
- **Name:** Tina
- **Project:** NexaBank Bank Account Management System
- **Stack:** Java · MySQL · JDBC · HTML · CSS · JavaScript

---

## 📄 License
This project is for educational purposes only.
