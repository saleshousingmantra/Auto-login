# Auto-login

A single-page login form that autofills saved credentials and signs in automatically.

## How it works
- After a successful login, the email and password are stored in the browser's built-in password manager via the Credential Management API (`navigator.credentials.store`) — never in localStorage.
- On the next visit, saved credentials are retrieved (`navigator.credentials.get`), filled into the form, and the **Log in** button is triggered automatically after a 3-second countdown (cancellable).
- Logging out calls `preventSilentAccess()` so the user isn't instantly signed back in.

## Setup
1. Replace the demo `loginRequest()` in `index.html` with your real backend call (example included in comments).
2. Serve over **HTTPS** (or `localhost`) — required for credential storage.

## Browser support
- **Chrome / Edge (desktop & Android):** saved credential is read via the Credential Management API and the form signs in automatically. If Chrome only autofills visually, one tap anywhere releases the values and auto-login starts.
- **Safari / iPhone / Firefox:** the email is pre-filled; tap the password field, pick the saved password, and auto-login starts.
- Must be opened over **HTTPS** (e.g. GitHub Pages). Opening the file from disk or viewing it on github.com will not autofill.
- After the first login, click **Save** on the browser's "Save password?" prompt.
