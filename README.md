# Catatan Keuangan

Aplikasi pencatatan keuangan pribadi berbasis PWA (Progressive Web App). Data tersimpan lokal di perangkat, tidak dikirim ke server manapun.

## Fitur

- Catat pemasukan & pengeluaran dengan kategori
- Format Rupiah otomatis
- Dashboard saldo bulan berjalan
- Grafik 7 hari terakhir & breakdown per kategori
- Export & Import CSV (untuk backup)
- 100% offline setelah install
- Triple-layer storage (localStorage + IndexedDB + auto-backup)
- Bisa di-install ke home screen seperti aplikasi native

## Panduan Deploy ke GitHub Pages

### Langkah 1: Buat Repository GitHub

1. Login ke https://github.com
2. Klik tombol **+** pojok kanan atas → **New repository**
3. Isi:
   - **Repository name**: `catatan-keuangan` (atau nama lain bebas)
   - **Public** (wajib untuk GitHub Pages gratis)
   - JANGAN centang "Add a README file" (karena kita upload sendiri)
4. Klik **Create repository**

### Langkah 2: Upload Semua File

**Opsi A — Lewat browser (paling mudah):**

1. Di halaman repo baru, klik **"uploading an existing file"**
2. Drag semua file dari folder ini ke area upload:
   - `index.html`
   - `manifest.webmanifest`
   - `sw.js`
   - `icon-180.png`, `icon-192.png`, `icon-512.png`
   - `.github/workflows/deploy.yml` (folder `.github` ikut)
3. Scroll ke bawah, tulis commit message "initial upload"
4. Klik **Commit changes**

**Opsi B — Lewat git command line:**

```bash
cd catatan-keuangan-github
git init
git add .
git commit -m "initial commit"
git branch -M main
git remote add origin https://github.com/USERNAME/catatan-keuangan.git
git push -u origin main
```

Ganti `USERNAME` dengan username GitHub kamu.

### Langkah 3: Aktifkan GitHub Pages

1. Di halaman repo, klik tab **Settings** (paling kanan)
2. Sidebar kiri, klik **Pages**
3. Di section "Build and deployment":
   - **Source**: pilih **GitHub Actions**
4. Tunggu sekitar 1-2 menit. Refresh halaman, akan muncul URL hijau:
   ```
   Your site is live at https://USERNAME.github.io/catatan-keuangan/
   ```

### Langkah 4: Install ke HP

1. Buka URL di atas pakai **Chrome** di HP
2. Tunggu app load penuh (1-2 detik)
3. Tap menu **⋮** (titik tiga) pojok kanan atas
4. Pilih **"Pasang aplikasi"** atau **"Install app"** (BUKAN "Add to Home screen")
5. Icon "K" muncul di home screen. Tap untuk buka langsung tanpa browser bar.

## Cara Update App Nanti

Edit file → push ke GitHub → tunggu 1-2 menit → app di HP auto-update saat dibuka.

```bash
# misal edit index.html
git add .
git commit -m "tambah fitur X"
git push
```

GitHub Actions akan otomatis deploy versi baru.

## Backup Data

**Wajib export CSV minimal seminggu sekali.** Tap tombol "CSV" di header app → simpan file ke Google Drive atau kirim ke WhatsApp diri sendiri.

Kalau data hilang (karena clear cache, ganti HP, dll), tap "Import" → pilih file CSV terakhir → data ter-restore.

## Struktur File

```
catatan-keuangan/
├── index.html              # aplikasi utama (manifest+icon embedded)
├── manifest.webmanifest    # PWA manifest (cadangan, jaga-jaga)
├── sw.js                   # service worker untuk offline
├── icon-180.png            # Apple touch icon
├── icon-192.png            # PWA icon kecil
├── icon-512.png            # PWA icon besar
├── .github/
│   └── workflows/
│       └── deploy.yml      # auto-deploy ke GitHub Pages
├── .gitignore
└── README.md
```

## Privasi

Semua data tersimpan **hanya di browser kamu** (localStorage + IndexedDB). Tidak ada server, tidak ada tracking, tidak ada akun. Kamu pemilik penuh data kamu.

## Pengembangan Lanjutan (Roadmap)

- [ ] Sinkronisasi via Telegram bot (integrasi dengan GAS OI Bot)
- [ ] Budget per kategori dengan alert
- [ ] Auto-import P&L dari Binance/Tokocrypto/Stockbit
- [ ] Reminder pajak bulanan (PPh Final UMKM)
- [ ] Multi-device sync via Google Sheets API
