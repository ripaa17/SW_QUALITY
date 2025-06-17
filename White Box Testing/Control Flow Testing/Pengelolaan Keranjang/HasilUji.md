
# ✅ Test Case - Tambah Barang ke Keranjang (`kasir.php`)

Kode ini berfungsi untuk menambahkan barang berdasarkan `kode_barang` ke keranjang belanja (disimpan di dalam `$_SESSION['cart']`). Jika barang sudah ada, maka jumlah akan ditambah dan diskon dihitung jika memenuhi syarat.

---

## 📌 Tujuan Pengujian
- Memastikan barang bisa ditambahkan ke keranjang dengan benar.
- Menambahkan jumlah barang jika barang sudah ada dalam keranjang.
- Menghitung diskon jika syarat minimum kuantitas tercapai.

---

## 🧪 Daftar Pengujian

| No | Nama Pengujian                    | Kondisi yang Diuji                                                             | Data Uji                  | Hasil yang Diharapkan                                                                                     | Status        |
|----|----------------------------------|--------------------------------------------------------------------------------|---------------------------|------------------------------------------------------------------------------------------------------------|---------------|
| 1  | Tambah Barang Baru ke Keranjang | Kirim kode barang via POST                                                    | `kode_barang = B001`      | Barang `B001` masuk ke `$_SESSION['cart']` dengan qty = 1 dan diskon = 0                                  | ✅ Passed      |
| 2  | Tambah Barang yang Sudah Ada    | Kirim kembali kode barang yang sudah ada di keranjang                         | `kode_barang = B001` lagi | Qty barang bertambah (qty += 1)                                                                           | ✅ Passed      |
| 3  | Hitung Diskon Sesuai Qty        | Barang diskon dengan minimum qty 3 dan diskon Rp 1000 per 3 item               | qty = 6                   | Diskon menjadi 2 × 1000 = Rp 2000                                                                         | ✅ Passed      |
| 4  | Tidak Ada Diskon                | Barang tidak memiliki diskon                                                  | Barang tanpa diskon       | Diskon tetap 0 meskipun qty bertambah                                                                     | ✅ Passed      |
| 5  | Validasi Barang Tidak Ada       | Kirim kode barang yang tidak ada di database                                  | `kode_barang = XYZ999`    | Tidak terjadi error, tidak ada barang ditambahkan, atau redirect ke `kasir.php` dengan aman               | ✅ Passed      |
| 6  | Validasi Array Key              | Barang sudah ada di keranjang, diuji dengan `array_search` pada `$_SESSION`   | Key ditemukan             | Index barang berhasil ditemukan dan qty berhasil diupdate                                                | ✅ Passed      |
| 7  | Cek Kelipatan Diskon            | Barang diskon dengan minimum qty 3, beli 7 unit                                | qty = 7                   | Diskon hanya diberikan untuk 6 barang (kelipatan 3), yaitu 2 × potongan                                   | ✅ Passed      |
| 8  | Redirect Setelah Input          | Setelah semua proses, sistem redirect ke halaman kasir                        | `header('location:kasir.php')` | Pengguna diarahkan kembali ke halaman `kasir.php` setelah menambahkan barang                           | ✅ Passed      |

---

## 💻 Contoh Struktur `$_SESSION['cart']`

```php
[
  [
    'id' => 1,
    'nama' => 'Pulpen',
    'harga' => 3000,
    'qty' => 3,
    'diskon' => 1000
  ],
  [
    'id' => 2,
    'nama' => 'Buku',
    'harga' => 10000,
    'qty' => 1,
    'diskon' => 0
  ]
]
