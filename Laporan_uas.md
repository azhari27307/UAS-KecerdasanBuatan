# LAPORAN UAS KECERDASAN BUATAN

## 1. Judul Proyek
**Prediksi Kelayakan Air Minum (Water Potability) Berdasarkan Parameter Kimia Menggunakan Algoritma Klasifikasi**

**Nama Kelompok:**
1. Azhari Ahmad Fauzani (NIM: 2406107)
2. Luthfi Muhammad Fikri (NIM: 2406003) 

**Domain Proyek (Latar Belakang):**
Akses terhadap air minum yang aman dan bersih adalah kebutuhan dasar manusia dan faktor krusial dalam menjaga kesehatan masyarakat. Secara tradisional, penentuan status kelayakan air (potabilitas) memerlukan pengujian laboratorium yang ekstensif terhadap berbagai parameter kimia dan fisik, seperti tingkat pH, kekerasan air (hardness), kandungan sulfat, trihalometana, dan karbon organik. Proses uji laboratorium ini seringkali memakan waktu, membutuhkan biaya yang tidak sedikit, dan bergantung pada tenaga ahli khusus. 

Dengan pesatnya pemanfaatan Kecerdasan Buatan (AI) pada domain kesehatan dan lingkungan, pendekatan *machine learning* menawarkan solusi pendamping yang lebih cepat dan efisien. Proyek ini bertujuan untuk menganalisis dan membangun model klasifikasi yang mampu memprediksi secara otomatis apakah suatu sampel air aman untuk dikonsumsi atau tidak berdasarkan metrik kandungan kimianya. Implementasi sistem klasifikasi ini diharapkan dapat menjadi alat bantu evaluasi awal yang cepat, sehingga risiko penyakit akibat konsumsi air yang tidak memenuhi standar kesehatan dapat dicegah lebih dini.

## 2. Business Understanding

**Permasalahan Dunia Nyata dan Literatur Review:**
Akses terhadap air bersih merupakan indikator utama kualitas kesehatan masyarakat. Namun, kualitas sumber air sering terancam oleh pencemaran bahan kimia. Secara tradisional, pengujian kualitas air dilakukan melalui serangkaian proses laboratorium kimia yang kompleks, memakan waktu lama, dan membutuhkan biaya tinggi [1]. Penelitian terdahulu menunjukkan bahwa penerapan algoritma klasifikasi mampu mendeteksi kelayakan air berdasarkan parameter fisika dan kimia dengan tingkat presisi yang baik, sehingga dapat mempercepat proses evaluasi tanpa harus selalu bergantung penuh pada uji laboratorium konvensional [2]. *(Catatan untuk Rhey: Ganti angka di dalam kurung siku dengan nama penulis jurnal yang relevan nanti ya).*

**Tujuan Proyek:**
Membangun dan membandingkan kinerja model *machine learning* untuk memprediksi secara akurat apakah suatu sampel air layak minum atau tidak layak minum berdasarkan metrik kandungan kimianya.

**Siapa Pengguna Sistem:**
* Instansi pengawasan kesehatan lingkungan dan masyarakat.
* Fasilitas pengolahan air bersih pelat merah maupun swasta.
* Peneliti lingkungan yang membutuhkan alat bantu penapisan awal kualitas sumber air di suatu daerah.

**Solusi dan Manfaat Implementasi AI:**
Solusi yang ditawarkan adalah sebuah sistem penapisan otomatis berbasis klasifikasi data tabular. Manfaat utamanya meliputi efisiensi waktu evaluasi kelayakan air, penghematan alokasi biaya pengujian laboratorium awal, dan kemampuan identifikasi cepat terhadap air yang terkontaminasi untuk mencegah masalah kesehatan di masyarakat.

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
* Ukuran Data: Terdiri dari 3276 baris sampel pengujian dan 10 kolom fitur. *(Catatan: Sesuaikan angka 3276 ini dengan jumlah baris persis dari dataset Kaggle yang kamu download nanti).*

**Tipe Data dan Target Klasifikasi:**
* **Tipe Data:** Seluruh fitur prediktor berjenis numerik bertipe *float* atau angka desimal.
* **Target Klasifikasi:** Atribut target klasifikasinya adalah **Potability** yang berisi nilai biner, yaitu `1` (Layak Minum) dan `0` (Tidak Layak Minum).
