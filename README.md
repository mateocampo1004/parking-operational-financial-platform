# 🚗 Parking Operational & Financial Management Platform

Production-grade operational and financial management system developed for **Morvaden**, designed to support real-world parking business operations and electronic invoicing under Ecuadorian SRI regulations.

> Source code is private for commercial and intellectual property reasons.  
> This repository documents architecture, technical decisions, and production deployment strategy.

---

## 🏢 Client Context

This platform was developed for **Morvaden**, a real-world parking operation requiring:

- Operational vehicle flow control
- Financial reconciliation and daily cash management
- Electronic invoicing compliant with SRI (Ecuador)
- Secure, auditable financial operations
- Thermal POS printing integration

The system is currently running in production.

---

## 📊 Production Metrics

- Deployment: Production (since 2026)
- Tickets processed per day: 30–60
- Electronic invoices per day: ~50
- Active operational users: 3
- Deployment mode: Windows Service
- VPS migration: Architecture-ready

---

# 🏗 High-Level Architecture

Jetpack Compose Desktop (UI)  
↓  
Spring Boot Backend (Modular Monolith)  
↓  
fe-local (Electronic Invoicing Microservice)  
↓  
SRI Ecuador  

The system separates operational logic from fiscal logic, ensuring maintainability, security, and regulatory isolation.

---

# 🧠 Backend Architecture

### Stack

- Kotlin
- Spring Boot
- PostgreSQL
- Flyway (schema versioning)

### Core Modules

- Ticket lifecycle management (entry / exit)
- Cash shift management (daily close)
- Weekly financial close
- Monthly financial close
- Expense control
- User and permission matrix
- Audit logging
- Electronic document synchronization

### Architectural Rationale

A modular monolith architecture was chosen to:

- Maintain transactional consistency
- Reduce infrastructure complexity
- Simplify operational deployment
- Allow future service extraction if scaling requires it

---

# 🧾 Electronic Invoicing Microservice (fe-local)

The fiscal logic is isolated into an independent service responsible for:

- XML generation compliant with SRI v2.1.0
- XSD validation
- Digital signature using PKCS#12 certificates
- AES-256-GCM encryption for secure certificate handling
- Webhook-based status synchronization
- Automatic RIDE PDF generation

### Why Separation?

- Fiscal regulations evolve independently
- Security boundary between business and tax logic
- Easier scalability for cloud/VPS environments

---

# 💻 Desktop Application

Built with:

- Jetpack Compose Desktop
- Ktor HTTP client
- MSI installer via Gradle

### Capabilities

- Real-time ticket operations
- Financial closing interfaces
- Expense control
- Thermal ESC/POS printing integration

---

# 🔐 Security Design

- AES-256-GCM encryption for sensitive certificate credentials
- Audit logging of critical system actions
- Environment-based configuration isolation
- Separation between fiscal and operational domains

---

# 🗄 Database & Persistence

- PostgreSQL
- Flyway-managed migrations
- Transactional financial operations
- Structured logging configuration

---

# 🚀 Deployment Strategy

Current:

- Windows Service deployment
- Local production infrastructure
- Version-controlled database migrations

Planned:

- VPS/cloud migration
- Infrastructure hardening
- Multi-client scaling

---

# 🧩 Engineering Challenges Addressed

- Secure digital certificate workflow
- AES-256-GCM implementation with proper IV handling
- Asynchronous webhook reconciliation
- Financial closing logic with transactional integrity
- Direct ESC/POS command generation
- Modular separation between fiscal and operational services

---

# 📁 Documentation Structure

/docs  
- technical-decisions.md  
- production-overview.md  
- diagrams/  
- screenshots/  

---

# 📌 Positioning

This system represents:

- Real-world financial software in production
- Government tax authority integration
- Modular backend architecture
- Secure credential management
- Desktop operational platform

Developed for Morvaden as a commercial-grade operational solution.
