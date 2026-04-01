# 💰 ExpenseLog — Daily Expense Tracker (MERN + Excel)

A full-stack MERN application for tracking daily expenses with automated Excel export functionality.

---

## 🏗️ Tech Stack

| Layer     | Technology                          |
|-----------|-------------------------------------|
| Frontend  | React 18, React Router, Chart.js    |
| Backend   | Node.js, Express.js                 |
| Database  | MongoDB + Mongoose                  |
| Excel     | ExcelJS (multi-sheet, styled)       |
| Auth      | JWT + bcrypt                        |
| Scheduler | node-cron (auto-export at 11:59 PM) |

---

## 📁 Project Structure

```
expense-tracker/
├── server/                    # Express backend
│   ├── index.js               # App entry + cron job
│   ├── models/
│   │   ├── User.js            # User schema
│   │   └── Expense.js         # Expense schema
│   ├── controllers/
│   │   ├── authController.js
│   │   ├── expenseController.js
│   │   └── excelController.js # Excel generation core
│   ├── routes/
│   │   ├── authRoutes.js
│   │   ├── expenseRoutes.js
│   │   ├── excelRoutes.js
│   │   └── categoryRoutes.js
│   ├── middleware/
│   │   └── authMiddleware.js
│   └── exports/               # Generated Excel files (auto-created)
│
└── client/                    # React frontend
    └── src/
        ├── App.js
        ├── index.css
        ├── context/
        │   └── AuthContext.js
        ├── services/
        │   └── api.js
        ├── pages/
        │   ├── Dashboard.js
        │   ├── Expenses.js
        │   ├── Reports.js
        │   ├── Login.js
        │   └── Register.js
        └── components/
            ├── Layout.js
            └── AddExpenseModal.js
```

---

## 🚀 Setup & Run

### Prerequisites
- Node.js v18+
- MongoDB (local or Atlas)

### 1. Backend Setup

```bash
cd server
cp .env.example .env
# Edit .env: set MONGO_URI and JWT_SECRET
npm install
npm run dev
```

### 2. Frontend Setup

```bash
cd client
npm install
npm start
```

App runs at **http://localhost:3000**, API at **http://localhost:5000**

---

## 📊 Excel Export Features

### Daily Report (1 Sheet)
- Color-coded category rows
- Payment method column
- Total & average summary block
- Professional Arial font formatting

### Monthly Report (3 Sheets)
| Sheet | Content |
|-------|---------|
| 📊 Monthly Summary | Budget vs Actual, Category Breakdown table |
| 📋 All Expenses    | Full sortable list with auto-filter |
| 📈 Category Analysis | Per-category totals, averages, % share |

### Auto-Export (Cron)
- Runs every day at **11:59 PM**
- Exports Excel for every registered user who has expenses that day
- Saved to `server/exports/` directory

---

## 🔗 API Endpoints

### Auth
| Method | Endpoint            | Description         |
|--------|---------------------|---------------------|
| POST   | /api/auth/register  | Create account      |
| POST   | /api/auth/login     | Login               |
| GET    | /api/auth/profile   | Get current user    |

### Expenses
| Method | Endpoint                   | Description              |
|--------|----------------------------|--------------------------|
| POST   | /api/expenses              | Create expense           |
| GET    | /api/expenses              | Get all (with filters)   |
| GET    | /api/expenses/today        | Today's expenses         |
| GET    | /api/expenses/summary      | Stats & trends           |
| PUT    | /api/expenses/:id          | Update expense           |
| DELETE | /api/expenses/:id          | Delete expense           |

### Excel
| Method | Endpoint                          | Description              |
|--------|-----------------------------------|--------------------------|
| GET    | /api/excel/export/daily?date=     | Download daily .xlsx     |
| GET    | /api/excel/export/monthly?month=&year= | Download monthly .xlsx |
| GET    | /api/excel/exports                | List saved exports       |

---

## ✅ Features Summary

- 🔐 JWT Authentication (register/login)
- ➕ Add / Edit / Delete expenses
- 🔍 Search & Filter by category, date, payment method
- 📊 Dashboard with doughnut & line charts
- 📥 One-click Daily Excel download
- 📥 Monthly Excel with 3-sheet analysis
- ⏰ Auto-nightly Excel export via cron
- 📱 Fully responsive design
