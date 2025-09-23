# 📊 Laporan Analisis Kualitas Data: Retail Store Sales

Dokumen ini merangkum analisis kualitas data dari dataset **Retail Store Sales**. Analisis ini dilakukan berdasarkan observasi pada sampel data untuk mengidentifikasi potensi masalah sebelum tahap pembersihan data (*data cleaning*) dan pemodelan, meniru laporan yang akan dihasilkan oleh `ydata-profiling`.

Tujuan dari analisis ini adalah untuk mendapatkan pemahaman mendalam tentang struktur, isi, dan masalah yang ada di dalam data.

---

## 📜 Ringkasan Eksekutif

Secara keseluruhan, dataset ini **memerlukan perhatian khusus** pada kualitas datanya. Analisis awal menyoroti beberapa area utama yang memerlukan pembersihan, terutama terkait **nilai yang hilang secara signifikan di banyak kolom** dan **potensi data yang tidak konsisten**.

* **Jumlah Variabel/Kolom:** 11
* **Masalah Utama Teridentifikasi:** Nilai hilang, tipe data yang perlu dikonversi, dan masalah integritas data.

---

## ⚠️ Masalah Utama yang Teridentifikasi

Berikut adalah rincian masalah kualitas data yang ditemukan dari sampel data:

### 1. Nilai yang Hilang (*Missing Values*)
Ini adalah masalah paling signifikan dalam dataset ini. Terdapat banyak sel kosong yang tersebar di berbagai kolom. Kolom yang teridentifikasi memiliki nilai hilang adalah:
* `Item`
* `Price Per Unit`
* `Quantity`
* `Total Spent`
* `Discount Applied`

Terlihat pola di mana jika `Item` hilang, kolom numerik lain seperti `Price Per Unit`, `Quantity`, dan `Total Spent` seringkali ikut hilang. Ini dapat mempersulit proses imputasi atau analisis.

### 2. Tipe Data yang Perlu Diperbaiki
Beberapa kolom terdeteksi dengan tipe data yang tidak sesuai dan memerlukan konversi untuk analisis.
* **Kolom Tanggal sebagai Teks:** Kolom `Transaction Date` saat ini dalam format teks (contoh: `2024-04-08`). Ini perlu diubah menjadi format *datetime* agar bisa digunakan untuk analisis berbasis waktu.
* **Kolom Boolean dengan Nilai Hilang:** Kolom `Discount Applied` berisi nilai `True`/`False` tetapi juga memiliki nilai kosong. Ini akan membuatnya dibaca sebagai tipe data 'object' bukan 'boolean' dan perlu penanganan khusus.

### 3. Integritas Data
Ada indikasi masalah integritas data. Sebagai contoh:
* Pada beberapa baris, nilai `Total Spent` seharusnya merupakan hasil perkalian `Price Per Unit` dan `Quantity`. Namun, ketika salah satu dari nilai ini hilang, integritas kalkulasi tersebut menjadi tidak valid. Contohnya, pada baris `TXN_7482416` dan `TXN_7422454`, nilai-nilai ini tidak lengkap.

### 4. Potensi Inkonsistensi pada Data Kategorikal
Meskipun tidak terlihat langsung pada sampel kecil, kolom seperti `Category`, `Payment Method`, dan `Location` sangat rentan terhadap inkonsistensi penulisan.
* **Contoh Potensial:** Mungkin ada nilai seperti `"Credit Card"` dan `"credit card"`, atau `"Online"` dan `"In-store"` yang penulisannya tidak seragam di seluruh dataset. Hal ini perlu divalidasi.

---

## 🛠️ Rencana Tindak Lanjut (Proses Pembersihan Data)

Berdasarkan temuan di atas, langkah-langkah pembersihan data berikut sangat direkomendasikan:
1.  **Menangani Nilai Hilang:**
    * Investigasi lebih lanjut pada baris dengan nilai yang hilang.
    * Untuk `Discount Applied`, asumsikan nilai yang hilang berarti `False` (tidak ada diskon) bisa menjadi strategi awal.
    * Untuk `Item`, `Price Per Unit`, `Quantity`, dan `Total Spent`, pertimbangkan untuk menghapus baris jika data yang hilang terlalu banyak, atau coba lakukan imputasi jika memungkinkan (misalnya, menghitung `Total Spent` jika `Price` dan `Quantity` tersedia).
2.  **Mengonversi Tipe Data:**
    * Ubah kolom `Transaction Date` ke tipe `datetime`.
    * Setelah menangani nilai hilang di `Discount Applied`, konversi kolom tersebut ke tipe `boolean`.
3.  **Memvalidasi Integritas Data:**
    * Buat kolom baru untuk memvalidasi `Total Spent` dengan mengalikan `Price Per Unit` * `Quantity`. Bandingkan hasilnya dengan kolom `Total Spent` yang ada untuk menemukan diskrepansi.
4.  **Standarisasi Data Kategorikal:**
    * Periksa nilai unik di setiap kolom kategori

---

## ✅ Kesimpulan

Analisis pada sampel data ini menunjukkan bahwa dataset `Retail Store Sales` memiliki masalah kualitas data yang nyata dan perlu ditangani secara serius. Melakukan langkah-langkah pembersihan yang diuraikan di atas akan sangat penting untuk memastikan keandalan dan akurasi analisis atau model apa pun yang dibangun di atas data ini.
