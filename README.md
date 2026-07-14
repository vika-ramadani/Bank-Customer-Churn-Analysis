# Analisis Customer Churn Bank
## Gambaran Proyek:
Customer churn merupakan tantangan bagi industri perbankan karena dapat mengurangi pendapatan serta meningkatkan biaya untuk memperoleh nasabah baru. Namun, bank belum mengetahui karakteristik nasabah yang memiliki kecenderungan churn maupun faktor-faktor yang berkaitan dengan keputusan tersebut. Oleh karena itu, dilakukan analisis data untuk mengidentifikasi pola churn sehingga dapat menjadi dasar dalam menyusun strategi retensi pelanggan yang lebih efektif.
## Permasalahan Bisnis: 
Bank mengalami customer churn dan ingin memahami karakteristik nasabah yang cenderung churn.
## Tujuan Analisis:
Mengidentifikasi faktor-faktor yang berkaitan dengan customer churn dan karakteristik nasabah yang memiliki resiko churn lebih tinggi.
## Dataset:
Dataset yang digunakan adalah **Bank Customer Churn Dataset** yang diperoleh dari [Kaggle](https://www.kaggle.com/datasets/shantanudhakadd/bank-customer-churn-prediction/data). Dataset terdiri dari **10000 baris** nasabah dengan **14 kolom**/variabel, meliputi informasi demografis, profil keuangan, aktivitas nasabah, serta status churn(Excited). Variabel-variabel tersebut digunakan untuk menganalisi karakteristik nasabah yang berkaitan dengan customer churn.
<img width="1916" height="815" alt="image" src="https://github.com/user-attachments/assets/c43e8177-d557-4b67-847f-9b50549c5b3d" />

## Data Cleaning:
Proses pembersihan data yang dilakukan meliputi :
1. Missing Value : Tidak ditemukan missing value pada seluruh kolom.
3. Invalid Value : Seluruh nilai berada dalam rentang yang valid sesuai dengan karakteristik masing-masing variabel.
4. Duplicate Data : Tidak ditemukan data duplikat berdasarkan 'CustomerId'.
5. Inaccurate Value : Tidak ditemukan indikasi nilai yang tidak akurat.
6. Inconsistent Value : Tidak ditemukan inkonsistensi penulisan pada variabel kategorikal.
7. Outlier : Ditemukan beberapa nilai outlier berdasarkan metode **Interquartile Range (IQR)**. Nilai tersebut tetap dipertahankan karena masih berada dalam rentang yang wajar dan merepresentasikan kondisi bisnis yang mungkin terjadi.
8. Tipe Data : Semua tipe data sesuai dengan karakteristik masing-masing variabel.
9. Format: Tidak diperlukan perubahan format data karena seluruh data telah memiliki format yang konsisten..

## Data Transformasi
Sebelum melakukan Exploratory Data Analysis (EDA), dilakukan proses transformasi data (data binning) untuk mengelompokkan beberapa variabel numerik menjadi data kategorikal agar pola analisis lebih mudah diidentifikasi. Kolom baru yang ditambahkan meliputi:
1. **BalanceGroup**
     Mengelompokkan saldo nasabah berdasarkan rentang nominal saldo (business rule) agar mempermudah analisis karakteristik customer churn.
   * Tidak Ada Saldo (Rp0)
   * Saldo Rendah (Rp1 – Rp5.000.000)
   * Saldo Menengah (Rp5.000.001 – Rp10.000.000)
   * Saldo Tinggi (Rp10.000.001 – Rp15.000.000)
   * Saldo Sangat Tinggi (Rp15.000.001 – Rp20.000.000)
   * Saldo Premium (> Rp20.000.000)

2. **CreditScoreGroup**
   Mengelompokkan skor kredit nasabah berdasarkan tingkat kelayakan finansial, yaitu:
   * Rendah (350 - 500)
   * Cukup (501 – 600)
   * Sedang (601 – 700)
   * Baik (701 – 800)
   * Sangat Baik (801 - 850)


## Exploratory Data Analysis (EDA):
Analisis eksploratif dilakukan untuk memahami karakteristik customer churn melalui beberapa fokus analisis berikut.
### 1. Gambaran Umum Customer Churn
Pertanyaan analisis : Berapa persentase nasabah yang mengalami churn?
  <img width="500" height="250" alt="image" src="https://github.com/user-attachments/assets/7df5f27c-18cc-43ea-80a6-1c11692962a3" />

Hasil menunjukkan bahwa sebanyak 20% (2.037 nasabah) dari total 10.000 berhenti berlangganan. Persentase churn ini cukup serius, karena angka ini sudah diatas rata-rata industri perbankan (umumnya dibawah 15%). Tentunya hal ini mengindikasikan adanya potensi penurunan likuiditas (kekurangan uang kas) dan pembengkakan biaya akuisisi(mencari nasabah baru) bagi bank.

### 2. Karakteristik Demografis Nasabah
Pertanyaan analisis :
* Negara mana yang memiliki churn tertinggi?
  <img width="1267" height="333" alt="image" src="https://github.com/user-attachments/assets/288f49ec-2964-4213-b2f7-e2c4c9116300" />
  _**Persentase Churn = Total nasabah churn / Total Keseluruhan Nasabah** masing-masing kategori_.

  Berdasarkan rasio tingkat kehilangan nasabah (jumlah nasabah churn dibagi dengan total keseluruhan nasabah) di masing-masing wilayah/negara, hasil menunjukkan bahwa **negara Jerman mendominasi dengan tingkat persentase churn nasabah yang tinggi yaitu 32%** hampir 2 kali lipat dibandingkan Prancis (16%) dan Spanyol (17%). Hal ini mengindikasikan bahwa adanya masalah operasional, kualitas layanan, atau ketatnya kompetisi perbankan khusus wilayah Jerman. Oleh karena itu, wilayah Jerman membutuhkan perhatian ketat untuk merancang strategi baru guna meningkatkan retensi pelanggan.

* Apakah terdapat perbedaan churn antara laki-laki dan perempuan?
  <img width="1072" height="396" alt="image" src="https://github.com/user-attachments/assets/b2e738ce-34e8-4be8-9356-e915c0ea71fb" />
  _**Persentase Churn = Total nasabah churn / Total Keseluruhan Nasabah** masing-masing kategori_.
  
  Hasil menunjukkan bahwa gender perempuan (Female) memiliki persentase tingkat kehilangan nasabah yang tinggi yaitu 25% dibanding laki-laki (Male) di angka 16%. Selisih sebesar 9% ini mengindikasikan bahwa adanya perbedaan loyalitas antara nasabah perempuan dan laki-laki, sehingga nasabah perempuan memerlukan pendekatan atau strategi baru tanpa mengabaikan nasabah laki-laki untuk meningkatkan retensi pelanggan. 

* Kelompok usia mana yang memiliki churn rate tertinggi?
  <img width="1057" height="701" alt="image" src="https://github.com/user-attachments/assets/f0f58b2a-ba37-4c35-8192-ce44c075cad1" />
  _**Persentase Churn = Total nasabah churn / Total Keseluruhan Nasabah** masing-masing kategori_.
   _**Catatan:** Pengelompokan usia (*Age Group*) tidak dibuat sebagai kolom baru pada dataset, melainkan dilakukan langsung menggunakan fitur **Group** pada PivotTable saat proses analisis._
  
  Berdasarkan Usia (Age), churn rate tertinggi di dominasi oleh usia 48-57 sebanyak 55% dimana angka ini terbilang sangat tinggi, disusul oleh usia 58-67 sebanyak 40%. Rentang usia ini tergolong dalam kategori usia pra-pensiun hingga awal pensiun, sehingga usia dalam rentang ini (48-67) biasanya menutup rekening bank karena memasuki fase pensiun dengan memusatkan keuangan pada 1 bank saja atau penggunaan aplikasi digital bank yang terlalu rumit. Oleh karena itu, pihak bank dapat merencanakan strategi baru seperti layanan digital yang ramah lansia, optimaliasi layanan bantuan tatap muka atau program tabungan hari tua yang kompetitif.

### 3. Karakteristik Finansial Nasabah
Pertanyaan analisis:
* Apakah nasabah dengan saldo tertentu memiliki churn lebih tinggi?
  <img width="1098" height="461" alt="image" src="https://github.com/user-attachments/assets/b7b07bbe-56bf-4489-a1ac-8758d835aa1f" />
  _**Persentase Churn = Total nasabah churn / Total Keseluruhan Nasabah** masing-masing kategori_

  Berdasarkan hasil analisis, kategori saldo menunjukkan perbedaan churn rate, namun tidak membentuk pola yang konsisten. Nasabah dengan saldo rendah dan saldo tinggi sama-sama memiliki churn rate sebesar 26%, sedangkan nasabah tanpa saldo memiliki churn rate paling rendah (14%). Temuan ini mengindikasikan bahwa besarnya saldo rekening saja belum cukup untuk menjelaskan customer churn, sehingga kemungkinan terdapat faktor lain yang memiliki pengaruh lebih besar, seperti usia, status keaktifan, atau jumlah produk yang dimiliki.
  
* Bagaimana hubungan credit score dengan churn?
  <img width="1031" height="440" alt="image" src="https://github.com/user-attachments/assets/ee788988-fb95-441b-bdfb-34908e83e875" />
   _**Persentase Churn = Total nasabah churn / Total Keseluruhan Nasabah** masing-masing kategori_.
  
  Hasil menunjukkan perbandingan yang relatif merata atau tidak terlalu ekstrem antar kategori Skor kredit, dimana rata-rata kategori nasabah churn dalam rentang 20% - 24%, perbandingan selisih antar kategori skor kredit yaitu 4% mengindikasikan bahwa churn dalam kategori skor cenderung sama di setiap tingkatan. Oleh karena itu, dapat disimpulkan bahwa variabel skor kredit tidak begitu berpengaruh terhadap churn pelanggan.

### 4. Hubungan Nasabah dengan Bank
Pertanyaan analisis:
* Apakah lama menjadi nasabah berkaitan dengan churn?
  <img width="1594" height="399" alt="image" src="https://github.com/user-attachments/assets/322dfcdb-43ec-476d-8421-3003bfd806dc" />
   _**Persentase Churn = Total nasabah churn / Total Keseluruhan Nasabah** masing-masing kategori_.
  
  Pengaruh lama menjadi nasabah terhadap churn menunjukkan hasil yang bersifat homogen atau cenderung stabil, perbedaan rentang yang berkisar 17%-23% yang tidak terlalu jauh antar tahun. Meskipun fluktuasinya tipis, terlihat tren positif di mana risiko churn perlahan menurun dari nasabah baru di tahun ke-0 (23%) hingga mencapai titik paling aman pada nasabah tahun ke-7 (17%). Namun, risiko ini terpantau kembali meningkat di tahun ke-9 (22%). Maka dari itu, dapat ditarik kesimpulan bahwa lama menjadi nasabah (Tenure) tidak begitu berpengaruh terhadap loyalitas nasabah.

* Apakah jumlah produk yang dimiliki memengaruhi churn?
  <img width="1331" height="442" alt="image" src="https://github.com/user-attachments/assets/17ba324a-e56c-4d4d-9a31-ea0d0fad416b" />
  _**Persentase Churn = Total nasabah churn / Total Keseluruhan Nasabah** masing-masing kategori_.
  
  Nasabah dengan 4 produk memiliki churn rate sebesar 100%. Namun, kelompok ini hanya terdiri dari 60 nasabah sehingga ukuran sampelnya relatif kecil. Oleh karena itu, temuan ini perlu diinterpretasikan secara hati-hati. Sebaliknya, kelompok dengan 3 produk memiliki churn rate tinggi (83%) dengan jumlah nasabah yang lebih besar (266), sehingga pola tersebut lebih layak dijadikan perhatian. Nasabah dengan 2 produk menunjukkan tingkat retensi terbaik dengan churn rate hanya 8%, sedangkan churn meningkat tajam pada kelompok yang memiliki 3–4 produk.

* Apakah kepemilikan kartu kredit berkaitan dengan churn?
  <img width="1426" height="421" alt="image" src="https://github.com/user-attachments/assets/fc047dc1-bdbd-473d-8744-cc46d7e4c791" />
  _**Persentase Churn = Total nasabah churn / Total Keseluruhan Nasabah** masing-masing kategori_.

  Berdasarkan hubungan churn dengan kepemilikan kartu kredit nasabah, hasil menunjukkan bahwa tidak ada perbedaan yang cukup signifikan antara nasabah yang memiliki kartu kredit(20%) dan yang tidak(21%). Hal ini mengindikasikan bahwa kepemilikan kartu kredit tidak begitu berpengaruh terhadap keputusan nasabah untuk melakukan churn. Tentunya kepemilikan kartu ini belum juga mampu membuat nasabah bertahan.


* Apakah nasabah yang tidak aktif memiliki churn rate lebih tinggi?
  <img width="1366" height="402" alt="image" src="https://github.com/user-attachments/assets/7b174d7d-e8bd-4e5e-80e0-4b8f7559630f" />
   _**Persentase Churn = Total nasabah churn / Total Keseluruhan Nasabah** masing-masing kategori_.
  
  Tingkat keaktifan nasabah memiliki korelasi yang kuat terhadap keputusan meninggalkan bank. Hasil menunjukkan bahwa nasabah yang tidak aktif memiliki churn rate sebesar 27%, hampir dua kali lipat dibanding nasabah yang aktif (14%). Hal ini mengindikasikan bahwa status ketidakaktifan nasabah berpengaruh terhadap penurunan loyalitas nasabah. Oleh karena itu, bank dapat memantau keaktifan nasabah untuk mendeteksi nasabah pasif agar dapat melakukan tindakan penyelamatan sebelum churn terjadi.
  
### 5. Segmentasi Nasabah
Pertanyaan analisis: 
* Segmen nasabah mana yang memiliki tingkat churn tertinggi?
  <img width="586" height="177" alt="image" src="https://github.com/user-attachments/assets/f236305d-e202-4853-91fd-367d893bfd1e" />
  
  Hasil tersebut menunjukkan bahwa nasabah pra-pensiun (48-57 tahun) di Germany, terutama perempuan, merupakan kelompok dengan tingkat churn yang relatif lebih tinggi dibandingkan segmen demografis lainnya.

  <img width="509" height="198" alt="image" src="https://github.com/user-attachments/assets/4ed8552f-321b-45aa-bb29-33821f61b2ab" />
  
  Pada dataset ini, seluruh nasabah yang memiliki 4 produk tercatat mengalami churn. Namun, kelompok ini hanya terdiri dari 60 nasabah, sehingga hasil tersebut perlu diartikan secara hati-hati dan tidak dapat langsung disamaratakan.
Smentara itu, kepemilikan 3 produk menunjukkan keterkaitan dengan churn rate yang sangat tinggi, terutama pada nasabah yang sudah tidak aktif.

## Dashboard
<img width="1095" height="708" alt="image" src="https://github.com/user-attachments/assets/a70e9d8a-22fb-46bd-a4b0-064c6640f648" />

Klik disini untuk melihat dashboard di [Tableau](https://public.tableau.com/shared/8XW82FZP5?:display_count=n&:origin=viz_share_link)

## Insight Utama
Berdasarkan seluruh hasil analisis,  diperoleh beberapa karakteristik yang paling sering muncul pada segmen nasabah dengan churn rate tinggi, yaitu:
1. Berasal dari Germany.
2. Berusia 48–57 tahun (dengan kecenderungan churn yang masih tinggi pada kelompok 58–67 tahun).
3. Didominasi oleh perempuan.
4. Berstatus tidak aktif (Inactive Member).
5. Memiliki 3 produk perbankan.

Karakteristik tersebut dapat dijadikan dasar bagi bank untuk mengidentifikasi kelompok nasabah yang perlu diprioritaskan dalam program retensi pelanggan.

## Rekomendasi Bisnis
1. Prioritaskan program retensi pada nasabah di Germany, khususnya perempuan berusia 48–57 tahun, karena memiliki churn rate tertinggi.
2. Tingkatkan ketertarikan nasabah tidak aktif melalui promo seperti diskon, cashback, atau bebas biaya transaksi tentunya ini dapat menarik minat pelanggan perempuan. Kemudian menyederhanakan aplikasi agar mudah digunakan terutama untuk usia 48-57 yang menjadi tingkat rentan churn.
3. Mengevaluasi strategi pada nasabah yang memiliki 3 produk, karena churn rate kelompok ini sangat tinggi.
4. Melakukan analisis lebih lanjut terhadap nasabah dengan 4 produk untuk memahami lebih dalam penyebab churn, meskipun seluruh nasabah pada kelompok ini mengalami churn dengan tingkat observasi paling sedikit.

## Tools 
Microsoft Excel, Tableau
