# AI booking assistant for dive centres

Interactive mock-up of a WhatsApp and web assistant for dive and water-sports centres. Open `index.html` in a browser: no server, no keys, made-up data.

Interface in English and Spanish (selector at the top; English by default, `?lang=es` opens it in Spanish).

**[▶ Try the demo](https://miguelpalaciosgg.github.io/asistente-reservas-ia/)**

## What it shows
Four scripted conversations on a phone and, next to it, an **Under the hood** panel with what the assistant looks up before answering:

| Conversation | What you see |
|---|---|
| Try dive · new customer | Price from the catalogue, free places on Saturday, pre-filled booking link and a booking paid with Bizum |
| Returning customer | Per-customer memory: it knows her certification, her dives and that she prefers mornings |
| In Spanish / In English | Replies in the customer's language and the link opens the booking page in that language |
| Hand over to a person | Medical question: the assistant doesn't answer it, alerts the centre and an instructor takes over |

## How it is designed
- **Live catalogue with tool use**: prices are not pasted into the prompt; the model calls tools (`catalog`, `slots`, `quote`) that read the booking engine's public API. If a price changes or a trip fills up, the assistant knows.
- **Per-customer memory**: on WhatsApp by phone number (provided by Meta's API); on the website, by cookie. One summary per conversation and scheduled deletion (GDPR).
- **Leads to the booking**: it never takes payment in the chat; it sends the booking widget link with activity, day, time and party size filled in, and payment goes through the centre's own gateway (card or Bizum). The booking is tagged with source "Assistant".
- **Hand-over to a person**: a `handoff_to_human(reason)` tool for health questions, complaints, large groups or when the customer asks; the bot goes quiet and the team carries on from their dashboard.
- **Cost**: with a small model (Claude Haiku), a fraction of a cent per conversation.

## History
The first version (2025) was a web chatbot in Node.js with Gemini and Firestore, with per-customer conversation memory and the centre's information in a JSON file. This mock-up is the redesign: live catalogue instead of hand-copied data, WhatsApp, hand-over to a person and booking tracking.

---
The centre, prices, names and links in the demo are fictitious.
