# CardCapture AI — Vercel deployment

This repository layout is prepared for Vercel. The web app is `index.html` and the AI endpoint is `api/extract.js`.

## Deploy
1. Upload the files/folders in this ZIP to the root of your GitHub repository:
   - `index.html`
   - `api/extract.js`
   - `package.json`
   - `README.md`
2. Import or redeploy that GitHub repository in Vercel.
3. In Vercel: **Project → Settings → Environment Variables**, add:
   - Name: `OPENAI_API_KEY`
   - Value: your secret OpenAI API key
   - Environments: Production (and Preview if you want to test preview deployments)
4. Optional environment variable: `OPENAI_MODEL` = `gpt-4.1-mini`
5. Redeploy after adding the environment variable.
6. Open your deployed HTTPS URL on your phone. Take a front photo and optional back photo, then tap **Extract with AI**.

## Notes
- Keep the API key in Vercel environment variables. Never place it in `index.html` or commit it to GitHub.
- This uses the OpenAI Responses API with image input and strict JSON-schema output.
- Images are resized/compressed in the browser (1200px, JPEG quality 0.68) before upload to reduce the chance of exceeding Vercel serverless request-body limits.
- Contact records remain in local browser storage; they do not automatically sync between phone and laptop. Export CSV/JSON backups.
- AI extraction sends card images to OpenAI through your Vercel function. Use only if permitted by your privacy requirements.
- Verify extracted names, phone numbers, email addresses and domains against the original card. No OCR system guarantees perfect accuracy.
