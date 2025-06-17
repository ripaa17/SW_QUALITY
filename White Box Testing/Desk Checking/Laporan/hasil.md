# ✅ Hasil Uji (Test Case) - Proses Transaksi Penjualan

## 📄 Deskripsi
Pengujian proses transaksi yang mencakup penyimpanan data transaksi dan detailnya ke dalam database serta penghitungan otomatis uang kembali menggunakan metode desk checking.

---

## ⚙️ Lingkungan Uji
- Bahasa: PHP
- Database: MySQL
- Fitur: Transaksi Penjualan
- File Terkait: `proses_transaksi.php`

---

## ✅ Test Case 1 - Transaksi Sukses

**Input:**
- Session User: `nama = kasir1`
- Session Cart:
  ```php
  $_SESSION['cart'] = [
    ['id' => 1, 'harga' => 10000, 'qty' => 2, 'diskon' => 0],
    ['id' => 2, 'harga' => 5000, 'qty' => 1, 'diskon' => 0]
  ];

