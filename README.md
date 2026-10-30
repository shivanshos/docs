# ShivanshOS public documentation

Canonical Mintlify source for the planned **docs.shivanshsethi.in** site.

This repository preserves pre-existing legacy pages while adding a navigable public identity and resource register. It does not host private account details, cloud credentials, the portfolio homepage, or AIO3 documentation.

## Production deployment

1. Connect `shivanshos/docs` (branch `main`, content root `/`) to a **new Mintlify deployment**.
2. In that project's Mintlify dashboard, set custom domain `docs.shivanshsethi.in`.
3. Apply Mintlify's returned domain verification and DNS records via your DNS provider; do not guess the DNS target.
4. Make sure the new deployment is public and search-indexable; do not modify the existing `docs.aio3.ai` deployment.
5. Check public page routes, generated `/sitemap.xml`, `/robots.txt`, canonical URLs and certificate.
6. Add the domain property in Google Search Console, submit its sitemap and validate structured data on separately deployed profile pages.

## Source fidelity

All external URLs are human-readable references, not XML `<loc>` entries for this host. Proof status is shown per item. Any planned, inaccessible or unverified link is clearly marked, not silently considered active.

## Navigation

`docs.json` defines public navigation. Keep Archive items to preserve legacy paths. Add badges or videos only after verifying original issuers, authorship and licenses.

## Development

Use the Mintlify CLI with `mint dev`, `mint validate` and `mint broken-links` where available.
