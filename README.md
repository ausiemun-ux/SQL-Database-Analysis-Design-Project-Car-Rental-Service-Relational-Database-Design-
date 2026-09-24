# SQL-Database Analysis & Design Car Rental Service Project [Relational Database Design]
A relational database system for a car rental service, built in Oracle APEX. Models the full reservation-to-payment lifecycle across five entities (Customer, Vehicle, Reservation, Rental, Payment) and answers three business questions on fleet utilization, customer retention, and payment risk using multi-table SQL.

## Project Overview

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

<img width="1354" height="1035" alt="Car Rental Relational Schema" src="https://github.com/user-attachments/assets/7c4b3722-c243-4ab8-8658-a8f8493fc5d1" />

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

## Entity-Relationship Diagram

<img width="1342" height="1007" alt="ERD Car Rental" src="https://github.com/user-attachments/assets/1e2a8b07-ef21-4016-b048-70efc6c83b90" />

## Business Questions Answered

The database was validated against three business questions, each backed by
a multi-table SQL query:

1. **Fleet Utilization & Revenue Optimization** — Which vehicles are most
   frequently rented vs. sitting idle, and how does that affect revenue?
   *Finding: the Tesla Model 3 led the fleet with 10 rentals and $6,949 in
   revenue, but rental count alone didn't determine profitability — the BMW
   X5 generated $5,881 from just 4 rentals due to a higher daily rate.*

2. **Customer Behavior & Retention** — Who are the most valuable repeat
   customers, and what rental patterns define them?
   *Finding: across 87 records and 67 unique customers, rental duration —
   not frequency — was the strongest driver of customer value. SUVs were
   the most-rented category overall.*

3. **Operational Risk & Payment Reliability** — Which rentals carry the
   highest nonpayment/delay risk?
   *Finding: 85 of 100 rentals were paid on time; the 15 late payments
   totaled $8,775 in delayed revenue and weren't correlated with rental
   length — meaning "only chase long rentals" wouldn't be an effective
   collections strategy.*

## Tech Stack

- **Database:** Oracle APEX (schema design, implementation, sample data)
- **Query language:** SQL (multi-table joins, GROUP BY aggregation, CASE-based classification)
- **Modeling:** Entity-Relationship diagramming, relational schema design, normalization

## Team

Group project for MIS 632 — Database Analysis & Design, Drexel LeBow.
Team: Luan Nguyen, Auspicious Munemo, Bradley Chikwavarara, Benjamin Tawiah, Mirlan Ulanov.
*My primary contribution: [fill in — e.g., ER modeling / the payment-reliability query / schema implementation in APEX]*




























