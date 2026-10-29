# Hydrotech Email Signatures

A static, frontend-only page where team members sign in, fill in their details and copy the company email signature.

## What's in here

- `index.html`: the whole site in one file. Preview images are embedded, so it runs on any static host.
- `email/`: the five PNGs that the **copied** signature loads in people's inboxes.

## Deploy

1. Upload the `email/` folder so the images are public at `https://htechcore.com/email/` (for example `https://htechcore.com/email/hc-logo.png`).
   To host them somewhere else, change `ASSET_BASE` in the `CONFIG` block near the top of the script in `index.html`.
2. Host `index.html` on any static host over https (for example `sign.htechcore.com`). The passcode check needs https.
3. Open the page, sign in, copy a signature and send yourself a test email before sharing the link with the team.

## Change the team passcode

The starter passcode is `hydrotech2026`. Change it before sharing:

```
# macOS
echo -n 'new-passcode' | shasum -a 256
# Ubuntu
echo -n 'new-passcode' | sha256sum
```

Paste the hash into `PASSCODE_SHA256` in the `CONFIG` block.

## About the sign-in

The sign-in runs entirely in the browser. It checks for an @htechcore.com address and the passcode hash, which keeps casual visitors out. Anyone who reads the page source can get past it, so don't put anything secret on this page.
