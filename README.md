# Prediksi Kelayakan Air Minum Menggunakan Machine Learning

## Deskripsi Proyek

Proyek ini merupakan tugas UAS Mata Kuliah **Kecerdasan Buatan** yang bertujuan membangun model *machine learning* untuk memprediksi apakah suatu sampel air layak dikonsumsi (*potable*) atau tidak berdasarkan parameter kimia yang terdapat pada dataset.

Algoritma yang digunakan pada proyek ini adalah:

- Decision Tree
- K-Nearest Neighbors (KNN)

Model dikembangkan menggunakan bahasa pemrograman **Python** dengan pustaka **scikit-learn**.

## Anggota Kelompok

| Nama | NIM |
|------|-----|
| Azhari Ahmad Fauzani | 2406107 |
| Luthfi Muhammad Fikri | 2406003 |

## Dataset

Dataset yang digunakan merupakan **Water Potability Dataset** yang diperoleh dari Kaggle.

Dataset berisi:

- 3276 data
- 9 fitur
- 1 target (Potability)

## Tahapan Proyek

- Data Understanding
- Exploratory Data Analysis (EDA)
- Data Preparation
- Modeling
- Evaluation

## Algoritma yang Digunakan

- Decision Tree
- K-Nearest Neighbors (KNN)

## Hasil Evaluasi

| Metrik | Decision Tree | KNN |
|--------|--------------:|----:|
| Accuracy | 63.26% | 62.80% |
| Precision | 51.02% | 50.00% |
| Recall | 30.74% | 41.80% |
| F1-Score | 38.36% | 45.54% |

## Referensi

Referensi jurnal yang digunakan terdapat pada folder **Jurnal/**.

## Mata Kuliah

UAS Kecerdasan Buatan

Program Studi Teknik Informatika

Institut Teknologi Garut

## Cara Menjalankan
1. Buka file `UAS_Uji_Kelayakan_Air_Minum.ipynb` di Google Colab.
2. Upload dataset `water_potability.csv`.
3. Jalankan semua *cell* secara berurutan.
