# Laporan Proyek Machine Learning - Sopyan

## Domain Proyek
### Latar belakang
Sistem penyewaan sepeda (bike-sharing) merupakan evolusi dari sistem rental tradisional, di mana seluruh proses mulai dari keanggotaan, peminjaman, hingga pengembalian dilakukan secara otomatis. Saat ini, lebih dari 500 program bike-sharing beroperasi di seluruh dunia, menyediakan ratusan ribu sepeda sebagai solusi mobilitas perkotaan yang efisien, ramah lingkungan, dan mendukung gaya hidup sehat (Shaheen et al., 2010).

Namun, proses penyewaan sepeda sangat dipengaruhi oleh kondisi lingkungan dan musiman, seperti cuaca, hari dalam seminggu, dan jam operasional. Oleh karena itu, untuk menjaga keseimbangan permintaan dan ketersediaan sepeda, dibutuhkan model prediksi yang akurat. Melalui pendekatan predictive analytics berbasis machine learning, proyek ini bertujuan untuk memprediksi jumlah penyewaan sepeda dan mengidentifikasi faktor-faktor yang paling berpengaruh terhadap permintaan tersebut.

## Business Understanding
### Problem Statements
Sistem penyewaan sepeda telah menjadi alternatif transportasi yang semakin populer di kota-kota besar. Namun, permintaan terhadap sepeda sangat fluktuatif dan dipengaruhi oleh berbagai faktor seperti cuaca, musim, serta hari kerja atau hari libur. Ketidakpastian ini menyulitkan operator dalam mengelola ketersediaan sepeda dan merencanakan strategi distribusi yang efisien. Dengan adanya data historis dan informasi lingkungan yang terus dikumpulkan, muncul peluang untuk membangun sistem prediktif yang dapat membantu pengambilan keputusan secara lebih akurat dan berbasis data.

Berdasarkan konteks tersebut, proyek ini berfokus pada dua pertanyaan utama:
1. Bagaimana cara membangun model yang dapat memprediksi jumlah penyewaan sepeda secara akurat berdasarkan faktor-faktor seperti cuaca, musim, dan hari kerja?
2. Apa saja faktor utama yang paling memengaruhi jumlah penyewaan sepeda, dan bagaimana cara mengoptimalkan model prediktif untuk menangkap hubungan tersebut secara tepat?
   
### Goals
1. Membangun model machine learning yang mampu memprediksi jumlah penyewaan sepeda harian dan/atau per jam secara akurat.
2. Mengidentifikasi fitur-fitur penting yang paling memengaruhi pola penyewaan sepeda, seperti cuaca, hari libur, dan musim.

### Solution Statements
Untuk mengatasi tantangan ini, beberapa pendekatan solusi inovatif akan diterapkan, yaitu:
1. Menggunakan Random Forest Regressor sebagai model awal. Algoritma ini dipilih karena kemampuannya dalam menangani data yang tidak linier dan mengelola fitur yang kompleks dengan sangat baik.
2. Proses feature importance analysis akan dilakukan untuk mengidentifikasi variabel-variabel yang paling berpengaruh terhadap prediksi jumlah penyewaan sepeda, memberikan wawasan lebih dalam tentang faktor-faktor utama yang mempengaruhi permintaan.
3. Setelah model Random Forest dibuat, saya akan membandingkan hasil prediksi dengan model lain untuk membuktikan apakah Random Forest merupakan pilihan yang tepat. Beberapa model alternatif yang akan saya uji meliputi:
   - Gradient Boosting Regressor: Model ini menggunakan teknik boosting yang dapat meningkatkan akurasi model dengan mengoreksi kesalahan secara bertahap. Saya akan mengevaluasi apakah Gradient Boosting memberikan hasil yang lebih baik daripada Random Forest.
   - Linear Regression: Model ini akan saya gunakan sebagai pembanding dengan pendekatan yang lebih sederhana. Walaupun lebih mudah diinterpretasikan, Linear Regression memiliki keterbatasan dalam menangkap hubungan non-linear antara variabel. Saya akan mengevaluasi seberapa efektif Linear Regression dalam memprediksi penyewaan sepeda.
   - K-Nearest Neighbors (KNN): Model berbasis instance ini akan memberikan alternatif untuk prediksi dengan cara mengukur kedekatan data. KNN akan saya uji untuk melihat apakah model ini memberikan hasil yang berbeda atau lebih baik dibandingkan dengan model lainnya.
  
###  Evaluation Metrics
Untuk mengevaluasi kinerja setiap model, saya akan menggunakan metrik evaluasi berikut:
- Root Mean Squared Error (RMSE): Mengukur deviasi prediksi terhadap nilai aktual. Cocok untuk model regresi karena memberikan penalti lebih besar pada kesalahan besar.
- R² Score: Mengukur seberapa besar variabilitas target yang dapat dijelaskan oleh model. Nilai mendekati 1 menunjukkan model yang baik dalam memprediksi jumlah penyewaan sepeda.
  
## Data Understanding
### Informasi Data
Dataset yang digunakan dalam proyek ini berisi data penyewaan sepeda yang dikumpulkan selama dua tahun (2011-2012) dari sistem Capital Bikeshare di Washington, D.C., USA. Dataset ini mencatat informasi terkait kondisi penyewaan sepeda setiap jam, serta informasi cuaca dan musim. Data ini tersedia secara publik dan dapat diunduh melalui tautan berikut:
-  [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/275/bike+sharing+dataset)

Dataset ini terdiri dari dua agregasi utama: data per jam dan per hari. Variabel-variabel yang tercatat meliputi cuaca, waktu, musim, suhu, kelembaban, dan kecepatan angin, serta jumlah penyewaan sepeda oleh pengguna terdaftar dan non-terdaftar.

### Variabel dalam Dataset 
- Datetime: Waktu pengambilan data dalam format timestamp.
- Season: Musim saat penyewaan dilakukan (1: Spring, 2: Summer, 3: Fall, 4: Winter).
- Year: Tahun penyewaan (2011 atau 2012).
- Month: Bulan penyewaan (1-12).
- Hour: Jam penyewaan (0-23, format 24 jam).
- Holiday: Menunjukkan apakah hari tersebut merupakan hari libur (1: Ya, 0: Tidak).
- Workingday: Menunjukkan apakah hari tersebut merupakan hari kerja (1: Ya, 0: Tidak).
- Weather: Kode yang menggambarkan kondisi cuaca (1: Clear, 2: Mist, 3: Light Rain, 4: Heavy Rain).
- Temp: Suhu udara pada saat penyewaan dilakukan (derajat Celsius).
- Humidity: Kelembaban udara (persentase).
- Windspeed: Kecepatan angin pada saat penyewaan (km/h).
- Casual: Jumlah penyewaan sepeda oleh pengguna non-anggota.
- Registered: Jumlah penyewaan sepeda oleh pengguna anggota.
- Count: Total jumlah penyewaan sepeda (Casual + Registered).

### Tahapan untuk Memahami Data
Analisis eksplorasi data dilakukan untuk memahami hubungan antar variabel dan pola yang ada. Ini mencakup pembuatan grafik distribusi, analisis korelasi antar variabel, serta identifikasi outliers atau nilai yang hilang.
- Histogram: Memvisualisasikan distribusi data.
- Boxplot: Mengidentifikasi outlier dan melihat sebaran data.
- Heatmap: Memvisualisasikan korelasi antar fitur.

Visualisasi data dilakukan menggunakan grafik histogram dan Heatmap untuk mendapatkan insight mengenai struktur dan hubungan antar variabel.

## Data Preparation
1. Pemeriksaan Missing Values
Dilakukan untuk memastikan tidak ada nilai yang hilang pada dataset. Jika ditemukan, nilai tersebut akan diimputasi atau dihapus agar model tidak terpengaruh oleh data yang hilang.

2. Pemeriksaan Duplikat Data
Duplikat dalam data akan diidentifikasi dan dihapus untuk menghindari bias dan overfitting pada model.

3. Identifikasi dan Penanganan Outliers
Outliers yang terdeteksi melalui metode IQR dan boxplot akan dipertimbangkan untuk dihapus jika dianggap mempengaruhi akurasi model.

4. Splitting Data (Pembagian Data)
Data dibagi menjadi training set (80%) dan test set (20%) untuk melatih dan menguji model, menggunakan train_test_split().

5. Fitur dan Target

- Fitur (X):
Variabel yang digunakan untuk memprediksi target antara lain: season, yr, mnth, hr, holiday, weekday, workingday, weathersit, temp, atemp, hum, windspeed.

- Target (y):
Variabel yang diprediksi adalah jumlah penyewaan sepeda, yaitu cnt.

Data preparation ini bertujuan untuk memastikan dataset bersih dan siap digunakan dalam pembangunan model prediktif.

## Modeling
Pada tahap pemodelan, saya akan memulai dengan Random Forest Regressor sebagai model utama untuk memprediksi jumlah penyewaan sepeda. Setelah itu, saya akan membandingkan performanya dengan beberapa model lain, yaitu Gradient Boosting Regressor, Linear Regression, dan K-Nearest Neighbors (KNN) untuk memastikan apakah Random Forest sudah menjadi pilihan terbaik.

1. Random Forest Regressor (Model Utama)
Pada tahap pemodelan, saya menggunakan Random Forest Regressor sebagai model utama karena kemampuannya dalam menangani data yang non-linear dan kompleks. Random Forest menggabungkan banyak pohon keputusan untuk menghasilkan prediksi yang lebih stabil dan akurat. Kelebihan dari model ini adalah kemampuannya untuk menangani data dengan banyak fitur dan variabel, serta tidak rentan terhadap overfitting jika dibandingkan dengan model pohon keputusan tunggal.

2. Gradient Boosting
Algoritma ini bekerja dengan membangun model secara bertahap dan memperbaiki kesalahan dari model sebelumnya melalui proses boosting. Kelebihan dari GradientBoosting adalah kemampuannya dalam menghasilkan prediksi yang sangat akurat, terutama untuk data kompleks.

3. Linear Regression
Saya gunakan sebagai pendekatan yang lebih sederhana dan interpretatif. Model ini cocok untuk melihat hubungan linier antara variabel independen dengan target. Kelebihan dari Linear Regression adalah kecepatan dalam pelatihan model dan kemudahan interpretasi.

4. K-Nearest Neighbors (KNN)
KNN memprediksi nilai target berdasarkan kedekatan data dengan titik data lain yang serupa. Kelebihannya adalah model ini tidak memerlukan pelatihan yang intensif dan cukup fleksibel untuk menangkap pola lokal.

#### Pemilihan Model Terbaik
Setelah melatih model-model di atas, saya akan membandingkan hasilnya berdasarkan Root Mean Squared Error (RMSE) dan R² Score. Jika Random Forest memberikan hasil terbaik, maka model ini akan dipilih sebagai model utama. Jika diperlukan, hyperparameter tuning akan dilakukan menggunakan GridSearchCV atau RandomizedSearchCV untuk meningkatkan performa model Random Forest.

Dengan pendekatan ini, saya berharap dapat menemukan model yang paling akurat untuk memprediksi jumlah penyewaan sepeda.

## Evaluation
Untuk mengevaluasi performa model regresi yang dibangun, saya menggunakan dua metrik utama, yaitu Root Mean Squared Error (RMSE) dan R² Score. Pemilihan kedua metrik ini disesuaikan dengan konteks permasalahan prediksi jumlah penyewaan sepeda, di mana penting untuk mengukur akurasi dan kemampuan model dalam menjelaskan variabilitas data.

1. Root Mean Squared Error (RMSE)
Metrik ini memberikan penalti lebih besar terhadap kesalahan prediksi yang besar, sehingga cocok untuk kasus di mana outlier atau deviasi tinggi perlu diwaspadai. Semakin kecil nilai RMSE, semakin baik performa model.

2. R² Score
R² Score digunakan untuk melihat seberapa baik model menjelaskan variansi dari target. Nilai R² berkisar antara 0 hingga 1. Nilai mendekati 1 menunjukkan bahwa model mampu menjelaskan hampir seluruh variabilitas data target.

### Hasil Evaluasi 
- Random Forest Regressor memberikan performa terbaik, dengan nilai R² sebesar 0.9441 dan RMSE sebesar 42.07. Model ini mampu menangkap pola data yang kompleks dengan akurasi tinggi.
- Model Gradient Boosting Regressor berada di posisi kedua, dengan R² sebesar 0.8495 dan RMSE 69.04, menunjukkan performa yang cukup baik meskipun tidak seakurat Random Forest.
- Model K-Nearest Neighbors (KNN) mencatat performa yang relatif baik dengan R² sebesar 0.9123 dan RMSE 52.70, namun tetap lebih rendah dibanding Random Forest.
- Linear Regression memiliki performa terendah, dengan R² sebesar 0.3880 dan RMSE sebesar 139.21. Hasil ini menunjukkan bahwa model linier kurang mampu menangkap pola kompleks dalam data penyewaan sepeda.

Berdasarkan hasil tersebut, saya memilih Random Forest Regressor sebagai model terbaik karena konsisten memberikan hasil evaluasi paling unggul dibandingkan model lainnya.

