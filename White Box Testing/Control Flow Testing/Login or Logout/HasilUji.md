# ✅ Test Case - Halaman Login (`login.php`)

Halaman ini mendokumentasikan hasil pengujian dari halaman login yang dibuat dengan HTML, PHP, dan Bootstrap, termasuk fitur spinner loading dan validasi awal.

---

## 📌 Tujuan
Melakukan pengujian pada halaman login untuk memastikan fungsi form, interaksi pengguna, tampilan, dan feedback error berjalan sebagaimana mestinya.

---

## 🧪 Daftar Test Case

| No | Nama Pengujian            | Kondisi yang Diuji                     | Data Uji                                     | Hasil yang Diharapkan                                                              | Status        |
|----|---------------------------|----------------------------------------|----------------------------------------------|-------------------------------------------------------------------------------------|---------------|
| 1  | Tampil Form Login         | Akses halaman `login.php`              | -                                            | Form login tampil dengan field Username, Password, checkbox, dan tombol Sign In     | ✅ Passed      |
| 2  | Spinner Loading           | Saat halaman dimuat                    | -                                            | Spinner muncul selama 2.5 detik, kemudian hilang otomatis                           | ✅ Passed      |
| 3  | Username Kosong           | Input kosong pada field username       | Username: *(kosong)* <br> Password: `admin`  | Muncul pesan bahwa username harus diisi *(belum tersedia)*                          | ⚠️ Perlu Validasi |
| 4  | Password Kosong           | Input kosong pada field password       | Username: `admin` <br> Password: *(kosong)*  | Muncul pesan bahwa password harus diisi *(belum tersedia)*                          | ⚠️ Perlu Validasi |
| 5  | Login Gagal               | Username/password salah                | Username: `salah` <br> Password: `salah123`  | Alert merah muncul dengan pesan dari `$_SESSION['error']`                           | ✅ Passed      |
| 6  | Login Berhasil            | Username/password benar (valid)        | Username: `admin` <br> Password: `admin123`  | Berhasil login dan redirect ke dashboard (tidak dapat diuji tanpa backend)          | ⚠️ Belum Diuji |
| 7  | Checkbox "Sudah"          | Checkbox muncul di form login          | -                                            | Checkbox dengan label “Sudah” tampil di bawah input password                        | ✅ Passed      |
| 8  | Reset Error Session       | Uji `$_SESSION['error']` setelah gagal | Dua kali login gagal                         | Pesan error hanya muncul sekali, lalu `$_SESSION['error']` dikosongkan              | ✅ Passed      |

---

## 💬 Catatan Tambahan

- Spinner loading menggunakan JavaScript `setTimeout` selama 2,5 detik.
- Error login ditangani oleh PHP menggunakan `$_SESSION['error']`.
- Tidak ada validasi input kosong di sisi klien (JavaScript atau HTML5).
- Desain mengikuti tema dark dari Bootstrap 4.5.

---

## 🔧 Rekomendasi Perbaikan

- Tambahkan validasi `required` pada input username dan password.
- Gunakan JavaScript untuk memvalidasi form sebelum dikirim ke server.
- Pastikan login backend menggunakan hashing password dan prepared statement.
- Terapkan sistem keamanan tambahan seperti CAPTCHA dan limit login attempt.

---
