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

## Data Transformasi
Sebelum melakukan analisis eksploratif (EDA), dilakukan proses transformasi data (data binning) untuk menyederhanakan variabel numerik kontinu menjadi data kategorikal agar pola analisis lebih mudah diidentifikasi. Kolom baru yang ditambahkan meliputi:AgeGroup: Mengelompokkan usia nasabah dari rentang 18 hingga 97 tahun menjadi 6 fase kelompok usia.BalanceGroup: Mengelompokkan nominal saldo nasabah menjadi 6 kategori, termasuk memisahkan nasabah yang tidak memiliki saldo (0).CreditScoreGroup: Mengelompokkan skor kredit nasabah menjadi 5 tingkatan kelayakan finansial.Segmen (Gabungan): Mengombinasikan variabel-variabel kritis seperti Aktivitas, Jumlah Produk, Usia, dan Gender untuk memetakan segmen spesifik nasabah.

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
Berdasarkan rasio tingkat kehilangan nasabah (jumlah nasabah churn dibagi dengan total keseluruhan nasabah) di masing-masing wilayah/negara, hasil menunjukkan bahwa **negara Jerman mendominasi dengan tingkat persentase churn nasabah yang tinggi yaitu 32%** hampir 2 kali lipat dibandingkan Prancis (16%) dan Spanyol (17%). Hal ini mengindikasikan bahwa adanya masalah operasional, kualitas layanan, atau ketatnya kompetisi perbankan khusus wilayah Jerman. Oleh karena itu, wilayah Jerman membutuhkan perhatian ketat untuk merancang strategi baru guna meningkatkan retensi pelanggan.

* Apakah terdapat perbedaan churn antara laki-laki dan perempuan?
  <img width="859" height="511" alt="image" src="https://github.com/user-attachments/assets/8e4bcf5e-502f-48ea-9ca9-9cf807a755c3" />
  Hasil menunjukkan bahwa gender perempuan (Female) memiliki persentase tingkat kehilangan nasabah yang tinggi yaitu 25% dibanding laki-laki (Male) di angka 16%. Selisih sebesar 9% ini mengindikasikan bahwa adanya perbedaan loyalitas antara nasabah perempuan dan laki-laki, sehingga nasabah perempuan memerlukan pendekatan atau strategi baru tanpa mengabaikan nasabah laki-laki untuk meningkatkan retensi pelanggan. 

* Kelompok usia mana yang memiliki churn rate tertinggi?
  <img width="978" height="648" alt="image" src="https://github.com/user-attachments/assets/64818877-5361-4b06-b611-6891d6335fd2" />
  Berdasarkan Usia (Age), churn rate tertinggi di dominasi oleh usia 48-57 sebanyak 55% dimana angka ini terbilang sangat tinggi, disusul oleh usia 58-67 sebanyak 40%. Rentang usia ini tergolong dalam kategori usia pra-pensiun hingga awal pensiun, sehingga usia dalam rentang ini (48-67) biasanya menutup rekening bank karena memasuki fase pensiun dengan memusatkan keuangan pada 1 bank saja atau penggunaan aplikasi digital bank yang terlalu rumit. Oleh karena itu, pihak bank dapat merencanakan strategi baru seperti layanan digital yang ramah lansia, optimaliasi layanan bantuan tatap muka atau program tabungan hari tua yang kompetitif.

### 3. Karakteristik Finansial Nasabah
Pertanyaan analisis:
* Apakah nasabah dengan saldo tertentu memiliki churn lebih tinggi?
  <img width="911" height="628" alt="image" src="https://github.com/user-attachments/assets/4fb26abb-c410-4c3b-9def-f6f8169732f0" />
 Perbandingan antar nasabah yang memiliki saldo cenderung seimbang sehingga tidak memperlihatkan pengaruh churn yang begitu ekstrem, dimana rata-rata nasabah yang memiliki saldo mengalami churn dalam rentang 22% - 26%. Namun, jika dibandingkan dengan nasabah yang sama sekali tidak memiliki saldo (14%), hasil menunjukkan selisih sekitar ~10% yang mengindikasikan bahwa nasabah yang bersaldo cenderung churn dibandingkan nasabah yang tidak memiliki saldo.
  
* Bagaimana hubungan credit score dengan churn?
  <img width="1182" height="392" alt="image" src="https://github.com/user-attachments/assets/70cfa6d8-4ff2-4ee1-8cbe-119b4bc01ace" />
  Hasil menunjukkan perbandingan yang relatif merata atau tidak terlalu ekstrem antar kategori Skor kredit, dimana rata-rata kategori nasabah churn dalam rentang 20% - 24%, perbandingan selisih antar kategori skor kredit yaitu 4% mengindikasikan bahwa churn dalam kategori skor cenderung sama di setiap tingkatan. Oleh karena itu, dapat disimpulkan bahwa variabel skor kredit tidak begitu berpengaruh terhadap churn pelanggan.

### 4. Hubungan Nasabah dengan Bank
Pertanyaan analisis:
* Apakah lama menjadi nasabah berkaitan dengan churn?
  <img width="1203" height="331" alt="image" src="https://github.com/user-attachments/assets/08387167-6639-40be-8d1e-2163c49f13ef" />
  Pengaruh lama menjadi nasabah terhadap churn menunjukkan hasil yang bersifat homogen atau cenderung stabil, perbedaan rentang yang berkisar 17%-23% yang tidak terlalu jauh antar tahun. Meskipun fluktuasinya tipis, terlihat tren positif di mana risiko churn perlahan menurun dari nasabah baru di tahun ke-0 (23%) hingga mencapai titik paling aman pada nasabah tahun ke-7 (17%). Namun, risiko ini terpantau kembali meningkat di tahun ke-9 (22%). Maka dari itu, dapat ditarik kesimpulan bahwa lama menjadi nasabah (Tenure) tidak begitu berpengaruh terhadap loyalitas nasabah.

* Apakah jumlah produk yang dimiliki memengaruhi churn?
  <img width="1190" height="329" alt="image" src="https://github.com/user-attachments/assets/a1f2fe06-510e-4ccb-b12e-a60b50a14df1" />
  Berdasarkan jumlah produk yang digunakan pelanggan, hasil menunjukkan korelasi yang sangat ekstrem. Pelanggan yang menggunakan 4 produk 100% mengalami churn, begitupun terlihat 83% pelanggan dengan penggunaan 3 produk menunjukkan kecenderungan melakukan churn. Hal ini tentu mengindikasikan bahwa semakin banyak produk yang digunakan nasabah, resiko terjadinya churn justru meningkat secara drastis.

* Apakah kepemilikan kartu kredit berkaitan dengan churn?
  <img width="1182" height="348" alt="image" src="https://github.com/user-attachments/assets/74fb4cce-7ac0-4119-b964-a9ff3cd226f2" />
  Berdasarkan hubungan churn dengan kepemilikan kartu kredit nasabah, hasil menunjukkan bahwa tidak ada perbedaan yang cukup signifikan antara nasabah yang memiliki kartu kredit(20%) dan yang tidak(21%). Hal ini mengindikasikan bahwa kepemilikan kartu kredit tidak begitu berpengaruh terhadap keputusan nasabah untuk melakukan churn. Tentunya kepemilikan kartu ini belum juga mampu membuat nasabah bertahan.


* Apakah nasabah yang tidak aktif memiliki churn rate lebih tinggi?
  <img width="1123" height="303" alt="image" src="https://github.com/user-attachments/assets/a3e5d938-2441-4142-8379-3bb9bb971824" />
  Tingkat keaktifan nasabah memiliki korelasi yang kuat terhadap keputusan meninggalkan bank. Hasil menunjukkan bahwa nasabah yang tidak aktif memiliki churn rate sebesar 27%, hampir dua kali lipat dibanding nasabah yang aktif (14%). Hal ini mengindikasikan bahwa status ketidakaktifan nasabah berpengaruh terhadap penurunan loyalitas nasabah. Oleh karena itu, bank dapat memantau keaktifan nasabah untuk mendeteksi nasabah pasif agar dapat melakukan tindakan penyelamatan sebelum churn terjadi.
  
### 5. Identifikasi Segmen Beresiko Tinggi
Pertanyaan analisis: 
* Segmen nasabah mana yang memiliki tingkat churn tertinggi?
  <img width="586" height="177" alt="image" src="https://github.com/user-attachments/assets/f236305d-e202-4853-91fd-367d893bfd1e" />

<img width="509" height="198" alt="image" src="https://github.com/user-attachments/assets/4ed8552f-321b-45aa-bb29-33821f61b2ab" />



## Dashboard
## Insight Utama
## Rekomendasi Bisnis
## Tools 
