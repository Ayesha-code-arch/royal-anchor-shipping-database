# Royal Anchor Shipping Database

## Overview

This project designs a comprehensive relational database for Royal Anchor Shipping (RAC), a British container‑shipping company. The system manages vessel scheduling, cargo tracking, customer bookings and crew operations across an international fleet. A 22‑table schema enforces referential integrity and business rules through primary/foreign keys, check constraints, triggers and indexes.

## Entities & Schema

The database includes tables such as:

- **Container_Vessel** – stores vessel identifiers, IMO numbers, capacity (TEUs), vessel type and dimensions.

- **Ports and Routes** – `Port` and `Route` tables record ports of call and linear service routes with origin/destination, total nautical miles and estimated duration.

- **Bookings and Containers** – `Container_Booking` captures customer bookings, linking vessels, schedules and containers. `Goods_Assignment` assigns individual goods to bookings and containers, tracking commodity type, weight, refrigeration requirement and hazardous status.

- **Crew and Certification** – `Crew_Member` and `Department` tables manage crew assignments to vessels and departments. Triggers (e.g., `trg_crew_member_cert_date`) ensure certifications are valid by enforcing future expiry dates.

- **Customers, Goods & Invoices** – tables capture customer information, cargo details and invoice payments; supporting many‑to‑many relationships via junction tables.

A full Entity‑Relationship Diagram (ERD) is provided in the report along with tables listing primary keys, foreign keys, not‑null constraints, check constraints, unique constraints and indexes.

## Constraints & Business Rules

Key constraints implemented include:

- **Primary keys** for each table to uniquely identify records.
- **Foreign keys** to enforce referential integrity across related entities (e.g., bookings reference vessels, goods reference bookings).
- **Not‑null constraints** to ensure critical fields (e.g., booking_date, customer_name) are always provided.
- **Check constraints** enforcing business logic, such as positive container capacity, crew certification expiry dates in the future, and valid container types.
- **Unique constraints** for attributes like IMO numbers and container codes to avoid duplication.
- **Triggers** (e.g., `trg_crew_member_cert_date`) verifying that crew certification expiry dates are not in the past.
- **Indexes** on frequently queried columns (e.g., booking date, vessel ID) to improve performance.

## Usage

The SQL DDL scripts and sample data can be created by following the schema described in the report:

1. Create tables using the provided definitions, ensuring primary/foreign keys and constraints are applied.
2. Insert sample data for vessels, ports, routes, crew members, customers and bookings.
3. Use the included complex queries to generate reports such as:
   - Tracking temperature‑sensitive cargo.
   - Monitoring vessel schedules and delays.
   - Verifying crew certification compliance.

## Files

- **DataAnalysis1_92_100_single.docx** – the full coursework report with the ERD, table definitions, constraints, assumptions and example SQL queries.
- Additional SQL scripts and sample datasets can be added under a `src/` or `sql/` directory.

## License

This project is licensed under the MIT License – see the LICENSE file for details.

## Acknowledgements

This database design was developed for the CI7230 coursework at Kingston University. It draws on requirements provided by the Royal Anchor Shipping case study.
