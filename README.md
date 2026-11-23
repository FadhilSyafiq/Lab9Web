# Praktikum 9 - PHP Modular
## Nama: Fadhil Syafiq Abdullah
## NIM: 312510161
## Kelas: I251B
## Mata Kuliah: Pemrograman Web

### Tujuan Praktikum
1. Menjelaskan pengertian, tujuan, dan manfaat modularisasi program.
2. Membedakan include, require, include_once, dan require_once.
3. Membuat template halaman yang digunakan bersama oleh beberapa halaman.
4. Membuat dan menggunakan function PHP dengan parameter dan nilai kembalian.
5. Menyusun struktur direktori aplikasi PHP secara modular.
6. Menerapkan routing berdasarkan parameter URL dengan validasi halaman.
7. Mengintegrasikan modularisasi dan routing ke aplikasi database dari praktikum sebelumnya.

### Kebutuhan Perangkat
- Web server lokal: XAMPP (Apache + MySQL)
- PHP 8.x
- Browser
- Visual Studio Code
- Git

### Cara Menjalankan
1. Salin folder repository ke C:\xampp\htdocs\
2. Jalankan Apache dan MySQL melalui XAMPP Control Panel.
Buka di browser:
- Latihan 1 dan 2: http://localhost/lab9_php_modular/home.php
- Latihan 3 (router): http://localhost/lab9_php_modular/router/index.php
- Latihan 4 (CRUD): http://localhost/Lab9Web/latihan4_crud/index.php
4. Untuk Latihan 4, pastikan database latihan1 dan tabel data_barang dari Praktikum 8 sudah ada.

### Struktur Direktori

Lab9Web/
├── README.md
├── screenshots/
├── lab9_php_modular/            ← Latihan 1, 2, dan 3
│   ├── header.php
│   ├── footer.php
│   ├── style.css
│   ├── home.php, about.php, kontak.php
│   ├── helpers.php
│   ├── suhu.php, nilai.php, belanja.php, fungsi.php
│   └── router/
│       ├── index.php
│       ├── views/
│       ├── modules/fungsi/
│       └── assets/css/
└── latihan4_crud/               ← Latihan 4
    ├── index.php
    ├── config/database.php
    ├── helpers/functions.php
    ├── views/
    ├── modules/barang/
    └── assets/

### Praktik: Menguji include dan require
buat `pesan.php` dan `uji-include.php`, ubah nama `pesan.php` sementara, lalu amati pesan error dan apakah baris setelah pemanggilan tetap dijalankan. Ulangi dengan `require`.

Hasil Pengamatan:

| Konstruksi | Jika file tidak ditemukan | Baris setelah Pemanggilan |
| :--- | :---: | ---: |
| `include` | Warning | Tetap dijalankan |
| `require` | Fatal error | Tidak dijalankan |

Output `include`:

Output `require`:


### Latihan1 - Template Multi-halaman
buat aplikasi dengan halaman Home, Profil, dan Kontak. Ketiganya harus menggunakan header dan footer yang sama.

File: `header.php`, `footer.php`, `style.css`, `home.php`, `about.php`, `kontak.php`

Output:
Halaman Home:

Halaman Tentang:

Halaman Kontak:

Analisis hasil:
1. Bagian mana yang digunakan bersama oleh semua halaman? Header (judul dan navigasi) dan footer.
2. Apa yang terjadi jika teks navigasi diubah pada header.php? Perubahan langsung terlihat di semua halaman yang memuat header tersebut.
3. Mengapa konten halaman tidak diletakkan seluruhnya di header.php? Header hanya untuk bagian yang sama di semua halaman. Konten tiap halaman berbeda, jadi harus ada di file masing-masing.
4. Apa manfaat require_once dibanding menyalin kode header ke setiap halaman? Tidak ada kode berulang, perawatan lebih mudah, dan file hanya dimuat satu kali.

### Latihan2 - Function