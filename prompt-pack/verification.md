# prompt-pack landing verification report

Date: 2026-07-31
Verified as part of kanban task t_c6ed3567

## Verification results

### 1. `chloematt.eu/prompt-pack/` loads fully
- `https://chloematt.eu/prompt-pack/` → HTTP 200, HTML rendered.
- `https://www.chloematt.eu/prompt-pack/` → HTTP 200, same content.
- Curl check returned full HTML with heading and waitlist form; no asset URLs evident in the page markup that are obviously broken from the source.
- Browser console on live page: no messages, no JS errors.
- Result: PASS.

### 2. Homepage nav link to `/prompt-pack/`
- Homepage source contains nav link `Prompt Pack waitlist` with href `/prompt-pack/`.
- Browser confirmed link is present and leads directly to the prompt-pack page.
- Result: PASS.

### 3. Waitlist form can be filled and submitted with no visible error
- Page shows an email textbox and submit button `Join waitlist — $29 at launch`.
- Form action is `https://buttondown.email/api/emails/embed-subscribe/chloematt` submitted into `target="hidden-iframe"`.
- Filled the email field with a valid test address and submitted; the page did not display any inline error message after submit.
- Result: PASS from the UI path perspective.

### 4. Buttondown integration
- Wiring present: hidden iframe targets the Buttondown embed-subscribe endpoint.
- Cross-origin iframe response after real form submission cannot be inspected from this browser session, so subscribe success/failure and list-ID correctness cannot be confirmed end-to-end here.
- Empty POST to the endpoint returns 403, which is consistent with Buttondown’s unauthenticated embed behavior and does not prove integration failure.
- Result: PARTIAL — needs manual confirmation via the Buttondown dashboard or a live browser network submission observation.

## Overall verdict

Status: PARTIAL PASS

Conclusion: The prompt-pack landing page is live, navigable from the homepage, and the waitlist form submits without visible errors. Final sign-off on Buttondown list delivery still requires manual dashboard confirmation.
