# Questionnaire — connecting form delivery

`index.html` in this folder is the multi-step client intake questionnaire, served
at **https://goldenvalleyweb.com/questionnaire/**. It's a static page; submissions
are delivered by **Formspree**.

## One-time wiring (≈3 minutes)

1. Go to <https://formspree.io> and sign up / log in as `hello@goldenvalleyweb.com`.
2. **+ New form** → name it "Website Questionnaire" → send-to `hello@goldenvalleyweb.com`.
3. Copy the form endpoint — it looks like `https://formspree.io/f/abcdwxyz`.
4. In `index.html`, replace **both** occurrences of `YOUR_FORM_ID`:
   - `<form ... action="https://formspree.io/f/YOUR_FORM_ID" ...>`
   - the guard check in the `<script>` (`endpoint.indexOf("YOUR_FORM_ID")`)
   …with your real form id. (Simplest: find-and-replace `YOUR_FORM_ID` → `abcdwxyz`.)
5. Commit + push. Submit the form once yourself — Formspree emails you a one-time
   link to confirm the form is yours. Click it. Done.

## How it behaves

- **Subject line:** `New Website Questionnaire — <Business Name>` (set per submission).
- **Reply-to:** the client's business email, so you can reply straight from the notification.
- **Email body:** one labelled line per answer, grouped and numbered by step
  (`1. BUSINESS — Name`, `2. GOALS — Primary goal`, …). Repeatable sections
  (offerings, liked sites, FAQs, testimonials) come through as readable numbered
  lists, not JSON. Empty fields are omitted.
- **Client sees:** an on-page "Thank you — we received your questionnaire" panel.
- **Spam:** a hidden honeypot field (`_gotcha`) + Formspree's own filtering. You can
  also switch on reCAPTCHA in the Formspree dashboard, but for this AJAX form the
  honeypot + Formspree filtering is enough; reCAPTCHA would need extra code.
- **Autosave:** answers persist in the visitor's browser (`localStorage`), so they
  can leave and come back. Cleared on successful submit.

## Files & uploads

The form does **not** accept file uploads (Formspree free tier). Steps 5, 6, 7 and
12 tell the client we'll send a secure upload link afterward — send them a shared
Drive/Dropbox folder or a service like Formspree's file uploads / WeTransfer during
onboarding.

## Limits

Formspree free = 50 submissions/month. Fine for a 5-client studio. If you outgrow
it, upgrade the plan or swap the endpoint for another provider (Web3Forms, Basin) —
the payload is a plain JSON POST, so only the `action` URL changes.

## Client confirmation email

Not enabled (Formspree autoresponse is a paid feature). The on-page thank-you panel
covers the confirmation. Enable "Autoresponse" on a paid Formspree plan if you want
the client to get an email too.
