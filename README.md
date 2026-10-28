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
- **Chrome / Edge / Chromium:** full autofill + auto-login.
- **Safari / Firefox:** native password-manager autofill fills the fields; user clicks Log in.
