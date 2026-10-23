# 2 Park Site Ops

Field app for JCC Management at 2 Park Avenue: drawings and markups, punch, RFIs, submittals, daily logs, change orders and building ops. Served at https://2park.contentpad.io (CNAME file). Managed from the ContentPad dashboard: app.contentpad.io/site-ops.html (repo cpd-dashboard).

- One static page (`index.html`). It holds no keys. Every read and write goes through the ContentPad API (`cpd-api`, routes `/site/*`, source `site.js` in dexaintdead/cpd-api).
- Logins are email plus a 6-digit PIN that is emailed by the API. They are not ContentPad memberships.
- Data lives in `site_users`, `site_items` and `site_item_events` (worker-only, RLS service_role). Files are in a private R2 prefix.
- Local testing: when the page runs on `127.0.0.1` it calls `http://127.0.0.1:8787`.

- `index.html` is generated: `build_live.py` (demo → live API) plus `theme_2park.py` (the 2 Park Avenue skin). Source copies live in the ContentPad project under claude/site-ops/.
