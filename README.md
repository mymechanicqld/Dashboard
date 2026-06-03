# My Mechanic QLD — Operations Dashboard

Standalone single-file CRM dashboard for [mymechanicqld.com.au](https://www.mymechanicqld.com.au/).
Reads booking submissions from Supabase and shows them with stats, pipeline,
analytics, and inquiry management.

Hosted via **GitHub Pages** — open the published URL and enter the dashboard
password to view.

## Password

Access is gated by a client-side password. The page stores only the **SHA-256
hash** of the password, never the plaintext.

- **Default password:** `mmqld-admin` — **change this.**
- To set a new password, compute its hash and replace `PASSWORD_HASH` in
  `index.html` (search for `PASSWORD_HASH`):

  ```bash
  printf '%s' 'your-new-password' | shasum -a 256
  ```

## Security note

This is a **convenience gate, not strong security.** The dashboard reads
Supabase directly from the browser, so the database key is present in the page
and a technical visitor can reach the data without the password. For real
protection, lock down the Supabase RLS policies (so the public key cannot
SELECT/UPDATE/DELETE) and move the dashboard behind Supabase Auth.

## Deploy (GitHub Pages)

1. Repo **Settings → Pages**
2. Source: **Deploy from a branch** → branch `main` → folder `/ (root)`
3. Save. The dashboard publishes at `https://mymechanicqld.github.io/Dashboard/`.
