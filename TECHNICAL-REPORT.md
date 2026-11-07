# Technical Report — Cynbit Project Intelligence

**Assignment:** Full Stack Developer Intern — Improve Cynbit's Website  
**Prototype:** Project Intelligence / Guided Project Brief Builder  
**Target website:** https://www.cynbit.in/

## 1. Executive summary

This project proposes a conversion-oriented improvement to Cynbit's website: a guided project discovery experience. Instead of asking a prospective client to compose an enquiry from a blank contact form, the prototype asks a small sequence of structured questions and produces a concise project brief. The result is a more useful starting point for a discovery conversation.

## 2. Website review and problem statement

The public website communicates Cynbit's service areas, including AI automation, custom software development, cloud/backend systems, and digital growth. It also provides a contact page with a project enquiry narrative and contact channels.

**Opportunity identified:** visitors may understand the broad service categories but still be unsure which service fits their problem, what information to provide, or how to structure an initial enquiry. A blank or minimally guided enquiry creates avoidable friction and can result in incomplete leads.

**Problem statement:** How might Cynbit help a prospective client turn an early-stage idea into a structured enquiry without requiring the visitor to understand technical service boundaries?

This is a qualitative UX hypothesis based on reviewing publicly visible pages; no private analytics, conversion data, or user interviews were available. The expected impact should be validated with real traffic and user testing.

## 3. Proposed solution

Build a four-step Project Intelligence wizard:

1. **Service intent:** software development, AI automation, cloud/backend, digital growth, or guidance.
2. **Project context:** current stage, indicative budget, and preferred timeline.
3. **Contact and requirement:** name, email, optional organization, and a short project description.
4. **Brief and next action:** suggested service direction, reviewable summary, copy action, and email handoff.

The flow uses progressive disclosure so visitors only see a manageable number of questions at a time. The summary makes the collected information transparent before the visitor takes action.

## 4. Technical architecture

The prototype is a client-side React application bundled with Vite.

- `src/main.jsx`: application shell, navigation, wizard steps, state, validation, recommendation mapping, summary, and handoff actions.
- `src/styles.css`: design system, responsive layout, component states, and mobile breakpoints.
- `index.html`: application entry point and metadata.

**State model:** a single form object stores the visitor's selections and text fields. The active step is stored separately. Validation is performed before advancing. The suggested service is derived from the service selection rather than duplicated in state.

**Data flow:** user input → local React state → client-side validation → recommendation and summary → clipboard or `mailto:` handoff.

## 5. Technology choices

| Technology | Reason |
|---|---|
| React | Component-driven UI and predictable state updates for a multi-step flow. |
| Vite | Lightweight development server and optimized production build. |
| JavaScript | Keeps the prototype straightforward to run and review. |
| CSS | Responsive styling without adding a UI framework dependency. |
| Lucide React | Consistent interface iconography. |

A database and backend API were intentionally not added because the assignment asks for a working prototype and the current scope can be demonstrated without collecting or persisting personal data. This keeps setup simple and avoids creating an unapproved production integration.

## 6. UX and accessibility considerations

- Progressive disclosure divides the enquiry into clear stages.
- Visible progress indicates how much of the flow remains.
- Inputs have associated labels and required fields are validated.
- Selection states are visually distinct.
- Layout adapts to mobile screens.
- The visitor can review the generated brief before sending it.
- The email action is explicit; the prototype does not silently submit personal information.

Further accessibility work before production should include a full keyboard-only test, screen-reader testing of step changes and validation announcements, and contrast verification against WCAG 2.2 AA.

## 7. Security and privacy

The prototype does not store data on a server and contains no API secrets. Email handoff relies on the visitor's local email client. Client-side validation improves usability but is not a security boundary. If connected to a production API, server-side validation, spam controls, rate limiting, secure transport, access controls, data minimization, and a privacy/retention notice would be required.

## 8. Testing performed / verification checklist

The source includes manual test scenarios for:

- Required service selection.
- Project stage, budget, and timeline selection.
- Invalid and valid email input.
- Minimum project-description length.
- Recommendation mapping for each service category.
- Copy-to-clipboard and email handoff.
- Responsive layouts at desktop and mobile widths.

**Note:** Run `npm install` and `npm run build` in the target environment before submission. Browser-based interaction and cross-device testing should be completed after deployment; no production analytics or real-user conversion test has been performed.

## 9. Expected impact and measurement

The feature is intended to improve enquiry quality and reduce the effort required to start a conversation. Measure its impact using:

- Wizard start-to-completion rate.
- Step-level abandonment rate.
- Percentage of completed briefs with usable project details.
- Click-through rate on the email handoff.
- Qualified enquiry rate compared with the existing contact path.

A controlled A/B test or staged rollout would be needed to establish causal conversion impact.

## 10. Limitations and future improvements

- The prototype is not integrated with Cynbit's production codebase or CRM.
- `mailto:` depends on the visitor having an email client configured.
- The recommendation is deterministic and rule-based, not AI-generated.
- No persistence, analytics, or automated acknowledgement is included.

Future iteration could add a secure enquiry API, CRM integration, file attachment support, analytics events with consent, and an accessible server-rendered implementation integrated into the existing website.

## 11. References

- Cynbit official website: https://www.cynbit.in/
- Services: https://www.cynbit.in/services
- Contact: https://www.cynbit.in/contact

---

**Submission note:** This report describes the prototype implementation. Add the final GitHub repository URL, deployed prototype URL, commit history, and actual build/test results after publishing and verifying them.
