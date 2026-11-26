# Smart Parking Reservation System

A web application where drivers find, reserve and pay for a parking space in advance, and parking owners manage their lots online.

## Problem

Drivers in large cities lose time searching for a free parking space and cannot know in advance whether a lot is full. Owners of private parking lots still track spaces and payments by hand and have no simple online channel for bookings.

## Key features (MVP)

1. **Map search** — see parking lots on a map with free spaces, rates and opening hours.
2. **Reservation** — book a space for a specific date and time slot.
3. **Online payment** — pay for a reservation with Stripe Checkout (test mode).
4. **AI assistant** — describe what you need in plain words; the agent finds and books a space.
5. **Occupancy forecast (ML)** — see how busy a lot will be at a given hour.
6. **Owner dashboard** — manage lots, spaces and rates; see reservations and revenue.

## Team

| Member | Group | Roles |
| --- | --- | --- |
| Eldana Amanzhol | IT1-2316 IS | Team Lead, Backend, Frontend, ML/AI, DevOps/QA |

The project is based on the thesis *"Development of a parking space management information system with a reservation function"* (supervisor: Karimzhan N.B.), written by a team of three: Amanzhol E., Seitzhan R., Zhassyuzak N. In this course the project is developed individually by Eldana Amanzhol.

## Tech stack

| Layer | Technology |
| --- | --- |
| Frontend | React, TypeScript, Vite, Leaflet + OpenStreetMap |
| Backend | Python, FastAPI, SQLAlchemy, Alembic |
| Database | PostgreSQL |
| Auth | JWT, bcrypt |
| Payment | Stripe Checkout (test mode) + webhooks |
| AI agent | OpenAI API with function calling |
| ML | pandas, scikit-learn, joblib |
| DevOps / QA | Docker Compose, GitHub Actions, pytest, Render |

## Project structure

```
smart-parking/
├── frontend/   # React + TypeScript web app (driver and owner UI)
├── backend/    # FastAPI REST API, database models, payments, AI agent
├── ml/         # occupancy dataset generator, training notebooks, saved model
├── docs/       # milestone documents, architecture diagram, presentation
├── .gitignore
└── README.md
```

## Branches

- `main` — stable, demo-ready code
- `dev` — integration branch; features are merged here first
- `feature/<name>` — one branch per task, merged into `dev` by pull request

## Getting started

Local setup with Docker Compose will be added in Milestone 2:

```
docker compose up
```

## Roadmap

- [x] **Milestone 1 (weeks 1–2):** idea, MVP, architecture, repository, plan
- [ ] **Milestone 2 (weeks 3–7):** backend, auth, map search, reservations, payment, owner dashboard
- [ ] **Milestone 3 (weeks 8–12):** occupancy forecast, AI assistant, testing, deployment
