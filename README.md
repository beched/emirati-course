# Emirati Arabic — Speak in 1 Hour

A fast, practical **Emirati Arabic** course: a coherent 23‑lesson path, a Petrov‑style
verb‑conjugation drill engine, Anki‑style flashcards, a graded ~850‑word vocabulary bank,
a reviewed conversation phrasebook, a root/word builder, and an English→Emirati
"arabicizer". All Arabic is fully vowel‑marked and every line has optional Arabizi.

It runs **fully offline** as an installable PWA on iPhone/Safari.

## Contents

| Path | What it is |
|---|---|
| `pwa/index.html` | **The app** — one self‑contained file (all HTML/CSS/JS inline). Works as an installable offline PWA *and* opens standalone as a local file. |
| `pwa/manifest.json`, `pwa/sw.js`, `pwa/icon-*.png` | PWA plumbing (web‑app manifest, offline service worker, icons) |
| `emirati-ebook.html` | Companion **ebook** (print / read in a browser) |
| `emirati-ebook.epub` | The ebook as a validated **EPUB** (Apple Books / e‑readers) |

There is deliberately **one** copy of the app — edit `pwa/index.html` directly; there is no
build step.

> The four Al Ramsa sample PDFs used as source material are **not** included (third‑party
> copyright); they're excluded via `.gitignore`.

## Deploy the offline PWA (GitHub Pages)

A service worker needs HTTPS, so host it and install from Safari:

1. In this repo: **Settings → Pages → Deploy from branch → `main` / root**.
2. Wait for the green check, then open **`https://beched.github.io/emirati-course/pwa/`** in
   Safari on your iPhone (all paths are relative, so it works from that sub‑path).
3. Let it load fully, then **reload once** so the service worker takes control.
4. **Share → Add to Home Screen** → it opens as a standalone app.
5. Toggle **Airplane Mode** and reopen from the Home Screen — it works offline.

Alternative one‑click host: drag the **`pwa`** folder onto **app.netlify.com/drop**.

Local test on a Mac (service workers are allowed on `localhost`):

```bash
cd pwa && python3 -m http.server 8000   # then open http://localhost:8000
```

## Updating

Edit `pwa/index.html`, then **bump the cache name** in `pwa/sw.js`
(`emirati-arabic-v1` → `v2`) so installed devices fetch the new version on their next
online load.

## Notes

- Progress (lessons, drills, flashcards) is stored in `localStorage` and persists in the
  installed app. iOS may clear it after ~7 days of not opening the app (a Safari limitation).
- Vocabulary and register are grounded in the Al Ramsa Institute Emirati Arabic series (A1–B2),
  plus a reviewed conversation phrasebook. Dialect isn't normally vowel‑marked, so treat the
  tashkeel as a pronunciation aid.

🤖 Built with [Claude Code](https://claude.com/claude-code)
