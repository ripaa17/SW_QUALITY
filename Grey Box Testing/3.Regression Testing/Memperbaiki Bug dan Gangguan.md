# Pengujian Regression Testing
Gray Box Testing juga mengalami Bug dan Gangguan pada Penambahan barang, tetapi barang sudah bisa ditambahkan dan ada pada list barang namun ada warning ketika barang sudah ditambahkan ke list barang
## 🧪 Regression Testing – Fitur Penambahan Barang

| No | Langkah Uji                                         | Deskripsi                                              | Hasil Sebelum Perbaikan                     | Hasil Setelah Perbaikan                     |
|----|-----------------------------------------------------|--------------------------------------------------------|---------------------------------------------|---------------------------------------------|
| 1  | Akses halaman tambah barang                         | Klik menu **Barang > Tambah Barang**                  | Form tampil, tetapi error saat submit       | ✅ Form tampil tanpa error                  |
| 2  | Submit form dengan data lengkap                     | Isi semua field: Nama, Kode, Harga, Jumlah            | 🔴 Gagal simpan, muncul warning `headers sent` | ✅ Data berhasil disimpan ke database       |
| 3  | Periksa isi database setelah submit                 | Cek tabel `barang` di database                        | ❌ Tidak ada data baru                      | ✅ Data baru muncul di tabel                |
| 4  | Redirect setelah berhasil simpan                    | Harus diarahkan ke daftar barang / tampil alert       | ❌ Tidak redirect (karena error header)      | ✅ Redirect ke halaman list barang       

Pada tabel diatas adalah pengujian grey box testing yang sudah dilakukan dengan 4 langkah uji sehingga hasilnya valid.



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
