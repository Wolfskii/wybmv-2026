# Will you be my Valentine? 💖

A little Svelte app to ask someone special.

![Two bears](img/please.gif)

- **Run locally:** `npm install` then `npm run dev`
- **Build:** `npm run build` (output in `dist/`)
- **Preview build:** `npm run preview`

### Deploy to Dokploy

Use **Build Type: Dockerfile** so the app is built inside the image (the repo’s `Dockerfile` runs `npm run build` then serves `dist/` with Nginx). If you used Static and see the default “Welcome to nginx!” page, switch to Dockerfile and redeploy.

| Field | Value |
|-------|--------|
| **Build Path** | `/` |
| **Watch Paths** | `src/, public/, index.html, package.json, package-lock.json, vite.config.js, svelte.config.js, Dockerfile` (or leave empty) |
| **Enable Submodules** | No |
| **Branch** | `main` |
| **Build Type** | **Dockerfile** |
| **Docker File** | `Dockerfile` (path to Dockerfile, relative to repo root) |
| **Docker Context Path** | `.` (repo root; default) |
| **Docker Build Stage** | `production` (or leave empty — Docker uses the last stage) |
| **Single Page Application (SPA)** | Yes (tick) |
| **Path** | `/` (serve at domain root) |
| **Internal Path** | `/` (default) |
| **Strip Path** | No |
| **Container Port** | `80` (Nginx) |

**Host:** Set your custom domain if you have one; otherwise leave the default.

Trigger a build in the Dokploy UI after pushing. The Dockerfile builds the app and copies only the built `dist/` into the Nginx image, so you get the Valentine app, not the default Nginx page.

---

Made with Svelte 5 + Vite.
