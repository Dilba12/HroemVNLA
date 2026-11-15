# Hroem VNLA — Menu & Dasbor

Aplikasi toko online **Hroem VNLA** (Ekstrak Vanili) dalam satu berkas HTML.

## Masalah gambar di mobile & solusinya

### Akar masalah
Gambar disimpan sebagai **base64 data URL di `localStorage`**. `localStorage`:
- Tidak sinkron antar perangkat (desktop ≠ HP)
- Punya kuota terbatas (~5 MB di browser)
- Bisa kehabisan kuota → gambar hilang

### Solusi yang diterapkan
1. **Kompresi gambar** — 400px max, quality 0.6 (dari 640px/0.78)
2. **Dukungan URL gambar** — bisa gunakan gambar dari hosting luar (https://...)
3. **Onerror handler** — gambar yang error tidak memblok layout
4. **Peringatan kuota** di beranda admin
5. **Fallback simpan tanpa gambar** jika kuota penuh (data teks tetap aman)
6. **Validasi gambar** di saveItem

### Cara pakai gambar URL (disarankan)
1. Host gambar di Imgur / GitHub repo / Cloudinary / hosting mana saja
2. Salin URL gambar (harus diawali `https://` dan berakhiran `.jpg/.png/.webp/.gif`)
3. Di halaman admin → Lapak → edit item → tempel URL di kolom "Atau tempel URL gambar"
4. Semua perangkat (desktop, HP) akan melihat gambar yang sama

### Aktifkan GitHub Pages
Buka https://github.com/Dilba12/hroem-vnla → Settings → Pages → Source: `Save branch: master, folder: /` → Save.
Setelah aktif, buka: https://dilba12.github.io/hroem-vnla

### Cadangan data
Di Pengaturan → Data → Ekspor cadangan (file JSON). Impor di browser baru untuk migrasi data.