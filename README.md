Pomona Research in Mathematics Experience
==============

This is the code for the Pomona Resarch in Mathematics Experience Database website.

Installation
-----------

If you already have Nginx and PostgreSQL installed and configured on your system, you can proceed with the steps below to set up a copy of the website.

```{sh}
git clone https://github.com/prime-db/prime-db.git prime-db
cd prime-db
```

#### 1. Prepare your Python environment:

```{sh}
apt install python3.10-venv
python -m venv env
. env/bin/activate
```

#### 2. Install dependencies:

```{sh}
pip install Flask gunicorn python-dotenv psycopg2-binary
```

#### 3. Configure environment variables:

Copy the example environment file and edit with your database credentials:

```{sh}
cp .env.example .env
# Edit .env with your PostgreSQL credentials
```

The following environment variables are available:
- `DB_USERNAME` - PostgreSQL username (required)
- `DB_PASSWORD` - PostgreSQL password (required)
- `DB_HOST` - Database host (default: localhost)
- `DB_PORT` - Database port (default: 5432)
- `DB_NAME` - Database name (default: prime_db)

#### 4. Initialize the database:

```{sh}
python init_db.py
```

#### 5. Run the server:

```{sh}
gunicorn --bind 0.0.0.0:57 app:app
```

For development, use:

```{sh}
python app.py
```
