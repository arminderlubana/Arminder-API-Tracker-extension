# Arminder-API-Tracker-extension
Chrome Manifest V3 extension
I created a ready-to-install Chrome Manifest V3 extension. It activates only for the configured website, records API timing details, and exports the results as JSON to Chrome’s Downloads folder.

**Installation**
Extract the downloaded ZIP file.
Open chrome://extensions in Chrome.
Enable Developer mode.
Click Load unpacked.
Select the extracted arminder-api-tracker folder.
Open the extension and select Settings.
Configure:
Website URL, for example: https://your-website.com

  **API patterns, for example:**
  /api/
  /graphql
  /odata/

**Information captured**
Request URL
HTTP method
Resource type
Request start date and time
Response completion date and time
Time to first response headers
Total request duration in milliseconds
HTTP status code and status text
Request and response headers
Request form data or body metadata
Cache status
Server IP address, when Chrome provides it
Network error details
Initiating website

Sensitive values in Authorization, Cookie, Set-Cookie, and similar headers are automatically redacted.

The extension uses Chrome’s webRequest API to observe request lifecycle events. Manifest V3 still supports this API for observing and analyzing network traffic, although blocking behavior is restricted.

**JSON download behavior**

Files are created with names similar to:
  arminder+2026-09-04T06-15-30-123Z.json

The extension exports automatically when:

You navigate away from the configured website.
You close the tracked website tab.

You can also click Export JSON from the extension popup at any time.

**Important timing clarification**

The totalDurationMs value represents the browser-observed, end-to-end request duration. It includes browser processing, connection and network time, server processing, downloading, and related overhead. It is not the server’s internal execution time alone.

Chrome’s webRequest API does not expose response bodies, so the extension captures response headers, status, completion time, and timing information, but not response content.
