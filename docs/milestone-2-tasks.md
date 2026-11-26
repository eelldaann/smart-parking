# Milestone 2 tasks (weeks 3–7)

Each task below is one GitHub issue: copy the title into the issue title and the text into the description. Assignee for all tasks: Eldana Amanzhol.

---

## T1 Backend setup: FastAPI, Docker Compose, PostgreSQL

**Week:** 3 · **Depends on:** repository (Milestone 1)

- [ ] Create FastAPI project in `backend/`
- [ ] Add Docker Compose with PostgreSQL
- [ ] Database schema and Alembic migrations: users, lots, spaces, reservations, payments

## T2 Frontend setup: React app, routing, login and sign-up pages

**Week:** 3–4 · **Depends on:** repository (Milestone 1)

- [ ] Create React + TypeScript app with Vite in `frontend/`
- [ ] Add routing and a basic layout
- [ ] Login and sign-up pages

## T3 Auth API: registration, login, JWT, roles

**Week:** 4 · **Depends on:** T1

- [ ] Registration and login endpoints
- [ ] Password hashing with bcrypt, JWT tokens
- [ ] Driver and owner roles

## T4 Owner API: lots, spaces and rates

**Week:** 5 · **Depends on:** T3

- [ ] Create, edit and delete parking lots
- [ ] Manage spaces and hourly rates
- [ ] Only the owner of a lot can change it

## T5 Reservation API: time slots without double booking

**Week:** 5 · **Depends on:** T3

- [ ] Check availability for a date and time slot
- [ ] Create and cancel a reservation
- [ ] Database constraint against overlapping reservations

## T6 Map search page

**Week:** 6 · **Depends on:** T2, T4

- [ ] Show lots on a Leaflet map
- [ ] Filters: price, free spaces, opening hours
- [ ] Lot card with address, rates, hours and free spaces

## T7 Stripe Checkout (test mode) and payment webhook

**Week:** 6 · **Depends on:** T5

- [ ] Create a Checkout session for a reservation
- [ ] Webhook marks the reservation as paid
- [ ] Handle failed and cancelled payments

## T8 Booking UI: choose a slot, pay, "My bookings"

**Week:** 7 · **Depends on:** T6, T7

- [ ] Choose date and time slot on the lot card
- [ ] Redirect to payment and back
- [ ] "My bookings" page with status

## T9 Owner dashboard

**Week:** 7 · **Depends on:** T4, T7

- [ ] List of the owner's lots
- [ ] Reservations per lot
- [ ] Revenue summary

## T10 API tests and CI

**Week:** 7 · **Depends on:** T5, T7

- [ ] pytest tests for auth, reservations and payments
- [ ] GitHub Actions workflow runs tests on every push
