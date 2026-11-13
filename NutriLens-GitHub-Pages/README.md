# NutriLens — GitHub Pages

## Hosting frontend di GitHub Pages

1. Buat repository GitHub bernama **NutriLens**.
2. Upload seluruh isi folder ini ke root repository (jangan upload folder pembungkus `NutriLens-main`).
3. Buka **Settings → Pages**.
4. Pada bagian **Build and deployment**, pilih **GitHub Actions**.
5. Buka tab **Actions** dan tunggu workflow `Deploy NutriLens to GitHub Pages` selesai.
6. Aplikasi akan tersedia di `https://USERNAME.github.io/NutriLens/`.

Jika nama repository bukan `NutriLens`, ubah nilai `GITHUB_PAGES_BASE` di `.github/workflows/deploy.yml` menjadi `/<nama-repository>/`.

## Penting: API Gemini

GitHub Pages hanya meng-host frontend statis. Endpoint analisis `/api/analyze` pada `server.ts` membutuhkan backend Node.js dan tidak akan berjalan di GitHub Pages.

Agar fitur analisis foto berfungsi:
- Deploy backend `server.ts` secara terpisah ke layanan backend (misalnya VPS/CyberPanel atau layanan serverless yang kompatibel).
- Simpan `GEMINI_API_KEY` sebagai environment variable/secret di backend, jangan di frontend atau repository.
- Atur GitHub repository secret bernama `VITE_API_BASE_URL` ke URL backend, contoh `https://api-domain-anda.com` (tanpa garis miring di akhir).

Tanpa backend tersebut, halaman dan antarmuka NutriLens tetap dapat dibuka, tetapi analisis AI tidak akan berfungsi.

## Menjalankan lokal

```bash
npm install
npm run dev
```

Untuk build frontend statis:

```bash
npm run build:pages
```
