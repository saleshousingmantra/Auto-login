# Auto-login

A single-page login form that autofills saved credentials and signs in automatically.

## How it works
- After a successful login with **Remember me** checked, the email and password are saved in this browser's `localStorage`.
- On the next visit both fields are filled automatically and the **Log in** button is triggered after a 3-second countdown (cancellable). Works in every browser, no tap needed.
- Chrome/Edge also save to the browser password manager (Credential Management API) as a fallback.
- **Forget saved login on this device** (shown after login) clears the stored details. Logging out returns to the form; the next page load signs in automatically again.

> ⚠️ The password is only base64-encoded, not encrypted. Anyone with access to the browser/device (or any script running on the same domain) can read it. Fine for demos and personal devices; for production use a server-issued "remember me" token instead.

## Setup
1. Replace the demo `loginRequest()` in `index.html` with your real backend call (example included in comments).
2. Serve over **HTTPS** (or `localhost`) — required for credential storage.

## Browser support
- **Chrome / Edge (desktop & Android):** saved credential is read via the Credential Management API and the form signs in automatically. If Chrome only autofills visually, one tap anywhere releases the values and auto-login starts.
- **Safari / iPhone / Firefox:** the email is pre-filled; tap the password field, pick the saved password, and auto-login starts.
- Must be opened over **HTTPS** (e.g. GitHub Pages). Opening the file from disk or viewing it on github.com will not autofill.
- After the first login, click **Save** on the browser's "Save password?" prompt.
