# Media for tedt.org

Public static media is delivered by GitHub Pages at https://media.tedt.org/.

Files belong under `public/files/SHA256.extension`. Client uploads are limited to 5 MiB; Git-added files to 50 MiB; the complete artifact to 750 MiB. The manifest records URLs, MIME types, sizes and checksums. Immutable filenames must match actual bytes. Git LFS and Releases are not used.

The workflow validates the entire public tree and regenerates its manifest. Pending uploads are private until a public entry references them. It only acknowledges an upload after the deployed bytes match its checksum. Empty polling runs do not redeploy the site.

`scripts/publish.py` is copied from `TedTschopp/tedt.org/_code/micropub_publish.py`; update the source and its checked-in template together. The media-only publisher credential cannot read draft entry source. Its repository-scoped GITHUB_TOKEN cannot modify the main website repository. Keep private queue payloads outside the checkout and all public artifacts.

Set `INDIEWEB_MEDIA_SYNC_ENABLED=true` only after the Micropub service and main rendering code are deployed. See the main repository's `docs/indieweb-publishing.md` for account setup, release and rollback.

## Shared Visitor Analytics

Published HTML uses the deferred TedT.org analytics v1 runtime for GA4, Microsoft Clarity, and Cloudflare Web Analytics. Authentication/payment operations, API responses, and independent downloads are excluded. Run `python3 scripts/site_analytics.py public --mode standard --check` on the final publication directory. Configuration and the integration contract are maintained at https://github.com/TedTschopp/tedt.org/blob/main/docs/analytics.md.
