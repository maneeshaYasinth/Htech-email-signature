# Hydrotech Email Signatures

A static, frontend-only page where team members sign in, fill in their details and copy the company email signature.

## What's in here

- `index.html`: the whole site in one file. Preview images are embedded, so it runs on any static host.
- `email/`: the five PNGs that the **copied** signature loads in people's inboxes.

## Deploy

The site is hosted on Vercel at https://mailing.htechcore.com. The Vercel project is linked to this repo, so every push to `main` redeploys it. There's no build step.

- The images are served from `/email/` (for example `https://mailing.htechcore.com/email/hc-logo.png`). `ASSET_BASE` in the `CONFIG` block near the top of the script in `index.html` points there.
- **Don't rename, move or delete anything in `email/`.** Every signature people have already sent loads these image URLs, and those emails can't be updated.
- After a change, open the page, sign in, copy a signature and send yourself a test email.

## Change the team passcode

The passcode is shared with the team privately. To change it, hash the new one:

```
# macOS
echo -n 'new-passcode' | shasum -a 256
# Ubuntu
echo -n 'new-passcode' | sha256sum
```

Paste the hash into `PASSCODE_SHA256` in the `CONFIG` block.

## About the sign-in

The sign-in runs entirely in the browser. It checks for an @htechcore.com address and the passcode hash, which keeps casual visitors out. Anyone who reads the page source can get past it, so don't put anything secret on this page.
