# Hair Booking App

A MERN-stack booking app for a single-stylist hair salon.

## Overview

Customers can browse services, view available days, and book an appointment. The stylist has one account to set their availability and view or cancel upcoming bookings. The system prevents double-booking: each day has one fixed 5-hour slot, and a day that is already booked cannot be booked again.

## Tech Stack

- **Frontend:** React (Vite)
- **Backend:** Node.js, Express
- **Database:** MongoDB (Atlas) with Mongoose
- **Auth:** JWT, bcrypt

## User Roles

- **Customer:** registers, logs in, books and cancels their own appointments
- **Stylist:** a single account, seeded manually, who manages availability and bookings

## Features (v1)

- **Auth:** customer registration and login; stylist login
- **Stylist:** set availability per date (open or blocked, with a working window), view upcoming bookings, cancel a booking
- **Customer:** browse services, view available days, book a slot, view and cancel own bookings
- **System:** conflict check on booking creation (one booked appointment per day)

## Out of Scope for v1

- Payments
- SMS or email reminders
- Reviews
- Recurring appointments
- Variable-length services

## Data Model

| Collection | Fields |
|---|---|
| **Users** | name, email (unique), password (hashed), role (customer / stylist) |
| **Services** | name, description, price |
| **Availability** | date, isAvailable, startTime, endTime |
| **Appointments** | customer (ref User), service (ref Service), date, status (booked / cancelled) |

**Booking rule:** a booking is allowed only if the date has an Availability entry with `isAvailable: true` and no existing Appointment with `status: "booked"` on that date.

## Project Structure

- `client/` - React frontend
- `server/` - Express API

## Status

In development. Planning and schema design complete; backend setup next.
