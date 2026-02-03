# Will you be my Valentine? 💖

A little Svelte app to ask someone special.

![Two bears](img/please.gif)

- **Run locally:** `npm install` then `npm run dev`
- **Build:** `npm run build` (output in `dist/`)
- **Preview build:** `npm run preview`

### Deploy to Dokploy

Use the **Static** build type. In your Dokploy project (after connecting the GitHub repo), use these settings:

| Field | Value |
|-------|--------|
| **Build Path** | `dist` (folder to serve after build; the build runs from repo root) |
| **Watch Paths** | `src/, public/, index.html, package.json, package-lock.json, vite.config.js, svelte.config.js` (or leave empty) |
| **Enable Submodules** | No |
| **Branch** | `main` |
| **Build Type** | **Static** |
| **Single Page Application (SPA)** | Yes (tick) |
| **Path** | `/` (serve at domain root) |
| **Internal Path** | `/` (default) |
| **Strip Path** | No |
| **Container Port** | `80` (Nginx) |

**Host:** Set your custom domain if you have one; otherwise leave the default.

If Dokploy has a **Build Command** (or similar) field, set it to:

```bash
npm ci && npm run build
```

That produces the static files in `dist/`, which are then served by Nginx. Trigger a build in the Dokploy UI if it doesn’t start automatically.

---

Made with Svelte 5 + Vite.
