# Analisis Customer Churn Bank
## Gambaran Proyek:
Bank mengalami kehilangan nasabah (customer churn) yang dapat berdampak pada penurunan pendapatan dan loyalitas pelanggan. Namun, belum diketahui karakteristik nasabah yang paling beresiko churn serta faktor-faktor apa saja yang berkaitan dengan keputusan nasabah untuk meninggalkan bank. Oleh karena itu, diperlukan analisis data untuk mengidentifikasi pola churn sehingga bank dapat menyusun strategi retensi pelanggan yang lebih efektif.
## Permasalahan Bisnis: 
Bank mengalami customer churn dan ingin memahami karakteristik nasabah yang cenderung churn.
## Tujuan Analisis:
Mengidentifikasi faktor-faktor yang berkaitan dengan customer churn dan karakteristik nasabah yang memiliki resiko churn lebih tinggi.
## Dataset:
Dataset yang digunakan adalah **Bank Customer Churn Dataset** yang diperoleh dari [Kaggle](https://www.kaggle.com/datasets/shantanudhakadd/bank-customer-churn-prediction/data). Dataset terdiri dari **10000 baris** nasabah dengan **14 kolom**/variabel, meliputi informasi demografis, profil keuangan, aktivitas nasabah, serta status churn(Excited). Variabel-variabel tersebut digunakan untuk menganalisi karakteristik nasabah yang berkaitan dengan customer churn.
<img width="900" height="400" alt="image" src="https://github.com/user-attachments/assets/680c756a-19e8-40c8-aba8-73f6081df2b7" />

## Data Cleaning:
Proses pembersihan data yang dilakukan meliputi :
1. Missing Value : Tidak ditemukan missing value pada seluruh kolom.
3. Invalid Value : Tidak ditemukan nilai di luar nilai asli masing-masing variabel.
4. Duplicate Data : Tidak ditemukan data duplikat berdasarkan 'CustomerId'.
5. Inaccurate Value : Tidak ditemukan indikasi nilai yang tidak akurat.
6. Inconsistent Value : Tidak ditemukan inkonsistensi penulisan pada variabel kategorikal.
7. Outlier : Ditemukan beberapa outlier berdasarkan metode IQR pada beberapa variabel, namun tetap dipertahankan karena masih valid secara bisnis.
8. Tipe Data : Semua tipe data sesuai dengan karakteristik masing-masing variabel.
9. Format: Tidak diperlukan perubahan format data.

## Exploratory Data Analysis (EDA):
Analisis eksploratif dilakukan untuk memahami karakteristik customer churn melalui beberapa fokus analisis berikut.
### 1. Gambaran Umum Customer Churn
Pertanyaan analisis : Berapa persentase nasabah yang mengalami churn?
  <img width="500" height="250" alt="image" src="https://github.com/user-attachments/assets/7df5f27c-18cc-43ea-80a6-1c11692962a3" />

Hasil menunjukkan bahwa sebanyak 20% (2.037 nasabah) dari total 10.000 berhenti berlangganan. Persentase churn ini cukup serius, karena angka ini sudah diatas rata-rata industri perbankan (umumnya dibawah 15%). Tentunya hal ini mengindikasikan adanya potensi penurunan likuiditas (kekurangan uang kas) dan pembengkakan biaya akuisisi(mencari nasabah baru) bagi bank.

### 2. Karakteristik Demografis Nasabah
Pertanyaan analisis :
* Negara mana yang memiliki churn tertinggi?
  <img width="1177" height="395" alt="image" src="https://github.com/user-attachments/assets/47bb6ffe-0b15-4666-ae7d-d4431e482996" />

Jika ditinjau berdasarkan rasio tingkat kehilangan nasabah (jumlah nasabah churn dibagi dengan total keseluruhan nasabah) di masing-masing wilayah/negara, hasil menunjukkan bahwa **negara Jerman mendominasi dengan tingkat persentase churn nasabah yang tinggi yaitu 32%** hampir 2 kali lipat dibandingkan Prancis (16%) dan Spanyol (17%). Hal ini mengindikasikan bahwa adanya masalah operasional, kualitas layanan, atau ketatnya kompetisi perbankan khusus wilayah Jerman. Oleh karena itu, wilayah Jerman membutuhkan perhatian ketat untuk merancang strategi baru guna meningkatkan retensi pelanggan.

* Apakah terdapat perbedaan churn antara laki-laki dan perempuan?
  <img width="1152" height="598" alt="image" src="https://github.com/user-attachments/assets/e6705bed-b74b-4532-8983-5cf105a14210" />


* Kelompok usia mana yang memiliki churn rate tertinggi?
  <img width="600" height="350" alt="image" src="https://github.com/user-attachments/assets/6fb5eee7-1a7c-480d-aaf1-a39633160709" />

### 3. Karakteristik Finansial Nasabah
Pertanyaan analisis:
* Apakah nasabah dengan saldo tertentu memiliki churn lebih tinggi?
  <img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/f82f4998-15c6-4fab-8a76-c8393bc8fc46" />
  
* Bagaimana hubungan credit score dengan churn?
  <img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/65771bc0-69a5-4fd5-bf9c-5c4d1b164297" />

### 4. Hubungan Nasabah dengan Bank
Pertanyaan analisis:
* Apakah lama menjadi nasabah berkaitan dengan churn?
  <img width="1233" height="350" alt="image" src="https://github.com/user-attachments/assets/e34aa2fe-00f7-4299-8ede-3a11dc245ce7" />

* Apakah jumlah produk yang dimiliki memengaruhi churn?
  <img width="1180" height="358" alt="image" src="https://github.com/user-attachments/assets/0e94262b-cdf0-417f-a47c-de43bd5d889e" />

* Apakah kepemilikan kartu kredit berkaitan dengan churn?
  <img width="1179" height="365" alt="image" src="https://github.com/user-attachments/assets/9e341a1a-fe9c-4f9f-9646-6c69b2f6d68c" />

* Apakah nasabah yang tidak aktif memiliki churn rate lebih tinggi?
  <img width="1232" height="362" alt="image" src="https://github.com/user-attachments/assets/c1cbc04b-6a3a-4124-aaa2-e985a0d575ca" />
  
### 5. Identifikasi Segmen Beresiko Tinggi
Pertanyaan analisis: 
* Segmen nasabah mana yang memiliki tingkat churn tertinggi?
  <img width="928" height="599" alt="image" src="https://github.com/user-attachments/assets/1a1ce03f-b648-4aaf-8fb4-3db061b60bf9" />

## Dashboard
## Insight Utama
## Rekomendasi Bisnis
## Tools 
