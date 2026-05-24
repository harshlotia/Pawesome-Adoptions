# Pawesome Adoptions

A full-stack pet adoption web application built with Flask, allowing users to browse adoptable pets, submit adoption requests, and enabling admins to manage the entire adoption pipeline.

Developed as a final project for **DSCI-D532 Applied Database Technologies** — Spring 2024, Indiana University Bloomington.

**Team:** Sarvesh Soni, Shraddha Gupta, Harsh Lotia

---

## Features

- **Browse & Filter Pets** — Search by name, breed, gender, age, and size with live searchable dropdowns
- **Sorting** — Sort listings by newest, age, or size
- **Pagination** — 15 pets per page
- **User Accounts** — Sign up, log in, and manage your profile (phone, address)
- **Adoption Requests** — Express interest in a pet and track your request status from your profile
- **Admin Panel** — Admins can manage pets, users, organizations, and adoption requests via Flask-Admin
- **Auto-population** — Database seeds itself from `Pet.csv` and `Org.csv` on first run
- **Security** — CSRF protection on all forms, hashed passwords with Werkzeug

---

## Tech Stack

| Layer | Technology |
|---|---|
| Backend | Python, Flask |
| ORM | SQLAlchemy |
| Database | SQLite |
| Auth | Flask-Login |
| Forms | Flask-WTF, WTForms |
| Admin | Flask-Admin |
| Frontend | Jinja2, Bootstrap 4 |

---

## Getting Started

### Prerequisites

- Python 3.8+
- pip

### Installation

```bash
# Clone the repository
git clone https://github.com/harshlotia/Pawesome-Adoptions.git
cd Pawesome-Adoptions/proj_adt

# Install dependencies
pip install flask flask-sqlalchemy flask-login flask-admin flask-wtf werkzeug pandas

# Run the app
python app.py
```

The app will be available at `http://127.0.0.1:5000`.

> On first run, the database is automatically created and populated from `Pet.csv` and `Org.csv`.

### Creating an Admin User

Uncomment the `create_admin()` block in `app.py`, run the app once to create the admin user, then comment it out again. Admin credentials can be customized in that block.

---

## Project Structure

```
proj_adt/
├── app.py               # Main application — routes, models, admin views
├── Pet.csv              # Seed data for pets
├── Org.csv              # Seed data for organizations
├── requirements.txt     # Python dependencies
├── static/
│   └── styles.css       # Custom styles
├── templates/
│   ├── base.html
│   ├── index.html       # Pet listing with filters
│   ├── pet_detail.html  # Individual pet page + adoption request
│   ├── login.html
│   ├── signup.html
│   ├── user_details.html
│   ├── about.html
│   └── admin/           # Admin panel templates
└── instance/
    └── pet_adoption.db  # SQLite database (auto-generated)
```

---

## Database Schema

| Table | Description |
|---|---|
| `Pet` | Pet listings with breed, age, size, gender, status, and organization |
| `User` | Registered users with hashed passwords and optional admin flag |
| `Organization` | Shelters/rescues linked to pets |
| `Request` | Adoption requests linking users to pets, with status tracking |

When an adoption request is **accepted**, the pet's status is set to `adopted` and all other pending requests for that pet are automatically declined.

---

## Live Demo

No live deployment — run locally following the steps above.
