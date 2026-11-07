# Cynbit Project Intelligence

A responsive, interactive project-discovery prototype for Cynbit Technologies. The experience helps prospective clients identify the type of support they need, describe their project, and prepare a structured brief for the Cynbit team.

## Problem & proposed improvement

Cynbit's website already explains its service ecosystem and provides a contact route. A visitor who is not yet sure how to describe a requirement can benefit from a guided intake flow. This prototype adds a four-step project brief builder to reduce uncertainty and make enquiries more actionable.

## Features

- Responsive landing page aligned to Cynbit's dark navy / teal visual identity.
- Five service-intent choices: software, AI automation, cloud/backend, digital growth, and guidance.
- Project stage, indicative budget, and timeline capture.
- Client-side validation for contact details and project description.
- Contextual suggested direction based on the selected service.
- Reviewable project summary, copy-to-clipboard, and email handoff to `opportunities@cynbit.in`.
- No API keys or database required for this front-end prototype.

## Tech stack

- React 18+
- Vite
- JavaScript (ES modules)
- CSS (responsive layout and component states)
- Lucide React icons

## Run locally

Requirements: Node.js 18+ and npm.

```bash
npm install
npm run dev
```

Open the local URL printed by Vite (normally `http://localhost:5173`).

## Production build

```bash
npm run build
npm run preview
```

The production output is generated in `dist/`.

## Deployment

Import this repository into Vercel or Netlify. Use the following settings:

- Build command: `npm run build`
- Output directory: `dist`
- Install command: `npm install`

No environment variables are required for the prototype.

## Implementation notes

- Wizard state is managed locally with React `useState`; the suggested direction is derived with `useMemo`.
- Validation runs before each step transition.
- The email action uses a `mailto:` handoff. It opens the visitor's configured email client; it does not silently transmit or persist data.
- The copy action uses the browser Clipboard API and requires a secure context (HTTPS or localhost) in supported browsers.
- This is a prototype, not a production CRM integration. A production implementation should submit to a server-side API, validate again on the server, apply spam protection/rate limiting, and store submissions only with an appropriate privacy notice and retention policy.

## Suggested evaluation

1. Complete the wizard with each service type and verify the recommendation changes.
2. Try to continue with missing fields and invalid email to test validation.
3. Resize to mobile width and check the navigation, form controls, and summary.
4. Test copy and email handoff on HTTPS or localhost.

## Scope

This repository is an independent prototype and is not connected to Cynbit's production website, database, CRM, or email infrastructure. The live production site remains unchanged.
