# MSL Trading Journal V15 AI Edition setup

## Publish the journal
1. Extract the ZIP.
2. Upload the files and folders inside it to the root of your existing GitHub Pages repository (not the ZIP itself and not an extra nested folder).
3. Commit the changes. Keep `ai-worker/` and `assets/` folders.
4. Open the site and refresh it. Download a backup regularly.
5. Add the HTTPS website to your Android home screen from the browser menu for an app-like PWA shortcut.

## Connect the AI
1. Follow `ai-worker/README.md` to create a Gemini API key and deploy `ai-worker/worker.js` as a Cloudflare Worker.
2. Configure Worker secrets `GEMINI_API_KEY` and `AI_ACCESS_CODE`, and the `ALLOWED_ORIGIN` variable to your exact GitHub Pages origin (origin only; no path).
3. Open the published journal, choose **MSL AI**, submit a question, and enter the Worker URL and private access code when prompted. Ask the question again after saving the connection. If you see “Origin not allowed”, set `ALLOWED_ORIGIN` to exactly `https://abiodunonifade37-cmd.github.io` (no `/MSL-TRADING-JOURNAL-V/` path and no trailing slash), then deploy the Worker again.
4. Use **full-screen AI workspace** in the MSL AI header to open the focused AI workspace. Press **Esc** or tap **Exit full screen** to return.
4. Never put the Gemini key in GitHub or into the journal app.

## Important
- This is a local-first app: trades remain in the browser on the current device. Back up regularly.
- Supabase-only trades do not migrate automatically.
- Real AI requires internet and provider quotas may change or incur charges.
- AI is a review assistant, not a signal service or a guarantee of profitability.
