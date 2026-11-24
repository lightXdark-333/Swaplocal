# SwapLocal — Django Marketplace + Local Delivery Starter

This is a starter MVP for a local C2C marketplace. It includes:
- Product listing, image upload, search and category filter
- User sign up, login and dashboard
- Purchase requests and seller status actions
- Delivery partner profile registration
- Django admin management

## Run in Replit

The project is set up to run from the Replit workflow using Python 3.13 and port 8000. On first setup, install the packages from `requirements.txt`, then apply the database migrations:

```bash
python -m pip install -r swaplocal/requirements.txt
./.pythonlibs/bin/python swaplocal/manage.py migrate
```

The app uses SQLite and stores its database at `swaplocal/db.sqlite3`. The homepage is the marketplace; `/admin/` opens Django's admin site. To create an admin login:

```bash
./.pythonlibs/bin/python swaplocal/manage.py createsuperuser
```

To run the app manually instead of using the Replit workflow:

```bash
./.pythonlibs/bin/python swaplocal/manage.py runserver 0.0.0.0:8000
```

The development workflow allows Replit preview hosts and uses the workspace `SESSION_SECRET` for Django's signing key when available. Keep `DEBUG` enabled only for development; set `DEBUG=false`, `DJANGO_SECRET_KEY`, `ALLOWED_HOSTS`, and `CSRF_TRUSTED_ORIGINS` appropriately before publishing.

## Requirements
- Python 3.10+ (Python 3.12 recommended)
- Internet for installing packages the first time

## Setup

### 1. Extract the ZIP and open a terminal in the project folder

### 2. Create and activate a virtual environment

Windows PowerShell:
```powershell
py -m venv .venv
.venv\Scripts\Activate.ps1
```

macOS / Linux:
```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install packages
```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Create database tables
```bash
python manage.py makemigrations marketplace
python manage.py migrate
```

### 5. Create an admin account
```bash
python manage.py createsuperuser
```

### 6. Run the development server
```bash
python manage.py runserver
```

Open http://127.0.0.1:8000/ in your browser. Admin: http://127.0.0.1:8000/admin/

## Important scope and safety notes
- This is a development starter, not a production-ready marketplace.
- Online payments, refunds, escrow/holding customer funds, live chat, geolocation matching, SMS/OTP, identity-document verification, agent payout automation and ratings are not implemented yet.
- The delivery profile currently stores phone and service area only; an administrator must manually verify users using an appropriate process before real delivery work.
- Do not collect identity documents or bank/mobile-wallet credentials without a lawful, secure, consent-based process.
- Before deployment: set `DEBUG = False`, use environment variables for `SECRET_KEY`, configure `ALLOWED_HOSTS`, HTTPS, secure cookies, production database/storage, backups, logging, rate limits, privacy policy, terms, dispute/refund rules and security testing.
- Use a Bangladesh-authorized payment provider and confirm the applicable legal requirements before accepting or holding customer funds. Never store payment card or mobile-wallet PINs.
- Product images are uploaded to local media storage in development; use validated uploads and managed object storage in production.

## Next development milestones
1. Add a private, real-time buyer/seller messaging system (Django Channels/WebSockets).
2. Add seller acceptance and delivery job creation.
3. Add location-aware agent matching with explicit location permission and a configurable radius.
4. Add delivery pickup/delivery OTP and audit logs.
5. Integrate an approved payment gateway and verified payout workflow.
6. Add ratings and moderation after completed transactions.
