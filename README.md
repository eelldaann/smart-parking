# Smart Parking Reservation System

A web application where drivers find, reserve and pay for a parking space in advance, and parking owners manage their lots online.

> **Milestone 2:** the full source code (backend, frontend, tests, Figma screens) is in [`smart-parking-m2.zip`](smart-parking-m2.zip). The report is in [docs/milestone-2.md](docs/milestone-2.md).

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
| Backend | Python, FastAPI |
| Database | SQLite (PostgreSQL planned for deployment) |
| Payment | Stripe Checkout (test mode) + webhooks, mock provider as plan B |
| AI agent | OpenAI-compatible API with function calling |
| ML | pandas, scikit-learn (Milestone 3) |
| DevOps / QA | pytest, GitHub Actions, Render (Milestone 3) |

## Project structure

```
smart-parking/
├── frontend/   # React + TypeScript web app (driver and owner UI)
├── backend/    # FastAPI REST API, payments, AI agent, tests
├── ml/         # occupancy forecast model (Milestone 3)
├── docs/       # milestone documents, architecture diagram, Figma screens
├── .gitignore
└── README.md
```

## Branches

- `main` — stable, demo-ready code
- `dev` — integration branch; features are merged here first
- `feature/<name>` — one branch per task, merged into `dev` by pull request

## Getting started

```bash
# 1. Backend (http://localhost:8000, docs at /docs)
cd backend
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
uvicorn app.main:app --reload

# 2. Frontend (http://localhost:5173), in a second terminal
cd frontend
npm install
npm run dev
```

No keys are needed for a demo: payments use a mock checkout and the AI agent runs in offline mode. Add Stripe test keys and an OpenAI key in `backend/.env` (see `backend/.env.example`) for the real services.

## Roadmap

- [x] **Milestone 1:** idea, MVP, architecture, repository, plan
- [x] **Milestone 2:** AI agent, payment system (Stripe test mode + mock), Figma design, map search, reservations, owner dashboard — see [docs/milestone-2.md](docs/milestone-2.md)
- [ ] **Milestone 3:** ML occupancy forecast, registration and login, testing, deployment
