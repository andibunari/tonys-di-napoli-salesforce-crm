# Tony's Di Napoli — Salesforce Restaurant CRM

A custom Salesforce CRM built to manage reservations, guests, menu items, and orders for a real-world restaurant. This is a portfolio project demonstrating end-to-end Salesforce admin skills — from data modeling to automation, UI, and reporting.

**Why this project:** I waited tables at Tony's Di Napoli in NYC for 10 years. After earning three Salesforce certifications (Associate, Admin, Platform App Builder), I wanted to ground my admin skills in a domain I actually understand. Most demo orgs feel generic. This one solves real problems I saw on the floor.

---

## 📋 What This CRM Does

A restaurant manager using this CRM can:
- Track every reservation, guest, table, menu item, and order
- See which days are busiest and plan staffing
- Identify VIP guests and their preferences
- Find best-selling menu items and revenue per item
- Get a single dashboard view of restaurant performance

---

## 🏗️ What I Built

### Data Model — 5 Custom Objects

| Object | Purpose |
|--------|---------|
| **Table** | Tracks each table at the restaurant — number, capacity, location, status |
| **Guest** | Customer records with contact info, preferences, VIP status, visit history |
| **Reservation** | Bookings linking a Guest to a Table at a date and time |
| **Menu Item** | Restaurant menu — name, category, price, dietary tags, availability |
| **Order** | Items ordered during a reservation — quantity, status, total price |

Real Tony's location names are used in picklist values (Main Floor Dining Room, Wine Room, Party Room, Café, Main Bar, etc.) for authenticity.

### Automation — 3 Flows + 2 Validation Rules

**Flow 1 — Reserve a Table:** When a reservation is created, the linked table's status flips to "Reserved" automatically.

**Flow 2 — Release a Table:** When a reservation is marked Completed or Cancelled, the linked table's status returns to "Available."

**Flow 3 — Track Guest Visits:** When a reservation is marked Completed, the linked guest's Total Visits counter increments by 1 and Last Visit Date updates to today. Built with null-safe formula handling using `BLANKVALUE()`.

**Validation Rule 1:** Guests must have either a phone number OR an email — at least one contact method required.

**Validation Rule 2:** Reservation party size cannot exceed the linked table's capacity. Prevents double-booking small tables for large parties.

### UI — Custom Lightning App

Custom-branded Restaurant CRM Lightning App with Tony's Di Napoli logo, dedicated nav for Tables / Guests / Reservations / Menu Items / Orders / Reports / Dashboards, custom page layouts, and compact layouts for fast record scanning.

### Reports & Dashboard

**3 Reports built:**
- **Busiest Reservation Days** — reservations grouped by date, sum of party sizes (covers)
- **Top Ordered Menu Items** — menu items ranked by quantity sold and revenue (filtered to served orders only)
- **VIP Guests by Total Visits** — loyalty leaderboard

**1 Executive Dashboard** — Restaurant Overview, including:
- Total Reservations metric (with conditional formatting)
- Total Covers metric (with thresholds based on real Tony's operational benchmarks)
- Bar charts for busiest days and top menu items
- Lightning Table for VIP guest list

---

## 🛠️ Skills & Tools Demonstrated

- Salesforce Lightning Platform
- Custom Object & Field Design
- Master-Detail vs Lookup Relationships
- Roll-Up Summary Fields (with filters)
- Record-Triggered Flows (with entry conditions and null-safe formulas)
- Validation Rules
- Custom Report Types
- Reports (Tabular, Summary, Matrix)
- Lightning Dashboards (Metric, Chart, Table widgets)
- Custom Lightning App + Page Layouts + Compact Layouts
- Industry-informed UX decisions

---

## 🚧 Known Issues & v2 Roadmap

I built this as v1 with the goal of shipping rather than perfecting. Below is a list of items I would address in a v2 — capturing them publicly demonstrates how I think about technical debt and prioritization.

- **Total_Visits redundancy** — Currently a flow-driven Number field on Guest. In v2 I'd convert it to a formula field that references the filtered Total_Reservations roll-up. Eliminates the flow and prevents data drift.
- **Last Visit Date logic** — Currently captures the date the reservation was marked Completed, not the actual reservation date. Needs adjustment.
- **Sample data realism** — Some early sample orders have placeholder pricing. Future versions will use realistic pricing throughout.
- **Walk-in tracking** — Restaurant has significant walk-in traffic that the current data a model doesn't capture. Would add a Walk_In__c object and link to Guest in v2.
- **Formal flow testing** — Flows 1 and 2 work as expected from informal testing but would benefit from documented test cases.

---

## 📬 Contact

I'm actively looking for Salesforce Administrator roles. If you're hiring or know of openings, I'd love to connect.

- **LinkedIn:** [linkedin.com/in/andi-bunari](https://www.linkedin.com/in/andi-bunari/)
- **Email:** bunariandi@gmail.com

---

*Built April 2026.*
