# Prediksi Kelayakan Air Minum Menggunakan Machine Learning

## Deskripsi Proyek

Proyek ini merupakan tugas UAS Mata Kuliah **Kecerdasan Buatan** yang bertujuan membangun model *machine learning* untuk memprediksi apakah suatu sampel air layak dikonsumsi (*potable*) atau tidak berdasarkan parameter kimia yang terdapat pada dataset.

Algoritma yang digunakan pada proyek ini adalah:

- Decision Tree
- K-Nearest Neighbors (KNN)

Model dikembangkan menggunakan bahasa pemrograman **Python** dengan pustaka **scikit-learn**.

---

## Anggota Kelompok

| Nama | NIM |
|------|-----|
| Azhari Ahmad Fauzani | 2406107 |
| Luthfi Muhammad Fikri | 2406003 |

---

## Struktur Repository

```text
UAS-KecerdasanBuatan/
├── README.md
├── Laporan_uas.md
├── uas_model.ipynb
└── data/
    ├── dataset/
    └── Jurnal/
```

---

## Dataset

Dataset yang digunakan adalah **Water Potability Dataset** yang diperoleh dari Kaggle.

Informasi dataset:

- Jumlah data: 3276
- Jumlah fitur: 9
- Target: Potability (Layak/Tidak Layak)

---

## Tahapan Proyek

### 1. Data Understanding
Memahami karakteristik dataset, sumber data, atribut, serta target klasifikasi.

### 2. Exploratory Data Analysis (EDA)
Melakukan analisis distribusi data, hubungan antar fitur, dan mengidentifikasi karakteristik dataset melalui visualisasi.

### 3. Data Preparation
Membersihkan data, menangani nilai kosong, melakukan normalisasi, dan membagi dataset menjadi data latih dan data uji.

### 4. Modeling
Membangun model menggunakan algoritma Decision Tree dan K-Nearest Neighbors (KNN), kemudian membandingkan performanya.

### 5. Evaluation
Mengevaluasi model menggunakan Confusion Matrix, Accuracy, Precision, Recall, dan F1-Score untuk menentukan model terbaik.

---

## Algoritma yang Digunakan

- Decision Tree
- K-Nearest Neighbors (KNN)

---

## Hasil Evaluasi

| Metrik | Decision Tree | KNN |
|--------|--------------:|----:|
| Accuracy | 63.26% | 62.80% |
| Precision | 51.02% | 50.00% |
| Recall | 30.74% | 41.80% |
| F1-Score | 38.36% | 45.54% |

---

## Cara Menjalankan Proyek

1. Clone atau unduh repository ini.
2. Buka file `UAS_Uji_Kelayakan_Air_Minum.ipynb` menggunakan Google Colab atau Jupyter Notebook.
3. Pastikan dataset tersedia pada folder `data/dataset/`.
4. Jalankan seluruh *cell* secara berurutan.
5. Hasil evaluasi model akan ditampilkan pada bagian akhir notebook.

---

## Laporan

Laporan lengkap mengenai Business Understanding, Data Understanding, EDA, Data Preparation, Modeling, Evaluation, Kesimpulan, dan Referensi tersedia pada file **Laporan_uas.md**.

---

## Referensi

Referensi jurnal ilmiah yang digunakan pada penelitian ini terdapat pada folder **data/Jurnal/**.

---

## Mata Kuliah

- **Mata Kuliah:** Kecerdasan Buatan
- **Program Studi:** Teknik Informatika
- **Institut:** Institut Teknologi Garut
