# MedSprint — Vite project

Converted from the static single-file `index.html` to a proper Vite project.

## Run it

```bash
npm install
npm run dev
```

Then open the local URL Vite prints (usually http://localhost:5173).

Build for production:

```bash
npm run build   # outputs to dist/
npm run preview # preview the production build locally
```

## What changed from the original

- **Structure**: split the single HTML file into `index.html` (markup only),
  `src/style.css` (all styles), and `src/main.js` (all behavior), the standard
  Vite layout.
- **Logo bug fixed**: the original HTML pointed at `assets/dypu-logo.png` etc.,
  but no `assets/` folder shipped in the zip — the logo `<img>` tags were
  broken (404s) wherever it was actually deployed. The four PNGs are now in
  `public/assets/` and the paths point at `/assets/...`, which Vite serves
  correctly both in dev and in the production build. All four PNGs
  themselves are valid, undamaged images (verified: `dypu-logo.png` 481×139,
  `ieee-sb-logo.png` 592×286, `ieee-mh-logo.png` 886×163, `ieee-yp-logo.png`
  792×180) — it was only the path that was wrong.
- **Neon glow buttons**: `.btn-primary` and `.btn-ghost` now carry layered
  colored `box-shadow` glows with a slow pulse animation, intensifying on
  hover.
- **Animated background**: three blurred, slowly-drifting color "orbs"
  (`.orb-1/2/3`), a subtle animated scanline overlay, and a canvas-based
  particle field (`#bgCanvas`, driven by `initParticleBackground()` in
  `src/main.js`) with glowing dots that drift and connect with faint lines.
  Everything in this section respects `prefers-reduced-motion` and is
  disabled/frozen for users who have that setting on.
- **CONFIG block preserved**: `registerUrl`, `submissionRepoUrl`, and
  `eventDateISO` still live at the top of `src/main.js` — same as before,
  edit those before you deploy.

## If you add the IIT Bombay logo later

Drop the file into `public/assets/`, then add an `<img>` tag next to the
others in the `.org-strip` block in `index.html`.
