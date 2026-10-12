# CardCapture AI — setup

This build adds front/back capture and an optional vision-model extraction step. The API key is kept on the server, not in browser code.

## Requirements
- Node.js 18 or newer
- An OpenAI API key with API billing enabled

## Run locally
1. Put `index.html` and `server.js` in the same folder.
2. Open a terminal in that folder.
3. Set your API key as an environment variable (do not paste it into the HTML or commit it to source control).

### Windows PowerShell
```powershell
$env:OPENAI_API_KEY="YOUR_API_KEY"
$env:OPENAI_MODEL="gpt-4.1-mini"
node server.js
```

### macOS / Linux
```bash
export OPENAI_API_KEY="YOUR_API_KEY"
export OPENAI_MODEL="gpt-4.1-mini"
node server.js
```

4. Open `http://localhost:8080`. For use on your phone, deploy this server to a private HTTPS host and open its URL on the phone. For local-network testing, the phone and computer must be on the same Wi-Fi; use the computer's LAN IP and allow the port through the firewall.
5. Click **Extract with AI**. The app sends both card images to your backend, which calls the OpenAI Responses API and returns structured fields. Review the fields before saving.

## Privacy and accuracy
- AI extraction requires internet access and sends card images to the model provider through your backend. Do not scan sensitive cards unless your organization's policies permit it.
- The model can still misread small, blurry, reflective, or stylized text. Always verify phone numbers, email addresses, and names against the original card.
- Local OCR remains available as a fallback. CSV export and local browser storage continue to work.
- API usage may incur charges. Never put `OPENAI_API_KEY` in client-side HTML or a public repository.
