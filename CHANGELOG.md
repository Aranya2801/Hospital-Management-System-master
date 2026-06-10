# Changelog

All notable changes to MedCore HMS are documented here.  
Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), versioning follows [Semantic Versioning](https://semver.org/).

---

## [2.0.0] — 2024-05-01 🎉 Major Release

### ✨ Added
- **AI-powered no-show prediction** using Random Forest model (84.3% accuracy)
- **Real-time bed occupancy maps** with Socket.IO WebSocket streaming
- **Telemedicine module** — WebRTC video consultations with screen sharing
- **Progressive Web App (PWA)** — installable, offline-capable
- **Multi-step patient registration** with Aadhar deduplication
- **Advanced analytics dashboard** — revenue trends, KPIs, doctor performance
- **HIPAA-compliant audit logging** — every data access recorded
- **Insurance claims management** with ICD-10/CPT code support
- **GST-compliant billing** — CGST/SGST itemized calculations
- **Role-based access control** — 8 granular roles
- **Emergency triage system** with ESI level 1–5 scoring
- **Lab order management** with result integration
- **Inventory forecasting** with auto reorder alerts
- **Multi-language prescription engine** with drug interaction checker
- **Email/SMS notification** system — appointment reminders, lab results
- **Docker Compose** full-stack deployment
- **GitHub Actions CI/CD** pipeline with test coverage
- **OpenAPI/Swagger** documentation at `/api-docs`
- **Redis caching** with intelligent cache invalidation
- **Soft delete** (paranoid mode) for all patient records
- **Rate limiting** with per-route configuration
- **JWT refresh token rotation** with Redis blacklisting

### 🔒 Security
- bcrypt cost factor upgraded from 10 to 12
- Account lockout after 5 failed attempts
- TLS 1.3 enforced via Nginx
- Content Security Policy headers via Helmet.js
- CORS restricted to configured origins

### 🏗️ Architecture
- Migrated from monolith to layered service architecture
- Sequelize ORM with full migration support
- Winston structured logging with log rotation
- Socket.IO for real-time events (beds, alerts, chat)

---

## [1.5.0] — 2023-11-15

### Added
- Patient profile photos upload
- Bill PDF generation with PDFKit
- Appointment token number system
- Doctor availability matrix
- Basic analytics charts

### Fixed
- Appointment double-booking edge case
- Bill total rounding errors
- JWT token not invalidated on password change

---

## [1.4.0] — 2023-09-01

### Added
- Prescription management with multi-item support
- Lab order ordering workflow
- Ward and bed management
- Admission/Discharge/Transfer (ADT) module

### Changed
- Switched from MongoDB to MySQL for relational data integrity
- Refactored API routes to `/api/v1/` prefix

---

## [1.3.0] — 2023-07-10

### Added
- Doctor scheduling and availability
- Appointment booking with time slots
- Email notifications for appointments
- Patient search with full-text indexing

---

## [1.2.0] — 2023-05-20

### Added
- Basic billing and payment tracking
- Department management
- Staff management module

---

## [1.1.0] — 2023-03-15

### Added
- Doctor registration and profile management
- Appointment status workflow
- Basic reporting

---

## [1.0.0] — 2023-01-10 🚀 Initial Release

### Added
- Patient registration and management
- Basic appointment booking
- User authentication with JWT
- Admin dashboard
- MySQL database schema
