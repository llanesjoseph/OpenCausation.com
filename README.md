# OpenCausation.com

Coming-soon landing page for **OpenCausation.com** — an introductory gateway to structured medical causation review.

A single static page: a full-screen holographic-library hero (with the wordmark, "Coming Soon," and tagline baked into the render) plus a readable description section covering the seven review factors — timing, mechanism, exposure details, objective findings, individual health factors, competing explanations, and documentation quality.

## Structure

```
public/
  index.html            # the page (self-contained CSS, gentle fades, responsive)
  assets/library-bg.png # hero render (1672×941)
firebase.json           # Firebase Hosting config (site: opencausation)
.firebaserc             # Firebase project/target
porkbun.sh              # Porkbun DNS API helper (reads creds from ~/.porkbun.json)
```

## Deploy

```bash
firebase deploy --only hosting
```

Live at `opencausation.web.app`, with custom domains `opencausation.com` and `www.opencausation.com`.

## Design notes

- The hero image carries the wordmark/tagline, so it renders in an aspect-ratio box that **always fits entirely** (never crops the text) and scales with the viewport; off-aspect windows get cinematic letterbox bands.
- Animated holographic glyphs (stethoscope, crosshair) are overlaid on their baked icons and scale with the image via container units.
- Respects `prefers-reduced-motion`.

## DNS

`porkbun.sh` manages records via the Porkbun API. Credentials live in `~/.porkbun.json` (never committed).

```bash
./porkbun.sh list                 # show current records
./porkbun.sh point-firebase <TXT> <A_IP>   # clean slate + point at Firebase
```
