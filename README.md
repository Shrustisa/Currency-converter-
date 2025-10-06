Currency Converter

 Overview

This is a simple, standalone web application for converting currencies in real-time. It features a clean, responsive user interface built with HTML, CSS, and vanilla JavaScript. The app fetches a list of world currencies and exchange rates from the free [Frankfurter API](https://www.frankfurter.app/docs), allowing users to convert amounts between any two supported currencies (e.g., default: USD to INR).

The design uses a modern gradient background, blur effects, and mobile-friendly layouts. It includes input validation, error handling, and basic caching to optimize API usage.

Features

- Dynamic Currency Selection: Automatically loads and populates dropdowns with over 170 world currencies (e.g., USD - United States Dollar).
- Real-Time Conversion: Converts user-entered amounts using live exchange rates.
- Caching: Stores fetched rates in memory (per browser session) to avoid redundant API calls.
- Input Validation: Checks for valid amounts (>0) and handles same-currency selections.
- Error Handling: Displays user-friendly messages for API failures, invalid inputs, or network issues.
- Last Updated Info: Shows the date of the latest exchange rate used.
- Responsive Design: Works seamlessly on desktop, tablet, and mobile devices (uses media queries for smaller screens).
- No Dependencies: Pure frontend—no build tools, servers, or external libraries required.

Demo

- Open `index.html` in any modern web browser (Chrome, Firefox, Safari, etc.).
- The app requires an internet connection to fetch data from the API.

How to Use

1. Run the App:
   - Save the provided code as `index.html`.
   - Double-click the file to open it in your default browser, or serve it via a local server (e.g., using Python's `python -m http.server` or VS Code's Live Server extension).

2. Convert Currency:
   - Enter an amount in the input field (e.g., `1`).
   - Select the source ("From") and target ("To") currencies from the dropdowns.
   - Click the "Convert" button.
   - View the result below (e.g., "1 USD = 83.50 INR").
   - If needed, the app will show errors or the last update date.

3. Example:
   - Amount: 100
   - From: EUR
   - To: GBP
   - Result: "100 EUR = 84.25 GBP" (rates vary in real-time).

Technologies & Styling

- HTML5: Structure for inputs, selects, and dynamic content.
- CSS3: 
  - Flexbox for centering and layout.
  - Linear gradients, backdrop-filter (blur), and box-shadows for a glassmorphism effect.
  - Animations (hover scale) and responsive media queries.
  - Google Fonts: Poppins (loaded implicitly via font-family; ensure connectivity or host locally).
- JavaScript (ES6+):
  - Async/await for API fetches.
  - DOM manipulation for populating options and updating UI.
  - Local caching with a simple object to store rates.
- API: Frankfurter (https://api.frankfurter.app)
  - `/currencies`: Lists currency codes and names.
  - `/latest?from={from}&to={to}`: Provides exchange rates (base: from currency).

No external JS libraries (e.g., no jQuery or Axios) are used—keeping it lightweight (~5KB total).

API Details

- Endpoints Used:
  - `GET https://api.frankfurter.app/currencies`: Returns JSON like `{"USD":"United States Dollar", "EUR":"Euro", ...}`.
  - `GET https://api.frankfurter.app/latest?from=USD&to=EUR`: Returns JSON like `{"base":"USD", "rates":{"EUR":0.92}, "date":"2023-10-01"}`.
- Rate Limits: Frankfurter is free for non-commercial use but has undocumented limits. For high-traffic apps, consider alternatives like ExchangeRate-API or a paid service.
- Accuracy: Rates are updated daily (weekdays) and based on ECB (European Central Bank) data. Not for financial advice—always verify with official sources.
- CORS: The API supports browser CORS, so no proxy needed.

Setup & Development

Quick Start
- No installation required! Just open `index.html`.
- For development:
  1. Clone or copy the file.
  2. Edit in a code editor (e.g., VS Code).
  3. Test API calls in browser dev tools (Network tab).

Customization
- Add Currencies: The app auto-loads all from the API; filter if needed in `loadCurrencies()`.
- Styling: Modify CSS in the `<style>` tag (e.g., change gradient colors).
- Caching: Extend `cache` with timestamps for expiration (e.g., clear after 24h).
- Offline Mode: Add service workers for PWA support (not included).
- Fonts: If Poppins fails to load, fallback to system fonts like `-apple-system, BlinkMacSystemFont, sans-serif`.

Potential Improvements
- Add reverse conversion button.
- Support multiple "To" currencies.
- Integrate a more robust API (e.g., with historical rates).
- Add unit tests for conversion logic.
- Deploy to GitHub Pages or Netlify for hosting.

Limitations

- No Persistent Storage: Cache resets on page refresh; rates may not be the absolute latest.
- API Dependency: Offline use is limited (currencies load once, but conversions fail without net).
- Precision: Rounds to 2 decimal places; for crypto or high-precision needs, use a different API.
- Browser Support: Modern browsers only (ES6 features like `async/await`).
- Security: Client-side only—no sensitive data handled, but avoid in production without HTTPS.
