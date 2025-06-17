# ✅ Test Case - Proses Transaksi Penjualan (`transaksi_proses.php`)

Kode ini menangani proses akhir transaksi penjualan di aplikasi kasir. Setelah pengguna menekan tombol "Bayar", data keranjang akan disimpan ke dalam tabel `transaksi` dan `transaksi_detail`, lalu diarahkan ke halaman transaksi selesai.

---

## 📌 Tujuan Pengujian
- Menyimpan data transaksi dan detail barang ke database.
- Menghitung kembalian dari pembayaran.
- Menghapus isi keranjang (`$_SESSION['cart']`).
- Redirect ke halaman transaksi selesai dengan parameter `idtrx`.

---

## 🧪 Daftar Pengujian

| No | Nama Pengujian                     | Kondisi yang Diuji                                                                 | Data Uji                                    | Hasil yang Diharapkan                                                                                                                                     | Status        |
|----|-----------------------------------|------------------------------------------------------------------------------------|---------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| 1  | Simpan Transaksi Utama           | Proses penyimpanan data ke tabel `transaksi`                                       | `total=30000`, `bayar=50000`                | Data tersimpan dengan benar di tabel `transaksi` dengan nilai `kembali = 20000`                                                                            | ✅ Passed      |
| 2  | Simpan Detail Transaksi          | Setiap barang dalam `$_SESSION['cart']` disimpan ke tabel `transaksi_detail`       | 2 item di keranjang                         | Semua item tersimpan di `transaksi_detail` dengan perhitungan `total = harga * qty` dan `diskon` sesuai                                                    | ✅ Passed      |
| 3  | Hitung Kembalian                 | Bayar > Total, selisih menjadi `kembali`                                           | bayar = 100000, total = 85000               | Nilai kembalian = 15000                                                                                                                                   | ✅ Passed      |
| 4  | Nominal dengan Format Rupiah     | Input dengan format `Rp 50.000` dibersihkan menjadi angka murni                    | bayar = `Rp 50.000`                         | Nilai bayar disimpan sebagai `50000`                                                                                                                       | ✅ Passed      |
| 5  | Kosongkan Keranjang              | Setelah transaksi berhasil                                                         | `$_SESSION['cart']` ada isinya              | Isi `$_SESSION['cart']` menjadi array kosong                                                                                                               | ✅ Passed      |
| 6  | Redirect Setelah Transaksi       | Setelah semua proses selesai                                                       | -                                           | Halaman dialihkan ke `transaksi_selesai.php?idtrx=<id_transaksi>`                                                                                          | ✅ Passed      |
| 7  | ID Transaksi Tersimpan Otomatis  | Ambil ID transaksi dari `mysqli_insert_id` setelah insert ke `transaksi`           | -                                           | `id_transaksi` valid dan digunakan untuk menyimpan ke tabel `transaksi_detail`                                                                            | ✅ Passed      |
| 8  | Penanganan Banyak Barang         | Transaksi dengan 10 barang dalam keranjang                                         | 10 item dalam session                       | Semua 10 item tersimpan ke `transaksi_detail`                                                                                                              | ✅ Passed      |
| 9  | Transaksi Tanpa Login Kasir      | Session tidak berisi data login                                                    | Kosongkan `$_SESSION['nama']`               | Sistem diarahkan ke halaman login atau error tertangani (tergantung implementasi di `authcheckkasir.php`)                                                  | ⚠️ Tergantung Implementasi |

---

## 💾 Contoh Data Tabel

### `transaksi`

| id_transaksi | tanggal_waktu       | nomor   | total | nama      | bayar | kembali |
|--------------|---------------------|---------|-------|-----------|-------|---------|
| 17           | 2025-06-17 22:15:12 | 685493  | 30000 | kasir1    | 50000 | 20000   |

### `transaksi_detail`

| id_transaksi_detail | id_transaksi | id_barang | harga | qty | total | diskon |
|---------------------|--------------|-----------|-------|-----|--------|--------|
| 201                 | 17           | 4         | 5000  | 2   | 10000 | 0      |
| 202                 | 17           | 7         | 10000 | 2   | 20000 | 0      |

---

## 💡 Saran Perbaikan

- Validasi jumlah bayar < total (jika perlu).
- Gunakan prepared statements untuk keamanan dari SQL Injection.
- Simpan detail nama kasir dari session dengan validasi keamanan.
- Tampilkan flash message atau halaman sukses setelah redirect ke `transaksi_selesai.php`.

---
