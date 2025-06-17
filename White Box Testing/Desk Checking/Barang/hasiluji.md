# ✅ Desk Checking Test Case - Halaman Login (`login.php`)

Dokumen ini digunakan untuk mendokumentasikan hasil uji login sistem secara manual menggunakan metode *desk checking*. Metode ini digunakan untuk mengecek logika program, alur input-output, serta respon sistem terhadap berbagai jenis data uji **tanpa dieksekusi langsung**.

---

## 📌 Tujuan Pengujian

- Memverifikasi apakah login berhasil saat kredensial valid.
- Memastikan pesan error muncul saat username atau password salah.
- Memastikan *session* terset dengan benar saat login sukses.
- Mengecek apakah pengguna diarahkan ke `index.php` setelah login sukses.
- Memastikan keamanan dasar (SQL Injection belum ditangani → catatan).

---

## 🧪 Daftar Pengujian

| No | Kasus Uji                         | Input                               | Ekspektasi Output                                                   | Status |
|----|----------------------------------|-------------------------------------|----------------------------------------------------------------------|--------|
| 1  | Login Berhasil                   | username: `admin`, password: `123`  | Redirect ke `index.php`, session `userid`, `nama`, `role_id` aktif | ✅     |
| 2  | Username Salah                   | username: `salah`, password: `123`  | Tampil: `Username & password salah`                                 | ✅     |
| 3  | Password Salah                   | username: `admin`, password: `xxx`  | Tampil: `Username & password salah`                                 | ✅     |
| 4  | Input Kosong                     | username: ``, password: ``          | Tampil: `Username & password salah` (tanpa validasi input kosong)   | ⚠️     |
| 5  | SQL Injection Attempt            | username: `' OR 1=1--`, password: `x`| Login berhasil (karena raw query) → harusnya ditolak!               | ❌     |
| 6  | Session Error Cleared            | Login gagal, lalu login benar       | Setelah gagal login, pesan error hilang setelah reload              | ✅     |
| 7  | Loading Overlay Berfungsi        | Halaman ditampilkan                 | Spinner muncul 2.5 detik, lalu menghilang otomatis                  | ✅     |
| 8  | Password Tidak Ter-enkripsi      | Database menyimpan plaintext password| Data tidak dienkripsi → risiko keamanan tinggi                      | ❌     |

---

## 🔍 Desk Checking Step-by-Step (Login Berhasil)

1. **User Input**:
   - Username: `admin`
   - Password: `123`

2. **Alur Program**:
   - Mengecek `isset($_POST['masuk'])`
   - `$_POST['username'] = 'admin'`, `$_POST['password'] = '123'`
   - Query: `SELECT * FROM user WHERE username='admin' AND password='123'`
   - Jika ditemukan (`mysqli_num_rows > 0`)
     - Ambil data: `id_user`, `nama`, `role_id`
     - Simpan ke session
     - Redirect ke `index.php`

3. **Ekspektasi**:
   - Session `$_SESSION['userid']` diset
   - Tidak muncul pesan error
   - Halaman dialihkan ke `index.php`

✅ **Lolos desk checking**

---

## 🛠 Catatan & Saran Perbaikan

| Area | Masalah | Saran |
|------|---------|-------|
| Keamanan | Password dalam query SQL langsung | Gunakan `password_hash()` dan `password_verify()` |
| SQL Injection | Tidak ada sanitasi input | Gunakan *prepared statements* (mysqli `prepare()`) |
| Validasi | Input kosong tidak divalidasi | Tambahkan validasi `if (empty(...))` |
| UX | Tidak ada "lupa password" atau feedback login sukses | Tambahkan fitur & notifikasi yang sesuai |
| UX | Checkbox "remember me" tidak ada fungsinya | Tambahkan logika atau hapus jika tidak digunakan |

---
