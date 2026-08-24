# Ventureboard

A startup operating system for aligning work, projects, evidence, decisions, and operating modes across the company.

## Run locally

From this directory:

```bash
python3 -m http.server 8080
```

Then open `http://localhost:8080` in a browser.

The app is dependency-free and saves task changes in your browser's local storage. It includes a weekly leadership dashboard, task management, capacity tracking, projects, shared knowledge, and decision tracking.

## Google sign-in

Google sign-in is wired through Google Identity Services. To enable it, create a **Web application** OAuth client in the [Google Identity setup](https://developers.google.com/identity/gsi/web/guides/get-google-api-clientid) flow, add your deployed URL (or `http://localhost:8080` while developing) as an authorized JavaScript origin, then paste its public client ID into `index.html`:

```html
<meta name="google-client-id" content="YOUR_CLIENT_ID.apps.googleusercontent.com" />
```

The client ID is public; never add a client secret to this static app. This build uses the Google credential only to identify the current profile in this browser, because workspace data is local storage. A production shared-data app must verify the returned ID token on a server and issue a secure server-managed session, as described in the [Google Identity integration guidance](https://developers.google.com/identity/gsi/web/guides/integrate).
