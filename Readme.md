Link collab untuk melihat kualitas data dari smartwatch:
"https://colab.research.google.com/drive/1_G2NF7pkV68EkLnJDdBZXE4ZYI6GBKhP#scrollTo=COnw7JXXrNM4"

Link untuk data:
https://www.kaggle.com/datasets/mohammedarfathr/smartwatch-health-data-uncleaned

Penjelasan Laporan Analisis Kualitas Data ydata-profiling
Dokumen ini menjelaskan informasi yang muncul setelah menggunakan ydata-profiling pada dataset kesehatan smartwatch dan menguraikan dampak penting dari penggunaan alat ini dalam proses analisis data.

1. Data yang Muncul dalam Laporan ydata-profiling
Saat Anda menjalankan ydata-profiling pada sebuah dataset, ia menghasilkan laporan HTML interaktif yang terbagi menjadi beberapa bagian utama:

a. Overview (Gambaran Umum)
Bagian ini memberikan statistik tingkat tinggi tentang keseluruhan dataset.

Dataset statistics: Jumlah variabel (kolom), jumlah observasi (baris), persentase nilai yang hilang (Missing cells), dan jumlah baris duplikat.

Variable types: Rangkuman jenis-jenis tipe data yang ada di dalam dataset (misalnya, Numeric, Categorical).

b. Variables (Detail per Variabel)
Ini adalah bagian paling mendalam, di mana setiap kolom (variabel) dianalisis secara individual.

Untuk Variabel Numerik (contoh: Heart Rate (BPM), Step Count):

Statistics: Statistik deskriptif lengkap seperti rata-rata, median, standar deviasi, nilai minimum, dan maksimum.

Histogram: Grafik visual yang menunjukkan distribusi data. Dari sini, Anda bisa melihat apakah datanya condong (skewed), normal, atau memiliki beberapa puncak (multimodal).

Common Values: Daftar nilai yang paling sering muncul.

Extreme Values: Daftar nilai terkecil dan terbesar, yang sangat berguna untuk mendeteksi outlier (pencilan).

Untuk Variabel Kategorikal (contoh: Activity Level):

Counts: Grafik batang (bar chart) yang menunjukkan jumlah atau frekuensi dari setiap kategori.

Frequencies: Tabel yang merinci persentase setiap kategori.

Dari sini Anda bisa melihat ketidakseimbangan kelas atau inkonsistensi penulisan (misalnya, Highly_Active vs Highly Active).

c. Correlations (Korelasi)
Bagian ini menunjukkan bagaimana variabel-variabel numerik saling berhubungan satu sama lain.

Correlation Matrix (Heatmap): Disajikan dalam bentuk heatmap berwarna, di mana warna yang lebih terang atau lebih gelap menunjukkan korelasi yang lebih kuat (baik positif maupun negatif). Misalnya, Anda bisa melihat apakah Step Count berkorelasi positif dengan Heart Rate (BPM).

Jenis Korelasi: Biasanya menggunakan metode Pearson, Spearman, dll.

d. Missing Values (Nilai yang Hilang)
Bagian ini memberikan visualisasi yang jelas tentang data yang hilang.

Matrix: Diagram yang menunjukkan pola nilai yang hilang di seluruh dataset.

Count: Grafik batang yang mengurutkan variabel berdasarkan jumlah nilai yang hilang.

e. Alerts (Peringatan)
Ini adalah salah satu fitur paling kuat dari ydata-profiling. Sistem secara otomatis menandai potensi masalah dalam data Anda.

High correlation: Peringatan jika dua atau lebih variabel sangat berkorelasi, yang bisa menjadi masalah untuk beberapa model.

Missing: Peringatan tentang kolom dengan persentase data hilang yang tinggi.

Skewed: Peringatan jika distribusi data sangat tidak seimbang.

Zeros: Peringatan jika sebuah kolom memiliki persentase nilai nol yang tinggi.

Duplicates: Peringatan jika ditemukan baris duplikat.

2. Dampak Penggunaan ydata-profiling
Penggunaan ydata-profiling memiliki dampak yang sangat signifikan dalam siklus hidup proyek data, terutama pada tahap awal.

a. Efisiensi dan Penghematan Waktu
Automatisasi EDA: ydata-profiling secara drastis mengurangi waktu yang dibutuhkan untuk Exploratory Data Analysis (EDA). Tanpa alat ini, seorang analis data harus menulis kode manual untuk setiap statistik dan visualisasi, yang bisa memakan waktu berjam-jam. Dengan ydata-profiling, semua itu dihasilkan hanya dengan beberapa baris kode.

b. Identifikasi Masalah Kualitas Data yang Cepat
Menjadi Peta Jalan Pembersihan: Laporan, terutama bagian Alerts, berfungsi sebagai daftar periksa (to-do list) untuk pembersihan data. Anda bisa langsung melihat masalah seperti:

Kolom Sleep Duration (hours) memiliki nilai 'ERROR' (tipe data salah).

Terdapat baris duplikat.

Heart Rate (BPM) memiliki nilai outlier yang tidak masuk akal.

Kolom User ID memiliki nilai yang hilang.

Ini memungkinkan Anda untuk langsung merancang strategi pembersihan data yang terarah.

c. Pemahaman Data yang Mendalam dan Cepat
Memahami Distribusi: Tanpa perlu membuat plot manual, Anda bisa langsung memahami karakteristik setiap variabel. Misalnya, Anda bisa melihat bahwa sebagian besar data Stress Level berada di tingkat rendah hingga menengah.

Melihat Hubungan: Matriks korelasi memberikan gambaran cepat tentang variabel mana yang mungkin saling mempengaruhi, yang menjadi dasar untuk rekayasa fitur atau pemilihan model di tahap selanjutnya.

d. Komunikasi yang Lebih Baik
Laporan yang Mudah Dibagikan: Laporan HTML yang dihasilkan bersifat interaktif dan mudah dipahami bahkan oleh pihak non-teknis (seperti manajer produk atau analis bisnis). Ini menjadikannya alat komunikasi yang hebat untuk menyajikan temuan awal tentang kondisi data kepada tim.

Secara keseluruhan, ydata-profiling mengubah proses analisis data awal dari tugas yang repetitif dan manual menjadi proses yang otomatis, cepat, dan mendalam. Dampaknya adalah kualitas data yang lebih baik, keputusan pembersihan yang lebih tepat, dan penghematan waktu yang signifikan.
