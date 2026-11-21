# ZAMIN TEMP MAIL

A one-page responsive temporary mail UI with a small Vercel serverless API proxy.

## Files
- `index.html` — complete UI, CSS and browser JavaScript.
- `api/mail.js` — Vercel Function that calls GrabMail.
- `vercel.json` — Vercel project config.

## Deploy free with GitHub + Vercel
1. Create a new GitHub repository (for example `zamin-temp-mail`).
2. Upload `index.html`, the `api` folder and `vercel.json` to the repository root.
3. Sign in to Vercel and choose **Add New → Project**.
4. Import the GitHub repository.
5. Keep the framework preset as **Other**. No build command or output directory is required.
6. Deploy. Vercel serves `index.html` and the `/api/mail` serverless function automatically.
7. Open the deployed URL and press **Generate email**.

## API notes
- This project uses GrabMail's public `@grabmail.io` domain and does not need an API key.
- Addresses are generated client-side; GrabMail does not have a mailbox-create endpoint.
- Inbox: `GET /api/mail?action=inbox&address=...`
- Read: `GET /api/mail?action=read&address=...&id=...`
- Delete: `DELETE /api/mail?action=delete&address=...&id=...`
- The browser only displays the plain-text body, avoiding unsafe rendering of incoming HTML.
- GrabMail public inboxes are not private. Anyone who knows an address may be able to read it. Do not use for sensitive accounts.
- Provider limits and retention can change; check https://grabmail.io/docs/api.

## Troubleshooting
- If `/api/mail` returns 404, confirm the `api` folder is at the repository root and redeploy.
- If Vercel reports a function/runtime error, check the deployment's Function Logs.
- Some websites block disposable email domains; that is a sender policy, not a website bug.
- GrabMail documents a free API limit of 60 requests/minute and 1,000 requests/day per IP. Avoid rapid repeated refreshes.
