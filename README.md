# User Guide

## Installation

1. Clone the repository and install dependencies:
   ```bash
   git clone <repository>
   cd seo-analysis
   npm install
   ```
2. Run the development build:
   ```bash
   npm run dev
   ```
3. In Chrome, open `chrome://extensions`, enable **Developer mode**, click **Load unpacked**, and select the `dist` folder created by the dev server.

## Running an Analysis

1. Navigate to the webpage you want to audit.
2. Open the extension popup and optionally set a focus keyword.
3. Click **Analyze Page**. The dashboard renders prioritized issues, AI summary (when configured), and recommendations.
4. Use **Copy Summary** or **Export JSON** to share results.

## Settings & Privacy

- Open the options page to configure auto-run, theme, default export behaviour, and telemetry verbosity.
- Telemetry data stays local; adjust verbosity in settings. Review logs by reading `telemetryEvents` from `chrome.storage.local`.

## Troubleshooting

| Scenario | Action |
| --- | --- |
| Popup shows "Analysis already running" | Wait for the current run to finish before re-triggering. |
| Popup shows "Could not inject analyzer into the page" | Open a standard HTTP/HTTPS tab (no chrome:// pages), click the extension puzzle icon → Manage extension, grant site access (and “Allow access to file URLs” if needed), then refresh the page and retry. |
| Report fetch failed | Run analysis again or check telemetry logs. |
| "Unexpected error" | Refresh the page and retry; review options to ensure permissions are granted. |

If the injection error persists:
- Keep the page you want to audit active and open the popup again; Chrome only grants temporary access to the active tab.
- Visit `chrome://extensions`, toggle **Developer mode**, click the **Service worker** link for this extension, and re-run the analysis. Any runtime errors displayed there will point to missing permissions or disallowed URLs (e.g., Chrome Web Store pages). Adjust site access accordingly and reload the page before trying again.

For detailed documentation, see the README references and analyzer-specific docs.
