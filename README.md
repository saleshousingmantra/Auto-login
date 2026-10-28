# Auto-login

A single-page login form that autofills saved credentials and signs in automatically.

## How it works
- Every account you log in with (with **Remember me** checked) is added to a **Saved accounts** list in this browser's `localStorage`.
- On page load the **most recently used** account's email and password are filled in and **Log in** is triggered after a 3-second countdown (cancellable).
- **Tap any saved account** to fill its email + password and log in immediately. Tap **×** to remove it.
- **Use another account** clears the form so you can log in with (and save) a new one.
- Chrome/Edge also save to the browser password manager (Credential Management API) as a fallback.

> ⚠️ The password is only base64-encoded, not encrypted. Anyone with access to the browser/device (or any script running on the same domain) can read it. Fine for demos and personal devices; for production use a server-issued "remember me" token instead.

## Setup
1. Replace the demo `loginRequest()` in `index.html` with your real backend call (example included in comments).
2. Serve over **HTTPS** (or `localhost`) — required for credential storage.

## Browser support
- **Chrome / Edge (desktop & Android):** saved credential is read via the Credential Management API and the form signs in automatically. If Chrome only autofills visually, one tap anywhere releases the values and auto-login starts.
- **Safari / iPhone / Firefox:** the email is pre-filled; tap the password field, pick the saved password, and auto-login starts.
- Must be opened over **HTTPS** (e.g. GitHub Pages). Opening the file from disk or viewing it on github.com will not autofill.
- After the first login, click **Save** on the browser's "Save password?" prompt.
