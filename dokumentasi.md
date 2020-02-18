# Dokumentasi Praktik ETL menggunakan Knime

## Business Understanding
Data yang digunakan merupakan kumpulan sentimen dan review yang terdapat pada setiap aplikasi di google playstore. Data tersebut berisikan nama aplikasi, review, sentimen, sentimen polaritas, dan sentimen subjektifitas. Sentimen berisikan positif ataukah negatifnya review pembeli terhadap aplikasi. Sentimen polaritas berisikan angka positif ataukah negatifnya review dan penilaian pembeli terhadap aplikasi. Sedangkan sentimen subjektifitas berisikan penilaian pembeli terhadap aplikasinya.

## Data Understanding
Jumlah Baris : 64.295
Jumlah Kolom : 5
1. App: Nama aplikasi di google playstore (string)
2. Translated_Review: Review pembeli terhadap aplikasi yang diubah bahasanya kedalam bahasa inggris (string)
3. Sentiment: Penilaian positif dan negatif dari review pembeli terhadap aplikasi (double)
4. Sentiment_Polarity: Angka dari -1 hingga 1 yang menunjukan kecenderungan penilaian pembeli terhadap aplikasi (double)
5. Sentiment_Subjectivity: Penilaian pembeli terhadap aplikasi (double)

## Data Preparation
Data dibagi menjadi 2 bagian yaitu:
Data Atas: Translated_Review, Sentiment_Polarity, Sentiment_Subjectivity
Data Bawah: App, Sentiment.
Untuk keterangannya akan dijelaskan di bawah.
1. Load data dari csv dengan File Reader
![](https://github.com/adhityairvan/knime-bigdata/raw/master/Screenshot%20from%202020-02-17%2009-18-20.png)
2. Split kolom data yang telah di-load dengan menggunakan Column Splitter
![](https://github.com/adhityairvan/knime-bigdata/raw/master/Screenshot%20from%202020-02-17%2009-20-13.png)
3. Bagian bawah dari data yang telah di-split, dimasukkan kedalam database, terdapat 3 langkah dalam proses ini
  a. Membuat database terlebih dahulu dengan menggunakan MySQL Connector
  ![](https://github.com/adhityairvan/knime-bigdata/raw/master/Screenshot%20from%202020-02-17%2009-20-13.png)
  b. Membuat table di dalam database dengan menggunakan DB Table Creator
  ![](https://github.com/adhityairvan/knime-bigdata/raw/master/Screenshot%20from%202020-02-17%2009-20-13.png)
  c. Menuliskan data kedalam table yang telah dibuat
  ![](https://github.com/adhityairvan/knime-bigdata/raw/master/Screenshot%20from%202020-02-17%2009-20-13.png)

## Data Modeling
Data yang telah dibuat pada Data Preparation di atas, langsung di-join menggunakan Joiner
![](https://github.com/adhityairvan/knime-bigdata/raw/master/Screenshot%20from%202020-02-17%2009-20-13.png)

## Evaluation
Join berhasil dilakukan yang telah dibahas di Data Modeling di atas

## Deployment
Hasil join dituliskan di dalam 2 format
1. Di dalam csv file dengan menggunakan CSV Writer
![](https://github.com/adhityairvan/knime-bigdata/raw/master/Screenshot%20from%202020-02-17%2023-39-46.png)
2. Di dalam database dengan menggunakan 2 langkah
  a. Membuat table database dengan menggunakan DB Table Creator
  ![](https://github.com/adhityairvan/knime-bigdata/raw/master/Screenshot%20from%202020-02-17%2023-39-46.png)
  b. Menuliskan database yang telah dibuat
  ![](https://github.com/adhityairvan/knime-bigdata/raw/master/Screenshot%20from%202020-02-17%2023-39-46.png)