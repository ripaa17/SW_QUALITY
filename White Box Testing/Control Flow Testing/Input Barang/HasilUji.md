
# ✅ Test Case - Halaman Daftar Barang (`barang_list.php`)

Halaman ini menampilkan daftar barang dari database, serta menyediakan aksi untuk tambah, edit, hapus, dan mencetak barcode. Juga terdapat notifikasi `$_SESSION['success']` setelah aksi berhasil dilakukan.

---

## 📌 Tujuan Pengujian
Memastikan seluruh fungsi utama pada halaman daftar barang bekerja dengan baik dan sesuai harapan, termasuk:
- Tabel data barang
- Tombol aksi
- Notifikasi keberhasilan (flash message)
- Konfirmasi hapus

---

## 🧪 Daftar Pengujian

| No | Nama Pengujian          | Kondisi yang Diuji                              | Data Uji                                | Hasil yang Diharapkan                                                                 | Status        |
|----|-------------------------|--------------------------------------------------|-----------------------------------------|----------------------------------------------------------------------------------------|---------------|
| 1  | Tampilkan Flash Success | Setelah berhasil tambah/edit/hapus barang       | `$_SESSION['success'] = 'Data berhasil'` | Pesan alert hijau (`alert-success`) muncul dan menghilang setelah reload               | ✅ Passed      |
| 2  | Tampilkan Daftar Barang | Akses halaman `barang_list.php`                 | -                                       | Tabel muncul berisi data dari database                                                 | ✅ Passed      |
| 3  | Tambah Data Barang      | Klik tombol "Tambah data"                       | -                                       | Dialihkan ke `/barang_add.php`                                                         | ✅ Passed      |
| 4  | Cetak Barcode           | Klik tombol "Cetak Barcode"                     | -                                       | Dialihkan ke `/barang_cetak_barcode.php`                                               | ✅ Passed      |
| 5  | Tampilkan Kolom Tabel   | Tabel memuat kolom ID, Kode, Nama, Harga, Stok  | -                                       | Semua kolom muncul dengan isi data valid                                               | ✅ Passed      |
| 6  | Aksi Edit Barang        | Klik link "Edit"                                | ID Barang: `101`                        | Dialihkan ke `/barang_edit.php?id=101`                                                 | ✅ Passed      |
| 7  | Aksi Hapus Barang       | Klik link "Hapus" dan klik "Ya"                 | ID Barang: `102`                        | Barang terhapus dari database, flash success ditampilkan                               | ✅ Passed      |
| 8  | Konfirmasi Hapus        | Klik link "Hapus"                               | -                                       | Muncul pop-up konfirmasi `apakah anda yakin?` sebelum menghapus                       | ✅ Passed      |
| 9  | Looping Data Berhasil   | Data ditampilkan dengan `while ($view->fetch_array())` | Isi data dari query SQL     | Semua baris ditampilkan tanpa error/terpotong                                          | ✅ Passed      |

---

## 📋 Contoh Output yang Diharapkan

```html
<div class="alert alert-success" role="alert">
    Data berhasil dihapus
</div>
