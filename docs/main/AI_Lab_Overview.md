### Concierge Webex AI Agent Overview

The Concierge AI Agent is the first agent on the call. It answers the initial questions and decides when to transfer the caller.

The Concierge AI Agent can handle:

- **Initial questions** — Greet the caller and understand why they need Webex Event Health.
- **Office hours** — Share Cisco Event Pharmacy hours and availability.
- **Cisco Event Pharmacy policies** — Answer policy questions and other general pharmacy questions.
- **Call transfer** — Send the caller to the right specialist agent when the request goes beyond FAQ.

## Story

You are designing the **Concierge AI Agent** for **Webex Event Health**. This is the first agent the caller reaches.

- If the caller wants to **order over-the-counter (OTC) medication**, the Concierge transfers the call to another **Webex AI Agent** that completes the order and schedules delivery.
- If the caller wants to **evaluate symptoms**, the Concierge moves the call to a **third-party AI Agent**. That agent determines whether the caller can try OTC medication or should seek urgent medical assistance and contact a doctor.

You will configure this Concierge agent and connect it to a voice flow. The specialist agents and transfers are completed in **Configure Multi Agentic Flow**.
