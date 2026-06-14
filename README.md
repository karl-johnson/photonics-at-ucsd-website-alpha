# OpenOptics Website

Static site built with [Astro](https://astro.build), hosted on GitHub Pages. Deploys automatically on every push to `main`.

## Getting started

```bash
npm install
npm run dev       # http://localhost:4321
npm run build     # outputs to dist/
npm run preview   # preview the built site locally
```

## Adding a project

All project data lives in **`src/data/projects.json`**. Add a new entry following this schema:

```json
{
  "id": "your-project-slug",           // URL slug — lowercase, hyphenated
  "title": "Project Display Name",
  "tagline": "One-sentence hook",
  "description": "A paragraph describing the project, what it teaches, and who it's for.",
  "image": null,                        // or a path to an image in public/images/
  "docsUrl": "https://docs.google.com/...",
  "parameters": {
    "budget":                  0,       // 0–10
    "complexity":              0,
    "manufacturingDifficulty": 0,
    "outreachImpact":          0,
    "setupTime":               0,
    "portability":             0
  },
  "tags": ["tag1", "tag2"]
}
```

Parameter descriptions are in `src/data/parameters.json`. To add a new parameter axis, add it there and also add the key to each project in `projects.json`.

## Adding images

Place images in `public/images/` and set `"image": "/images/your-file.jpg"` in the project entry.

## Deploying

Push to `main`. The GitHub Actions workflow (`.github/workflows/deploy.yml`) builds and deploys to GitHub Pages automatically.

**First-time setup:** In your repo → Settings → Pages → Source: select "GitHub Actions".

Also update `astro.config.mjs`:
```js
site: 'https://your-org.github.io',
base: '/your-repo-name',
```

## License

Site source: MIT. Project documentation: CC BY 4.0. Hardware designs: CERN-OHL-S.
