# Monitoring Stok Beras

Aplikasi single-page (HTML/CSS/JS) untuk memantau stok beras di gudang: pencatatan barang masuk, pengajuan barang keluar dengan alur approval, dashboard ringkasan, grafik, pencarian/filter, serta ekspor Excel, cetak PDF, dan backup/restore data.

Data disimpan di `localStorage` browser (tanpa backend/database), jadi cocok untuk demo, tugas kuliah, atau prototipe cepat.

## Cara pakai

Cukup buka `index.html` langsung di browser, atau jalankan lewat server statis apa saja, contohnya:

```bash
npx serve .
# atau
python3 -m http.server 8000
```

Lalu buka `http://localhost:8000`.

## Login

| Role  | Username | Password  |
|-------|----------|-----------|
| Admin | admin    | beras123  |
| User  | user     | user123   |
| User  | rakha    | Batom2025 |

- **Admin**: bisa input stok masuk, menyetujui/menolak pengajuan, menghapus data, dan restore backup.
- **User**: hanya bisa mengajukan barang keluar dan melihat data.
- Hint kredensial di halaman login sudah dihapus dari tampilan — simpan info ini di tempat aman (README ini, password manager, dsb).
- Untuk menambah akun **user** baru berikutnya, edit array `USERS` di bagian `<script>` pada `index.html`. Untuk akun **admin**, edit objek `ADMIN` di baris yang sama. Ganti juga kredensial ini sebelum dipakai secara serius — di sini kredensial tersimpan sebagai teks biasa di kode, jadi jangan pakai untuk data produksi/sensitif.

## Fitur

- Dashboard: total stok, total masuk, total keluar, jumlah pengajuan menunggu
- Grafik batang (masuk vs keluar) dan pie (komposisi jenis transaksi)
- Input stok masuk (khusus Admin) & pengajuan stok keluar (Admin/User)
- Approval pengajuan (setujui/tolak) dengan validasi stok tersedia
- Pencarian, filter status, dan filter tanggal yang bisa dikombinasikan
- Ekspor ke Excel (`.xlsx`), cetak/ekspor ke PDF via dialog print browser
- Backup data ke file `.json` dan restore dari file backup
- Mode gelap (dark mode)

## Struktur file

```
.
├── index.html   # seluruh aplikasi (markup, style, dan logic)
├── logo.png     # logo yang tampil di sidebar & halaman login
└── README.md
```

> Jika `logo.png` tidak ditemukan (misalnya lupa di-push), aplikasi otomatis menampilkan ikon gudang sebagai cadangan — tidak akan muncul gambar patah.

## Catatan teknis

- Dependensi dimuat via CDN: Bootstrap 5, Font Awesome, SweetAlert2, Chart.js, SheetJS (xlsx).
- Tidak ada proses build — file `index.html` bisa langsung dibuka atau di-deploy ke GitHub Pages.
- Karena penyimpanan memakai `localStorage`, data bersifat lokal per browser/perangkat dan akan hilang jika cache/situs data dibersihkan. Gunakan tombol **Backup** secara berkala jika datanya penting.

## Deploy ke GitHub Pages

1. Push repo ini ke GitHub.
2. Buka **Settings → Pages**.
3. Pilih branch `main` dan folder root (`/`), lalu simpan.
4. Situs akan tersedia di `https://<username>.github.io/<nama-repo>/`.
