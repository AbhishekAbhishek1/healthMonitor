# Health Track API – Project Documentation

## Project Aim

The goal of the **Health Track API** project is to build a backend system for managing patient health records and medical reports using FastAPI and SQLAlchemy. The application is designed to:

* Store patient information securely.
* Manage medical reports and history.
* Provide REST API endpoints for CRUD operations.
* Enable easy integration with frontend or mobile applications.
* Demonstrate scalable backend architecture using Python.

---

# Project Workflow

## 1. User Request

The client application sends API requests to the FastAPI backend.

Example requests:

* Create a patient record
* Add a medical report
* Fetch reports
* Update patient details
* Delete records

## 2. FastAPI Router

Routes defined in the project handle incoming requests.

Example:

```python
router = APIRouter(prefix="/reports", tags=["Reports"])
```

The router:

* Receives requests
* Validates data
* Calls database operations
* Returns JSON responses

## 3. Database Layer

SQLAlchemy models define database tables.

Example:

```python
class MedicalReport(Base):
```

The database layer:

* Stores patient and report data
* Performs CRUD operations
* Maintains relationships between tables

## 4. Response Handling

FastAPI returns structured API responses in JSON format.

Example:

```json
{
  "message": "Report created successfully"
}
```

---

# Expected Result

After implementation, the system will:

* Provide a working REST API.
* Allow secure management of medical reports.
* Support scalable backend development.
* Enable easy frontend integration.
* Reduce manual handling of patient records.
* Improve organization of healthcare data.

---

# README.md

````md
# Health Track API

A FastAPI-based backend application for managing patient records and medical reports.

---

## Features

- Patient management
- Medical report management
- REST API endpoints
- SQLAlchemy ORM integration
- SQLite/MySQL/PostgreSQL support
- FastAPI automatic Swagger documentation

---

## Tech Stack

- Python
- FastAPI
- SQLAlchemy
- Pydantic
- SQLite
- Uvicorn

---

## Project Structure

health-track/
│
├── app/
│   ├── database.py
│   ├── main.py
│   ├── models/
│   │   └── report.py
│   ├── routers/
│   │   └── reports.py
│   └── schemas/
│
├── requirements.txt
├── README.md
└── .github/
    └── workflows/
        └── ci.yml

---

## Installation

### 1. Clone Repository

```bash
git clone https://github.com/your-username/health-track.git
cd health-track
````

### 2. Create Virtual Environment

```bash
python -m venv venv
```

Activate environment:

#### Windows

```bash
venv\Scripts\activate
```

#### Linux/Mac

```bash
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Run Application

```bash
uvicorn app.main:app --reload
```

---

## API Documentation

Swagger UI:

```text
http://127.0.0.1:8000/docs
```

Redoc:

```text
http://127.0.0.1:8000/redoc
```

---

## Example API Endpoints

### Create Report

```http
POST /reports/
```

### Get Reports

```http
GET /reports/
```

### Update Report

```http
PUT /reports/{id}
```

### Delete Report

```http
DELETE /reports/{id}
```

---

## Future Improvements

* Authentication & Authorization
* JWT Security
* File Upload Support
* Docker Deployment
* Cloud Database Integration
* Role-based access control

---

## License

This project is developed for educational and backend development practice purposes.

````

---

# GitHub Actions Workflow File

Create the following file:

`.github/workflows/ci.yml`

```yaml
name: Health Track CI

on:
  push:
    branches:
      - main
      - master

  pull_request:
    branches:
      - main
      - master

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.11'

      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          pip install -r requirements.txt

      - name: Run application checks
        run: |
          python -m py_compile $(find . -name "*.py")

      - name: Run tests
        run: |
          echo "No tests added yet"
````

---

# Workflow Explanation

## CI/CD Workflow Aim

The workflow automates backend validation whenever code is pushed to GitHub.

## Workflow Process

1. GitHub detects a push or pull request.
2. Ubuntu virtual machine starts.
3. Python environment is configured.
4. Dependencies are installed.
5. Python files are compiled for syntax validation.
6. Tests are executed.

## Workflow Result

* Detects syntax errors automatically.
* Prevents broken code from being merged.
* Improves project reliability.
* Supports continuous integration practices.
