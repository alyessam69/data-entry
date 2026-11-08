# 🧪 Lab Data Entry — Soap & Shift (PWA)

Writes the **Soap Bar Daily Log** and the **Shift Hourly Report** straight into the
encrypted cloud. Now an installable, offline-capable PWA — the same page, plus a
home-screen icon.

## Install on the phone

Tap the **⬇️ Install app** button next to the title (it appears as soon as the app is
installable).

**Android (Chrome)** — the button opens the native install dialog → *Install*.
**iPhone (Safari)** — the button shows the steps: Share ⬆️ → *Add to Home Screen* → *Add*.
**Desktop Chrome** — the button explains it, or use the install icon in the address bar.

Offline the page still opens and every box still works — only the cloud needs a network.

## The cloud (unchanged)

| App | Document |
|---|---|
| Soap Bar Daily Log | `lab/soap-pro-v2-9f8e4d2c1b7a6053e4d89a12.json` |
| Shift Hourly Report | `lab/shift-40266e02ffb7ac507bcc846a.json` |

`https://soap-lab-shift-sync-default-rtdb.europe-west1.firebasedatabase.app`

- Encryption: **AES-GCM 256 + PBKDF2 120k**, PIN `2780` (the PIN box at the top of the app).
- The `salt` of each document is never changed, so every phone keeps decrypting it.
- Only the boxes you fill are written — the rest of the document stays exactly as it is.
- Every write keeps a backup on the phone (`Undo the last change`).

## Repo layout

```
index.html              the whole app + the PWA bits (install button, SW registration)
manifest.webmanifest    PWA manifest (name, icons, standalone display)
sw.js                   service worker — offline shell, never caches the cloud
icons/                  192 / 512 / maskable / apple-touch icons
README.md               this file
.nojekyll               keep GitHub Pages from processing the files
```

## The deep links still work

`?app=soap&oshift=1&line=1&batch=1&w=109.5,109.6&fix=1&bn=3100241611&m=16.5&fa=0.05`
`?app=shift&shift=A&hour=10&r=25,0.1&p=14.5,0.05&t=0.6,8.2,0.07`
`&go=1` saves as soon as the page opens (it still asks to confirm).
