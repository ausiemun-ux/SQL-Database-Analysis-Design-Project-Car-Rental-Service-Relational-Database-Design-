# SQL-Database Analysis & Design Car Rental Service Project [Relational Database Design]
A relational database system for a car rental service, built in Oracle APEX. Models the full reservation-to-payment lifecycle across five entities (Customer, Vehicle, Reservation, Rental, Payment) and answers three business questions on fleet utilization, customer retention, and payment risk using multi-table SQL.

## Project Overview (for README.md body)

```markdown
# Car Rental Service — Relational Database Design

A relational database designed and implemented in Oracle APEX to support the
full operational lifecycle of a car rental business — from customer
registration and vehicle inventory through reservation, active rental, and
payment processing.

## Business Problem

Car rental operations involve several interdependent workflows: customers
browse and reserve vehicles, pick them up to begin an active rental, and pay
upon return. Managing this manually or across disconnected systems creates
data redundancy, booking conflicts, and unreliable reporting. This project
analyzes those operational requirements and translates them into a
normalized relational schema that enforces business rules (e.g., a vehicle
cannot be double-booked) and supports accurate management reporting.

## Data Model

The schema is built around five core entities:

| Entity | Role |
|---|---|
| **Customer** | Identity and legal details (license number, DOB) required for rental agreements |
| **Vehicle** | Fleet inventory — make, model, daily rate, status, category |
| **Reservation** | A booking intent — links a customer to a vehicle for a future date range |
| **Rental** | The actual fulfilled transaction — a reservation converts to a rental only if the customer follows through |
| **Payment** | One or more financial transactions tied to a single rental |

A key design decision was separating **Reservation** from **Rental**: a
reservation represents booking intent and doesn't always convert into an
actual rental (e.g., cancellations), so modeling them as distinct entities
with a 0-or-1 relationship keeps the data accurate to how the business
actually operates.
