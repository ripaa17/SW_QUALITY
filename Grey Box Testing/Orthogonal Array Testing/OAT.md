# Pengujian Array Ortogonal (OAT) 
  Pengujian Array Ortogonal (OAT)adalah teknik pengujian perangkat lunak yang menggunakan array ortogonal untuk membuat kasus uji. Ini adalah pendekatan
  pengujian statistik yang sangat berguna ketika sistem yang akan diuji memiliki input data yang besar. Pengujian susunan ortogonal membantu memaksimalkan 
  cakupan pengujian dengan memasangkan dan menggabungkan input serta menguji sistem dengan
  jumlah kasus pengujian yang relatif lebih sedikit untuk menghemat waktu.
  
🧩 FAKTOR & LEVEL UNTUK SETIAP FITUR
---
pada tahap ini terdapat beberapa faktor yang akan  diuji dari fitur login, penambahan barang, penambahan user, dan transaksi, yang dimana pengujian ini akan dibagi menjadi 3 level yaitu sebagai berikut :
| **Fitur**             | **Faktor**                     | **Level 1**                             | **Level 2**                         | **Level 3**                    |
|----------------------|--------------------------------|-----------------------------------------|-------------------------------------|-------------------------------|
| **Login**            | Username & Password            | Username dan password valid (terdaftar) | Username salah atau tidak terdaftar | Username atau password kosong |
| **Penambahan Barang**| Nama, Kode, Harga, Jumlah      | Semua input valid dan lengkap           | Harga negatif                       | Jumlah/stok kosong            |
| **Penambahan User**  | Role & Input User              | Role = Admin, data user valid           | Role = Kasir, data user valid       | Role tidak valid atau kosong  |
| **Transaksi**        | Jenis Pembayaran & Jumlah Item | Tunai dengan 1 item                     | Kartu dengan 5 item                 | QRIS dengan lebih dari 10 item|

---
📋 TABEL ORTHOGONAL ARRAY (L9)
berdasarkan faktor dan level pengujian yang sudah dibuat,maka akan dilakukan matriks kasus pengujian dengan 9 kasus uji yaitu sebagai berikut :
| TC   | Login           | Barang          | User             | Transaksi       | Validitas     | Keterangan                                                                 |
|------|------------------|------------------|-------------------|------------------|---------------|----------------------------------------------------------------------------|
| TC1  | Valid            | Lengkap & Valid  | Admin Valid       | Tunai - 1 Item   | ✅ Valid      | Semua input valid dan sesuai aturan sistem                                |
| TC2  | Valid            | Harga Negatif    | Kasir Tanpa Nama  | Kartu - 5 Item   | ✅ Valid      | Diterima jika harga negatif diizinkan untuk uji batas input               |
| TC3  | Valid            | Stok Kosong      | Role Tidak Valid  | QRIS - >10 Item  | ❌ Tidak Valid| Stok habis dan role user tidak valid                                      |
| TC4  | Password Salah   | Lengkap & Valid  | Kasir Tanpa Nama  | QRIS - >10 Item  | ✅ Valid      | Valid jika sistem hanya memperingatkan login tapi tetap proses transaksi  |
| TC5  | Password Salah   | Harga Negatif    | Role Tidak Valid  | Tunai - 1 Item   | ❌ Tidak Valid| Password salah, harga negatif, dan role user tidak sah                    |
| TC6  | Password Salah   | Stok Kosong      | Admin Valid       | Kartu - 5 Item   | ✅ Valid      | Simulasi login gagal, tapi data transaksi dan user masih valid            |
| TC7  | Username Kosong  | Lengkap & Valid  | Role Tidak Valid  | Kartu - 5 Item   | ❌ Tidak Valid| Username kosong dan role tidak sesuai                                     |
| TC8  | Username Kosong  | Harga Negatif    | Admin Valid       | QRIS - >10 Item  | ✅ Valid      | Diterima jika sistem izinkan auto-identifikasi & uji harga negatif        |
| TC9  | Username Kosong  | Stok Kosong      | Kasir Tanpa Nama  | Tunai - 1 Item   | ❌ Tidak Valid| Username kosong dan barang tidak tersedia                                 |

---

| Kolom        | Makna/Penjelasan                                                                 |
|--------------|-----------------------------------------------------------------------------------|
| **Login**    | Status login pengguna: apakah berhasil login atau tidak (misal: username/password salah). |
| **Barang**   | Kondisi data barang yang diuji:                                                  |
|              | - **Lengkap & Valid** → Semua data barang diisi dengan benar.                    |
|              | - **Harga Negatif** → Harga barang bernilai minus (uji validasi input harga).    |
|              | - **Stok Kosong** → Stok barang = 0, menguji respon sistem terhadap stok habis.   |
| **User**     | Role dan data pengguna sistem:                                                    |
|              | - **Admin Valid** → Pengguna admin yang sah.                                     |
|              | - **Kasir Tanpa Nama** → Role kasir, tapi nama tidak diisi.                      |
|              | - **Role Tidak Valid** → Role bukan "admin" atau "kasir", contoh: "tamu", "xxx". |
| **Transaksi**| Simulasi jenis dan jumlah transaksi:                                              |
|              | - **Tunai / Kartu / QRIS** → Metode pembayaran.                                  |
|              | - **1 Item / 5 Item / >10 Item** → Jumlah item dalam transaksi.
----
Dari hasil pengujian sebanyak 9 kasus, ditemukan bahwa 5 kasus berjalan dengan valid dan 4 kasus lainnya tidak valid. Kasus yang valid menunjukkan bahwa sistem mampu menangani data yang benar, termasuk beberapa kondisi khusus seperti harga negatif atau informasi login yang tidak lengkap namun tetap diproses sesuai logika sistem. Sementara itu, kasus yang tidak valid disebabkan oleh beberapa faktor seperti stok barang yang kosong, peran pengguna yang tidak sesuai (misalnya bukan admin atau kasir), serta login dengan username atau password yang salah. Secara keseluruhan, sistem sudah cukup baik dalam menangani skenario dasar, namun tetap perlu diperkuat dengan validasi yang lebih ketat terhadap input harga, role pengguna, data login, dan ketersediaan stok agar transaksi berjalan aman dan sesuai aturan.
