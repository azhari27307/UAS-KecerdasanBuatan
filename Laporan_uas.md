# LAPORAN UAS KECERDASAN BUATAN

## 1. Judul Proyek
**Prediksi Kelayakan Air Minum (Water Potability) Berdasarkan Parameter Kimia Menggunakan Algoritma Klasifikasi**

**Nama Kelompok:**
1. Azhari Ahmad Fauzani (NIM: 2406107)
2. Luthfi Muhammad Fikri (NIM: 2406003) 

**Domain Proyek (Latar Belakang):**
Akses terhadap air minum yang aman dan bersih merupakan kebutuhan dasar manusia yang sangat penting untuk menjaga kesehatan masyarakat. Air yang tidak memenuhi standar kualitas dapat menjadi media penyebaran berbagai penyakit sehingga kualitas air perlu terus dipantau dan dijaga (Adhitama et al., 2017; Palupi, 2025). Penentuan kualitas air pada umumnya dilakukan melalui pengujian berbagai parameter kualitas air di laboratorium, baik parameter fisika, kimia, maupun mikrobiologi. Pengujian tersebut memerlukan waktu, biaya, dan tenaga ahli untuk memperoleh hasil yang akurat (Adhitama et al., 2017).

Perkembangan teknik machine learning memungkinkan proses klasifikasi kualitas air dilakukan secara otomatis berdasarkan data parameter kualitas air sehingga dapat membantu proses identifikasi awal kondisi air secara lebih cepat dibandingkan pengujian manual (Palupi, 2025; Syarifuddin, 2022; Fattah, 2024).

## 2. Business Understanding

**Permasalahan Dunia Nyata dan Literatur Review:**
Akses terhadap air bersih merupakan indikator penting dalam menjaga kesehatan masyarakat. Namun kualitas air dapat mengalami penurunan akibat pencemaran sehingga diperlukan proses pemantauan secara berkala. Pengujian kualitas air secara konvensional masih bergantung pada pemeriksaan laboratorium sehingga membutuhkan waktu dan biaya yang relatif besar (Adhitama et al., 2017).

Berbagai penelitian menunjukkan bahwa algoritma klasifikasi seperti Decision Tree, Naïve Bayes, K-Nearest Neighbor (KNN), maupun Support Vector Machine (SVM) mampu digunakan untuk mengklasifikasikan kualitas air dengan tingkat akurasi yang cukup baik sehingga dapat dimanfaatkan sebagai alat bantu dalam proses evaluasi awal kualitas air (Palupi, 2025; Syarifuddin, 2022; Fattah, 2024).

**Tujuan Proyek:**
Membangun dan membandingkan kinerja model *machine learning* untuk memprediksi secara akurat apakah suatu sampel air layak minum atau tidak layak minum berdasarkan metrik kandungan kimianya.

**Siapa Pengguna Sistem:**
* Instansi pengawasan kesehatan lingkungan dan masyarakat.
* Fasilitas pengolahan air bersih pelat merah maupun swasta.
* Peneliti lingkungan yang membutuhkan alat bantu penapisan awal kualitas sumber air di suatu daerah.

**Solusi dan Manfaat Implementasi AI:**
Solusi yang ditawarkan adalah sebuah sistem penapisan otomatis berbasis klasifikasi data tabular. Manfaat utamanya meliputi efisiensi waktu evaluasi kelayakan air, penghematan alokasi biaya pengujian laboratorium awal, dan kemampuan identifikasi cepat terhadap air yang terkontaminasi untuk mencegah masalah kesehatan di masyarakat.

Berbagai penelitian juga menunjukkan bahwa penerapan teknik data mining dan machine learning mampu membantu proses klasifikasi kualitas air berdasarkan parameter yang tersedia sehingga dapat menghasilkan prediksi kualitas air secara lebih cepat (Palupi, 2025; Fattah, 2024).

## 3. Data Understanding

**Sumber Data:**
Data yang digunakan dalam proyek ini merupakan dataset publik yang diperoleh dari platform Kaggle dengan topik *Water Quality Dataset*.

**Deskripsi Setiap Fitur:**
Dataset ini merekam berbagai parameter kimia dan fisik, di antaranya:
* **pH:** Tingkat keasaman atau kebasaan sampel air.
* **Hardness:** Kapasitas air untuk mengendapkan sabun yang disebabkan oleh kalsium dan magnesium.
* **Solids:** Total padatan yang terlarut dalam air.
* **Chloramines:** Jumlah senyawa kloramin dalam air.
* **Sulfate:** Jumlah senyawa sulfat terlarut dalam air.
* **Conductivity:** Tingkat konduktivitas listrik air.
* **Organic_carbon:** Konsentrasi karbon organik total.
* **Trihalomethanes:** Jumlah senyawa trihalometana.
* **Turbidity:** Tingkat kekeruhan sampel air.
* **Potability:** Metrik penentu status kelayakan air.

**Ukuran dan Format Data:**
* Format Data: CSV 
* Ukuran Data: Terdiri dari 3276 baris sampel pengujian dan 10 kolom fitur.

Sebelum dilakukan proses pemodelan, dilakukan pemeriksaan terhadap nilai kosong (*missing value*) pada setiap atribut dataset. Hasil pemeriksaan menunjukkan bahwa terdapat tiga atribut yang memiliki nilai kosong, yaitu **pH** sebanyak **491 data**, **Sulfate** sebanyak **781 data**, dan **Trihalomethanes** sebanyak **162 data**. Sementara itu, atribut lainnya tidak memiliki nilai kosong sehingga hanya ketiga atribut tersebut yang memerlukan proses imputasi pada tahap *data preparation*.

| Fitur | Jumlah Data Kosong |
|-------|-------------------:|
| pH | 491 |
| Hardness | 0 |
| Solids | 0 |
| Chloramines | 0 |
| Sulfate | 781 |
| Conductivity | 0 |
| Organic_carbon | 0 |
| Trihalomethanes | 162 |
| Turbidity | 0 |
| Potability | 0 |

**Tabel Jumlah Data Kosong pada Setiap Fitur**

**Tipe Data dan Target Klasifikasi:**
* **Tipe Data:** Seluruh fitur prediktor berjenis numerik bertipe *float* atau angka desimal.
* **Target Klasifikasi:** Atribut target klasifikasinya adalah **Potability** yang berisi nilai biner, yaitu `1` (Layak Minum) dan `0` (Tidak Layak Minum).

## 4. Exploratory Data Analysis (EDA)

**Visualisasi Distribusi Data:**
Berdasarkan pengecekan distribusi pada target `Potability`, ditemukan adanya ketidakseimbangan kelas. Jumlah sampel air dengan kategori `0` (Tidak Layak) lebih dominan dibandingkan dengan kategori `1` (Layak).

<img width="549" height="393" alt="image" src="https://github.com/user-attachments/assets/dcbec975-bc07-4320-af00-5a97359b0578" />

**Analisis Korelasi Antar Fitur:**
Berdasarkan visualisasi matriks korelasi, hampir seluruh parameter kimia air menunjukkan nilai korelasi linier yang sangat lemah (mendekati 0). Nilai korelasi paling menonjol hanya berada pada angka -0.17 antara fitur Solids dan Sulfate. Hal ini menandakan tidak terjadinya multikolinearitas antar variabel prediktor.

<img width="866" height="783" alt="image" src="https://github.com/user-attachments/assets/92956983-2ad7-4555-a23e-197e200e3130" />

**Deteksi Data Tidak Seimbang:**
Ketimpangan proporsi pada variabel target menunjukkan bahwa dataset ini termasuk dalam kategori data tidak seimbang. Hal ini berpotensi membuat model pembelajaran mesin lebih mudah mengenali kelas mayoritas.

**Insight Awal dari Pola Data:**
Ketiadaan korelasi yang kuat antar parameter kimia menunjukkan bahwa setiap fitur berdiri sendiri dan memberikan informasi yang unik. Oleh karena itu, seluruh fitur (9 kolom) layak dipertahankan untuk fase pemodelan tanpa perlu ada pemangkasan dimensi. Selain itu, perlu diwaspadai bahwa ketidakseimbangan target kelas berisiko menghasilkan akurasi yang bias terhadap kelas dominan.

## 5. Data Preparation

**Pembersihan Data:**
Proses penanganan data kosong (*null value*) dilakukan menggunakan teknik imputasi. Berdasarkan identifikasi awal, terdapat nilai kosong pada kolom `ph`, `Sulfate`, dan `Trihalomethanes`. Nilai-nilai kosong tersebut diisi menggunakan nilai rata-rata (*mean*) dari masing-masing kolom terkait untuk mempertahankan keutuhan jumlah baris data.

**Encoding Data Kategorik:**
Tahap *encoding* (seperti *label encoding* atau *one-hot encoding*) tidak diterapkan pada proyek ini karena seluruh sembilan fitur parameter kualitas air di dalam dataset sudah berekstensi numerik (*float*).

**Normalisasi / Standardisasi Data Numerik:**
Seluruh fitur numerik distandarisasi menggunakan fungsi `StandardScaler`. Proses penyamaan skala angka ini sangat esensial karena kita menggunakan algoritma K-Nearest Neighbors (KNN) yang menghitung metrik jarak antar titik data. Tanpa standarisasi, fitur dengan rentang angka yang besar (seperti `Solids` atau `Sulfate`) akan mendominasi perhitungan model.

**Split Data (Train-Test):**
Dataset dipisahkan ke dalam variabel fitur prediktor (X) dan variabel target (y), kemudian dibagi dengan rasio **80:20** menggunakan *random state*. Berdasarkan hasil eksekusi pemisahan data, diperoleh:
*   Jumlah data latih (*training*): 2620 sampel
*   Jumlah data uji (*testing*): 656 sampel

## 6. Modeling

**Pemilihan Algoritma:**
Berbagai algoritma machine learning telah banyak dibandingkan untuk menyelesaikan permasalahan klasifikasi sehingga pemilihan algoritma yang sesuai menjadi salah satu faktor penting dalam memperoleh performa model yang optimal (Setiawati, 2023).
Pada proyek ini, digunakan 2 (dua) algoritma klasifikasi *machine learning*, yaitu:
1. Decision Tree (Pohon Keputusan)
2. K-Nearest Neighbors (KNN)

**Alasan Pemilihan 2 Algoritma:**
*   **Decision Tree:** Dipilih karena memiliki kemampuan menghasilkan aturan keputusan yang mudah dipahami dan banyak digunakan dalam penelitian klasifikasi kualitas air dengan tingkat akurasi yang baik (Palupi, 2025).
*   **K-Nearest Neighbors (KNN):** K-Nearest Neighbors dipilih karena bekerja berdasarkan kedekatan jarak antar data dan telah terbukti mampu digunakan untuk klasifikasi kualitas air menggunakan parameter fisika maupun kimia (Syarifuddin, 2022).
  
**Implementasi Model:**
Implementasi dilakukan menggunakan pustaka `scikit-learn` melalui bahasa pemrograman Python:
*   Model Decision Tree dibangun menggunakan kelas `DecisionTreeClassifier` dengan membatasi kedalaman maksimum pohon (`max_depth=4`) untuk menjaga agar model tidak *overfitting* serta hasil visualisasinya tetap mudah dibaca.
*   Model KNN dibangun menggunakan kelas `KNeighborsClassifier` dengan konfigurasi tetangga terdekat sebanyak 5 (`n_neighbors=5`).
*(Catatan: Kode implementasi secara utuh terdapat di dalam file `uas_model.ipynb`).*

**Perbandingan Model:**
Kedua algoritma dilatih menggunakan himpunan data latih yang sama (`X_train_scaled` dan `y_train`). Setelah model mengenali pola data, keduanya diinstruksikan untuk memprediksi kelayakan air pada himpunan data uji (`X_test_scaled`) agar komparasinya berjalan secara adil.

**Visualisasi Model:**
Visualisasi bentuk percabangan dari algoritma Decision Tree telah berhasil di-*render* (menggunakan plot_tree). Grafik pohon keputusan menampilkan titik-titik pemisahan (node) seperti pada kondisi kandungan `Sulfate <= -2.11`, `pH <= -0.676`, dan batas impuritas (gini), yang bermuara pada keputusan akhir di setiap daun (*leaf*) untuk kelas 'Layak' atau 'Tidak Layak'.

<img width="2345" height="1205" alt="image" src="https://github.com/user-attachments/assets/f803bbec-2c33-487c-82ab-914d21ea1d3f" />

## 7. Evaluation

**Confusion Matrix:**

<img width="1189" height="390" alt="image" src="https://github.com/user-attachments/assets/81201213-bcfb-4938-8e1e-a5afaab67877" />

Berdasarkan hasil pengujian pada 656 data uji, didapatkan performa klasifikasi sebagai berikut:
*   **Decision Tree:** Model ini mampu mengklasifikasikan 340 sampel sebagai 'Tidak Layak' (True Negative) dengan tepat, namun memiliki 169 kesalahan klasifikasi pada sampel 'Layak' (False Negative).
*   **K-Nearest Neighbors (KNN):** Model ini mampu mengklasifikasikan 310 sampel sebagai 'Tidak Layak' (True Negative), dengan jumlah prediksi positif yang lebih seimbang dibandingkan Decision Tree.

**Metrik Evaluasi:**
### Perbandingan Metrik Evaluasi Model

| Metrik | Decision Tree | K-Nearest Neighbors (KNN) |
|--------|--------------:|--------------------------:|
| Accuracy | **63.26%** | 62.80% |
| Precision | **51.02%** | 50.00% |
| Recall | 30.74% | **41.80%** |
| F1-Score | 38.36% | **45.54%** |

**Tabel 7.1 Perbandingan Metrik Evaluasi Model Decision Tree dan K-Nearest Neighbors (KNN)**

**Analisis Hasil:**
Dari perbandingan metrik di atas, model **Decision Tree** unggul dalam tingkat akurasi secara keseluruhan (63.26%) dibandingkan model KNN (62.80%). Namun, jika meninjau dari nilai **Recall** dan **F1-Score**, model **KNN** memberikan performa yang lebih baik dalam mendeteksi sampel air layak minum (kategori positif). Hal ini menunjukkan bahwa Decision Tree sedikit lebih cenderung bias terhadap kelas mayoritas ('Tidak Layak'), sedangkan KNN memberikan hasil klasifikasi yang lebih moderat di antara kedua kelas tersebut.

Hasil penelitian ini juga menunjukkan kecenderungan yang serupa dengan beberapa penelitian terdahulu bahwa algoritma Decision Tree dan KNN mampu digunakan untuk melakukan klasifikasi kualitas air, meskipun tingkat akurasi sangat dipengaruhi oleh karakteristik dataset yang digunakan (Palupi, 2025; Syarifuddin, 2022).

## 8. Kesimpulan dan Rekomendasi

**Ringkasan Hasil Modeling dan Evaluasi:**
Kedua algoritma klasifikasi berhasil diimplementasikan untuk memisahkan sampel air yang aman dan berbahaya dengan kinerja akurasi di atas 62%. Secara umum, model Decision Tree memberikan akurasi keseluruhan yang paling optimal di antara keduanya.

**Apakah Tujuan Proyek Tercapai?**
Tujuan proyek untuk membangun sistem prediksi awal kualitas air telah tercapai. Sistem sudah mampu membaca parameter kimia dan mengeluarkan prediksi status kelayakannya secara otomatis.

**Kelebihan dan Keterbatasan Model:**
*   **Kelebihan:** Proses komputasinya sangat cepat dan efisien.
*   **Keterbatasan:** Akurasi di angka 63% masih tergolong rendah untuk langsung diimplementasikan pada sektor kesehatan krusial tanpa pengawasan ahli. Tingkat metrik Recall yang rendah menunjukkan bahwa model masih cukup sering keliru menilai air yang sebenarnya layak minum menjadi tidak layak.

**Rekomendasi Perbaikan:**
Untuk pengembangan selanjutnya, disarankan menambah kuantitas sampel dataset untuk mengatasi ketidakseimbangan kelas. Penggunaan algoritma *ensemble* tingkat lanjut seperti Random Forest atau XGBoost, serta penerapan *hyperparameter tuning*, sangat direkomendasikan guna mendongkrak persentase akurasi di masa depan.

**Kesimpulan:**
Hasil penelitian ini sejalan dengan penelitian Palupi (2025), Syarifuddin (2022), dan Fattah (2024) yang menunjukkan bahwa algoritma machine learning dapat diterapkan untuk melakukan klasifikasi kualitas air berdasarkan parameter yang tersedia.

## 9. Referensi
*   Adhitama, Y., Rosyid, R., & Amalyah. (2017). Analisis kualitas air minum depot isi ulang sebagai indikasi pencemaran melalui pengujian total coli di wilayah Kalibata. Jurnal TechLINK, 1(2), 35–44.
*   Fattah, N. F. (2024). Penerapan data mining untuk klasifikasi kualitas air dengan algoritma Support Vector Machine pada Dinas Lingkungan Hidup dan Pertanahan Provinsi Sumatera Selatan. Jurnal PROSISKO, 11(2), 145–158.
*   Palupi, E. S. (2025). Klasifikasi kualitas air bersih di Jakarta menggunakan algoritma Decision Tree dan algoritma Naïve Bayes. JATI (Jurnal Mahasiswa Teknik Informatika), 9(1), 1259–1265.
*   Setiawati, I. (2023). Komparasi algoritma machine learning dari dataset prediksi analisis butir soal harian siswa. Jurnal Cakrawala Informasi, 3(1), 1–7.
*   Syarifuddin, M. N. (2022). Klasifikasi kualitas air pada program penyediaan air minum dan sanitasi berbasis masyarakat Desa Semenpinggir dengan metode algoritma K-Nearest Neighbor. Jurnal Multidisciplinary Applications of Quantum Information Science (Al-Mantiq), 2(1), 55–61.

## 10. Lampiran (Opsional)
*   File data asli dan jurnal rujukan berada di dalam folder `Dataset/`
*   File *source code* berada di folder notebook
*   File Pustaka berada di folder Jurnal
