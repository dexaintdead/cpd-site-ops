# JCC Site Ops

Field app for JCC Management at 2 Park Avenue: drawings and markups, punch, RFIs, submittals, daily logs, change orders and building ops. Served at https://dexaintdead.github.io/cpd-site-ops/ until the custom domain site.contentpad.io is pointed here (then add a CNAME file).

- One static page (`index.html`). It holds no keys. Every read and write goes through the ContentPad API (`cpd-api`, routes `/site/*`, source `site.js` in dexaintdead/cpd-api).
- Logins are email plus a 6-digit PIN that is emailed by the API. They are not ContentPad memberships.
- Data lives in `site_users`, `site_items` and `site_item_events` (worker-only, RLS service_role). Files are in a private R2 prefix.
- Local testing: when the page runs on `127.0.0.1` it calls `http://127.0.0.1:8787`.
