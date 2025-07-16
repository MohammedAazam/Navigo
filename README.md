# 🗺️ Mall Navigation & Product Location Backend

A Django-powered backend for an indoor **mall navigation website** that helps customers find stores and products in real-time — with support for **3D indoor maps**.

---

## 👥 Team Members & Roles

| Team Member      |
|------------------|
| Mohammed Aazam   |
| Preethi          | 
| Sakshi           | 
| Saniya           | 

---

## ⚙️ Tech Stack

- **Backend:** Django, Django REST Framework
- **Database:** PostgreSQL
- **3D Model:** `.glb` (glTF) format for web rendering
- **API Testing:** Postman
- **Version Control:** Git + GitHub

---

## 📆 ✅ Day 2 — Backend Task Plan

### 🎯 Day 2 Main Goal
- ✅ Migrate all models into PostgreSQL
- ✅ Add dummy data for Floors, Stores & Products
- ✅ Test in Django Admin
- ✅ Add basic serializers for DRF APIs
- ✅ Upload and test a 3D map placeholder in media/

### 👥 Team Member Tasks

#### Mohammed Aazam — Team Lead & Repo Maintenance
- Pull team changes & test migrations.
- Create superuser & test admin.
- Add dummy Floors, Stores, Products.
- Write data seeding steps in README.md.
- Merge & resolve conflicts. Push clean repo.

#### Preethi — DB Validation & Dummy Data
- Verify DB connection on other machines.
- Add or verify dummy data.
- Check foreign keys and data consistency.
- Test Admin filters & search.

#### Sakshi — Migrations & Serializers
- Run makemigrations & migrate.
- Create serializers.py in stores/ & products/.
- Use ModelSerializer for Floor, Store, Product.
- Push serializers to GitHub.

#### Saniya — 3D Map File & Media Test
- Upload dummy mall_map.glb to media/models/.
- Test URL access locally.
- Add media serving in mall_nav/urls.py.
- Document storage in README.md.

### ✅ Day 2 Checklist
- [ ] Models migrated
- [ ] Dummy data seeded
- [ ] Admin tested
- [ ] Serializers ready
- [ ] 3D map file tested
- [ ] Commits pushed & reviewed

**Team X6 — Let’s smash Day 2! 🚀**
