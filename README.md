# Minpro 2 PBO — Sistem Pemesanan Tiket Kapal

**Nama**  : Rizki Adrianur Saputra

**NIM**   : 2509116049

**Kelas** : B

---

## Deskripsi Singkat Program

Program ini merupakan Sistem Pemesanan Tiket Kapal berbasis Java yang dijalankan melalui console/CLI. Program ini merupakan pengembangan dari Minpro 1 dengan menambahkan konsep **Inheritance**, **Encapsulation**, **validasi input**, **dummy data**, **struktur MVC**, dan **Polymorphism**.

Pengguna dapat melakukan beberapa proses, yaitu:

- Menambahkan data pemesanan.
- Menampilkan seluruh data pemesanan.
- Mengubah data pemesanan.
- Menghapus data pemesanan.
- Mengakhiri program melalui menu keluar.

Program menyimpan data pemesanan sementara selama program berjalan menggunakan `ArrayList<Pemesanan>`. Saat program pertama kali dijalankan, `ArrayList` sudah berisi **2 dummy data** sehingga menu Tampilkan Pemesanan langsung menampilkan data tanpa perlu input dari awal.

---

## Struktur Folder

Struktur package pada project (mengikuti struktur MVC) adalah sebagai berikut:

```
Sistem_pemesanan_tiket_Kapal
└── Source Packages
    ├── controller
    │   └── PemesananController.java
    ├── main
    │   └── Sistem_pemesanan_tiket_Kapal.java
    ├── model
    │   ├── Kapal.java
    │   ├── KapalEkonomi.java
    │   ├── KapalVIP.java
    │   ├── Pemesanan.java
    │   └── Penumpang.java
    └── view
        └── PemesananView.java
```

---

## Struktur Kelas

| Kelas | Tanggung Jawab |
|---|---|
| `Kapal` | **Superclass.** Menyimpan data umum kapal berupa nama kapal, tujuan, dan harga tiket. |
| `KapalEkonomi` | **Subclass** dari `Kapal`. Menambahkan atribut `fasilitasEkonomi`. |
| `KapalVIP` | **Subclass** dari `Kapal`. Menambahkan atribut `fasilitasVIP`. |
| `Penumpang` | Menyimpan data penumpang berupa nama, NIK, dan umur. |
| `Pemesanan` | Menggabungkan data `Penumpang` dan `Kapal`, jumlah tiket, serta menghitung total harga. |
| `PemesananView` | Menampilkan menu, menerima input, dan memvalidasi input pengguna. |
| `PemesananController` | Menjalankan alur program dan mengelola proses CRUD data pemesanan. |
| `Sistem_pemesanan_tiket_Kapal` | Class utama yang berisi method `main`. |

---

## Alur dan Gambaran Output Program

### Program Dimulai dan Pengisian Dummy Data

Program dijalankan melalui method `main` pada kelas `Sistem_pemesanan_tiket_Kapal`. Method tersebut membuat objek `PemesananController` lalu memanggil `jalankanProgram()`.

Saat objek `PemesananController` dibuat, constructor memanggil method `isiDummyData()` yang menambahkan 2 data awal ke dalam `ArrayList`:

| ID | Penumpang | Kapal | Tujuan | Jenis | Jumlah Tiket |
|---|---|---|---|---|---|
| 101 | Andi | KM Bukit Siguntang | Balikpapan | VIP | 2 |
| 102 | Budi | KM Lambelu | Makassar | Ekonomi | 1 |

Data pemesanan disimpan sementara di dalam memori menggunakan `ArrayList<Pemesanan>` selama program berjalan, dan dapat ditambah, ditampilkan, diubah, atau dihapus lewat menu yang tersedia.

### Menu Utama

Program menampilkan menu utama secara berulang menggunakan perulangan `do-while`. Perulangan akan terus berjalan sampai pengguna memilih menu Keluar.

| No. | Menu | Fungsi |
|---|---|---|
| 1 | **Tambah Pemesanan** | Menambahkan data pemesanan tiket kapal. |
| 2 | **Tampilkan Pemesanan** | Menampilkan seluruh data pemesanan yang tersimpan. |
| 3 | **Ubah Pemesanan** | Mengubah data pemesanan yang telah tersimpan. |
| 4 | **Hapus Pemesanan** | Menghapus data pemesanan yang dipilih. |
| 5 | **Keluar** | Mengakhiri program. |

<img width="403" height="238" alt="Screenshot menu utama" src="https://github.com/user-attachments/assets/0bda7e13-9d02-411f-a5cd-a475a39341f4" />

Pada bagian ini, sistem menampilkan 5 menu utama, yaitu Tambah Pemesanan, Tampilkan Pemesanan, Ubah Pemesanan, Hapus Pemesanan, dan Keluar.

### 1. Tambah Pemesanan (Menu 1)

**Alur proses:**

- Pengguna memasukkan ID pemesanan. Sistem memeriksa format ID dan memastikan ID belum dipakai. Jika sudah dipakai, sistem menampilkan pesan "ID sudah digunakan." dan meminta input ulang.
- Pengguna memasukkan nama penumpang, NIK, dan umur.
- Sistem menampilkan tiga pilihan kapal beserta tujuan, jenis, dan harga tiket. Pengguna memilih salah satu.
- Berdasarkan pilihan, method `buatKapal()` pada controller membuat objek `KapalVIP` (pilihan 1) atau `KapalEkonomi` (pilihan 2 dan 3).
- Pengguna memasukkan jumlah tiket.
- Sistem membuat objek `Penumpang` dan `Pemesanan`, lalu menambahkannya ke `ArrayList` `daftarPemesanan`.
- Sistem menampilkan pesan "Pemesanan berhasil ditambahkan." beserta total harga dari `getTotalHarga()`.

**Pilihan kapal:**

| No. | Kapal | Tujuan | Jenis | Harga | Fasilitas |
|---|---|---|---|---|---|
| 1 | KM Bukit Siguntang | Balikpapan | VIP | Rp150000 | Kabin pribadi |
| 2 | KM Lambelu | Makassar | Ekonomi | Rp200000 | Kursi penumpang |
| 3 | KM Dorolonda | Parepare | Ekonomi | Rp175000 | Kursi penumpang |

**Output Program:**

<img width="495" height="571" alt="image" src="https://github.com/user-attachments/assets/c3aec39e-03c5-44d4-bd4f-3f72a6fda8f7" />

Pada bagian ini, pengguna memasukkan data penumpang, memilih kapal, dan menentukan jumlah tiket. Sistem menyimpan data serta menghitung total harga secara otomatis.

### 2. Tampilkan Pemesanan (Menu 2)

**Alur proses:**

- Sistem memeriksa isi `ArrayList` `daftarPemesanan`.
- Jika belum terdapat data, sistem menampilkan pesan "Belum ada data pemesanan."
- Jika terdapat data, sistem menggunakan perulangan `for` untuk mengambil setiap objek `Pemesanan`.
- Sistem menampilkan ID pemesanan, nama penumpang, NIK, umur, informasi kapal, jumlah tiket, dan total harga.
- Informasi kapal ditampilkan melalui method `tampilkanInfo()`. Hasil tampilan berbeda untuk kapal VIP dan Ekonomi (lihat bagian Polymorphism).

**Output Program:**

<img width="393" height="997" alt="image" src="https://github.com/user-attachments/assets/b6837b5b-68f7-45d7-9151-e1a8bf909c69" />

Pada bagian ini, data dummy langsung tampil tanpa perlu menambah data terlebih dahulu. Informasi kapal VIP dan Ekonomi ditampilkan dengan fasilitas yang berbeda (polymorphism).

### 3. Ubah Pemesanan (Menu 3)

**Alur proses:**

- Pengguna memasukkan ID pemesanan yang ingin diubah.
- Sistem mencari data berdasarkan `idPemesanan` pada `ArrayList`.
- Jika ID ditemukan, pengguna memasukkan data baru berupa nama penumpang, NIK, umur, pilihan kapal, dan jumlah tiket. Semua input baru divalidasi.
- Data `Penumpang` diperbarui menggunakan `setNama()`, `setNik()`, dan `setUmur()`.
- Data kapal dan jumlah tiket pada `Pemesanan` diperbarui menggunakan `setKapal()` dan `setJumlahTiket()`.
- Sistem menampilkan pesan "Data berhasil diubah."
- Jika ID tidak ditemukan, sistem menampilkan pesan "ID Pemesanan tidak ditemukan."

**Output Program:**

<img width="512" height="545" alt="image" src="https://github.com/user-attachments/assets/f470d58c-5cde-4c0e-8a46-ce6e891a78db" />

Pada bagian ini, pengguna memasukkan ID pemesanan yang ingin diperbarui. Setelah data baru dimasukkan, sistem memperbarui informasi pemesanan dan menampilkan pesan "Data berhasil diubah."

**Output setelah perubahan:**

<img width="412" height="258" alt="image" src="https://github.com/user-attachments/assets/c9ec51dc-a76f-490b-b3fc-0278f00f0a6d" />

### 4. Hapus Pemesanan (Menu 4)

**Alur proses:**

- Pengguna memasukkan ID pemesanan yang ingin dihapus.
- Sistem mencari data berdasarkan `idPemesanan`.
- Jika ID ditemukan, sistem menampilkan nama penumpang lalu meminta konfirmasi (`1` = Ya, `2` = Tidak).
- Jika pengguna memilih `1`, objek `Pemesanan` dihapus dari `ArrayList` menggunakan `remove()` dan sistem menampilkan "Data berhasil dihapus."
- Jika pengguna memilih `2`, sistem menampilkan "Penghapusan dibatalkan."
- Jika ID tidak ditemukan, sistem menampilkan pesan "ID Pemesanan tidak ditemukan."

**Output Program:**

<img width="358" height="257" alt="image" src="https://github.com/user-attachments/assets/69bed670-a2fd-4bde-a9ac-f15ce10b6b83" />

Pada bagian ini, pengguna memasukkan ID pemesanan dan mengonfirmasi penghapusan. Jika pengguna memilih "Ya", sistem menghapus data dari `ArrayList` dan menampilkan pesan "Data berhasil dihapus."

**Output setelah perubahan:**

<img width="436" height="782" alt="image" src="https://github.com/user-attachments/assets/d567e4d3-e13f-4afb-a167-e62530fe79ae" />

### 5. Keluar (Menu 5)

**Alur proses:**

- Pengguna memilih menu **5. Keluar**.
- Sistem menampilkan pesan "Program selesai." dan "Terima kasih."
- Nilai `pilihan` menjadi `5`, sehingga kondisi pada perulangan `do-while` tidak terpenuhi dan program berhenti.

**Output Program:**

<img width="678" height="410" alt="image" src="https://github.com/user-attachments/assets/e96bbc89-6a94-4b55-924d-9572432a0415" />

Pada bagian ini, pengguna memilih menu Keluar untuk mengakhiri program. Sistem menghentikan perulangan dan menampilkan pesan "Program selesai." dan "Terima kasih."

---

## Penerapan Konsep Wajib

### 1. Encapsulation

Encapsulation diterapkan dengan menggunakan access modifier `private` pada atribut yang terdapat di dalam class.

Contoh pada `model/Kapal.java`:

<img width="360" height="125" alt="image" src="https://github.com/user-attachments/assets/d8868de2-a462-4db4-9e51-5f5f921cbecc" />

Atribut tersebut tidak dapat diakses secara langsung dari luar class. Untuk mengambil dan mengubah data digunakan method getter dan setter yang di dalamnya juga terdapat validasi.

Contohnya:

**KapalVIP**

<img width="705" height="197" alt="image" src="https://github.com/user-attachments/assets/3833dadd-c846-4ba1-9b11-e5971c454637" />

**KapalEkonomi**

<img width="773" height="192" alt="image" src="https://github.com/user-attachments/assets/537040b6-d201-40a3-805e-ead19f1467cb" />

Penerapan encapsulation juga terdapat pada class `Kapal`, `Penumpang`, dan `Pemesanan`.

### 2. Inheritance

Program memiliki **1 superclass** dan **2 subclass**.

<img width="396" height="70" alt="image" src="https://github.com/user-attachments/assets/638afb04-5daf-4078-ad26-aa994e261164" />

- `KapalEkonomi` dan `KapalVIP` mewarisi atribut dan method dari `Kapal` menggunakan kata kunci `extends`.
- Constructor subclass memanggil constructor superclass menggunakan `super(namaKapal, tujuan, hargaTiket)`.
- Setiap subclass menambahkan atribut khusus, yaitu `fasilitasEkonomi` pada `KapalEkonomi` dan `fasilitasVIP` pada `KapalVIP`.
- Subclass mengambil data dari superclass melalui getter (`getNamaKapal()`, `getTujuan()`, `getHargaTiket()`) karena atribut superclass bersifat `private`.

### 3. Validasi Input

Validasi input diterapkan di dua lapisan: pada **view** (saat pengguna mengetik) dan pada **setter model** (sebagai lapisan pengaman data). Jika input tidak valid, sistem menampilkan pesan kesalahan dan meminta pengguna memasukkan ulang sampai benar.

**3.1 ID Pemesanan**

<img width="382" height="128" alt="image" src="https://github.com/user-attachments/assets/557744d3-42f1-402b-916f-6cb00b325ef1" />

ID tidak boleh kosong, harus terdiri dari 3 angka, dan tidak boleh sama dengan ID yang sudah digunakan.

**3.2 Nama Penumpang**

<img width="425" height="130" alt="image" src="https://github.com/user-attachments/assets/9f1ce51c-e3ed-4ee3-8d3b-95a7498e3c4c" />

Nama tidak boleh kosong dan hanya dapat berisi huruf serta spasi.

**3.3 NIK**

<img width="437" height="125" alt="image" src="https://github.com/user-attachments/assets/0e8a59cb-1f21-4885-8267-cf13de718d9c" />

NIK tidak boleh kosong dan harus terdiri dari tepat 16 digit dan hanya dapat berisi angka.

**3.4 Umur**

<img width="307" height="175" alt="image" src="https://github.com/user-attachments/assets/8afa5d18-335e-40bf-b7d6-44b640767a14" />

Umur tidak boleh kosong, harus berupa angka, maksimal 3 digit, dan nilainya harus lebih dari 0.

**3.5 Pilihan Kapal**

<img width="538" height="435" alt="image" src="https://github.com/user-attachments/assets/05d93148-8d87-4345-ad64-eb514f014339" />

Pengguna hanya dapat memilih kapal dengan pilihan 1 sampai 3.

**3.6 Jumlah Tiket**

<img width="355" height="48" alt="image" src="https://github.com/user-attachments/assets/a35157f7-bd26-4ba7-9981-7f559be4c448" />

Jumlah tiket harus berupa angka dan nilainya harus lebih dari 0.

Selain validasi tersebut, program menggunakan `try-catch` untuk menangani `NumberFormatException` sehingga program tetap berjalan ketika pengguna memasukkan input yang tidak sesuai, seperti huruf pada input yang harus berupa angka.

### 4. Dummy Data

Method `isiDummyData()` pada `PemesananController` dipanggil di dalam constructor sehingga `ArrayList<Pemesanan>` sudah berisi 2 data (ID `101` dan `102`) ketika program pertama kali berjalan. Menu Tampilkan Pemesanan langsung menampilkan data tersebut tanpa perlu menambah data terlebih dahulu.

Contoh gambar:

<img width="510" height="458" alt="image" src="https://github.com/user-attachments/assets/be1ee4eb-a703-45cc-9756-ed4eda8f3079" />

---

## Penerapan Nilai Tambah

### 1. Struktur MVC

Nilai tambah MVC diterapkan dengan memisahkan program ke dalam package `model`, `main`, `view`, dan `controller` (lihat bagian **Struktur Folder** di atas untuk susunan lengkapnya).

| Package | Kelas | Peran |
|---|---|---|
| `main` | `Sistem_pemesanan_tiket_Kapal` | Titik awal program. Hanya membuat objek controller dan menjalankannya. |
| `model` | `Kapal`, `KapalEkonomi`, `KapalVIP`, `Penumpang`, `Pemesanan` | Menyimpan data serta aturan data (atribut, getter/setter, perhitungan total harga). |
| `view` | `PemesananView` | Mengurus tampilan menu dan seluruh input dari pengguna beserta validasinya. |
| `controller` | `PemesananController` | Mengatur alur program, menyimpan `ArrayList<Pemesanan>`, mengisi dummy data, dan mengelola proses CRUD. |

Gambar MVC:

<img width="417" height="317" alt="image" src="https://github.com/user-attachments/assets/66d8f145-e3d9-4a9a-a63e-57558b6c1764" />

### 2. Polymorphism (Method Override)

Method `tampilkanInfo()` didefinisikan pada superclass `Kapal`, lalu **di-override** pada masing-masing subclass agar menampilkan fasilitas yang sesuai.

| Kelas | Letak Method | Hasil Tampilan |
|---|---|---|
| `Kapal` | `model/Kapal.java` | Nama kapal, tujuan, dan harga tiket. |
| `KapalEkonomi` | `model/KapalEkonomi.java` | Nama kapal, tujuan, harga tiket, dan **Fasilitas Ekonomi**. |
| `KapalVIP` | `model/KapalVIP.java` | Nama kapal, tujuan, harga tiket, dan **Fasilitas VIP**. |

Contoh gambar pada `Fasilitas VIP`:

<img width="673" height="142" alt="image" src="https://github.com/user-attachments/assets/b2e9af3d-045a-47e7-bc7f-7f78574d1269" />

Contoh gambar pada `Fasilitas Ekonomi`:

<img width="702" height="141" alt="image" src="https://github.com/user-attachments/assets/bb86fdb9-0372-43e7-91f9-8f67b38e7714" />

**Letak pemanggilan polymorphism:** pada `PemesananView.tampilkanDaftarPemesanan()` terdapat pemanggilan `p.getKapal().tampilkanInfo()`. Tipe variabelnya adalah `Kapal`, tetapi objek yang sebenarnya bisa berupa `KapalVIP` atau `KapalEkonomi`. Java secara otomatis memilih versi `tampilkanInfo()` yang sesuai dengan jenis objek pada saat program berjalan.

Selain itu, method `buatKapal()` pada controller mengembalikan tipe `Kapal` tetapi membuat objek `KapalVIP` atau `KapalEkonomi` (upcasting), sehingga satu `ArrayList<Pemesanan>` dapat menampung berbagai jenis kapal.
