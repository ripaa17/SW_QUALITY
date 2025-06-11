# Pengujian Regression Testing
Pengujian **Regression Testing** dilakukan setelah perbaikan bug dan gangguan pada konfigurasi **XAMPP**, yang sebelumnya menyebabkan fitur **Cetak Barcode** pada halaman **List Barang** tidak dapat berfungsi dengan semestinya setelah proses penambahan data barang baru pada aplikasi web kasir.

## Langkah-Langkah Pengujian
1. Memastikan XAMPP sudah berjalan normal (Apache dan MySQL aktif).
2. pada XAMPP klik config lalu klik php.ini
3. pada file php.ini hapus semua tanda (;) sebelum kata Extention lalu save
5. Melakukan login ke aplikasi web kasir.
6. Menambahkan data barang baru melalui fitur *Tambah Barang*.
7. Menavigasi ke menu **List Barang**.
8. Memastikan tombol atau opsi **Cetak Barcode** muncul pada data barang yang baru ditambahkan.
9. Melakukan klik pada opsi **Cetak Barcode**.
10. Memverifikasi hasil cetakan barcode muncul sesuai data barang yang ditambahkan.

## Hasil Pengujian
- **Status:** Berhasil
- **Bug Terdeteksi:** Tidak ada
- **Catatan:** Setelah perbaikan bug pada XAMPP, fitur Cetak Barcode dapat berjalan normal dan sesuai harapan.

## Kesimpulan
Berdasarkan hasil pengujian, seluruh tahapan berjalan dengan baik tanpa ditemukannya bug baru. Setelah konfigurasi pada file `php.ini` di XAMPP diperbaiki (dengan mengaktifkan seluruh ekstensi PHP yang diperlukan atau menghapus tanda `;` pada file `php.ini`), fitur **Cetak Barcode** kembali berjalan normal. Perbaikan ini mengembalikan fungsionalitas sistem sesuai spesifikasi yang diharapkan, serta memastikan stabilitas aplikasi pasca penambahan item baru di dalam database.
