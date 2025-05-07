# Laporan Proyek Machine Learning - Sinta Siti Nuriah
---

### By. [Sinta Siti Nuriah](https://www.linkedin.com/in/sintasitinuriah/) 
![job](https://eduauraapublic.s3.ap-south-1.amazonaws.com/webassets/images/blogs/highest-paying-jobs-in-india.jpg)

## Domain Proyek
Terdapat sekitar 80% mahasiswa di Indonesia bekerja tidak sesuai dengan jurusan kuliahnya. Padahal anggapan bahwa jurusan kuliah akan menentukan arah karier di masa depan masih banyak dipercayai oleh masyarakat[Afero et al. (2023)](https://e-journals.unmul.ac.id/index.php/PSIKO/article/view/12315). Hal-hal yang menyebabkan tejadinya kekeliruan ini antara lain:
- Minat, dan misi akan berubah seiring berjalannya waktu
- Lowongan kerja terbatas, tidak sebanding dengan jumlah lulusan. Hal ini menyebabkan statement "Dari pada gak kerja, mending kerjain yang ada!"

Masalah ini perlu diselesaikan secepatnya, mengingat angka pengangguran pada tahun 2023 di Indonesia mencapai 7,86 juta orang, atau setara dengan 5,32% dari total angkatan kerja nasional[Frisnoiry et al. (2024)](https://journal.stekom.ac.id/index.php/kompak/article/view/1866). Kemungkinan terbesar angka pengangguran ini akan bertambah seiring berjalannya waktu, maka dari itu harapan untuk pengembaagan job recommendation system ini menjadi solusi untuk meminimaliris angkan pengangguran dan pekerjaan yang tidak sesuai dengan bidangnya. 

---
# Business Understanding

## a. Problem Statement
- Tingginya ketidaksesuaian antara pekerjaan dan jurusan kuliah.
  Sekitar 80% mahasiswa di Indonesia bekerja tidak sesuai dengan jurusannya. Hal ini menimbulkan masalah ketidaksesuaian keterampilan dan berisiko menurunkan produktivitas kerja.
- Minat dan misi karier individu berubah seiring waktu.
  Banyak mahasiswa yang saat memilih jurusan belum memiliki pemahaman utuh tentang minat dan arah karier jangka panjang, sehingga pilihan jurusan tidak selalu mencerminkan preferensi karier saat lulus.
- Ketidakseimbangan antara jumlah lulusan dan lowongan pekerjaan.
  Jumlah lulusan yang terus meningkat tidak sebanding dengan jumlah lapangan kerja yang tersedia, sehingga banyak lulusan terpaksa bekerja di bidang yang tidak sesuai atau bahkan menganggur.
- Kurangnya sistem yang dapat merekomendasikan pekerjaan secara personal.
  Saat ini belum banyak sistem yang dapat membantu pencari kerja mencocokkan profil akademik dan minat mereka dengan kebutuhan pasar tenaga kerja secara efektif dan otomatis.

## b. Goals
- Mengurangi tingkat mismatch antara jurusan dan pekerjaan.
  Dengan menyediakan sistem rekomendasi pekerjaan yang mempertimbangkan latar belakang pendidikan dan kompetensi individu.
- Membantu mahasiswa memahami potensi karier yang sesuai dengan perkembangan minat dan keterampilan mereka.
  Sistem yang fleksibel dan adaptif terhadap perubahan preferensi individu selama masa studi hingga setelah lulus.
- Mengembangkan job recommendation system berbasis data.
  Untuk mendukung pengambilan keputusan karier secara objektif, terarah, dan berbasis kecocokan antara profil pribadi dan permintaan pasar.

## c. Solution Statement
- Mengembangkan sistem rekomendasi pekerjaan berbasis Content-Based Filtering.
- Mengintegrasikan Collaborative Filtering untuk meningkatkan personalisasi.
- Melakukan evaluasi terhadap model.
---

# Data Understanding
Dataset yang digunakan dengan keterangan sebagai berikut:
| Jenis      | Keterangan                                                                 |
|------------|------------------------------------------------------------------------------|
| Title      | Job Recommendation Dataset                                                 |
| Source     | [Kaggle](https://www.kaggle.com/datasets/lastman0800/job-recomendation-dataset) |
| License    | Unknown Authors                                               |
| Visibility | Public                                                                      |
| Tags       | Data Analytics, Data Visualization, Data Cleaning Classification                                   |
| Usability  | 4.71                                                                       |

Dataset yang disediakan adalah dataset rekomendasi pekerjaan yang terdiri dari enam kolom. Setiap baris dalam dataset ini merepresentasikan satu catatan unik yang menghubungkan seorang pengguna dengan sebuah pekerjaan dan mengevaluasi kesesuaian pekerjaan tersebut untuk pengguna. Berikut adalah penjelasan rinci dari masing-masing kolom dalam dataset:

| Kolom             | Tipe Data       | Deskripsi                                                                                         |
|-------------------|------------------|---------------------------------------------------------------------------------------------------|
| User_ID           | Integer          | ID unik untuk setiap pengguna dalam dataset.                                                     |
| Job_ID            | Integer          | ID unik untuk setiap pekerjaan dalam dataset.                                                    |
| User_Skills       | String (CSV)     | Daftar keterampilan yang dimiliki pengguna, dipisahkan dengan koma.                              |
| Job_Requirements  | String (CSV)     | Daftar keterampilan yang dibutuhkan untuk pekerjaan, dipisahkan dengan koma.                     |
| Match_Score       | Float (0 - 1)    | Skor kecocokan antara keterampilan pengguna dan kebutuhan pekerjaan. Semakin tinggi, semakin cocok. |
| Recommended       | Integer (0 atau 1)| Indikator biner: 1 jika pekerjaan direkomendasikan, 0 jika tidak.                                |


Jumlah data pada dataset ini adalah:
|Jumlah Baris |Jumlah Kolom|
|-------------|------------|
|100000         |6          |

Setiap Kolom pada dataset ini memiliki jumblah baris yang sama yaitu sekitar 100000 baris.

### a. Deskripsi Variabel
Dari hasil diatas terdapat:
- Total tabel yang ada pada dataset tersebut adalah 6 kolom
- tipe data `object` ada 2 kolom yaitu `User_Skills` dan `Job_Requirements`
- tipe data `int64` ada 3 kolom yaitu `User_ID`, `Job_ID`, dan `Recommended`
- tipe data `float64` hanya satu yaitu `Match_Score`

### b. Kondisi Data
- Dataset ini tidak memiliki nilai null/nan.
- Dataset ini tidak memiliki nilai duplikat.
- Dataset ini memiliki outliers pada fitur `User_ID`, `Job_ID`, `Match_Score` dan `Recommended`

### d. Univariate Analysis
- Visualisasi distribusi boxplot
![box](image/boxplot.png)
- Visualisasi distribusi histogram
![hist](image/unvariate-hist.png)

### e. Multivariate Analysis
- Korelasi antar variabel numerik dilakukan dengan heatmap atau matriks korelasi.
![corr](image/corr.png)
- Visualisasi Pairplot numerical columns 
![pair](image/pair.png)
- Visualisasi Top 10 User Skills
![skill](image/skill.png)
-Visualisasi Top 10 Job Requirements
![job](image/job.png)

---
# Data Preprocessing
## Penganganan Outliers
- Strategi penanganan Outliers pada `User_ID`, `Job_ID`, `Match_Score` dan `Recommended Menggunakan metode **IQR (Interquartile Range)**. Jumlah baris dataset setelah penanganan outlier sebanyak 80.073.

## Konversi Skills dan Job Requirements menjadi set
Konversi ini digunakan untuk preprocessing pada model lightFM.

## TF-IDF 
**TF-IDF (Term Frequency - Inverse Document Frequency)** adalah teknik vektorisasi teks yang digunakan untuk menilai seberapa penting suatu kata dalam sebuah dokumen relatif terhadap semua dokumen lainnya dalam kumpulan data.

- **TF (Term Frequency):** Mengukur seberapa sering kata muncul dalam dokumen.
- **IDF (Inverse Document Frequency):** Mengukur seberapa unik kata tersebut di seluruh dokumen.

Rumus:
```
TF-IDF(t, d) = TF(t, d) * log(N / DF(t))
```
Dimana:
- `t` adalah kata (term)
- `d` adalah dokumen (user skill/job requirement)
- `N` adalah jumlah total dokumen
- `DF(t)` adalah jumlah dokumen yang mengandung term `t`

TF-IDF membantu menonjolkan kata-kata penting yang bersifat spesifik dan mengurangi bobot kata-kata umum seperti "dan", "atau", "adalah", dll.

## Pre-processing Collaborative Filtering
### Inisialisasi Dataset

```python
from lightfm.data import Dataset

dataset = Dataset()
```

* Membuat objek Dataset untuk memetakan user dan item (pekerjaan) ke dalam indeks numerik.

### Fit ID Pengguna dan Pekerjaan

```python
dataset.fit(df['User_ID'], df['Job_ID'])
```

* Mendaftarkan semua user dan pekerjaan untuk digunakan dalam sistem rekomendasi.

### Buat Tuple Interaksi

```python
interactions = list(zip(df['User_ID'], df['Job_ID']))
interactions_labels = df['Recommended'].astype(float)
```

* Membuat pasangan user-job dan label interaksi sebagai masukan ke LightFM.

### Membangun Interaction Matrix

```python
(interaction_matrix, _) = dataset.build_interactions(zip(df['User_ID'], df['Job_ID'], interactions_labels))
```

* Interaction matrix akan menjadi input utama untuk proses pelatihan.

## Pembagian Data
- **Tujuan:** Memisahkan data menjadi data latih dan data uji untuk mengevaluasi performa model secara adil.
- **Metode:** `random_train_test_split` dari lightfm.
  - Rasio: 80% data latih dan 20% data uji.

# Model Development
## Content Based Filtering
### NearestNeighbors
**NearestNeighbors** dari sklearn adalah metode memory-based collaborative filtering. Ia mencari item terdekat (neighbors) menggunakan metrik kesamaan (misalnya cosine similarity).

**Keunggulan**:
  - Mudah diimplementasikan.
  - Tidak memerlukan proses training.
  - Sangat cocok untuk dataset kecil atau sedang.

## Collaborative Filtering
### LightFM
**LightFM** adalah library Python yang menggabungkan collaborative filtering dan content-based filtering melalui model pembelajaran representasi (embedding). LightFM menggunakan pembelajaran matrix factorization dengan pendekatan supervised (menggunakan loss function seperti BPR, logistic, hinge, atau WARP).

**Keunggulan**:
  - Dapat memanfaatkan fitur pengguna dan item (content-based).
  - Mendukung rekomendasi untuk item baru (cold start).
  - Cocok untuk skala besar.

# Evaluasi 
## ROC-AUC
**ROC-AUC** adalah metrik evaluasi untuk masalah klasifikasi biner yang mengukur kemampuan model dalam membedakan antara dua kelas (dalam kasusmu: pekerjaan yang direkomendasikan 1 dan tidak 0).

### ROC adalah kurva yang menunjukkan trade-off antara:
- True Positive Rate (TPR): berapa banyak item positif yang berhasil dikenali (juga disebut Recall)
- False Positive Rate (FPR): berapa banyak item negatif yang salah diklasifikasi sebagai positif

### AUC (Area Under Curve) adalah luas di bawah kurva ROC, dengan nilai antara:
- 1.0 = model sempurna
- 0.5 = model tebak-tebakan (random guess)
- < 0.5 = model buruk (prediksi berlawanan)

### Precision@K

**Precision@K** mengukur seberapa banyak rekomendasi yang relevan di dalam **K rekomendasi teratas** yang diberikan oleh model. Precision menghitung **proporsi item relevan** dalam K item yang diprediksi oleh model.

**Rumus Precision@K:**

$
\text{Precision@K} = \frac{\text{Jumlah item relevan di top-K}}{K}
$

Dimana:
- **Jumlah item relevan di top-K** adalah jumlah item yang relevan dalam K rekomendasi teratas.
- **K** adalah jumlah item teratas yang direkomendasikan.

### Recall@K

**Recall@K** mengukur seberapa banyak item relevan yang ditemukan di dalam **K rekomendasi teratas** yang diberikan oleh model. Recall menghitung **proporsi item relevan** yang berhasil diprediksi oleh model dari seluruh item relevan yang ada.

**Rumus Recall@K:**

$
\text{Recall@K} = \frac{\text{Jumlah item relevan di top-K}}{\text{Jumlah total item relevan}}
$

Dimana:
- **Jumlah total item relevan** adalah jumlah keseluruhan item relevan yang seharusnya direkomendasikan kepada pengguna.
- **K** adalah jumlah item teratas yang direkomendasikan.




---
# Referensi 
1. Afero, F. I., Dimala, C. P., & Ibad, M. C. (2023). Self-Efficacy as a Mediation the Influence of Proactive Personality on Career Adaptability in Early Adults. Psikostudia: Jurnal Psikologi, 12(4), 517-523.
2. Frisnoiry, S., Sihotang, H. M., Indri, N., & Munthe, T. (2024). Analisis Permasalahan Pengangguran Di Indonesia. Kompak: Jurnal Ilmiah Komputerisasi Akuntansi, 17(1), 366-375.