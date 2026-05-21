# AI Audit Management System

Enterprise-style audit management software built with Django, SQLite, Bootstrap 5, Chart.js, AJAX, and Groq AI.

## Features

- Role dashboards for Super Admin, Admin, Auditor, Manager, and Employee
- Registration, login, logout, password reset, profile picture upload, and role-based access
- Departments, users, audit categories, compliance rules, audits, checklists, findings, corrective actions, notifications, activity logs
- Audit workflow statuses: Pending, Assigned, In Progress, Under Review, Completed, Closed
- File uploads for PDF, DOCX, XLSX, PNG, JPG, and JPEG evidence/proofs
- AI assistant using Groq API with audit summaries, risk analysis, recommendations, corrective action suggestions, and chatbot
- PDF, Excel, and printable reports
- Chart.js analytics, KPI cards, responsive sidebar, dark mode, and modern enterprise UI

## Setup

```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

Create a `.env` file in the project root:

```env
DJANGO_SECRET_KEY=change-this-secret
DJANGO_DEBUG=1
DJANGO_ALLOWED_HOSTS=localhost,127.0.0.1
GROQ_API_KEY=your_groq_api_key
GROQ_MODEL=llama-3.3-70b-versatile
```

Run migrations and create data:

```bash
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser
python manage.py seed_demo
```

Start the server:

```bash
python manage.py runserver
```

Open `http://127.0.0.1:8000/`.

## Demo Users

After `python manage.py seed_demo`:

- `admin` / `Pass@12345`
- `auditor` / `Pass@12345`
- `manager` / `Pass@12345`
- `employee` / `Pass@12345`

## Groq AI

The AI assistant reads `GROQ_API_KEY` from `.env`. If no key is present, the system still works and returns a local audit-focused fallback response so development and demos do not break.

## Project Structure

```text
audit_management/   Django settings and root URL configuration
accounts/           Custom user, departments, notifications, activity logs
audits/             Audits, checklists, findings, actions, compliance records
dashboard/          Role-aware dashboards and analytics JSON
ai_assistant/       Groq service, AI history, AJAX assistant
reports/            PDF, Excel, printable report generation
templates/          Reusable Bootstrap templates
static/             Custom CSS and JavaScript
media/              Uploaded profile, evidence, proof, and report files
```

## Notes

- SQLite is configured by default in `audit_management/settings.py`.
- Django CSRF, ORM query protection, password hashing, session timeout, and role guards are enabled.
- Uploaded files are validated by extension at the model level.
