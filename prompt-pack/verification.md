# prompt-pack landing verification report

Date: 2026-07-31
Verified as part of kanban task t_c6ed3567

## Verification results

### 1. `chloematt.eu/prompt-pack/` loads fully
- `https://chloematt.eu/prompt-pack/` → HTTP 200, HTML rendered.
- `https://www.chloematt.eu/prompt-pack/` → HTTP 200, same content.
- Curl `-L` returned full HTML with heading and waitlist form; no asset URLs evident in the page markup.
- Browser console on live page: no messages, no JS errors.
- Result: PASS.

### 2. Homepage nav link to `/prompt-pack/`
- Homepage source contains nav link `Prompt Pack waitlist` with href `/prompt-pack/`.
- Browser confirmed link is present and leads directly to the prompt-pack page.
- Result: PASS.

### 3. Waitlist form can be filled and submitted with no visible error
- Page shows an email textbox and submit button `Join waitlist — $29 at launch`.
- Form action: `https://buttondown.email/api/emails/embed-subscribe/chloematt` with `target="hidden-iframe"`.
- Filled the email field with a valid test address and submitted; the page did not display any inline error message after submit.
- Result: PASS from the UI path perspective.

### 4. Buttondown integration
|- **Slug on page:** source `public/prompt-pack/index.html:304` and the live page both use
  `https://buttondown.email/api/emails/embed-subscribe/chloematt` (slug `chloematt`, correct spelling). Wiring is correct.
|- **Live response (2026-08-04):**
  - `GET` to `…/chloematt` → HTTP 302 (redirect `buttondown.email` → `buttondown.com`), followed to a Buttondown-styled **404 Error** page.
  - `POST` to the same endpoint → HTTP 403, body `error code: 1010` (Cloudflare WAF blocking unauthenticated programmatic traffic).
|- **Interpretation:** the endpoint is live and responding (not a DNS/dead-link 404), but the
  `GET` 404 + `POST` 403 mean programmatic confirmation of list delivery is not possible from this
  environment. The cross-origin hidden-iframe submit returns no readable feedback, so a real
  browser submission also gives no visible success/error signal.
|- **Result: PARTIAL** — slug is correctly wired on the page; end-to-end subscription capture
  requires manual confirmation via the Buttondown dashboard (subscriber count) or a live browser
  Network tab inspection. Needs Buttondown account access (held by Asep — not in repo).

## Overall verdict

Status: PARTIAL PASS

Conclusion: The prompt-pack landing page is live (chloematt.eu/prompt-pack/ → HTTP 200),
navigable from the homepage, and the waitlist form is correctly wired to the `chloematt`
Buttondown slug with no visible client-side errors. Checks 1–3 PASS. Check 4 (Buttondown
delivery) is documented but unverified end-to-end: the endpoint responds but GET→404 and
POST→403 (WAF) prevent programmatic proof, and the cross-origin iframe hides the submit result.
Final production sign-off on the waitlist requires Buttondown dashboard confirmation by the
account holder.
