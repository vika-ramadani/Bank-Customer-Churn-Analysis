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
<img width="650" height="300" alt="image" src="https://github.com/user-attachments/assets/7df5f27c-18cc-43ea-80a6-1c11692962a3" />
Hasil menunjukkan bahwa sebanyak 20% nasabah churn(keluar) dan 80% lainnya masih menjadi pelanggan, hal ini mengindikasikan bahwa persentase nasabah masih banyak 
### 2. Karakteristik Demografis Nasabah
Pertanyaan analisis :
* Negara mana yang memiliki churn tertinggi?
<img width="650" height="300" alt="image" src="https://github.com/user-attachments/assets/2cf33597-7882-4e29-8cc0-8cb731632300" />

* Apakah terdapat perbedaan churn antara laki-laki dan perempuan?
<img width="650" height="300" alt="image" src="https://github.com/user-attachments/assets/432e02f9-e98a-4462-a1a5-06502153be0a" />

* Kelompok usia mana yang memiliki churn rate tertinggi?

### 3. Karakteristik Finansial Nasabah
Pertanyaan analisis:
* Apakah nasabah dengan saldo tertentu memiliki churn lebih tinggi?
* Bagaimana hubungan credit score dengan churn?
* Apakah estimated salary menunjukkan pola tertentu terhadap churn?
### 4. Hubungan Nasabah dengan Bank
Pertanyaan analisis:
* Apakah lama menjadi nasabah berkaitan dengan churn?
* Apakah jumlah produk yang dimiliki memengaruhi churn?
* Apakah kepemilikan kartu kredit berkaitan dengan churn?
* Apakah nasabah yang tidak aktif memiliki churn rate lebih tinggi?
### 5. Identifikasi Segmen Beresiko Tinggi
Pertanyaan analisis: Segmen nasabah mana yang memiliki tingkat churn tertinggi?

## Dashboard
## Insight Utama
## Rekomendasi Bisnis
## Tools 
