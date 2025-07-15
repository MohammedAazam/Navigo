# 🗺️ Mall Navigation & Product Location Backend

A Django-powered backend for an indoor **mall navigation website** that helps customers find stores and products in real-time — with support for **3D indoor maps**.

---

## 👥 Team Members & Roles

| Team Member      | Responsibility                     |
|------------------|------------------------------------|
| Mohammed Aazam   | Project Setup & Version Control    |
| Preethi          | Database Setup & Environment Vars  |
| Sakshi           | Django Models Design               |
| Saniya           | 3D Map Planning & Media Storage    |

---

## ⚙️ Tech Stack

- **Backend:** Django, Django REST Framework
- **Database:** PostgreSQL
- **3D Model:** `.glb` (glTF) format for web rendering
- **API Testing:** Postman
- **Version Control:** Git + GitHub

---

## ✅ Day 1 — Detailed Assigned Tasks

---

### 🧑‍💻 Mohammed Aazam — Project Setup

**Goal:** Initialize project, create apps, push to GitHub.

**Tasks:**

1. **Create GitHub Repository**
   - Repo name: `mall-navigation-backend`
   - Add `.gitignore` (Python template)
   - Add `README.md`

2. **Set Up Virtual Environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # Mac/Linux
   venv\Scripts\activate     # Windows
   ```

3. **Install Required Packages**
   ```bash
   pip install django djangorestframework python-decouple psycopg2-binary
   pip freeze > requirements.txt
   ```

4. **Start Django Project**
   ```bash
   django-admin startproject mall_nav .
   ```

5. **Create Django Apps**
   ```bash
   python manage.py startapp stores
   python manage.py startapp products
   python manage.py startapp navigation
   ```

6. **Add Apps to `INSTALLED_APPS`**
   ```python
   INSTALLED_APPS = [
       ...
       'rest_framework',
       'stores',
       'products',
       'navigation',
   ]
   ```

7. **Push to GitHub**
   ``` Commit project structure, `.gitignore`, `requirements.txt`, and `README.md`. ```

✅ **Deliverable:** Repo live & accessible for all team members.

---

### 🧑‍💻 Preethi — Database Setup

**Goal:** Set up PostgreSQL database & user, connect via `.env`.

**Tasks:**

1. **Install PostgreSQL**  
   - Ensure local PostgreSQL server is running.

2. **Create Database & User**
   ```sql
   CREATE DATABASE mall_nav_db;
   CREATE USER malluser WITH PASSWORD 'yourpassword';
   ALTER ROLE malluser SET client_encoding TO 'utf8';
   ALTER ROLE malluser SET default_transaction_isolation TO 'read committed';
   ALTER ROLE malluser SET timezone TO 'UTC';
   GRANT ALL PRIVILEGES ON DATABASE mall_nav_db TO malluser;
   ```

3. **Add DB Config in `settings.py`**
   ```python
   DATABASES = {
       'default': {
           'ENGINE': 'django.db.backends.postgresql',
           'NAME': 'mall_nav_db',
           'USER': 'malluser',
           'PASSWORD': 'yourpassword',
           'HOST': 'localhost',
           'PORT': '5432',
       }
   }
   ```

4. **Use `.env` for DB Credentials**

   1. Install `python-decouple` if not done.

   ```python
   from decouple import config

   DATABASES = {
       'default': {
           'ENGINE': 'django.db.backends.postgresql',
           'NAME': config('DB_NAME'),
           'USER': config('DB_USER'),
           'PASSWORD': config('DB_PASSWORD'),
           'HOST': config('DB_HOST', default='localhost'),
           'PORT': config('DB_PORT', default='5432'),
       }
   }
   ```

   2. Create `.env`:
     ```
     DB_NAME=mall_nav_db
     DB_USER=malluser
     DB_PASSWORD=yourpassword
     DB_HOST=localhost
     DB_PORT=5432
     ```

✅ **Deliverable:** Run `python manage.py migrate` to confirm DB connection.

---

### 🧑‍💻 Sakshi — Draft Models

**Goal:** Design data models for store locations & products with 3D coordinates.

**Tasks:**

1. **`stores/models.py`**

   ```python
   from django.db import models

   class Floor(models.Model):
       level = models.IntegerField()
       name = models.CharField(max_length=50)

   class Store(models.Model):
       name = models.CharField(max_length=100)
       floor = models.ForeignKey(Floor, on_delete=models.CASCADE)
       x_coord = models.FloatField()
       y_coord = models.FloatField()
       z_coord = models.FloatField()
       category = models.CharField(max_length=50, blank=True)
   ```

2. **`products/models.py`**

   ```python
   from django.db import models
   from stores.models import Store

   class Product(models.Model):
       name = models.CharField(max_length=100)
       store = models.ForeignKey(Store, on_delete=models.CASCADE)
       price = models.DecimalField(max_digits=8, decimal_places=2)
       in_stock = models.BooleanField(default=True)
   ```

✅ **Deliverable:** Draft models shared in repo, ready for migrations on Day 2.

---

### 🧑‍💻 Saniya — 3D Map Planning & Media Storage

**Goal:** Decide on 3D model format and how to store/serve it.

**Tasks:**

1. **Decide Format**
   - Use `.glb` (glTF) — best for web browsers.

2. **Plan Storage**
   - Use `MEDIA` folder for development.
   - Future plan: switch to S3/CDN.

3. **Add Media Settings in `settings.py`**

   ```python
   MEDIA_URL = '/media/'
   MEDIA_ROOT = BASE_DIR / 'media'
   ```

4. **Create Folders**

   ```bash
   mkdir media
   mkdir media/models
   ```

5. **Naming Convention**
   - `mall_map.glb` → version as `mall_map_v1.glb` etc.

6. **Document in README**
   - So everyone knows where to place & update 3D map files.

✅ **Deliverable:** 3D plan clear & documented for team.

---

## ✅ End of Day 1 Checklist

- [x] GitHub repo created & pushed
- [x] Virtual environment & dependencies installed
- [x] Django project & apps created: `stores`, `products`, `navigation`
- [x] PostgreSQL database created & connected using `.env`
- [x] Draft models ready with 3D coordinates
- [x] 3D model format decided & storage plan clear
- [x] `.gitignore` excludes `.env` & `venv/`

---

## 📌 Next Steps for Day 2

- Run `makemigrations` & `migrate`
- Add dummy data for stores/products
- Test Admin site to verify models
- Start serializers for API endpoints



## 🚀 Let’s build a smarter indoor mall navigation system, together!

