# Glossary — EW Navigation App & EW Office Integration

This glossary defines **canonical terms** used across EW Navigation App initiatives.
All product artifacts should use these terms **consistently**.

If a term is missing or ambiguous, add it here before using it elsewhere.

---

## Core Product Terms

**EW Navigation App**  
The driver-facing mobile application (iOS / Android) providing truck-specific navigation and acting as the execution surface for EW Office transport workflows.

---

**EW Office**  
The back-office platform used by carriers and dispatchers for transport planning, cost calculation, execution management, and operational workflows.

---

**Navigation (Execution Layer)**  
The role of EW Navigation App as the system that executes routes and transport plans created in EW Office. Navigation does not plan routes at a business level; it executes them.

---

**Transport Execution**  
The phase where a planned transport is carried out by the driver, including navigation, stops, exceptions, and completion.

---

## User & Segment Terms

**Driver**  
A professional truck driver using EW Navigation App. May be company-employed or self-employed.

---

**Company Driver**  
A driver employed by a transport company, typically executing routes assigned by a dispatcher via EW Office.

---

**Owner-Operator**  
A self-employed driver who owns and drives their own truck and makes both operational and business decisions.

---

**Dispatcher / Planner**  
A back-office user of EW Office responsible for planning routes, assigning transports, and monitoring execution.

---

**BYOD (Bring Your Own Device)**  
Scenario where a driver uses a personal device rather than a company-managed one.

---

## Planning & Routing Terms

**Route**  
A calculated path from origin to destination, including intermediate stops, generated with truck-specific constraints.

---

**1:1 Route Fidelity**  
Principle that the route planned in EW Office should be executed identically in EW Navigation App, without silent recalculation or deviation.

---

**Stop**  
A planned intermediate location in a route (e.g. pickup, delivery, rest).

---

**Exception**  
Any deviation from the planned route or execution (e.g. blocked road, missed stop, delay).

---

## Metrics & Quality Terms

**MAD (Monthly Active Drivers)**  
Number of unique drivers active in EW Navigation App in a calendar month.

---

**Crash-Free Rate (CFR)**  
Percentage of navigation sessions completed without an app crash. Primary stability guardrail.

---

**ANR (App Not Responding)**  
Android-specific metric indicating unresponsive app behavior.

---

**Route Completion Rate**  
Percentage of started routes that reach their intended destination.

---

**App Store Rating**  
Weighted average user rating across app stores. Lagging indicator of perceived quality.

---

## Monetization Terms

**Freemium**  
Model where core navigation functionality is free, with optional paid enhancements.

---

**Premium Feature**  
A feature requiring payment or entitlement beyond the free baseline.

---

**Entitlement**  
Backend-controlled access right determining whether a user can access a paid or restricted feature.

---

**Attach Rate**  
Percentage of users who adopt a paid feature or bundle in addition to a base product.

---

**ARPU (Average Revenue Per User)**  
Average revenue generated per active user over a defined period.

---

## Initiative & Delivery Terms

**Initiative**  
A bounded product investment defined by a hypothesis, scope, metrics, and decision intent. Initiatives begin with a Birth Certificate.

---

**Birth Certificate**  
The mandatory entry artifact for an initiative, defining hypothesis, scope, metrics, risks, and rationale before discovery or delivery.

---

**Discovery**  
The phase focused on validating assumptions, reducing uncertainty, and learning before committing to delivery.

---

**PRD (Product Requirements Document)**  
A document translating validated discovery outcomes into buildable requirements.

---

**Guardrail Metric**  
A metric that must not degrade while pursuing an initiative (e.g. CFR, ANR).

---

**Phase**  
A relative planning unit (e.g. Discovery, MVP, Scale) used instead of fixed calendar commitments when uncertainty is high.

---

## Explicit Out-of-Scope Terms

**Embedded / OEM Navigation**  
Navigation solutions integrated directly into vehicle hardware. Explicitly out of scope for this context.

---

**Passenger Navigation**  
Navigation for non-professional or passenger vehicles. Out of scope.

---

## Usage Rules

- Use glossary terms **as defined here**
- Avoid inventing near-synonyms
- If a term is overloaded, clarify it or add a new definition
- When in doubt, update this glossary first