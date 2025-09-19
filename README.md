# 🏆 Scoreboard RW-021

Aplikasi scoreboard digital untuk lomba futsal RW-021.  
Dibuat menggunakan **HTML + CSS + JavaScript** sederhana.

---

## 📸 Tampilan
- Fullscreen scoreboard
- Kontrol skor (+ / -)
- Tombol reset skor
- Tombol fullscreen (bisa keluar juga)

---

## 🔗 Link Live
👉 [Klik di sini untuk membuka scoreboard](https://ridhosan1.github.io/scoreboard/)

> Link akan aktif setelah GitHub Pages selesai dideploy.

---

## 🚀 Cara Deploy ke GitHub Pages

1. Masuk ke menu **Settings** repo ini.
2. Pilih **Pages** di sidebar kiri.
3. Pada bagian **Build and deployment**, pilih **Static HTML** → klik **Configure**.
4. GitHub akan membuat file baru: `.github/workflows/static.yml`.
5. Ganti isi file tersebut dengan workflow berikut:

```yaml
name: Deploy static content to Pages

on:
  push:
    branches: ["main"]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: true

jobs:
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Setup Pages
        uses: actions/configure-pages@v5
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: '.'
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
