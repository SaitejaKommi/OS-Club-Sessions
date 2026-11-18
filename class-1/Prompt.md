Build a single-page web app called "Internet Inspector".

Rules:
- Browser only. No backend, no API keys, no login, no libraries.
- Use plain fetch() and performance.now() to measure time in ms.
- Simple, clean light UI with large readable text. Four cards, one under another.
- Wrap every request in try/catch. On failure show a short friendly error, not a crash.
- Use simple English for all labels and messages.

Card 1: My IP
- Button: "Find my IP".
- GET https://api.ipify.org?format=json
- Show: my public IP, my browser User-Agent (navigator.userAgent), time taken in ms.

Card 2: DNS lookup
- Text input (default: example.com) and a button "Look up".
- GET https://dns.google/resolve?name=<domain>&type=A
- Show: NOERROR if Status is 0, NXDOMAIN if Status is 3.
- Show: every IP from Answer[].data, the TTL, and time taken in ms.
- If there is no answer, show "No IP found for this name".

Card 3: HTTP request
- Three buttons: "200", "404", "500".
- GET https://httpbin.org/status/<code>
- Do NOT treat 404 or 500 as an error. Read response.status.
- Show: status code, a plain-English meaning, time in ms, and the first 200 characters of the body.
  200 = success; 404 = you asked for something that does not exist; 500 = the server had an error.

Card 4: Request log
- A table with columns: #, time, what, URL, result, ms.
- Every request from cards 1-3 adds one row. Newest at the bottom.
- A "Clear" button.

Under each card add one line called "What just happened" in simple English.
Example: "Your browser (the client) asked ipify's server: what is my public IP?"