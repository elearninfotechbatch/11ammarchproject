
# 🧑‍💼 Employee Management App

A full-stack **Employee Management System** built with **Django REST Framework** (backend) and **React** (frontend), powered by a **MySQL** database.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Tech Stack](#tech-stack)
- [Features](#features)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
  - [Backend Setup (Django)](#backend-setup-django)
  - [Frontend Setup (React)](#frontend-setup-react)
  - [Database Setup (MySQL)](#database-setup-mysql)
- [API Endpoints](#api-endpoints)
- [Environment Variables](#environment-variables)
- [Screenshots](#screenshots)
- [Contributing](#contributing)
- [License](#license)

---

## 🧾 Overview

The **Employee Management App** allows HR teams and administrators to manage employee records efficiently. It supports full **CRUD operations** (Create, Read, Update, Delete) on employee data through a clean, responsive React UI backed by a robust Django REST API.

---

## 🛠 Tech Stack

| Layer      | Technology                  |
|------------|-----------------------------|
| Frontend   | React, Axios, React Router  |
| Backend    | Django, Django REST Framework|
| Database   | MySQL                        |
| Auth       | JWT (JSON Web Tokens)        |
| Styling    | CSS / Bootstrap / Tailwind   |

---

## ✨ Features

- ✅ Add, view, update, and delete employee records
- ✅ Search and filter employees by name, department, or role
- ✅ JWT-based user authentication and authorization
- ✅ RESTful API with Django REST Framework
- ✅ Responsive UI built with React
- ✅ MySQL database integration
- ✅ Pagination for large datasets
- ✅ Form validation on both frontend and backend

---

## 📁 Project Structure

```
employee-management-app/
│
├── backend/                        # Django project
│   ├── manage.py
│   ├── requirements.txt
│   ├── backend/
│   │   ├── settings.py
│   │   ├── urls.py
│   │   └── wsgi.py
│   └── employees/                  # Django app
│       ├── models.py
│       ├── views.py
│       ├── serializers.py
│       ├── urls.py
│       └── admin.py
│
├── frontend/                       # React project
│   ├── package.json
│   ├── public/
│   └── src/
│       ├── App.jsx
│       ├── index.js
│       ├── components/
│       │   ├── EmployeeList.jsx
│       │   ├── EmployeeForm.jsx
│       │   └── Navbar.jsx
│       └── services/
│           └── api.js              # Axios API calls
│
└── README.md
```

---

## ✅ Prerequisites

Make sure you have the following installed:

- Python 3.10+
- Node.js 18+ and npm
- MySQL 8.0+
- pip
- Git

---

## 🚀 Getting Started

### Database Setup (MySQL)

```sql
CREATE DATABASE employee_db;
CREATE USER 'emp_user'@'localhost' IDENTIFIED BY 'your_password';
GRANT ALL PRIVILEGES ON employee_db.* TO 'emp_user'@'localhost';
FLUSH PRIVILEGES;
```

---

### Backend Setup (Django)

```bash
# 1. Clone the repository
git clone https://github.com/your-username/employee-management-app.git
cd employee-management-app/backend

# 2. Create and activate virtual environment
python -m venv venv
source venv/bin/activate        # On Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Configure environment variables (see .env section below)

# 5. Run migrations
python manage.py makemigrations
python manage.py migrate

# 6. Create superuser
python manage.py createsuperuser

# 7. Start the development server
python manage.py runserver
```

Backend runs at: `http://localhost:8000`

---

### Frontend Setup (React)

```bash
# 1. Navigate to frontend directory
cd ../frontend

# 2. Install dependencies
npm install

# 3. Start the React development server
npm start
```

Frontend runs at: `http://localhost:3000`

---

## 🔌 API Endpoints

| Method | Endpoint                    | Description              |
|--------|-----------------------------|--------------------------|
| GET    | `/api/employees/`           | List all employees       |
| POST   | `/api/employees/`           | Add a new employee       |
| GET    | `/api/employees/<id>/`      | Get employee by ID       |
| PUT    | `/api/employees/<id>/`      | Update employee by ID    |
| DELETE | `/api/employees/<id>/`      | Delete employee by ID    |
| POST   | `/api/auth/login/`          | User login (JWT token)   |
| POST   | `/api/auth/logout/`         | User logout              |

---

## ⚙️ Environment Variables

Create a `.env` file in the `backend/` directory:

```env
SECRET_KEY=your_django_secret_key
DEBUG=True

DB_NAME=employee_db
DB_USER=emp_user
DB_PASSWORD=your_password
DB_HOST=localhost
DB_PORT=3306
```

In `settings.py`, configure the database:

```python
DATABASES = {
    'default': {
        'ENGINE':   'django.db.backends.mysql',
        'NAME':     os.environ.get('DB_NAME'),
        'USER':     os.environ.get('DB_USER'),
        'PASSWORD': os.environ.get('DB_PASSWORD'),
        'HOST':     os.environ.get('DB_HOST', 'localhost'),
        'PORT':     os.environ.get('DB_PORT', '3306'),
    }
}
```

---

## 🧑‍💻 Employee Model

```python
# employees/models.py
from django.db import models

class Employee(models.Model):
    emp_id     = models.AutoField(primary_key=True)
    first_name = models.CharField(max_length=100)
    last_name  = models.CharField(max_length=100)
    email      = models.EmailField(unique=True)
    department = models.CharField(max_length=100)
    role       = models.CharField(max_length=100)
    salary     = models.DecimalField(max_digits=10, decimal_places=2)
    joined_on  = models.DateField(auto_now_add=True)

    def __str__(self):
        return f"{self.first_name} {self.last_name}"
```

---

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m "Add your feature"`
4. Push to the branch: `git push origin feature/your-feature`
5. Open a Pull Request

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

> Built with ❤️ using Django + React + MySQL
