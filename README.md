# Sistem Manajemen Perpustakaan Kampus

Perpustakaan adalah fasilitas penunjang akademik yang harus menjadi sumber informasi andalan mahasiswa. Tanpa sistem pengelolaan yang baik, pencarian buku, pemantauan peminjaman, dan pelayanan kepada mahasiswa menjadi sulit. Program ini dibuat sebagai solusi sederhana untuk mengelola koleksi buku, lokasi penyimpanannya, dan proses peminjaman. Selain itu, program ini menjadi sarana belajar menerapkan enam struktur data Java serta pola arsitektur MVC.

## Tugas Pemrograman Java

- **Mata Kuliah:** Pemrograman Berorientasi Objek
- **Dosen Pengampu:** M. Ibadurrahman Arrasyid Supriyanto, M.Kom.
- **Program Studi:** Sistem Informasi
- **Angkatan:** 2025
- **Kelompok:** 16

## Anggota Kelompok 12

## Anggota Kelompok

| No. | Nama | Kelas | NIM |
|---:|---|:---:|---:|
| 1 | Rizki Adrianur Saputra | B | 2509116049 |
| 2 | Putri Anggita Melasari | A | 2509116010 |
| 3 | Zahra Syifa Salsabila | B | 2509116057 |
| 4 | Awang Rifky Muhadzib | B | 2509116059 |


## Struktur File Proyek

Berikut adalah gambaran struktur file proyek Sistem Manajemen Perpustakaan Kampus.

```text

SistemManajemenPerpustakaanKampus/
└── Source Packages/
    ├── Main/
    │   └── Main.java
    ├── controller/
    │   └── PerpustakaanController.java
    ├── model/
    │   ├── Buku.java
    │   ├── Perpustakaan.java
    │   └── Transaksi.java
    └── view/
        └── PerpustakaanView.java

```

<img width="425" height="266" alt="image" src="https://github.com/user-attachments/assets/3d7e3b2c-829d-4d5a-aa87-89d41c2f64ca" />

### Keterangan Struktur Proyek

Proyek Sistem Manajemen Perpustakaan Kampus menggunakan bahasa pemrograman Java dengan struktur yang dibagi menjadi beberapa package, yaitu Main, controller, model, dan view. Pembagian ini bertujuan agar kode program lebih terstruktur, mudah dipahami, serta memisahkan bagian utama program, pengelolaan data, proses sistem, dan tampilan antarmuka.
- **`Main`**: Berisi file `Main.java` yang digunakan untuk memulai dan menjalankan program.
- **`controller`**: Berisi `PerpustakaanController.java` yang mengatur jalannya program dan menghubungkan bagian data dengan tampilan.
- **`model`**: Berisi `Buku.java`, `Perpustakaan.java`, dan `Transaksi.java` untuk mengatur data buku, koleksi perpustakaan, serta peminjaman dan pengembalian buku.
- **`view`**: Berisi `PerpustakaanView.java` yang menampilkan informasi dan menjadi tempat pengguna berinteraksi dengan program.
- **`pom.xml`**: Berisi pengaturan proyek Maven, termasuk informasi proyek dan kebutuhan library yang digunakan.
- **`nbactions.xml`**: Berisi pengaturan perintah untuk menjalankan atau melakukan aksi tertentu pada proyek melalui NetBeans.
