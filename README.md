# Laporan Proyek Machine Learning - Nimas Ristiya Rahma
## Domain Proyek

Proyek ini berfokus pada ekonomi dan bisnis, di mana perusahaan berencana merekrut karyawan baru. Oleh karena itu, perusahaan ingin memperkirakan kisaran gaji yang sesuai berdasarkan pengalaman kerja calon pelamar.

### Latar Belakang

Proses rekrutmen adalah kegiatan mencari dan menyeleksi calon karyawan untuk mengisi posisi tertentu[[1]](https://majoo.id/solusi/detail/rekrutmen-adalah#:~:text=Rekrutmen%20adalah%20proses%20mencari%20dan,mudah%20mencari%20karyawan%20yang%20berkualitas.). Rekrutmen menjadi penting karena menentukan kualitas pelamar yang akan bekerja di perusahaan. Salah satu indikator penting dari kualitas karyawan adalah pengalaman kerja; semakin lama pengalaman kerja, semakin baik kualitasnya. Berdasarkan e-Jurnal Riset Manajemen dari PRODI MANAJEMEN Fakultas Ekonomi Unisma, *"Pengalaman kerja adalah jam kerja yang tinggi atau pengalaman yang panjang, di mana pengalaman tersebut membantu dalam memecahkan berbagai masalah serta menyelesaikan tanggung jawab dengan baik sesuai kemampuan individu karyawan"*[[2]](http://riset.unisma.ac.id/index.php/jrm/article/view/8261).

Dalam proyek ini, perusahaan akan membangun beberapa model Machine Learning yang kemudian dievaluasi untuk menentukan model dengan prediksi terbaik dalam memperkirakan kisaran gaji berdasarkan pengalaman kerja pelamar.

## Business Understanding

### Problem Statements

Berdasarkan latar belakang di atas, masalah yang dihadapi adalah:
- Algoritma apa yang paling tepat untuk memprediksi gaji karyawan?
- Bagaimana menentukan apakah prediksi dari suatu model Machine Learning sudah cukup baik?

### Goals

Untuk menjawab pertanyaan di atas:
- Berbagai algoritma dapat digunakan untuk menyelesaikan masalah ini, tetapi proyek ini akan fokus pada penggunaan algoritma Linear Regression dan Random Forest.
- Evaluasi dilakukan untuk membandingkan kinerja kedua algoritma berdasarkan metrik tertentu.

### Solution Statements

Solusi yang diterapkan dalam proyek ini meliputi:
- Membangun dua model Machine Learning, yaitu menggunakan algoritma Linear Regression dan Random Forest.

  * Algoritma Linear Regression memprediksi nilai y berdasarkan x, dengan tujuan menemukan nilai m dan b yang meminimalkan error[[3]](https://medium.com/@adiptamartulandi/belajar-machine-learning-simple-linear-regression-di-python-e82972695eaf).

 ![image](https://github.com/user-attachments/assets/904416e5-eae6-4eda-bad9-9a3103c83073)

   Kelebihannya adalah kemampuannya untuk memprediksi jika terdapat hubungan linear antara variabel independen dan dependen, namun kekurangannya adalah hubungan linear ini jarang terjadi dalam kenyataan[[4]](https://caraguna.com/apa-itu-linear-regression-dalam-machine-learning/).
  
  ![image](https://github.com/user-attachments/assets/a78a11fe-4209-41a4-8cea-0fd779f6bb6d)

  
   * Algoritma Random Forest bekerja dengan menggabungkan beberapa model untuk melakukan prediksi, dan efisien ketika dataset berukuran besar.
   
   ![image](https://github.com/user-attachments/assets/caaf40a3-aeb7-405a-9fc6-a93e32363f72)


- Gaji yang diprediksi merupakan variabel kontinu, sehingga metrik evaluasi yang digunakan adalah Mean Squared Error (MSE), yang mengukur jarak antara prediksi dan nilai sebenarnya.

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
- **Random Forest**: Dapat menangani noise, missing value, dan dataset besar, tetapi interpretasinya lebih sulit dan memerlukan tuning yang tepat[[6]](https://eprints.umm.ac.id/39299/3/BAB%202.pdf).

## Evaluation

Evaluasi model dilakukan dengan menggunakan MSE, yang menghitung rata-rata selisih kuadrat antara prediksi dan nilai sebenarnya[[7]](https://www.dicoding.com/academies/319/tutorials/18595).

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
[1] https://majoo.id/solusi/detail/rekrutmen-adalah#:~:text=Rekrutmen%20adalah%20proses%20mencari%20dan,mudah%20mencari%20karyawan%20yang%20berkualitas.

[2] http://riset.unisma.ac.id/index.php/jrm/article/view/8261

[3] https://medium.com/@adiptamartulandi/belajar-machine-learning-simple-linear-regression-di-python-e82972695eaf

[4] https://caraguna.com/apa-itu-linear-regression-dalam-machine-learning/

[5] https://www.dqlab.id/kenali-analisis-regresi-linear-metode-pengolahan-data-yang-sering-digunakan

[6] https://eprints.umm.ac.id/39299/3/BAB%202.pdf

[7] https://www.dicoding.com/academies/319/tutorials/18595
