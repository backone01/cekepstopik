# EPS-TOPIK 2026 Examination Monitoring Dashboard & Status Checker

Dashboard analitik dan status checker mandiri untuk hasil ujian EPS-TOPIK Sektor Manufaktur 2026 (Semarang, Jakarta, Surabaya). Dibuat dengan **Bootstrap 5.3**, **Chart.js**, dan siap di-deploy secara instan ke **GitHub Pages**.

## Fitur Utama
1. **Statistik Lengkap & KPI**:
   - Total 17.619 peserta terdata.
   - Proporsi kelulusan: 2.031 peserta lulus (ambang batas kelulusan: 97.5 poin).
   - Passing rate keseluruhan: 12.66% (dari 16.045 peserta yang hadir).
2. **Visualisasi Data Interaktif**:
   - Grafik Donat (Proporsi Kelulusan).
   - Grafik Batang (Komparasi Hasil Ujian antar Lokasi: Semarang, Jakarta, Surabaya).
   - Grafik Distribusi Rentang Skor.
   - Tabel Breakdown Tepat Jumlah Orang Per Nilai (100.0, 97.5, 95.0, dst).
3. **Pengecekan Nilai Mandiri (Zero-Knowledge & Privacy Masked)**:
   - Peserta dapat memasukkan 16 digit (`0122026C...`) atau 8 digit nomor ujian miliknya.
   - Sistem mencocokkan menggunakan hash **SHA-256 client-side** (Web Crypto API).
   - Nama lengkap dan nomor ujian di tabel publik disamarkan demi privasi (`0122026C50****01`, `M******D R***Y P*****A`), namun pemilik nomor ujian tetap bisa memverifikasi skornya secara instan.
4. **Tabel Data Lengkap dengan Multi-Filter & Paginasi Cepat**:
   - Filter berdasarkan Status, Lokasi, Gender, Skor Eksak, dan Rentang Skor Min/Max.
   - Paginasi client-side instan (25 / 50 / 100 per halaman).

---

## Struktur Berkas untuk GitHub Pages
```
eps/
├── docs/
│   ├── index.html           # File utama dashboard (Bootstrap 5.3 + Chart.js)
│   ├── analytics.json       # Data agregasi ringkasan dan statistik
│   ├── peserta_data.json    # Data tabel 17.619 peserta (nama & nomor disamarkan)
│   └── peserta_lookup.json  # Mapping hash SHA-256 untuk pengecekan mandiri
├── dashboard.html           # Salinan identik dari docs/index.html
├── server.py                # Server lokal Flask (opsional)
└── README.md
```

---

## Cara Deploy ke GitHub Pages

1. **Inisialisasi Git & Push ke GitHub**:
   ```bash
   git init
   git add .
   git commit -m "feat: setup dashboard and static assets for GitHub Pages"
   git branch -M main
   git remote add origin https://github.com/<USERNAME-ANDA>/<NAMA-REPO-ANDA>.git
   git push -u origin main
   ```

2. **Aktifkan GitHub Pages**:
   - Buka repositori Anda di GitHub.
   - Masuk ke tab **Settings** -> **Pages**.
   - Pada bagian **Build and deployment**:
     - **Source**: Pilih `Deploy from a branch`.
     - **Branch**: Pilih `main` dan direktori folder `/docs`.
   - Klik **Save**.
   - Tunggu sekitar 1–2 menit, dashboard Anda akan aktif di:
     `https://<USERNAME-ANDA>.github.io/<NAMA-REPO-ANDA>/`
