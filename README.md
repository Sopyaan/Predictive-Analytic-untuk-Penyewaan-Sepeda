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
Untuk mengatasi tantangan prediksi jumlah penyewaan sepeda secara akurat, saya mengimplementasikan dan membandingkan empat algoritma regresi dengan pendekatan yang berbeda, yaitu:
- Random Forest Regressor: Cocok untuk menangani data non-linear dan kompleks. Model ini juga menyediakan fitur feature importance yang membantu memahami variabel-variabel paling berpengaruh terhadap permintaan penyewaan sepeda.
- Gradient Boosting Regressor: Model ini mengadopsi teknik boosting, yang secara bertahap memperbaiki kesalahan model sebelumnya. Saya mengevaluasi apakah pendekatan ini mampu menghasilkan error yang lebih rendah dibandingkan model lainnya.
- Linear Regression: Digunakan sebagai baseline model karena sifatnya yang sederhana dan mudah diinterpretasikan. Meski terbatas dalam menangkap hubungan non-linear, model ini tetap penting sebagai pembanding awal performa.
- K-Nearest Neighbors (KNN) Regressor: Merupakan model non-parametrik yang memprediksi berdasarkan kedekatan antar data. Saya mengujinya untuk melihat seberapa baik pendekatan ini bekerja dalam konteks prediksi penyewaan sepeda.

  
###  Evaluation Metrics
Untuk mengevaluasi kinerja setiap model, saya menggunakan metrik evaluasi berikut:
- Mean Squared Error (MSE): Metrik ini menghitung rata-rata kuadrat selisih antara nilai aktual dan nilai prediksi. MSE memberikan penalti yang lebih besar terhadap kesalahan prediksi yang besar, sehingga sangat cocok digunakan dalam kasus regresi. Semakin kecil nilai MSE, semakin baik performa model dalam melakukan prediksi.
  
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
Tahap eksplorasi data dilakukan untuk memahami pola, hubungan antar variabel, serta karakteristik distribusi dalam dataset. Berikut adalah hasil dari proses exploratory data analysis (EDA) yang dilakukan:
- Distribusi Data (Histogram)
<p align="center">
  <img src="https://github.com/Sopyaan/Predictive-Analytic-untuk-Penyewaan-Sepeda/blob/main/Image/Distribusi%20Data.png", width="" height="">
</p>

Kolom target cnt (jumlah penyewaan sepeda) menunjukkan distribusi yang menceng ke kanan (right-skewed), dengan sebagian besar observasi berada di angka rendah dan hanya sedikit yang memiliki penyewaan tinggi. Hal ini menunjukkan penyewaan dalam jumlah besar hanya terjadi pada kondisi tertentu (misalnya musim puncak atau jam sibuk).

- Deteksi Outliers (Boxplot & IQR)
<p align="center">
  <img src="https://github.com/Sopyaan/Predictive-Analytic-untuk-Penyewaan-Sepeda/blob/main/Image/Outliers.png", width="" height="">
</p>

Outlier ditemukan pada kolom casual, registered, dan windspeed. Namun, setelah ditelusuri, nilai-nilai ini masih relevan dalam konteks nyata seperti lonjakan permintaan saat hari libur atau kondisi cuaca ekstrem, sehingga tidak dihapus.

- Korelasi Antar Variabel (Heatmap)
<p align="center">
  <img src="https://github.com/Sopyaan/Predictive-Analytic-untuk-Penyewaan-Sepeda/blob/main/Image/Heatmap.png", width="" height="">
</p>

Hasil heatmap menunjukkan korelasi tinggi antara cnt dengan registered (0.97) dan casual (0.69). Fitur temp dan hr juga memiliki korelasi positif terhadap cnt, sedangkan hum dan windspeed menunjukkan korelasi negatif. Korelasi yang tinggi antara temp dan atemp (0.99) mengindikasikan bahwa salah satu dapat dihapus untuk menghindari duplikasi informasi dalam modeling.

## Data Preparation
Data preparation dilakukan untuk memastikan bahwa dataset dalam kondisi bersih, konsisten, dan siap digunakan dalam proses pemodelan. Berikut adalah tahapan yang dilakukan secara berurutan:

### 1. Pemeriksaan Missing Values
Saya memeriksa seluruh kolom dalam dataset menggunakan `.isnull().sum()` dan memastikan bahwa **tidak terdapat nilai yang hilang** pada fitur manapun.  
> ✅ Alasan: Nilai yang hilang dapat mengganggu proses pelatihan model dan menurunkan akurasi prediksi. Jika ditemukan, nilai tersebut akan diimputasi atau dihapus sesuai konteks.

### 2. Pemeriksaan Duplikat Data
Pemeriksaan dilakukan dengan `.duplicated().sum()`, dan hasilnya menunjukkan **tidak ada baris duplikat** dalam dataset.  
> ✅ Alasan: Data duplikat dapat menimbulkan bias dalam pelatihan dan menyebabkan model belajar pola yang tidak representatif.

### 3. Identifikasi dan Penanganan Outliers
Outliers diperiksa pada fitur numerik (`casual`, `registered`, `cnt`, `windspeed`) menggunakan **boxplot** dan metode **Interquartile Range (IQR)**.  
Meskipun ditemukan beberapa outliers, nilai-nilai tersebut masih dianggap wajar dalam konteks bisnis (seperti lonjakan saat musim panas atau akhir pekan), sehingga **tidak dihapus**.  
> ✅ Alasan: Outliers bisa menjadi indikasi penting dari perilaku nyata pengguna, dan penghapusannya bisa menghilangkan informasi bernilai.

### 4. Splitting Data (Pembagian Data)
Dataset dibagi menjadi dua bagian menggunakan `train_test_split()` dari `sklearn.model_selection`:
- **80%** untuk data latih (training set)
- **20%** untuk data uji (testing set)

> ✅ Alasan: Pembagian ini penting untuk melatih model pada satu subset dan mengevaluasinya pada data yang tidak pernah dilihat, agar performa model lebih objektif.

### 5. Fitur dan Target

- **Fitur (X):**  
  `season`, `yr`, `mnth`, `hr`, `holiday`, `weekday`, `workingday`, `weathersit`, `temp`, `atemp`, `hum`, `windspeed`

- **Target (y):**  
  `cnt` → jumlah total penyewaan sepeda (baik pengguna casual maupun registered)

> ✅ Alasan: Fitur yang dipilih merupakan kombinasi variabel waktu, cuaca, dan status hari yang diyakini memengaruhi jumlah penyewaan sepeda. Target `cnt` adalah variabel utama yang akan diprediksi.

## Modeling
Pada tahap ini, saya membandingkan empat model regresi untuk memprediksi jumlah penyewaan sepeda. Evaluasi dilakukan menggunakan Mean Squared Error (MSE) pada data pelatihan. Model dengan nilai MSE terendah akan dipilih sebagai model terbaik.

### Random Forest Regressor 
#### Tahapan:
- Pemilihan fitur.
- Pelatihan model dengan `RandomForestRegressor`.
- Evaluasi menggunakan MSE pada data latih.

#### Parameter:
- `n_estimators=50`
- `max_depth=16`
- `random_state=55`
- `n_jobs=-1`

#### Teori / Cara Kerja:
Random Forest adalah metode ensemble yang membentuk banyak pohon keputusan dari subset acak data. Prediksi akhir diperoleh dari rata-rata prediksi setiap pohon.

#### Kelebihan:
- Handal untuk dataset dengan banyak fitur.
- Kurang rentan terhadap overfitting.
- Mampu menangani data kategorikal dan numerik.

#### Kekurangan:
- Waktu pelatihan bisa relatif lama.
- Model sulit untuk diinterpretasikan.

### Gradient Boosting
#### Tahapan:
- Pelatihan model dengan `GradientBoostingRegressor`.
- Evaluasi menggunakan MSE.

#### Parameter:
- `n_estimators=100`
- `learning_rate=0.3`
- `max_depth=3`
- `random_state=55`
  
---

#### Teori / Cara Kerja:
Gradient Boosting membangun model secara bertahap. Setiap pohon baru fokus pada memperbaiki kesalahan dari pohon sebelumnya menggunakan pendekatan gradient descent.

#### Kelebihan:
- Akurat untuk data kompleks.
- Dapat bekerja baik tanpa banyak preprocessing.

#### Kekurangan:
- Waktu pelatihan lebih lama dibanding model linear.
- Rentan overfitting jika tidak dikontrol parameter (meski di sini tidak dilakukan tuning).

---
### Linear Regression
#### Tahapan:
- Pelatihan model menggunakan `LinearRegression`.
- Evaluasi menggunakan MSE.

#### Teori / Cara Kerja:
Model ini mencoba mencari hubungan linier antara variabel independen dan target menggunakan pendekatan **ordinary least squares**.

#### Kelebihan:
- Cepat dan mudah diinterpretasikan.
- Cocok untuk hubungan linier antar variabel.

#### Kekurangan:
- Kurang cocok untuk data dengan hubungan non-linier.
- Sensitif terhadap outlier.

---

### K-Nearest Neighbors (KNN)
#### Tahapan:
- Pelatihan model dengan `KNeighborsRegressor`.
- Evaluasi dengan MSE.
- Data perlu dinormalisasi agar skala fitur setara.

#### Parameter:
- `n_neighbors=10`

#### Teori / Cara Kerja:
KNN memprediksi nilai berdasarkan rata-rata dari k tetangga terdekat yang ditemukan berdasarkan jarak Euclidean.

#### Kelebihan:
- Tidak memerlukan pelatihan model (lazy learning).
- Cukup fleksibel untuk pola lokal.

#### Kekurangan:
- Proses prediksi lambat untuk data besar.
- Sangat sensitif terhadap skala data dan nilai parameter k.

---

#### Pemilihan Model Terbaik
Evaluasi dilakukan dengan menghitung nilai **Mean Squared Error (MSE)** dari keempat model pada data pelatihan. Model dengan MSE paling kecil dipilih sebagai model utama karena memberikan prediksi paling mendekati nilai aktual. 


## Evaluation
Untuk mengevaluasi performa model regresi yang dibangun, saya menggunakan Mean Squared Error (MSE). Pemilihan metrik ini disesuaikan dengan konteks permasalahan prediksi jumlah penyewaan sepeda, di mana penting untuk mengukur akurasi dan kemampuan model dalam menjelaskan variabilitas data.

1. Mean Squared Error (MSE)
Metrik ini menghitung rata-rata kuadrat selisih antara nilai aktual dan nilai prediksi. MSE memberikan penalti yang lebih besar terhadap kesalahan prediksi yang besar, sehingga sangat cocok digunakan dalam kasus regresi. Semakin kecil nilai MSE, semakin baik performa model dalam melakukan prediksi.


### Hasil Evaluasi 
#### Data Aktual dan Hasil Prediksi

| ID    | Nilai Aktual (y_true) | Prediksi Random Forest | Prediksi Boosting | Prediksi Linear Reg. | Prediksi KNN |
|-------|------------------------|--------------------------|--------------------|------------------------|---------------|
| 12830 | 425                    | **375.5**                | 450.5              | 450.3                  | 370.6         |

#### Evaluasi Performa Model (MSE)

| Model           | MSE (Train) | MSE (Test) |
|-----------------|--------------|-------------|
| Random Forest   | **0.3874**   | **1.8266**  |
| Boosting        | 2.8554       | 2.8737      |
| K-Nearest Neighbors (KNN) | 2.4765       | 2.9494      |
| Linear Regression | 20.2926      | 19.3798     |


#### Analisis
- **Random Forest** menunjukkan performa terbaik dengan MSE paling rendah pada data train dan test.
- **Boosting** dan **KNN** juga memberikan performa yang cukup baik, meskipun tidak seakurat Random Forest.
-  **Linear Regression** memiliki MSE tertinggi, mengindikasikan model terlalu sederhana untuk pola data ini.

### Kesimpulan
Model **Random Forest** dipilih sebagai model terbaik untuk implementasi akhir karena:
- Prediksi paling mendekati nilai aktual.
- MSE terendah di antara semua model.
- Tidak menunjukkan overfitting yang signifikan antara train dan test.
