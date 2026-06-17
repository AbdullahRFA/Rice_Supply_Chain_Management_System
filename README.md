# Rice Supply Chain Management System (RSCMS)

The **Rice Supply Chain Management System (RSCMS)** is a comprehensive full-stack enterprise platform built to streamline, trace, and manage transactions throughout the agricultural life cycle of rice. By digitizing workflows from farm to consumer, the platform eliminates structural inefficiencies, ensures fair market pricing, and establishes transparent communication channels between agricultural stakeholders.

---

## 🏗 System Architecture & Stakeholder Flow

The platform relies on a multi-role user architecture where each role acts as a functional node within the supply chain loop:

1. **Farmers:** List paddy yields, check real-time localized crop pricing, and sell raw crops directly to mills or registered dealers without predatory intermediaries.
2. **Mill Managers:** Monitor raw paddy acquisition, manage processing/milling inventories, log production metrics, and track distribution-ready rice batches.
3. **Dealers & Distributors:** Source processed rice from mills, handle wholesale procurement logistics, and manage regional supply allocations.
4. **Administrators:** Oversee platform security, verify user credentials, moderate market transaction listings, and view aggregate supply chain analytics.

---

## 🛠 Tech Stack

* **Backend Engine:** Django (Python) — Handles core business logic, ORM mapping, and database migrations.
* **API Layer:** Django REST Framework (DRF) — Exposes a modular, stateless RESTful API for decoupling front-end clients or potential mobile extensions.
* **Database:** SQLite (Development) / PostgreSQL-compatible structure — Utilizes relational models optimized with structured foreign keys to map sequential supply chain actions.
* **Authentication:** Token-based security mapping custom permission groups to distinct user roles.

---

## 🔑 Key Features

* **Multi-Tenant User Management:** Separate data views and granular action permissions depending on whether the authenticated account is a Farmer, Mill Manager, or Dealer.
* **Inventory Tracking:** Real-time logging of grain quantities, changing states (unprocessed paddy to refined rice varieties), and weight tracking.
* **Transaction Logging:** End-to-end transparent ledger records linking crop sales, purchase orders, and transport fulfillment steps.
* **Agricultural Market Insights:** Dynamic listing portals where current market rates for different rice varieties can be updated and queried.

---

## 📂 Directory Structure

```text
├── rscms/                   # Root project configuration directory
│   ├── __init__.py
│   ├── settings.py          # Main app configurations and permission setups
│   ├── urls.py              # Global URL routing definitions
│   └── wsgi.py
├── apps/                    # Decoupled feature modules (Typical DRF setup)
│   ├── authentication/      # Custom User models, registration, and user roles
│   ├── supply_chain/        # Models/Views for Paddy, Rice Batches, and Orders
│   └── inventory/           # Stock levels for Mills and Dealers
├── manage.py                # Django administrative utility script
├── requirements.txt         # Project dependencies
└── README.md                # Platform documentation

```

---

## 🚀 Installation & Local Setup

### Prerequisite Environment

Ensure you have **Python 3.10+** and **pip** installed locally.

### 1. Clone the Repository

```bash
git clone https://github.com/AbdullahRFA/Rice_Supply_Chain_Management_System.git
cd Rice_Supply_Chain_Management_System

```

### 2. Set Up a Virtual Environment

```bash
# Create environment
python -m venv venv

# Activate on Windows:
venv\Scripts\activate

# Activate on macOS/Linux:
source venv/bin/activate

```

### 3. Install Dependencies

```bash
pip install -r requirements.txt

```

### 4. Database Migrations & Initial Setup

Apply the migrations to build your local schema and construct the core tables for user roles, profiles, and supply chain tracking.

```bash
python manage.py makemigrations
python manage.py migrate

```

### 5. Create an Administrative Superuser

```bash
python manage.py createsuperuser

```

### 6. Boot the Local Server

```bash
python manage.py runserver

```

The application API and admin dashboards will be accessible locally at `[http://127.0.0.1:8000/](http://127.0.0.1:8000/)`.

---

## 📡 API Endpoints (Core Overview)

All primary requests interact with the endpoints using explicit payload verification. Here is a baseline summary of the underlying API routes:

| Method | Endpoint | Access Level | Description |
| --- | --- | --- | --- |
| **POST** | `/api/auth/register/` | Public | Registers a new user with an explicitly specified role |
| **POST** | `/api/auth/login/` | Public | Generates access token signatures upon validation |
| **GET/POST** | `/api/paddy-listings/` | Farmers / Mills | Handles raw crop supply postings and acquisitions |
| **GET/POST** | `/api/inventory/mill/` | Mill Managers | Tracks raw processing inputs and converted rice metrics |
| **POST** | `/api/orders/create/` | Dealers | Places a wholesale processed cargo acquisition request |

---

## 🛡 License

This project is licensed under the **MIT License**. Check out the `LICENSE` file in the root for details.
