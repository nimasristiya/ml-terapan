# Laporan Proyek Machine Learning - Nimas Ristiya Rahma
## Domain Proyek

Proyek ini berfokus pada ekonomi dan bisnis, di mana perusahaan berencana merekrut karyawan baru. Oleh karena itu, perusahaan ingin memperkirakan kisaran gaji yang sesuai berdasarkan pengalaman kerja calon pelamar.

### Latar Belakang
Analisis data merupakan alat yang penting dalam meningkatkan pengambilan keputusan di dunia bisnis. Salah satu aspek yang sering dianalisis adalah hubungan antara pengalaman kerja dan gaji. Penentuan gaji yang adil dan akurat dapat berkontribusi pada retensi karyawan dan kepuasan kerja, yang berujung pada peningkatan produktivitas organisasi [[1]](https://www.researchgate.net/publication/233352028_Multidisciplinarity_Interdisciplinarity_Transdisciplinarity_and_the_Sciences). Dalam konteks ini, penggunaan teknik analisis data seperti predictive analytics dapat membantu perusahaan untuk memahami pola dan tren dalam data historis dan menggunakannya untuk meramalkan gaji berdasarkan pengalaman kerja karyawan [[2]](https://onlinelibrary.wiley.com/doi/full/10.1609/aimag.v17i3.1230).

Dataset "Years of Experience and Employees Salary" yang digunakan dalam proyek ini mencakup dua fitur utama: tahun pengalaman dan gaji. Gaji sering kali dipengaruhi oleh banyak variabel, salah satunya adalah pengalaman kerja [[3]](https://eric.ed.gov/?id=ED103621). Menurut penelitian oleh Card (1999), pengalaman kerja yang lebih lama sering kali terkait dengan gaji yang lebih tinggi, karena pengalaman meningkatkan keterampilan dan efisiensi kerja. Oleh karena itu, model prediktif yang dibangun pada dataset ini bertujuan untuk memprediksi gaji berdasarkan tahun pengalaman yang dimiliki oleh seorang karyawan [[4]](https://davidcard.berkeley.edu/papers/causal_educ_earnings.pdf).

Penerapan model prediksi dalam konteks ini tidak hanya bermanfaat untuk keperluan kompensasi yang lebih adil, tetapi juga dapat digunakan oleh perusahaan untuk merencanakan pengembangan karier dan menetapkan standar gaji di berbagai level pengalaman [[5]](https://www.nber.org/system/files/working_papers/w17985/w17985.pdf). Dalam hal ini, penggunaan model regresi linear atau decision tree akan menjadi metode yang tepat untuk memahami hubungan antara dua variabel tersebut dan memprediksi gaji dengan akurat [[6]](https://www.sas.upenn.edu/~fdiebold/NoHesitations/BookAdvanced.pdf).

Dalam proyek ini, perusahaan akan membangun beberapa model Machine Learning yang kemudian dievaluasi untuk menentukan model dengan prediksi terbaik dalam memperkirakan kisaran gaji berdasarkan pengalaman kerja pelamar.

## Business Understanding
### Problem Statements
Berdasarkan latar belakang proyek, berikut adalah rincian masalah yang akan dibahas:

1. Algoritma mana yang paling sesuai untuk memprediksi kisaran gaji karyawan?
Dengan data yang tersedia mengenai pengalaman kerja karyawan, kita ingin mengetahui model mana yang dapat memprediksi kisaran gaji secara lebih akurat.

2. Bagaimana cara menilai apakah hasil prediksi dari suatu algoritma Machine Learning dapat dianggap baik?
Untuk menilai kualitas model, kita akan menggunakan metrik evaluasi yang dapat mengukur seberapa dekat hasil prediksi dengan nilai sebenarnya, dengan fokus pada Mean Squared Error (MSE) sebagai metrik utama.

### Tujuan
Tujuan dari proyek ini adalah untuk:

1. Mengevaluasi dua algoritma Machine Learning – Linear Regression dan Random Forest – untuk memprediksi kisaran gaji karyawan berdasarkan data pengalaman kerja.

2. Membandingkan kinerja kedua model dalam hal akurasi prediksi, menggunakan metrik MSE untuk menilai seberapa baik model dapat memprediksi gaji yang sebenarnya.

3. Menyarankan algoritma yang lebih baik untuk digunakan dalam konteks bisnis perusahaan, berdasarkan hasil evaluasi metrik MSE pada data latih dan data uji.

### Pernyataan Solusi
Solusi yang diusulkan untuk mencapai tujuan ini melibatkan pembuatan dua model Machine Learning dengan algoritma berikut:

1. Linear Regression
Algoritma ini digunakan untuk memprediksi nilai gaji berdasarkan pengalaman kerja karyawan (variabel independen). Tujuannya adalah untuk menemukan hubungan linear antara variabel input dan output, dengan meminimalkan error antara prediksi dan nilai yang sebenarnya.

Kelebihan: Linear Regression dapat memberikan hasil yang baik jika ada hubungan linier antara pengalaman kerja dan gaji.

Kekurangan: Pada kenyataannya, hubungan antara pengalaman kerja dan gaji mungkin tidak selalu linier, sehingga model ini bisa kurang akurat jika hubungan tersebut lebih kompleks.

2. Random Forest
Algoritma ini digunakan untuk membuat prediksi dengan menggabungkan beberapa pohon keputusan yang lebih kompleks. Random Forest efektif untuk menangani data yang besar dan non-linier, serta dapat mengatasi overfitting dengan lebih baik dibandingkan dengan model tunggal.

Kelebihan: Random Forest dapat menangani dataset besar dan kompleks, serta memberikan akurasi prediksi yang lebih baik dalam banyak kasus.

**Evaluasi Model**
Untuk mengukur seberapa baik model dalam memprediksi gaji karyawan, kita akan menggunakan Mean Squared Error (MSE). MSE mengukur seberapa jauh hasil prediksi model dari nilai sebenarnya, di mana semakin kecil nilai MSE, semakin baik model tersebut.

## Data Understanding

Dataset yang digunakan disediakan oleh [RubyDoby](https://www.kaggle.com/rubydoby) di [Kaggle](https://www.kaggle.com/), diunggah pada Januari 2022: [Years of experience and employees salary](https://www.kaggle.com/datasets/rubydoby/years-of-experience-and-employees-salary).

Dataset ini berisi 1500 baris dan 2 kolom:
- **Years of Experience**: jumlah tahun pengalaman kerja.
- **Salary**: jumlah gaji tahunan dalam dollar.

### Exploratory Data Analysis - Univariate Analysis
![image](https://github.com/user-attachments/assets/0c021315-ae35-4def-a42d-065d4ca87c03)


Dari analisis univariat, sebagian besar pengalaman kerja berkisar antara 8-14 tahun, dan gaji sebagian besar berada dalam rentang 86.000-90.000 dolar.

### Exploratory Data Analysis - Multivariate Analysis
![image](https://github.com/user-attachments/assets/7bd2f981-bf72-4925-8a01-b0c89bdddaf9)


Pola sebaran data menunjukkan korelasi positif antara **Years of Experience** dan **Salary**, dengan skor korelasi sebesar 0.8.

![image](https://github.com/user-attachments/assets/f277ce99-de64-4f06-b3c3-3b416b34a5ae)


## Data Preparation

Tahapan dalam persiapan data meliputi:
- Membagi data menjadi set pelatihan dan pengujian dengan rasio 80:10.
- Standarisasi data menggunakan StandardScaler dari library scikit-learn.

## Modeling

Setelah data siap, dua model akan dibangun:
- **Linear Regression**: Algoritma umum untuk regresi, mudah dipahami namun mungkin tidak selalu tepat untuk setiap kasus.
- **Random Forest**: Dapat menangani noise, missing value, dan dataset besar, tetapi interpretasinya lebih sulit dan memerlukan tuning yang tepat[[9]](https://eprints.umm.ac.id/39299/3/BAB%202.pdf).
- 
### Algoritma Linear Regression
### Cara Kerja Linear Regression
Linear Regression adalah algoritma yang digunakan untuk memodelkan hubungan antara variabel independen (fitur) dan variabel dependen (target) dengan cara menyesuaikan garis lurus (linear) pada data. Model ini berusaha menemukan hubungan linear terbaik antara fitur dan target dengan tujuan meminimalkan kesalahan prediksi yang dihitung menggunakan fungsi error (biasanya Mean Squared Error). 

Model ini dapat dirumuskan sebagai:
\[ y = mX + b \]
Di mana:
- \(y\) adalah target (misalnya gaji yang diprediksi),
- \(X\) adalah fitur (misalnya pengalaman kerja),
- \(m\) adalah koefisien yang menunjukkan kemiringan garis,
- \(b\) adalah intercept yang menunjukkan titik potong pada sumbu \(y\).

#### Parameter yang Digunakan
- **n_jobs**: Menentukan jumlah CPU yang akan digunakan untuk komputasi paralel. Pada model ini, kita menggunakan `n_jobs=-1` yang berarti menggunakan semua inti CPU yang tersedia.
  
  **Penjelasan**: Penggunaan paralelisasi mempercepat proses pelatihan ketika ada banyak data yang digunakan.

#### Kelebihan dan Kekurangan
- **Kelebihan**: 
   - Model yang sederhana dan mudah dipahami.
   - Bagus untuk prediksi ketika hubungan antar fitur dan target memang linier.
- **Kekurangan**:
   - Kurang efektif jika hubungan antara fitur dan target tidak linier, yang mungkin terjadi pada data dunia nyata.

### Algoritma Random Forest

#### Cara Kerja Random Forest
Random Forest adalah algoritma pembelajaran ensemble yang bekerja dengan membangun banyak pohon keputusan (decision trees). Setiap pohon dilatih pada subset acak dari data dan fitur yang ada, dan prediksi akhir dilakukan dengan mengambil rata-rata hasil prediksi dari semua pohon. Pendekatan ini membantu mengurangi overfitting dan meningkatkan akurasi model.

Random Forest bekerja dengan prinsip "bootstrap aggregating" (bagging), yaitu:
1. Mengambil sampel acak dari data pelatihan (dengan pengulangan) untuk setiap pohon keputusan.
2. Membangun pohon keputusan yang tidak dipangkas untuk setiap sampel data.
3. Melakukan prediksi dengan menggabungkan hasil dari seluruh pohon (biasanya dengan voting atau rata-rata untuk regresi).

#### Parameter yang Digunakan
- **n_estimators**: Menentukan jumlah pohon dalam hutan. Dalam model ini, kita menggunakan `n_estimators=50`, yang berarti model akan menggunakan 50 pohon keputusan.
  
  **Penjelasan**: Semakin banyak pohon, semakin baik model dalam menggeneralisasi data, namun membutuhkan lebih banyak waktu komputasi.
  
- **max_depth**: Menentukan kedalaman maksimum untuk setiap pohon keputusan. Pada model ini, kita menggunakan `max_depth=16`.
  
  **Penjelasan**: Kedalaman yang lebih tinggi memungkinkan pohon untuk menangkap kompleksitas data, tetapi dapat menyebabkan overfitting jika terlalu dalam. Pengaturan ini membantu mengontrol overfitting.

- **random_state**: Menentukan seed acak untuk memastikan bahwa pembagian data yang acak atau pemilihan subset acak dari fitur dapat direproduksi. Kita menggunakan `random_state=55`.

- **n_jobs**: Seperti pada Linear Regression, parameter ini mengontrol penggunaan paralelisasi untuk mempercepat pelatihan model.

#### Kelebihan dan Kekurangan
- **Kelebihan**:
   - Dapat menangani hubungan yang lebih kompleks dan non-linier dengan baik.
   - Tidak mudah overfitting karena menggunakan banyak pohon untuk mengambil keputusan kolektif.
   - Dapat menangani data besar dengan banyak fitur.
- **Kekurangan**:
   - Dapat lebih lambat dibandingkan dengan model sederhana seperti Linear Regression, terutama jika jumlah pohon (estimators) sangat besar.
   - Model yang lebih kompleks dan sulit untuk diinterpretasi.

### Penerapan dan Perbandingan Model
Setelah kedua model dibangun, kita akan menguji kinerja mereka menggunakan metrik **Mean Squared Error (MSE)** untuk menilai sejauh mana model dapat memprediksi kisaran gaji karyawan berdasarkan data pengalaman kerja.

Kita akan membandingkan hasil prediksi dari kedua model untuk menentukan algoritma mana yang lebih akurat dalam memprediksi gaji karyawan.

## Evaluation

Evaluasi model dilakukan dengan menggunakan MSE, yang menghitung rata-rata selisih kuadrat antara prediksi dan nilai sebenarnya[[10]](https://www.dicoding.com/academies/319/tutorials/18595).

![image](https://github.com/user-attachments/assets/ca5d665a-dbe7-47c7-91b0-3a40fff99f1f)


### Model dengan Algoritma Linear Regression
![image](https://github.com/user-attachments/assets/34ad19fe-002b-4062-b4e6-66d534e706af)


Model ini menunjukkan nilai MSE yang sangat tinggi, yaitu 113.458 pada pelatihan dan 127.004 pada pengujian, menunjukkan prediksi yang kurang akurat.

![image](https://github.com/user-attachments/assets/d0f285e1-7ef5-4ff6-bfce-080b8a16da1e)


### Model dengan Algoritma Random Forest
![image](https://github.com/user-attachments/assets/57d9ecb1-fcf5-48c3-9140-7a0f5b6870ca)


Model Random Forest memiliki nilai MSE yang lebih rendah, yaitu 13.235 pada pelatihan dan 15.922 pada pengujian, menunjukkan hasil prediksi yang lebih baik dibandingkan Linear Regression.

![image](https://github.com/user-attachments/assets/1ef09b35-62e4-4c74-a6ac-18315f12e7ad)


## Kesimpulan

Berdasarkan hasil evaluasi, model dengan algoritma Random Forest memberikan prediksi yang lebih akurat, sehingga dipilih sebagai model utama untuk memperkirakan gaji karyawan.

## Referensi
[1] https://eric.ed.gov/?id=ED103621

[2] https://www.sas.upenn.edu/~fdiebold/NoHesitations/BookAdvanced.pdf

[3] https://medium.com/@adiptamartulandi/belajar-machine-learning-simple-linear-regression-di-python-e82972695eaf

[4] https://caraguna.com/apa-itu-linear-regression-dalam-machine-learning/

[5] https://davidcard.berkeley.edu/papers/causal_educ_earnings.pdf

[6] https://eprints.umm.ac.id/39299/3/BAB%202.pdf

[7] https://www.dicoding.com/academies/319/tutorials/18595

[8] https://www.researchgate.net/publication/233352028_Multidisciplinarity_Interdisciplinarity_Transdisciplinarity_and_the_Sciences

[9] https://onlinelibrary.wiley.com/doi/full/10.1609/aimag.v17i3.1230

[10] https://majoo.id/solusi/detail/rekrutmen-adalah#:~:text=Rekrutmen%20adalah%20proses%20mencari%20dan,mudah%20mencari%20karyawan%20yang%20berkualitas.

[11] http://riset.unisma.ac.id/index.php/jrm/article/view/8261

[12] https://www.nber.org/system/files/working_papers/w17985/w17985.pdf

[13] https://www.dqlab.id/kenali-analisis-regresi-linear-metode-pengolahan-data-yang-sering-digunakan