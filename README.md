# FindLaw PPC Performance Email Generator

A self-contained HTML tool that generates professional, client-facing PPC performance emails. It uses AI to analyze a SHAPE dashboard screenshot and provides a clear, data-driven report suitable for law firm clients.

This tool is designed for PPC strategists to quickly create high-quality reports, complete with performance summaries, insightful analysis, and internal notes for tactical review.

 <!-- Optional: Replace with a URL to a screenshot of the tool -->

## Features

- **Single File, Zero Installation:** Runs entirely in a modern browser from a single HTML file. No server or build process required.
- **AI-Powered Analysis:** Leverages Google's Gemini models to analyze performance data from a SHAPE dashboard screenshot.
- **Dynamic Model Selection:** Automatically detects and lists compatible AI models available to your API key.
- **Client-Focused Output:** Generates a professional email in clean HTML, ready to be copied into any email client.
- **Internal Strategist Notes:** Provides a separate, ALL-CAPS section with tactical recommendations for the strategist, which is safely excluded from the main "Copy" action.
- **Data-Driven Summaries:** Includes:
  - **Executive Summary:** High-level, combined totals for all campaigns.
  - **Performance Summary:** A detailed breakdown of metrics (Spend, Impressions, Clicks, etc.) for each advertising platform.
- **Data Persistence:** Remembers your API key and Strategist's Name in your browser's local storage for convenience.

## How to Use

### One-Time Setup (60 seconds)

1.  **Download the HTML File:** Download the `FindLaw_PPC_Performance_Email_Generator.html` file from this repository.
2.  **Get a Google AI API Key:**
    *   Visit [Google AI Studio](https://aistudio.google.com/app/apikey) and create a new, free API key.
    *   Ensure your Google Cloud project has the "Generative Language API" or "Vertex AI API" enabled and is associated with a billing account (the free tier is very generous and typically sufficient for this tool).
3.  **Open the Tool & Add Key:**
    *   Double-click the downloaded HTML file to open it in your browser (Chrome is recommended).
    *   Paste your API key into the "Google AI API Key" field.
    *   Enter your name in the "Strategist's Name" field. Both will be saved in your browser for future use.
4.  **Load AI Models:**
    *   Click the **"Refresh models"** button. The "Model" dropdown should populate with available models. `gemini-1.5-flash` is a good starting point.

### Generating a Report (Daily Workflow)

1.  **Step 1: Fill in Details:**
    *   Enter the "Primary Contact Name" (e.g., "Jim") and the full "Law Firm Name."
    *   Select the report's start and end dates.
2.  **Step 2: Upload Screenshot:**
    *   Drag and drop (or click to upload) a screenshot of the client's SHAPE performance dashboard.
3.  **Step 3: Add Context (Optional):**
    *   If you have a Google Sheet with detailed contact data, paste its shareable link into the "Google Sheets URL" field. This will add a clickable link to the final email.
    *   Paste the raw contact data into the large text box to give the AI more context for its analysis.
4.  **Step 4: Generate & Copy:**
    *   Click the **"Generate Email"** button.
    *   Review the generated client email in the main output box.
    *   Review your internal-only notes in the yellow box below (these are not copied).
    *   Click the **"Copy"** button and paste the rich HTML into your email client (Gmail, Outlook, etc.).

## Troubleshooting

-   **"No compatible models found":** This usually means the Google Cloud project associated with your API key needs the **Vertex AI API** enabled.
-   **"Model not found" Error:** Try selecting a different model from the dropdown (e.g., `gemini-1.5-pro`).
-   **No Output / Empty Response:** The AI may have filtered the response. Try again, or simplify the input by removing the pasted contact data.
-   **Formatting Issues After Pasting:** Ensure you are pasting into your email client as rich text (not plain text) to preserve bolding and lists.

## For Developers

This tool is built with vanilla HTML, JavaScript, and Tailwind CSS (via CDN). All logic is self-contained in the HTML file for maximum portability. The AI interaction is handled via direct `fetch` calls to the Google Generative Language API.
