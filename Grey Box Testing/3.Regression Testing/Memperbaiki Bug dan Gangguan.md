# Pengujian Regression Testing
Pengujian dilakukan untuk memastikan bahwa perbaikan bug dan gangguan pada XAMPP berhasil memungkinkan sistem menampilkan **Cetak Barcode** pada fitur **List Barang** setelah proses penambahan data barang pada aplikasi web kasir.

## Langkah-Langkah Pengujian
1. Memastikan XAMPP sudah berjalan normal (Apache dan MySQL aktif).
2. Melakukan login ke aplikasi web kasir.
3. Menambahkan data barang baru melalui fitur *Tambah Barang*.
4. Menavigasi ke menu **List Barang**.
5. Memastikan tombol atau opsi **Cetak Barcode** muncul pada data barang yang baru ditambahkan.
6. Melakukan klik pada opsi **Cetak Barcode**.
7. Memverifikasi hasil cetakan barcode muncul sesuai data barang yang ditambahkan.

## Hasil Pengujian
- **Status:** Berhasil
- **Bug Terdeteksi:** Tidak ada
- **Catatan:** Setelah perbaikan bug pada XAMPP, fitur Cetak Barcode dapat berjalan normal dan sesuai harapan.

## Kesimpulan
Perbaikan bug dan gangguan pada XAMPP berhasil memperbaiki masalah sebelumnya. Fitur **Cetak Barcode** kini dapat diakses dan berfungsi dengan baik pada halaman **List Barang** setelah penambahan data barang baru.


# Dokumentasi Regression Testing: Perbaikan Fitur Cetak Barcode

Pengujian **Regression Testing** dilakukan setelah perbaikan bug dan gangguan pada konfigurasi **XAMPP**, yang sebelumnya menyebabkan fitur **Cetak Barcode** pada halaman **List Barang** tidak dapat berfungsi dengan semestinya setelah proses penambahan data barang baru.

Proses pengujian dimulai dengan memastikan environment berjalan stabil, yaitu layanan **Apache** dan **MySQL** pada XAMPP sudah aktif. Setelah aplikasi berjalan, pengujian dilanjutkan dengan login ke aplikasi web kasir dan melakukan penambahan data barang melalui fitur **Tambah Barang**.

Setelah data barang baru berhasil ditambahkan, penguji mengakses menu **List Barang** untuk melakukan validasi apakah tombol **Cetak Barcode** muncul sesuai dengan item yang baru saja ditambahkan. Penguji kemudian menekan tombol **Cetak Barcode** dan memverifikasi bahwa hasil cetakan barcode sesuai dengan data yang diinputkan sebelumnya.

Berdasarkan hasil pengujian, seluruh tahapan berjalan dengan baik tanpa ditemukannya bug baru. Setelah konfigurasi pada file `php.ini` di XAMPP diperbaiki (dengan mengaktifkan seluruh ekstensi PHP yang diperlukan atau menghapus tanda `;` pada file `php.ini`), fitur **Cetak Barcode** kembali berjalan normal. Perbaikan ini mengembalikan fungsionalitas sistem sesuai spesifikasi yang diharapkan, serta memastikan stabilitas aplikasi pasca penambahan item baru di dalam database.
