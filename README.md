# ApplianceSource

Independent specialist knowledge site in the PENG Nexus network. **Work computer** development only.

## Status
V0.1 educational reference prototype on a draft PR. Not a verified supplier directory, online shop or RFQ service. Noindex until verified publication.

## Content
- 6 educational product references, 3 topic summaries, 3 buying checklists.
- In-browser keyword search and category filtering.
- No manufacturer names, pricing, stock, certification or buyer information collected.

## Template maintenance
`site.json` is the source of truth for industry content. Regenerate using `peng-nexus` V0.1:
```powershell
cd D:\AgentForge\peng-nexus
node scripts/build.mjs --config ..\appliance-source\site.json --out ..\appliance-source\public
```
The generated `public/` files are committed in this standalone repository. No runtime dependence on PENG Nexus.

## Cloudflare Workers Static Assets (preview first)
- Repository: `auturock067-spec/appliance-source`
- Worker name: `appliance-source` (must match Cloudflare's existing project)
- The `wrangler.jsonc` file configures `assets.directory` as `./public`.
- Production branch: `main` (README only until PR approval/merge)
- Build command: leave empty; deploy command: `npx wrangler deploy`.
- Enable **Preview Builds** for feature branches; preview command: `npx wrangler preview`.
- Inspect the Worker Preview created from `feat/v0-1-site-foundation`. Only after acceptance, merge the PR to `main` for automatic production deployment.
- No API secrets needed in V0.1. Do not remove noindex or enable personal data collection without review.

## Preview acceptance workflow
- Worker Previews requires Wrangler 4.135.0 or newer and the committed `previews` configuration.
- Keep Production branch `main`. Preview Builds must use an empty build command and `npx wrangler preview`; do not check out another branch in the build command.
- After a feature-branch push, compare the Cloudflare build commit with the Draft PR head and open the exact HTTPS link shown by Cloudflare. Preview names may receive a suffix; do not infer the URL.
- Verify successful CI, HTML/CSS/JS loading, search/filter and zero results, 320/390/768/1440px layouts, disclaimers, `noindex,nofollow` and `robots.txt` before accepting the preview.
- Production publication and removal of noindex require owner approval.
