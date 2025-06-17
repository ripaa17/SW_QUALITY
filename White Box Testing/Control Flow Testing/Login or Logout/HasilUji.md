# ✅ Test Case - Modul Login, Logout & Daftar Barang

Dokumen ini mencatat hasil pengujian dari halaman login, logout, serta daftar barang dalam sistem manajemen data berbasis PHP + Bootstrap.

---

## 📌 Modul yang Diuji

- Login (`login.php`)
- Logout (`logout.php`)
- Daftar Barang (`barang_list.php`)
- Notifikasi Flash (`$_SESSION['error']`, `$_SESSION['success']`)

---

## 🧪 Daftar Test Case

### 🔐 Login

| No | Nama Pengujian          | Kondisi yang Diuji                     | Data Uji                                   | Hasil yang Diharapkan                                                                   | Status        |
|----|-------------------------|----------------------------------------|--------------------------------------------|------------------------------------------------------------------------------------------|---------------|
| 1  | Tampilkan Form Login    | Akses `login.php`                      | -                                          | Form login tampil lengkap (username, password, tombol, checkbox "Sudah")                | ✅ Passed      |
| 2  | Spinner Loading         | Saat halaman dimuat                    | -                                          | Spinner muncul selama 2.5 detik lalu hilang                                              | ✅ Passed      |
| 3  | Login Gagal             | Akun salah                             | Username: `salah` <br>Password: `salah123` | Muncul pesan alert merah dari `$_SESSION['error']`, lalu dikosongkan setelah tampil     | ✅ Passed      |
| 4  | Login Berhasil          | Akun valid                             | Username: `admin` <br>Password: `admin123` | Redirect ke halaman daftar barang (dashboard)                                            | ⚠️ Belum Diuji Backend |
| 5  | Username Kosong         | Username dikosongkan                   | Username: *(kosong)* <br> Password: `xxx`  | Muncul validasi input kosong *(tidak ada validasi saat ini)*                             | ⚠️ Perlu Validasi |
| 6  | Password Kosong         | Password dikosongkan                   | Username: `xxx` <br> Password: *(kosong)*  | Muncul validasi input kosong *(tidak ada validasi saat ini)*                             | ⚠️ Perlu Validasi |
| 7  | Checkbox “Sudah”        | Checkbox tampil                        | -                                          | Checkbox dengan label “Sudah” tampil                                                    | ✅ Passed      |

---

### 🚪 Logout

| No | Nama Pengujian          | Kondisi yang Diuji     | Data Uji         | Hasil yang Diharapkan                                  | Status    |
|----|-------------------------|------------------------|------------------|--------------------------------------------------------|-----------|
| 1  | Logout dari sistem      | Klik `logout.php`      | -                | Session dihapus, redirect ke login                     | ✅ Passed  |
| 2  | Akses halaman setelah logout | Setelah logout akses `barang_list.php` | - | Dialihkan kembali ke halaman login (jika ada session check) | ⚠️ Cek Session |

---

### 📦 Daftar Barang

| No | Nama Pengujian          | Kondisi yang Diuji                     | Data Uji                             | Hasil yang Diharapkan                                                                | Status    |
|----|-------------------------|----------------------------------------|--------------------------------------|---------------------------------------------------------------------------------------|-----------|
| 1  | Tampilkan Tabel Barang  | Akses `barang_list.php`               | -                                    | Semua data barang tampil dalam tabel                                                 | ✅ Passed  |
| 2  | Flash Success Message   | Setelah tambah/edit/hapus barang      | `$_SESSION['success'] = 'Data berhasil'` | Muncul alert hijau lalu tidak tampil ulang setelah reload                        | ✅ Passed  |
| 3  | Tombol Tambah Barang    | Klik tombol "Tambah data"             | -                                    | Redirect ke `/barang_add.php`                                                        | ✅ Passed  |
| 4  | Tombol Cetak Barcode    | Klik tombol "Cetak Barcode"           | -                                    | Redirect ke `/barang_cetak_barcode.php`                                              | ✅ Passed  |
| 5  | Aksi Edit Barang        | Klik link "Edit"                      | ID barang: `102`                     | Redirect ke `/barang_edit.php?id=102`                                                | ✅ Passed  |
| 6  | Aksi Hapus Barang       | Klik link "Hapus" dan konfirmasi "ya" | ID barang: `102`                     | Barang terhapus dari database, muncul pesan sukses                                   | ✅ Passed  |
| 7  | Konfirmasi Saat Hapus   | Klik link "Hapus"                     | -                                    | Muncul popup JavaScript `confirm("apakah anda yakin?")`                              | ✅ Passed  |

---

## 🔧 Rekomendasi Pengembangan

- Tambahkan validasi `required` di input login (HTML atau JavaScript).
- Terapkan sistem hash password dan prepared statements di backend.
- Tambahkan fitur pencarian & pagination di daftar barang.
- Pastikan semua aksi (edit, hapus) terlindungi dari akses tanpa login (session check).
- Tambahkan fitur logout otomatis jika session timeout.

---

## 📎 Keterangan

- Framework UI: Bootstrap 4.5
- Bahasa: PHP (native, procedural)
- Penanganan sesi: menggunakan `$_SESSION` untuk notifikasi

---
