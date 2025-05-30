# 🧪 Matriks Pengujian (Testing Matrix)

| TC   | Login           | Barang          | User             | Transaksi       | Output yang Diharapkan      | Status Uji     |
|------|------------------|------------------|-------------------|------------------|-----------------------------|----------------|
| TC1  | Valid            | Lengkap & Valid  | Admin Valid       | Tunai - 1 Item   | Transaksi Berhasil          | ✅ Valid       |
| TC2  | Valid            | Harga Negatif    | Kasir Tanpa Nama  | Kartu - 5 Item   | Tergantung validasi harga   | ✅ Valid       |
| TC3  | Valid            | Stok Kosong      | Role Tidak Valid  | QRIS - >10 Item  | Transaksi Ditolak           | ❌ Tidak Valid |
| TC4  | Password Salah   | Lengkap & Valid  | Kasir Tanpa Nama  | QRIS - >10 Item  | Gagal login (peringatan)    | ✅ Valid       |
| TC5  | Password Salah   | Harga Negatif    | Role Tidak Valid  | Tunai - 1 Item   | Login dan input ditolak     | ❌ Tidak Valid |
| TC6  | Password Salah   | Stok Kosong      | Admin Valid       | Kartu - 5 Item   | Stok kosong ditolak         | ✅ Valid       |
| TC7  | Username Kosong  | Lengkap & Valid  | Role Tidak Valid  | Kartu - 5 Item   | Gagal login & role salah    | ❌ Tidak Valid |
| TC8  | Username Kosong  | Harga Negatif    | Admin Valid       | QRIS - >10 Item  | Login auto / diterima       | ✅ Valid       |
| TC9  | Username Kosong  | Stok Kosong      | Kasir Tanpa Nama  | Tunai - 1 Item   | Gagal login & stok habis    | ❌ Tidak Valid |

