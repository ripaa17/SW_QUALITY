# Pengujian Array Ortogonal (OAT) 
  Pengujian Array Ortogonal (OAT)adalah teknik pengujian perangkat lunak yang menggunakan array ortogonal untuk membuat kasus uji. Ini adalah pendekatan
  pengujian statistik yang sangat berguna ketika sistem yang akan diuji memiliki input data yang besar. Pengujian susunan ortogonal membantu memaksimalkan 
  cakupan pengujian dengan memasangkan dan menggabungkan input serta menguji sistem dengan
  jumlah kasus pengujian yang relatif lebih sedikit untuk menghemat waktu.
   
🧩 FAKTOR & LEVEL UNTUK SETIAP FITUR
# 🧪 Orthogonal Array Testing (OAT) – Faktor & Level
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

## Tabel Pengujian Login (Implementasi OAT)

| TC   | Username   | Password   | Role     |
|------|------------|------------|----------|
| TC1  | Eva        | 123456     | Admin    | 
| TC2  | Eva        | salahpw    | Kasir    | 
| TC3  | Eva        | (kosong)   | (kosong) | 
| TC4  | Eeva       | 123456     | Kasir    | 
| TC5  | Eeva       | salahpw    | (kosong) | 
| TC6  | Eeva       | (kosong)   | Admin    | 
| TC7  | (kosong)   | 123456     | (kosong) | 
| TC8  | (kosong)   | salahpw    | Admin    | 
| TC9  | (kosong)   | (kosong)   | Kasir    | 

---

## 📝 Catatan

- **Metode:** Orthogonal Array Testing menggunakan array **L9**.
- **Faktor diuji:** `Username`, `Password`, dan `Role`.
- **Tujuan:** Mengurangi jumlah test case sambil tetap mencakup semua kombinasi *pairwise* yang penting.
- **Efisiensi:** Dari 27 kombinasi (3×3×3), hanya diuji 9 kombinasi mewakili cakupan maksimum.
- **Hasil:** Semua test case berjalan sesuai ekspektasi. Validasi input login berfungsi dengan baik.

---
### Pengujian Pada Penambahan Barang
| TC  | Kode   | Nama               | Harga  | Jumlah Stok |
|-----|--------|--------------------|--------|-------------|
| TC1 | B0059  | Bola Basket Besar  | 60000  | 10          | 
| TC2 | B0057  | Sabun Mandi        | 2500   | 10          | 
| TC3 | B0055  | Pasta Gigi         | 2000   | 20          | 
| TC4 | B0054  | Sampoo Botol 350ml | 16000  | 10          | 
| TC5 | B0053  | Balsem             | 5000   | 10          | 
| TC6 | B0056  | Sapu Lidi          | 10000  | 10          | 
| TC7 | B0052  | Sandal             | 12000  | 10          | 
| TC8 | B0051  | Minyak             | 22000  | 10          | 
| TC9 | B0040  | Salak Buah         | 5000   | 10          | 
---
Total Pengujian: 9
Berhasil (✅): 9
Gagal (❌): 0
Catatan:
Dari 9 pengujian yang dilakukan dengan data valid, seluruhnya berhasil ✅. Hal ini menunjukkan bahwa sistem dapat menambahkan barang dengan benar saat input sesuai. Untuk memastikan sistem lebih kuat, pengujian dengan data tidak valid (seperti kode duplikat, harga nol, atau nama kosong) juga perlu dilakukan.
