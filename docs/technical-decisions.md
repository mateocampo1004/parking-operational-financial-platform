# Technical Decisions

This document explains the architectural and engineering decisions behind the Parking Operational & Financial Platform.

---

## 1. Modular Monolith Architecture

The backend was implemented as a modular monolith using Kotlin and Spring Boot.

### Why not microservices?

- Lower infrastructure complexity
- Simplified deployment (Windows Service)
- Strong transactional consistency
- Reduced operational overhead
- Clear module separation within a single runtime

The architecture remains structured to allow future service extraction if scaling requires it.

---

## 2. Separation of Fiscal Logic (fe-local)

Electronic invoicing was extracted into an independent service.

### Reasons:

- Regulatory logic evolves independently
- Security isolation of digital certificates
- Clear separation between business operations and tax compliance
- Easier scaling in VPS/cloud environments

---

## 3. AES-256-GCM Encryption

Certificate credentials are encrypted using AES-256-GCM.

### Why GCM?

- Authenticated encryption
- Integrity verification
- Modern cryptographic standard
- Proper IV handling

---

## 4. Flyway for Schema Versioning

Database migrations are managed with Flyway.

### Benefits:

- Version-controlled schema evolution
- Deterministic deployment
- Safe production upgrades

---

## 5. Desktop-First Approach

Jetpack Compose Desktop was chosen instead of web frontend.

### Reasons:

- Controlled environment (on-site operations)
- Direct printer integration (ESC/POS)
- Reduced browser complexity
- Faster UI performance

---

## 6. Windows Service Deployment

Initial deployment targets Windows Service.

### Why?

- Simplified client infrastructure
- No container dependency
- Easier local maintenance

Architecture is VPS-ready for future migration.
