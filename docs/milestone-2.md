# Milestone 2 — AI agent, Figma design, payment system

**Student:** Eldana Amanzhol, IT1-2316 IS · **Course:** WEB programming · **Repository:** https://github.com/eelldaann/smart-parking

Milestone 2 delivers a working prototype with the three required parts: an AI agent, a payment system and the UI design in Figma. The source code is in [`smart-parking-m2.zip`](../smart-parking-m2.zip) in the repository root.

## 1. AI agent

A chat assistant that finds and books parking from a plain-language request, for example *"Central Mall tomorrow 14:00–16:00 under 500 KZT"*.

- **How it works:** an LLM with function calling (OpenAI-compatible Chat Completions API). The model does not touch the database; it calls three tools that use the same services as the REST API:
  - `search_lots` — lots by place, type and maximum price, with free spaces now;
  - `check_slot` — bookable spaces, price and forecast occupancy for a time slot;
  - `book_and_pay` — creates the reservation and a payment link.
- **Safety:** `book_and_pay` is refused unless the user has confirmed the booking (`user_confirmed: true`); the system prompt tells the model to repeat lot, time and price and ask first.
- **UI:** the chat window on the map page shows lot suggestions as buttons and a "Pay" button after booking.
- **Without an API key** the agent runs in offline demo mode (rule-based parsing of place, time and price), so it can be shown in class.
- Code: `backend/app/services/agent.py`, `frontend/src/components/ChatWidget.tsx`.

## 2. Payment system

- **Stripe Checkout in test mode:** the backend creates a Checkout Session for the reservation (amount in KZT), the driver pays on Stripe's page, and the booking becomes *paid* after the return to the success page or after the `checkout.session.completed` webhook (signature checked with HMAC-SHA256).
- **Plan B (risk from Milestone 1):** all payments go through one `PaymentProvider` interface. If Stripe is not available for a Kazakhstan account, `PAYMENT_PROVIDER=mock` switches to a built-in test checkout page with the same flow.
- Unpaid bookings hold a space for 30 minutes; double booking beyond the online spaces of a lot is blocked.
- The owner dashboard shows paid bookings and revenue per lot.
- Code: `backend/app/services/payments.py`, `frontend/src/pages/MockPay.tsx`, `frontend/src/pages/PaymentResult.tsx`.

## 3. Figma design

Four screens: map and booking, AI assistant, payment and confirmation, owner dashboard.

- Figma file: https://www.figma.com/design/oDqk3GvzZIiWQ72XW1gFYh/Smart-Parking-%E2%80%94-Milestone-2
- The same screens as images are in the archive: `docs/figma/screen-1.png` … `screen-4.png`.

## How to run

See the Getting started section of the main README. In short: `uvicorn app.main:app --reload` in `backend/`, `npm install && npm run dev` in `frontend/`, open http://localhost:5173.

## Tests

`python -m pytest` in `backend/` — 9 tests cover search, forecast, pricing, double booking, the mock payment flow, Stripe webhook signatures and the agent's confirmation rule.

## Next (Milestone 3)

Replace the baseline forecast with the trained ML model, add registration and login, deploy the app.
