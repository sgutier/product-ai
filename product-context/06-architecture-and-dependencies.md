# Architecture & Dependencies — EW Navigation App

This document describes the **high-level product and system architecture** of EW Navigation App and its **key dependencies**, focusing on integration with EW Office.

This is **not** a low-level technical design. It exists to:
- Inform feasibility discussions
- Surface cross-team dependencies early
- Prevent hidden coupling in initiatives

---

## High-level architecture (conceptual)

EW Navigation App consists of:

1. **Mobile App (Driver-facing)**
   - iOS and Android applications
   - Primary execution interface for drivers
   - Handles navigation, routing visualization, and driver interactions

2. **Navigation Services**
   - Routing and map services (external providers)
   - Truck-specific constraints (height, weight, hazmat, etc.)
   - Continuous dependency on map and traffic data quality

3. **EW Platform Services**
   - Identity & access (CIAM)
   - Entitlements and subscriptions
   - Core data services (users, companies, vehicles)

4. **EW Office Integration Layer**
   - Transport orders and route plans created in EW Office
   - Data synchronization between Office and Navigation
   - Ensures 1:1 route fidelity between planning and execution

---

## EW Office ↔ Navigation integration

Strategic integration principles:
- Routes planned in EW Office must be **executed as-is** in Navigation
- Navigation acts as the **execution surface**, not a planner
- Driver feedback and execution status should flow back to Office (where applicable)

Typical integration touchpoints:
- Route and stop data
- Transport order identifiers
- Driver identity and company context
- Execution status (started / completed / exceptions)

---

## Key internal dependencies (non-exhaustive)

- **CIAM** — authentication, driver identity
- **EW Office backend** — transport planning data
- **Payments / Entitlements** — premium access control
- **Data / Analytics** — usage, quality, monetization tracking
- **Customer Support / Ops** — incident handling, escalations

---

## External dependencies

- Map and routing providers (e.g. TomTom or equivalents)
- App Store / Play Store platforms
- Mobile OS constraints (background usage, permissions)

---

## Architectural constraints (important)

- Mobile performance and stability are critical
- Offline and degraded-network scenarios must be considered
- Navigation cannot depend on high-latency Office calls at runtime
- Changes impacting routing or maps have wide blast radius

---

## Implications for initiatives

When creating initiatives:
- Explicitly state which systems are touched
- Identify new data flows between Office and Navigation
- Call out dependency ownership early
- Avoid assuming “simple” integration — most are not