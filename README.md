# FindLaw PPC Performance Email Generator

A single-file HTML app that turns a SHAPE performance dashboard screenshot into a clean, client-facing PPC email for law firms. It uses Google’s Gemini models (via Google AI Studio) and includes an internal Strategist Notes section.

- Need help using the app? Watch: https://drive.google.com/file/d/13ZYcTjTUpq5nblmYjPPY0sEcjriEls72/view?usp=sharing
- Need help creating the API key? Watch: https://drive.google.com/file/d/1gz7rXEpBGzgW0zhe5fY30eZY7AVuohyx/view?usp=sharing

## Features

- Single-file, zero build: open `index.html` in a browser or host via GitHub Pages
- AI-powered summary of the uploaded SHAPE screenshot
- Executive Summary (combined totals) and Performance Summary (platform-level)
- LSA-aware output:
  - Hides CPC and Cost per conversion (CPA) for Local Services Ads
  - Renames Conversions to Leads, Conversion Rate to Lead Rate for LSA
- Optional Google Sheets link insertion (clean, single line)
- Insightful Analysis placeholder (left blank for the strategist)
- Internal Strategist Notes (ALL CAPS, in a separate, non-copied box)
- Local persistence: saves API key and Strategist’s Name to your own browser (localStorage)
- Rich “Copy” button (copies formatted HTML; falls back to text only if blocked)

## Live Hosting (GitHub Pages)

1. Create a public GitHub repo (e.g., `findlaw-ppc-report-generator`).
2. Add your HTML file as `index.html` at the repo root.
3. Go to Settings → Pages → “Deploy from a branch”, select your default branch and root (`/`).
4. Wait 1–2 minutes; your site will be live at `https://<your-username>.github.io/<repo-name>/`.

Tip: If you restrict your API key by HTTP referrer, add:
- `https://<your-username>.github.io`
- `https://<your-username>.github.io/<repo-name>/*`

## One-Time Setup

1. Get a Google AI Studio API key:
   - https://aistudio.google.com/app/apikey  
   - This key targets the “Generative Language” (Gemini) endpoints directly.
2. Open the app and paste your API key in Step 1 (“Google AI API Key”).
3. Click “Refresh models” and select a Gemini model (start with `models/gemini-1.5-flash`).

## How to Use (Daily Workflow)

1. Fill in details:
   - Primary Contact (optional), Law Firm Name, Start/End Dates, Strategist’s Name (saved).
2. Upload the SHAPE performance dashboard screenshot.
3. (Optional) Paste your Google Sheets URL (adds a single link line to the email).
4. Click “Generate Email.”
5. Review:
   - Executive Summary (combined totals)
   - Performance Summary (per platform)
     - LSA automatically hides CPC/CPA and shows Leads / Lead Rate
   - Insightful Analysis: left blank for your own text
   - Closing: “Please let me know…” + “Best Regards,” + Strategist’s Name
   - Strategist Notes (yellow box at bottom, not included when copying)
6. Click “Copy” to copy formatted HTML (Gmail/Outlook ready). If your browser blocks rich copy, select all in the box and Ctrl/Cmd+C.

## Data & Privacy

- API key is stored only in your browser (localStorage) on your machine.
- No keys or data are stored on a server by this app.
- The app sends your prompt and uploaded screenshot to Google’s API to generate the content.

## LSA Metric Rules

- For Local Services Ads (LSA):
  - CPC and CPA are omitted (LSA is billed by lead)
  - Conversions relabeled as Leads
  - Conversion Rate relabeled as Lead Rate (if visible in the screenshot)
- Google Ads / Microsoft Ads sections remain unchanged and may include CPC/CPA.

## Troubleshooting

Most model loading issues are config-related. Start here:

1. Verify your API key works:
   - Open in your browser:
     ```
     https://generativelanguage.googleapis.com/v1beta/models?key=YOUR_API_KEY
     ```
   - You should see a JSON list of models (e.g., `models/gemini-1.5-flash`).
   - If you see `403 PERMISSION_DENIED` or “API not enabled”: ensure you’re using an AI Studio key or enable “Vertex AI API” / “Generative Language API” for your Google Cloud project with billing linked.
   - If `refererNotAllowed`: your key has HTTP referrer restrictions—add your GitHub Pages origins (see above) or temporarily remove restrictions to test.

2. Browser/Network:
   - Try Chrome/Edge Incognito with extensions disabled.
   - Corporate VPNs or strict firewalls can block `googleapis.com`; try a different network.

3. “Generate” fails after models load:
   - Ensure you uploaded an image (required).
   - Try a different model (e.g., Flash vs Pro).
   - Open DevTools → Console for precise errors; 429 means quota; 400 may be safety filtering.

4. Google Sites:
   - Not supported for this app (sandbox/CORS prevents API calls). Use GitHub Pages.

## Contributing / Customizing

- You can adjust prompt wording inside `systemPrompt` in `index.html` to change tone/sections.
- The LSA clean-up is reinforced with a small post-processor to ensure CPC/CPA are removed and labels are updated even if the model slips.
- Styling uses Tailwind via CDN for quick brand tweaks (colors, fonts, spacing).

## License

If you keep this repository public, consider adding an MIT License so others can legally use and adapt it.

---

If you need help customizing, filing issues, or publishing to GitHub Pages, open an issue in the repo or reach out.

