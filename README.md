# MSL AI secure Worker setup

This is a small server-side proxy. The Gemini API key belongs in Cloudflare Worker secrets, **never in app.js, index.html, GitHub Pages, or a public repository**.

## 1. Create a Gemini API key
1. Open Google AI Studio: https://aistudio.google.com/app/apikey
2. Create an API key. Review the provider's current pricing, quotas, and terms before use; free quota can change.

## 2. Deploy the Worker
1. Sign in to Cloudflare and open Workers & Pages.
2. Create a Worker, then paste the contents of `worker.js` into its editor and deploy.
3. In the Worker settings, add these **secrets** (not plain-text variables):
   - `GEMINI_API_KEY` = your Gemini API key
   - `AI_ACCESS_CODE` = a long code you choose and keep private
4. Add this plain-text variable:
   - `ALLOWED_ORIGIN` = exact origin of your published journal, for example `https://YOUR-USERNAME.github.io` (no path or trailing slash). For a custom domain, use its exact origin instead.
5. Save and redeploy if requested. Copy the Worker URL, such as `https://your-worker.your-subdomain.workers.dev`.

## 3. Connect from the journal
1. Open MSL Journal V10 AI Edition on its published HTTPS address.
2. Open MSL AI and submit a question. When prompted, enter the Worker URL, then the `AI_ACCESS_CODE` you configured.
3. The URL and access code are stored only in this browser's local storage. Do not share them. If you suspect the code leaked, change the Worker secret.

## Security and privacy
- This Worker checks the exact browser origin and access code, but CORS is not authentication and a shared access code can be copied by anyone who can inspect a configured browser. For a public deployment, add Cloudflare rate limiting and stronger authentication before sharing the site widely.
- The app sends the latest 150 trade records, playbook, custom field names, and a short conversation history to the AI provider when you ask a question. Screenshot images are not sent. Do not put passwords, account credentials, or sensitive personal details in notes.
- AI calls require internet and may incur charges or hit provider quotas. Review current pricing/terms. Never store your provider API key in the app or repository.


## V15 frontend note
The V15 AI Studio uses the same secure Worker request contract as the V10.1 AI edition. Keep the Gemini API key and AI access code in Cloudflare Worker secrets; never put the Gemini key in frontend files.
