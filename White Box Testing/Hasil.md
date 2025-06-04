| Bagian | Path | Code | Jalur |
|--------|------|------|-------|
| A | Sudah Login sebagai Admin | ![A1](./patha1.png) | 1. Cek `isset($_SESSION["role"])`<br>2. Jika `true`, cek `role == "Admin"`<br>3. Jika `true`, redirect ke `admin/home.php` |
| A | Sudah Login sebagai User | ![A2](./patha2.png) | 1. Cek `isset($_SESSION["role"])`<br>2. Jika `true`, cek `role == "Admin"`<br>3. Jika `false`, redirect ke `user/lapangan.php` |
| B1 | Login Berhasil sebagai Admin | ![B1](./pathb1.png) | 1. Cek `isset($_POST["login"])`<br>2. Query ke tabel admin<br>3. Jika `$cariadmin == true`, set session<br>4. Redirect ke `admin/admin.php` |
| B2 | Login Berhasil sebagai User | ![B2](./pathb2.png) | 1. Cek `isset($_POST["login"])`<br>2. Query admin → kosong<br>3. Query user → `$cariuser == true`<br>4. Set session dan redirect ke `user/lapangan.php` |
| B3 | Login Gagal | ![B3](./pathb3.png) | 1. Cek `isset($_POST["login"])`<br>2. Query admin dan user keduanya gagal<br>3. Munculkan pesan error & refresh halaman |

Cyclomatic Complexity (V(G))
•	Jumlah simpul (Node) = 7 (cek session, cek role, login check, query admin, query user, cek hasil, error)
•	Jumlah edge = 9 (jalur cabang dan arah)
•	Jumlah komponen terhubung = 1
Rumus: V(G) = E - N + 2P
V(G) = 9 - 7 + 2(1) = 4
Hasil: Ada 4 jalur independen yang perlu diuji (A1, A2, B1, B2, B3 — B3 bisa dikelompokkan sebagai alternatif ke-4).


Kesimpulan
Pengujian Basic Path Testing pada kode kamu bisa dibagi ke 5 jalur eksekusi utama:
| Jalur | Kondisi           | Hasil Diharapkan                     |
|-------|-------------------|--------------------------------------|
| A1    | Session = Admin   | Redirect ke `admin/home.php`         |
| A2    | Session = User    | Redirect ke `user/lapangan.php`      |
| B1    | Login valid admin | Redirect ke `admin/admin.php`        |
| B2    | Login valid user  | Redirect ke `user/lapangan.php`      |
| B3    | Login gagal       | Tampilkan pesan error & refresh page |

![tabel](./tabel.png)
