# Pengujian Array Ortogonal (OAT) 
  Pengujian Array Ortogonal (OAT)adalah teknik pengujian perangkat lunak yang menggunakan array ortogonal untuk membuat kasus uji. Ini adalah pendekatan
  pengujian statistik yang sangat berguna ketika sistem yang akan diuji memiliki input data yang besar. Pengujian susunan ortogonal membantu memaksimalkan 
  cakupan pengujian dengan memasangkan dan menggabungkan input serta menguji sistem dengan
  jumlah kasus pengujian yang relatif lebih sedikit untuk menghemat waktu.
   
🧩 FAKTOR & LEVEL UNTUK SETIAP FITUR
--
pada tahap ini terdapat beberapa faktor yang akan  diuji dari fitur login, penambahan barang, penambahan user, dan transaksi.
---
# 🧪 Orthogonal Array Testing (OAT) – Faktor & Level

Dokumen ini berisi daftar **faktor dan level** dari 4 fitur yang diuji dalam sistem: **Login, Penambahan Barang, Penambahan User, dan Pembayaran Transaksi**. Teknik pengujian menggunakan pendekatan **Orthogonal Array (OAT)** untuk efisiensi pengujian kombinatorial.

---

## 🔐 Fitur Login

| Faktor     | Level 1 | Level 2 | Level 3               |
|------------|---------|---------|------------------------|
| Username   | Valid   | Salah   | Kosong                 |
| Password   | Valid   | Salah   | Kosong                 |
| Role       | Admin   | Kasir   | Tidak Diisi / Kosong   |

---

## 📦 Fitur Penambahan Barang

| Faktor         | Level 1         | Level 2         | Level 3             |
|----------------|------------------|------------------|----------------------|
| Kode Barang     | Unik (Valid)     | Duplikat         | Kosong               |
| Nama Barang     | Valid            | Kosong           | Karakter khusus      |
| Harga           | Valid (> 0)      | Nol (0)          | Negatif              |
| Jumlah Stok     | Valid (> 0)      | Nol (0)          | Negatif              |

---

## 👤 Fitur Penambahan User

| Faktor     | Level 1   | Level 2     | Level 3                  |
|------------|------------|-------------|---------------------------|
| Username   | Unik       | Sudah Ada   | Kosong                    |
| Password   | Valid      | Kosong      | Pendek (<6 karakter)     |
| Role Akses | Admin      | Kasir       | Tidak Diisi / Kosong      |

---

## 💳 Fitur Pembayaran Transaksi

| Faktor              | Level 1           | Level 2           | Level 3               |
|---------------------|--------------------|--------------------|------------------------|
| Qty (Jumlah Beli)   | Valid (> 0)        | Nol (0)            | Negatif (-1)          |
| Bayar (Uang Masuk)  | Cukup              | Tidak Cukup        | Tidak Valid (Non-angka)|
| Harga Barang        | Valid (> 0)        | Nol (0)            | Negatif               |
| Total Harga         | Sesuai Perhitungan | Tidak Sesuai       | Kosong                |

---

> 📝 **Catatan Umum:**
> - Pengujian dengan array ortogonal memungkinkan cakupan kombinasi yang efisien dan mewakili semua pasangan penting antar faktor.
> - Cocok diterapkan untuk sistem dengan banyak input kombinasi.
> - Dapat dikembangkan lebih lanjut untuk L9, L27, atau bentuk array lainnya sesuai jumlah faktor dan level.

---


## ✅ Tabel Pengujian Login (Implementasi OAT)

| TC   | Username   | Password   | Role     | Hasil yang Diharapkan                                      | Status |
|------|------------|------------|----------|-------------------------------------------------------------|--------|
| TC1  | Eva        | 123456     | Admin    | Login berhasil ke dashboard admin                           | ✅     |
| TC2  | Eva        | salahpw    | Kasir    | Gagal login: "Username dan Password salah"                  | ✅     |
| TC3  | Eva        | (kosong)   | (kosong) | Gagal login: "Username dan Password salah"                  | ✅     |
| TC4  | Eeva       | 123456     | Kasir    | Gagal login: "Username dan Password salah"                  | ✅     |
| TC5  | Eeva       | salahpw    | (kosong) | Gagal login: "Username dan Password salah"                  | ✅     |
| TC6  | Eeva       | (kosong)   | Admin    | Gagal login: "Username dan Password salah"                  | ✅     |
| TC7  | (kosong)   | 123456     | (kosong) | Gagal login: "Username dan Password salah"                  | ✅     |
| TC8  | (kosong)   | salahpw    | Admin    | Gagal login: "Username dan Password salah"                  | ✅     |
| TC9  | (kosong)   | (kosong)   | Kasir    | Gagal login: "Username dan Password salah"                  | ✅     |

---

## 📝 Catatan

- **Metode:** Orthogonal Array Testing menggunakan array **L9**.
- **Faktor diuji:** `Username`, `Password`, dan `Role`.
- **Tujuan:** Mengurangi jumlah test case sambil tetap mencakup semua kombinasi *pairwise* yang penting.
- **Efisiensi:** Dari 27 kombinasi (3×3×3), hanya diuji 9 kombinasi mewakili cakupan maksimum.
- **Hasil:** Semua test case berjalan sesuai ekspektasi. Validasi input login berfungsi dengan baik.

---
### Pengujian Pada Penambahan Barang
| TC  | Kode   | Nama               | Harga  | Jumlah Stok | Hasil yang Diharapkan           | Status |
|-----|--------|--------------------|--------|-------------|--------------------------------|--------|
| TC1 | B0059  | Bola Basket Besar  | 60000  | 10          | Berhasil tambah barang (valid) | ✅     |
| TC2 | B0055  | Sabun Mandi        | 2500   | 10          | Berhasil tambah barang (valid) | ✅     |
| TC3 | B0054  | Pasta Gigi         | 2000   | 20          | Berhasil tambah barang (valid) | ✅     |
| TC4 | B0053  | Sampoo Botol 350ml | 16000  | 10          | Berhasil tambah barang (valid) | ✅     |
| TC5 | B0056  | Balsem             | 5000   | 10          | Berhasil tambah barang (valid) | ✅     |
| TC6 | B0052  | Sapu Lidi          | 10000  | 10          | Berhasil tambah barang (valid) | ✅     |
| TC7 | B0051  | Sandal             | 12000  | 10          | Berhasil tambah barang (valid) | ✅     |
| TC8 | B0040  | Minyak             | 22000  | 10          | Berhasil tambah barang (valid) | ✅     |
| TC9 | B0088  | Salak Buah         | 5000   | 10          | Berhasil tambah barang (valid) | ✅     |
---
Total Pengujian: 9
Berhasil (✅): 9
Gagal (❌): 0
Catatan:
Dari 9 pengujian yang dilakukan dengan data valid, seluruhnya berhasil ✅. Hal ini menunjukkan bahwa sistem dapat menambahkan barang dengan benar saat input sesuai. Untuk memastikan sistem lebih kuat, pengujian dengan data tidak valid (seperti kode duplikat, harga nol, atau nama kosong) juga perlu dilakukan.
--
### Tabel Pengujian Pada Penambahan User
| TC  | Username | Password | Role Akses | Hasil yang Diharapkan                                     | Status |
|-----|----------|----------|-------------|------------------------------------------------------------|--------|
| TC1 | Eva      | 123456   | Admin       | Berhasil login dan masuk ke dashboard Admin                | ✅     |
| TC2 | Eva      | 098765   | Admin       | Gagal login (password salah)                               | ✅     |
| TC3 | Eva      | 123456   | Kasir       | Gagal login (role tidak sesuai)                            | ✅     |
| TC4 | Dede     | 098765   | Kasir       | Berhasil login dan masuk ke halaman transaksi Kasir        | ✅     |
| TC5 | Dede     | 121212   | Kasir       | Gagal login (password salah)                               | ✅     |
| TC6 | Dede     | 098765   | Admin       | Gagal login (role tidak sesuai)                            | ✅     |
| TC7 | Rahma    | 121212   | Kasir       | Berhasil login dan masuk ke halaman transaksi Kasir        | ✅     |
| TC8 | Rahma    | 123456   | Kasir       | Gagal login (password salah)                               | ✅     |
| TC9 | Rahma    | 121212   | Admin       | Gagal login (role tidak sesuai)                            | ✅     |

---
Total Pengujian: 9
Berhasil (✅): 9
Gagal (❌): 0

Catatan:
Semua test case login berdasarkan kombinasi username, password, dan role berhasil tervalidasi sesuai ekspektasi.
--
### Tabel Pengujian Fitur Pembayaran Transaksi
| TC  | Kode   | Nama Barang         | Harga  | Qty | Total   | Bayar   | Kembalian yang Diharapkan | Hasil yang Diharapkan           | Status |
|-----|--------|---------------------|--------|-----|---------|---------|-----------------------------|----------------------------------|--------|
| TC1 | B0059  | Bola Basket Besar   | 60000  | 1   | 60000   | 70000   | 10000                       | Transaksi berhasil              | ✅     |
| TC2 | B0055  | Sabun Mandi         | 2500   | 1   | 2500    | 2500    | 0                           | Transaksi berhasil              | ✅     |
| TC3 | B0054  | Pasta Gigi          | 2000   | 1   | 2000    | 5000    | 3000                        | Transaksi berhasil              | ✅     |
| TC4 | B0053  | Sampoo Botol 350ml  | 16000  | 1   | 16000   | 20000   | 4000                        | Transaksi berhasil              | ✅     |
| TC5 | B0056  | Balsem              | 5000   | 1   | 5000    | 4000    | -                           | Gagal: Uang bayar tidak cukup   | ✅     |
| TC6 | B0052  | Sapu Lidi           | 10000  | 0   | 0       | 10000   | -                           | Gagal: Qty tidak boleh 0        | ✅     |
| TC7 | B0051  | Sandal              | 12000  | -1  | -12000  | 12000   | -                           | Gagal: Qty tidak valid          | ✅     |
| TC8 | B0040  | Minyak              | 22000  | 1   | 22000   | abc     | -                           | Gagal: Input bayar tidak valid  | ✅     |
| TC9 | B0088  | Salak Buah          | 5000   | 1   | 5000    | 5000    | 0                           | Transaksi berhasil              | ✅     |
---
Dari 9 test case yang diuji, sistem berhasil menangani berbagai kondisi transaksi dengan baik, termasuk pembayaran yang cukup, kembalian, dan validasi input. Semua skenario berjalan sesuai harapan dengan hasil 100% berhasil (✅ semua). Fitur pembayaran dinyatakan berfungsi dengan baik dan stabil.
