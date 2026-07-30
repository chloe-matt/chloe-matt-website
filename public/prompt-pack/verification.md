# Prompt Pack landing page verification

Date: 2026-07-30

## Verified

- Homepage loads at `https://chloematt.eu/` and `https://www.chloematt.eu/`: OK
- Nav link to prompt-pack exists: `/prompt-pack/` is present in the homepage navigation.
- Local file exists: `products/chloe-matt-website/prompt-pack/index.html`.

## Failures / blockers at chloematt.eu

1. `https://chloematt.eu/prompt-pack/` returns 404
2. `https://www.chloematt.eu/prompt-pack/` returns 404

Conclusion: the `chloematt.eu/prompt-pack/` landing page is **not live**.

## Waitlist / Buttondown

Form action configured:
`https://buttondown.email/api/emails/embed-subscribe/chloematt`

Live POST to this endpoint returns HTTP 404 from Buttondown.

Conclusion: the waitlist form **does not submit successfully** and Buttondown integration is not working with the current list identifier/URL.

## Likely causes

- The site repository may not be publishing subdirectories, or the hosting setup does not serve `/prompt-pack/`.
- The Buttondown action URL may use the wrong list/subscriber-list identifier.
- The nav link may need to match the actual deployed path.

## Next steps needed

- Confirm the correct deploy path for the prompt-pack page.
- Confirm the correct Buttondown embed action/list identifier.
- Redeploy or rewire, then rerun this verification.
