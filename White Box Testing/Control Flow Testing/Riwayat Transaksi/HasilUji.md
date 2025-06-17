# ✅ Test Case - Cetak Struk Transaksi Selesai (`transaksi_selesai.php`)

File ini digunakan untuk mencetak bukti transaksi (struk) setelah proses pembayaran selesai. Menampilkan detail transaksi berdasarkan `id_transaksi`, serta mencetak struk otomatis dengan `window.print()` dan `self.close()`.

---

## 📌 Tujuan Pengujian
- Menampilkan detail transaksi dari database.
- Menampilkan daftar barang, kuantitas, harga, diskon, total.
- Menghitung kembali total, bayar, dan kembalian.
- Mencetak bukti transaksi dalam format HTML (untuk thermal printer / PDF).
- Menampilkan identitas toko.

---

## 🧪 Daftar Pengujian

| No | Nama Pengujian                    | Kondisi yang Diuji                                                          | Data Uji                      | Hasil yang Diharapkan                                                                                      | Status     |
|----|----------------------------------|-----------------------------------------------------------------------------|-------------------------------|-------------------------------------------------------------------------------------------------------------|------------|
| 1  | Ambil Transaksi dari DB          | `id_transaksi` dikirim via GET (`$_GET['idtrx']`)                           | `idtrx=17`                    | Data transaksi berhasil diambil dari tabel `transaksi`                                                     | ✅ Passed   |
| 2  | Ambil Detail Barang              | Mengambil barang dari `transaksi_detail` yang terkait dengan `id_transaksi` | Barang ada                    | Semua barang ditampilkan dengan nama, qty, harga, total, dan diskon jika ada                               | ✅ Passed   |
| 3  | Format Harga dan Total           | Harga dan total ditampilkan dengan format rupiah (`number_format`)          | Harga 10000, Diskon 2000      | Tampilan: Rp10.000, Diskon: Rp2.000, Total: Rp8.000                                                        | ✅ Passed   |
| 4  | Cetak Otomatis                   | Struk tercetak otomatis saat halaman dibuka (`window.print()`)              | Buka halaman transaksi_selesai.php | Printer dialog muncul otomatis dan tab tertutup otomatis (`self.close()`)                                 | ✅ Passed   |
| 5  | Tampilan Header Struk            | Menampilkan nama toko dan alamat di bagian atas                             | -                             | Header: "Toko Ripe", Alamat: "Jl Terusan Halimun no 56 A..."                                               | ✅ Passed   |
| 6  | Menampilkan Total Bayar & Kembali| Menampilkan `total`, `bayar`, dan `kembali`                                 | Total 50000, Bayar 60000      | Tertampil dan format rupiah sesuai, Kembali: 10000                                                         | ✅ Passed   |
| 7  | Diskon Barang Ditampilkan        | Barang dengan diskon memiliki keterangan `Diskon` di bawah total            | Diskon > 0                    | Ada label `Diskon` dan pengurangan nilai di bawah harga total                                              | ✅ Passed   |
| 8  | Tanpa Diskon Tetap Berjalan      | Barang tanpa diskon                                                        | Diskon = 0                    | Tidak menampilkan label `Diskon`, struk tetap tercetak dengan benar                                        | ✅ Passed   |
| 9  | Menampilkan Waktu Transaksi      | Menampilkan tanggal & waktu transaksi dengan format `d-m-Y H:i:s`           | 2025-06-17 20:30:00           | Tampilan: `17-06-2025 20:30:00`                                                                            | ✅ Passed   |
| 10 | Menangani ID Tidak Valid         | ID transaksi tidak ditemukan                                                | idtrx = 99999 (tidak ada)     | Tidak error (saran: tampilkan pesan error / redirect ke halaman error)                                     | ⚠️ Perlu Validasi |

---
