# ReTech-Cycle ♻️📱

[![Django](https://img.shields.io/badge/Django-5.0.3-092E20?style=for-the-badge&logo=django&logoColor=white)](https://www.djangoproject.com/)
[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Bootstrap](https://img.shields.io/badge/Bootstrap-4.1.1-7952B3?style=for-the-badge&logo=bootstrap&logoColor=white)](https://getbootstrap.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)

> **ReTech-Cycle** is a web-based e-waste management and circular economy platform built with Django. It bridges the gap between technology and sustainability by breathing new life into old, non-functional, and obsolete mobile devices through refurbishment, repair servicing, and a dedicated e-commerce marketplace.

---

## 📖 Table of Contents

- [About The Project](#-about-the-project)
- [Key Features](#-key-features)
  - [Customer Portal](#customer-portal)
  - [Servicing & Device Trade-In](#servicing--device-trade-in)
  - [Admin Dashboard & Operations](#admin-dashboard--operations)
- [Tech Stack](#-tech-stack)
- [Database Models](#-database-models)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation & Setup](#installation--setup)
  - [Running the Application](#running-the-application)
- [Key Endpoints & Routes](#-key-endpoints--routes)
- [Configuration](#-configuration)
- [Team & Acknowledgments](#-team--acknowledgments)
- [License](#-license)

---

## 🌍 About The Project

Electronic waste (e-waste) is one of the fastest-growing waste streams globally. Planned obsolescence and rapid upgrade cycles cause millions of viable mobile devices to end up in landfills each year.

**ReTech-Cycle** is developed to address this challenge by:
1. **Refurbishing & Reselling:** Providing quality-checked refurbished electronics at accessible prices.
2. **Extending Device Lifecycles:** Enabling users to book repair and maintenance servicing for damaged devices.
3. **Encouraging Device Trade-ins:** Providing a platform for users to sell or turn in obsolete devices for recycling instead of discarding them.

---

## ✨ Key Features

### Customer Portal
- **User Authentication & Profiles:** Registration and login for customers, complete with profile management, contact details, and custom avatar upload.
- **Product Catalog & Search:** Browse refurbished products with real-time keyword search.
- **Cookie-Based Shopping Cart:** Add products to cart with guest persistence, cart counters, and dynamic cart item removal without requiring immediate login.
- **Checkout & Delivery Management:** Specify custom shipping address, phone, and contact details during checkout.
- **Order Tracking:** Track real-time status of orders (`Pending`, `Order Confirmed`, `Out for Delivery`, `Delivered`).
- **Instant PDF Invoices:** Automatically generates and downloads PDF invoices for placed orders utilizing `xhtml2pdf`.

### Servicing & Device Trade-In
- **Repair Servicing Requests:** Submit device repair inquiries by uploading issue descriptions and device photos.
- **Service Order Tracking:** Monitor the progress of submitted repair orders.
- **Sell Your Device:** Submit old or broken devices directly to the platform for inspection and repurchase.

### Admin Dashboard & Operations
- **Role-Based Access Control:** Differentiated access and routing for standard customers versus system administrators.
- **Analytics Overview Cards:** Live counts for total registered customers, total listed products, and total customer bookings.
- **Product Catalog Management:** Full CRUD operations to add, view, update, and remove refurbished products with image uploads.
- **Customer Management:** View, edit customer records, or remove inactive accounts.
- **Order Lifecycle Management:** View all incoming bookings, update order statuses, or cancel orders.
- **Feedback & Support Inquiries:** Review user feedbacks and incoming support inquiries.

---

## 🛠 Tech Stack

| Layer | Technology |
|---|---|
| **Backend Framework** | [Django 5.0.3](https://www.djangoproject.com/) (Python) |
| **Frontend UI** | HTML5, CSS3, JavaScript, [Bootstrap 4](https://getbootstrap.com/), [Font Awesome 5](https://fontawesome.com/) |
| **Database** | SQLite3 (default development database) |
| **Form Handling** | Django Forms & `django-widget-tweaks` |
| **PDF Generation** | `xhtml2pdf`, `reportlab`, `pypdf` |
| **Image Handling** | `Pillow` |
| **Email Service** | Django Core Mail (SMTP backend) |

---

## 🗄 Database Models

The core business logic is encapsulated in the following models (`ecom/models.py`):

- **`Customer`**: Extends Django's `User` with profile pictures, address, and contact numbers.
- **`Product`**: Stores inventory items with name, price, description, and product images.
- **`Orders`**: Connects `Customer` and `Product` with shipping details, order dates, and status choices (`Pending`, `Order Confirmed`, `Out for Delivery`, `Delivered`).
- **`Servicing`**: Records repair service requests including customer reference, product name, problem description, and uploaded pictures.
- **`Feedback`**: Stores user feedback and reviews.

---

## 📂 Project Structure

```text
ReTech-Cycle/
├── ecom/                         # Main application directory
│   ├── migrations/               # Database migration files
│   ├── admin.py                  # Django admin registration
│   ├── apps.py                   # App configuration
│   ├── forms.py                  # Customer, Product, Servicing, and Order forms
│   ├── models.py                 # Database schemas
│   ├── tests.py                  # Unit and integration tests
│   └── views.py                  # Core views, business logic, and PDF generation
├── retechcycle/                  # Project configuration directory
│   ├── asgi.py                   # ASGI entrypoint
│   ├── settings.py               # Django configuration & settings
│   ├── urls.py                   # Main routing table
│   └── wsgi.py                   # WSGI entrypoint
├── static/                       # Static assets & media directories
│   ├── images/                   # Theme illustrations & banners
│   ├── product_image/            # Uploaded product catalog images
│   ├── profile_pic/              # User avatars
│   └── videos/                   # Video assets
├── templates/                    # HTML templates
│   ├── admin_*.html              # Admin portal templates
│   ├── customer_*.html           # Customer dashboard and servicing templates
│   ├── download_invoice.html     # HTML template rendered into PDF invoice
│   ├── index.html                # Public landing page
│   └── navbar.html / footer.html # Reusable UI components
├── manage.py                     # Django CLI management script
├── requirements.txt              # Project dependencies
├── LICENSE                       # MIT License
└── README.md                     # Project documentation
```

---

## 🚀 Getting Started

### Prerequisites

Ensure you have the following installed on your machine:
- **Python 3.10+** (or compatible 3.8+)
- **pip** (Python package installer)
- **Git**

### Installation & Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/kabirhiking/ReTech-Cycle.git
   cd ReTech-Cycle
   ```

2. **Create and activate a virtual environment:**
   - **Linux / macOS:**
     ```bash
     python3 -m venv venv
     source venv/bin/activate
     ```
   - **Windows:**
     ```bash
     python -m venv venv
     venv\Scripts\activate
     ```

3. **Install the dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Apply database migrations:**
   ```bash
   python manage.py makemigrations
   python manage.py migrate
   ```

5. **Create a superuser (for admin access):**
   ```bash
   python manage.py createsuperuser
   ```

### Running the Application

1. **Start the Django development server:**
   ```bash
   python manage.py runserver
   ```

2. **Open in browser:**
   - Public Storefront: [http://127.0.0.1:8000/](http://127.0.0.1:8000/)
   - Customer Login: [http://127.0.0.1:8000/customerlogin](http://127.0.0.1:8000/customerlogin)
   - Admin Portal: [http://127.0.0.1:8000/adminlogin](http://127.0.0.1:8000/adminlogin)
   - Django Native Admin: [http://127.0.0.1:8000/admin/](http://127.0.0.1:8000/admin/)

---

## 🔗 Key Endpoints & Routes

| URL Pattern | View / Purpose | Access |
|---|---|---|
| `/` | Storefront landing page & product catalog | Public |
| `/customersignup` | Customer registration | Public |
| `/customerlogin` | Customer authentication | Public |
| `/customer-home` | Customer dashboard & product listing | Customer |
| `/cart` | View cart and order summary | Public / Customer |
| `/customer-address` | Shipping details entry before payment | Customer |
| `/my-order` | View personal order history | Customer |
| `/download-invoice/<orderID>/<productID>` | Download PDF invoice | Customer |
| `/customer-servicing` | Device repair service options | Customer |
| `/customer-servicing-add` | Submit a repair request | Customer |
| `/customer-sell` | Submit device for sale/recycling | Customer |
| `/admin-dashboard` | Administrative overview & metrics | Admin |
| `/admin-products` | Product management listing | Admin |
| `/admin-add-product` | Add a new product | Admin |
| `/admin-view-booking` | Manage all orders & update status | Admin |
| `/view-customer` | Manage registered customer accounts | Admin |
| `/view-feedback` | View submitted customer feedback | Admin |

---

## ⚙️ Configuration

### Email Setup (Optional)
The project includes contact form email dispatch in `retechcycle/settings.py`. To configure outgoing mail notifications:
```python
EMAIL_BACKEND = 'django.core.mail.backends.smtp.EmailBackend'
EMAIL_HOST = 'smtp.gmail.com'
EMAIL_USE_TLS = True
EMAIL_PORT = 587
EMAIL_HOST_USER = 'your-email@gmail.com'
EMAIL_HOST_PASSWORD = 'your-app-password'
EMAIL_RECEIVING_USER = ['recipient@gmail.com']
```

> **Note:** For production deployment, make sure to set `DEBUG = False`, update `ALLOWED_HOSTS`, and store sensitive credentials (such as `SECRET_KEY` and email passwords) in environment variables.

---

## 👥 Team & Acknowledgments

Developed with ❤️ by:
- **Md. Meherub Hossain Yemon**
- **Md. Raihan Kabir**
- **Md. Sohel Rahman**

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
