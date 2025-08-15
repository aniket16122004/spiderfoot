# AURUM — Men's Clothing E‑commerce (Django)

A modern Django 5 e‑commerce foundation for a men's clothing brand.

## Tech Stack
- Python 3.12+
- Django 5
- PostgreSQL (with SQLite fallback for local dev)
- Bootstrap 5, Crispy Forms (Bootstrap 5)
- Whitenoise for static files
- python‑decouple for environment variables

## Getting Started

### 1) Create and activate virtualenv
```bash
python3 -m pip install --user --break-system-packages virtualenv
~/.local/bin/virtualenv -p python3 .venv
source .venv/bin/activate
```

### 2) Install dependencies
```bash
pip install -r requirements.txt
```

### 3) Environment variables
Copy `.env.example` to `.env` and adjust values as needed.
```bash
cp .env.example .env
```

- For local dev with SQLite, keep `USE_SQLITE=True`.
- For PostgreSQL, set `USE_SQLITE=False` and configure `DB_*` values.

### 4) Apply migrations and run
```bash
python manage.py migrate
python manage.py runserver
```
Then open http://127.0.0.1:8000/

### 5) Create admin user
```bash
python manage.py createsuperuser
```

## Static files
- Place global assets under `static/`.
- `collectstatic` will output to `staticfiles/` when deploying.

## Deployment (overview)
- Set `DEBUG=False`, configure `ALLOWED_HOSTS` and `CSRF_TRUSTED_ORIGINS`.
- Ensure Postgres is configured and reachable.
- Run `python manage.py collectstatic`.
- Serve using Gunicorn/Uvicorn behind a reverse proxy. Whitenoise can serve static files.

## Project Structure
```
aurum/            # Project settings
accounts/
products/
cart/
orders/
payments/
core/
templates/
static/
```

## Notes
This is the base scaffold. Next steps: implement models, views, URLs per app, authentication, catalog, cart, checkout, and payments.
