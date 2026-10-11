# Question Bank

This is a coverage map, not a script. Each area lists the questions a complete PRD needs answered. Skip anything already known, rephrase to fit the conversation, and ask the 3–5 most important frontier questions per round.

Legend: **(D)** is divergent: ask open-ended, with no suggestion. **(C)** is convergent: offer a recommended answer.

---

## Core areas (always cover)

### A. Problem and motivation → PRD §1–2
- (D) What problem are we solving, and for whom? What happens today without this?
- (D) How do people handle it today? What workarounds, tools, or spreadsheets do they use? Where does it hurt most?
- (D) Why now? What changed: a customer, a deadline, a competitor, a new capability?
- (D) If this works perfectly, what's different six months after launch?
- (C) Is this a new product, a new feature in an existing product, or a change to existing behavior?
- (D) What evidence do we have that the problem is real: data, quotes, tickets, lost deals?

### B. Users and journeys → PRD §3
- (D) Who is the primary user? Describe one real person, including their role, context, and skill level.
- (D) Who else is involved: secondary users, admins, approvers, people affected but not using it?
- (C) Who is explicitly *not* a target user for v1?
- (D) Walk me through one real session from start to finish, with a named person. Where do they come from, what do they do, and when do they know it worked?
- (D) What's the most common failure or edge case in that journey, and what should happen?
- (C) How often do they do this: many times a day, weekly, once?

### C. Scope and non-goals → PRD §5–6
- (D) What is the smallest version that would still solve the core problem?
- (C) Which of these capabilities are Must / Should / Could / Won't for v1? (Propose a MoSCoW split from what you've heard.)
- (C) What are we explicitly *not* building, even though someone might expect it?
- (C) What's deferred to v2, and is any of it emotionally important to the stakeholder?

### D. Capabilities (functional requirements) → PRD §4
For each feature area:
- (D) What must the user be able to do here?
- (C) What are the rules? (Permissions, limits, validation, states and transitions.)
- (C) What happens when it fails, or when input is empty, invalid, duplicated, or too large?
- (C) How do we know it's done? (Propose testable acceptance criteria in Given/When/Then or plain checkable statements.)
- (C) Notifications, history, undo, export: needed or not?

### E. Quality and constraints → PRD §7–8
- (C) Performance: what response time feels acceptable? What volume of data and users at launch and in 12 months?
- (C) Availability: what happens to the business if this is down for an hour? A day?
- (C) Security and privacy: what sensitive data is involved? Who can see what?
- (C) Accessibility: what target? (Suggest WCAG 2.1 AA for anything customer-facing.)
- (C) Platforms and devices: web, iOS, Android, desktop, API? Which browsers or OS versions?
- (C) Localization: which languages, currencies, time zones?
- (C) Hard constraints: budget, deadline, team size, mandated tech, existing systems we must use?

### F. Success metrics → PRD §9
- (D) How will you personally decide whether this was worth building?
- (C) What's the primary metric, its current baseline, and the target? (Propose one.)
- (C) What must *not* get worse? (Counter-metric, e.g. support tickets, error rate, churn.)
- (C) When do we measure: at launch, 30 days, 90 days?

### G. Risks, dependencies, and rollout → PRD §10–11
- (D) What could make this fail? What keeps you up at night about it?
- (C) What do we depend on: other teams, vendors, APIs, data, approvals?
- (C) Rollout: everyone at once, a beta group, a feature flag, phased by region or customer?
- (C) Who needs to sign off, and who owns the PRD and the delivery?
- (C) Target date or milestone? Is it fixed or flexible?

---

## Optional modules (pull in when the concern applies)

### Consumer / branded product
- (D) What should it *feel* like? Reference products you like and ones you don't.
- (C) Tone of voice for in-product text?
- (C) Monetization: free, freemium, subscription, one-time, ads? What's behind the paywall?
- (C) Onboarding: what's the first-run experience? Is sign-up required before value?

### B2B / enterprise
- (C) Multi-tenant? Roles and permissions model (e.g. owner / admin / member / viewer)?
- (C) SSO (SAML/OIDC), SCIM provisioning, audit log needed?
- (C) Integrations with existing systems (CRM, ERP, Slack, email, data warehouse)?
- (C) Data residency, retention, and deletion requirements?
- (C) SLAs, support tier, and who's on call?
- (D) Who is the buyer vs. the user, and what does each need to see to say yes?

### Regulated domain
- (C) Which regimes apply: GDPR, HIPAA, PCI-DSS, SOC 2, local data-protection law, industry rules?
- (C) What must be auditable, and for how long?
- (C) Any consent, age-gating, or record-keeping obligations?

### Payments / money
- (C) Payment provider? Currencies? Refunds, chargebacks, failed-payment handling?
- (C) Invoicing and tax requirements?

### API / developer product
- (D) Who calls this API, and what are they trying to accomplish?
- (C) Auth method, rate limits, versioning and deprecation policy?
- (C) SDKs, docs, and sandbox needed for v1?
- (C) Backward-compatibility guarantees?

### Data / analytics / reporting
- (C) What decisions will people make from this data? Which views or reports must exist?
- (C) Freshness: real-time, hourly, daily?
- (C) Source of truth for each metric? Export formats?

### AI / ML features
- (D) What does a *good* output look like? A bad one? Give examples.
- (C) What happens when the model is wrong? Human review, confidence thresholds, fallback?
- (C) Latency and cost-per-request budget?
- (C) Evaluation: how will quality be measured before and after launch?
- (C) What data may and may not be sent to a model provider?

### Mobile / offline / hardware
- (C) Must it work offline? What syncs, and how are conflicts resolved?
- (C) Push notifications? Background tasks? Device permissions (camera, location)?
- (C) Hardware constraints: battery, memory, connectivity, form factor?

### Migration / change to an existing product
- (D) What do current users do today that must keep working?
- (C) Data migration needed? Rollback plan?
- (C) How do we communicate the change to existing users?
