# juansanar.com

Personal website and blog of **Juan C. Sanchez-Arias, MD, PhD** — Medical Doctor, Scientist, and Data Scientist.

Built with **[Astro 5](https://astro.build/)** and deployed automatically to Netlify via GitHub Actions.

---

## 🚀 Quick Start

### 1. Run Locally
```bash
npm install
npm run dev
```
Open [http://localhost:4321](http://localhost:4321) to preview your site.

### 2. Build for Production
```bash
npm run build
```

---

## ✍️ Updating Content

- **Landing Page & Bio:** Edit [`src/pages/index.astro`](src/pages/index.astro).
- **Blog Posts:** Add or edit Markdown (`.md`) files in [`src/content/blog/`](src/content/blog/).
- **About Page:** Edit [`src/pages/about.astro`](src/pages/about.astro).
- **CV & Resume:** Replace PDFs in [`public/files/`](public/files/).

### 🚢 Deployment
All pushes to `main` automatically build and deploy in **~15 seconds** via GitHub Actions.

```bash
git add .
git commit -m "Your update message"
git push origin main
```
