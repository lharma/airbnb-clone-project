# 🧹 Database Normalization — ALX Airbnb Project

## 🧠 Overview
This document explains how the Airbnb database design was normalized up to **Third Normal Form (3NF)** to remove redundancy and improve consistency.

---

## 🧩 Step 1 — First Normal Form (1NF)
**Rule:**  
Each table cell must hold a single value, and each record must be unique.

**Applied Fixes:**
- Split multiple contact details into separate rows (User table).
- Created unique primary keys for each entity (`user_id`, `property_id`, `booking_id`, `payment_id`).
- Ensured all columns hold atomic values (no repeating groups).

✅ *Result:* Every table has a primary key, and no repeating fields.

---

## 🧩 Step 2 — Second Normal Form (2NF)
**Rule:**  
Table must be in 1NF and all non-key attributes must depend on the whole primary key.

**Applied Fixes:**
- Removed partial dependencies.
- Created separate tables where data depended on only part of a composite key (e.g., moved property info from Booking to Property table).

✅ *Result:* Each non-key attribute depends entirely on its table’s primary key.

---

## 🧩 Step 3 — Third Normal Form (3NF)
**Rule:**  
Table must be in 2NF and all columns should depend only on the primary key, not on other non-key attributes.

**Applied Fixes:**
- Removed derived or calculated fields (e.g., total_amount is computed but kept for faster queries).
- Moved user role information into `user_type` instead of a separate table for simplicity.
- Eliminated transitive dependencies (e.g., payment_status now belongs only in the Payment table, not Booking).

✅ *Result:* Database is in **Third Normal Form** — minimal redundancy, high integrity.

---

## 🧾 Summary Table

| Normal Form | Purpose | Example Fix |
|--------------|----------|-------------|
| **1NF** | Remove repeating data | Split contact details |
| **2NF** | Eliminate partial dependency | Separate Property from Booking |
| **3NF** | Remove transitive dependency | Keep payment info in its own table |

---

## ✅ Final Notes
- The final schema is **fully normalized (3NF)**.  
- Foreign keys maintain relationships between tables.  
- This structure supports scalability and clean data management for the Airbnb-like application.  
