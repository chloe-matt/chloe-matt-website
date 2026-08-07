# prompt-pack landing verification report

Date: 2026-07-31  
Verified: https://www.chloematt.eu/prompt-pack/, https://chloematt.eu/prompt-pack/

## Verification results

1. Landing page loads at `chloematt.eu/prompt-pack/`
   - Verified both `https://chloematt.eu/prompt-pack/` and `https://www.chloematt.eu/prompt-pack/`
   - HTTP 200, HTML rendered.

2. Nav link from homepage works
   - Verified homepage content at `https://www.chloematt.eu/` contains `/prompt-pack/`.

3. Waitlist form submits successfully
   - Form present on the prompt-pack page.
   - Clicked submit after entering a test email.
   - The form POSTS to `https://buttondown.email/api/emails/embed-subscribe/chloematt`
     into a hidden iframe; cross-origin iframe response is blocked from this browser session,
     so end-to-end subscribe success cannot be confirmed from here.

4. Buttondown integration
   - Page-level evidence: form action URL is `https://buttondown.email/api/emails/embed-subscribe/chloematt`.
   - Direct empty POST to that URL returns HTTP 403 from Buttondown, which is typical for
     bare unauthenticated embeds; this alone is not sufficient to prove subscribe flow failure
     or success.
   - Integration present, but full flow verification requires Buttondown dashboard confirmation
     or a success-state post-submit observable between the iframe.

## Conclusion

Page deployment is live. For items 3-4, automated verification from this browser session
is blocked by cross-origin iframe behavior; manual confirmation in Buttondown is needed
for a final sign-off.
