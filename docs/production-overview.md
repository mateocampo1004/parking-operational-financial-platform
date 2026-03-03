# Production Overview

This document describes the real-world production environment.

---

## Deployment

- Backend: Spring Boot application
- Electronic Invoicing: fe-local service
- Database: PostgreSQL
- Deployment mode: Windows Service
- Environment: Local production infrastructure

---

## Operational Load

- 30–60 tickets per day
- ~50 electronic invoices per day
- 3 active users

---

## Production Characteristics

- Real-time ticket lifecycle
- Daily financial closing
- Weekly and monthly reconciliation
- Expense tracking
- Audit logging
- Thermal POS printing

---

## Stability Considerations

- Flyway schema management
- Logging configuration
- Controlled environment deployment
- Modular separation of fiscal logic
