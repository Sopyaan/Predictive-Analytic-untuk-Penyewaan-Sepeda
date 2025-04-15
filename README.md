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
## Data Understanding

## Data Preparation

## Modeling

## Evaluation



