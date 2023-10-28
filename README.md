# EDA SUMMARY

## Descriptive Statistic
1. Data terdiri dari 10000 baris dan 14 kolom, tanpa nilai null dan dapat dilihat pula bahwa isi dataset sesuai dengan nama kolomnya
2. Summary masing-masing kolom selain kolom balance juga terbilang normal. Adapun kolom balance, dapat dilihat bahwa nilai mean dan median memiliki gap yang terbilang cukup jauh yaitu sekitar 20000
3. Rata-rata usia pelanggan Bank X adalah 39 tahun (pembulatan), median usia adalah 37 tahun, dan deviasi standar usia adalah 10 tahun. Ini berarti sebagian besar usia pelanggan berada dalam kisaran 29 hingga 49 tahun dari rata-rata (39 tahun).
4. Rata-rata pendapatan pelanggan adalah 100090, median pendapatan adalah 100193, dan deviasi standar pendapatan adalah 57510.
5. Rata-rata durasi masa langganan pelanggan adalah 5 tahun. Ini berarti secara keseluruhan, pelanggan Bank X rata-rata mempertahankan hubungan dengan bank X selama 5 tahun.

## Univariate Analysis
1. Terdapat 2 fitur yang memiliki outlier yaitu kolom CreditScore dan kolom Age. Berdasarkan boxplot, jumlah credit score normalnya berada di angka 600-700 dan untuk jumlah kredit score dibawah 390 dikategorikan outlier sedangkan Age berada di angka 32-44 tahun dan untuk umur 62 keatas di kategorikan sebagai outlier.
2. Adapun jika dilihat dari kdeplot dapat dilihat fitur Creditscore memiliki distribusi hampir normal sedangkan kolom age memiliki distribusi positif dengan ekor yang panjang ke kanan.
3. Selain kedua fitur tersebut diatas terdapat juga fitur Tenure dan EstimatedSalary yang datanya cenderung tidak memiliki outlier dengan distribusi yang normal dan fitur balance dengan data yang cenderung tidak memiliki outlier juga dan distribusi tidak normal dengan data yang kebanyakan berkumpul di angka 0-30000 dan 50000-200000.
4. Adapun untuk persebaran data kategorikal dapat dilihat bahwa pada fitur numofproducts jumlah nasabah yang memiliki 1 atau 2 produk unggul dengan angka yang sangat signifikan di bandingkan nasabah yang memiliki 3 atau 4 produk. Pada fitur geography jumlah nasabah dari france unggul dengan jumlah 2 kali lipat dari jumlah nasabah yang ada di germany atau spain. untuk fitur gender, male dan female memiliki perbedaan yang tidak begitu signifikan dengan jumlah 4543 untuk female dan 5457 untuk male. untuk fitur hascrcard sekitar 70 persen dari nasabah diketahui memiliki credit card. untuk fitur isactivemember keduanya memiliki jumlah yang hampir sama dimana member dengan isactive yang nilainya true unggul sebanyak 302 nasabah di banding yg nilainya false.
5. Untuk label, label disini memiliki ketimpangan presentase yang sangat signifikan dimana presentase jumlah nasabah yang churn adalah sebanyak 20,3% sedangkan presentase churn yang normal pada umumnya adalah 5-7%.

## Multivariate Analysis
1. Terdapat 2 fitur yang memiliki korelasi positif dengan label yaitu fitur balance dengan score 0.12 dan fitur Age dengan score 0.29. untuk itu, kedua fitur ini dapat dipertimbangkan untuk dipertahankan karena dibanding fitur lainnya kedua fitur ini dianggap paling relevan.
2. Adapun terkait korelasi antar fitur, terdapat 2 fitur yang memiliki korelasi negatif yaitu numofproducts dan balance dengan score sebesar -0.30. Karena korelasi antar fitur dapat mempengaruhi model maka dalam hal ini, kedua fitur harus menjalani uji mulkolinearitas untuk menentukan fitur mana yang lebih baik dipertahankan dan mana yang harus di hapus.
3. Berdasarkan visualisasi diatas kita bisa lihat terdapat korelasi antara creditscore dan age terhadap exited, dari scatter plotnya kita mengetahui nasabah yang memiliki creditscore dibawah 400 dan berumur diantara 35-60an memiliki kencederungan untuk churn.
4. kita juga dapat melihat terdapat pola menarik pada number of product, dimana nasabah yang mengambil lebih dari 2 produk lebih cenderung untuk churn.


# PRE-PROCESSING SUMMARY
1.	Handling missing value : mengecek missing value pada data menggunakan ‘df.isna().sum(). Kami tidak menemukan missing value pada data sehingga pada tahap ini tidak ada yang perlu di handle.
2.	Handling duplicated data : mengecek data duplicate dengan menggunakan ‘df.duplicated().sum(). Kami juga tidak menemukan nilai duplikat disini sehingga tidak ada yang perlu di handle dalam tahap ini.
3.	Handling outliers : mengecek outliers dengan boxplot dan menemukan 2 fitur yang memiliki outliers yaitu Age dan CreditScore. Selanjutnya kami melakukan pengecekan deskriptif statistik dan menyimpulkan bahwa berdasarkan mean, median, min dan max baris data kedua fitur tersebut diatas masih tergolong normal sehingga kami juga tidak melakukan Tindakan apa-apa untuk keduanya.
4.	Feature selection : mengecek fitur yang memiliki pengaruh terhadap label dengan function ‘mutual_info_classif’ dari modul ‘sklearn.feature_selection’. Dari proses ini terdapat tiga fitur dengan nilai 0 (tidak memiliki pengaruh apapun pada label) yaitu Tenure, RowNumber dan Customer Id. Pada tahap ini kami memutuskan untuk menghapus RowNumber dan CustomerId dan mempertahankan Tenure untuk eksplorasi lebih lanjut terlebih dahulu
5.	Feature Extraction : pada tahap ini kami mengekstrak 9 fitur baru dari fitur-fitur yang sudah tersedia sebelumnya yaitu : <br>
a.	Age_Group : merupakan fitur baru berisikan pengelompokan Age/usia berdasarkan range <br>
b.	Balance_Category : merupakan fitur untuk mengelompokan Balance/saldo yang dimiliki nasabah berdasarkan range <br>
c.	CreditScore_Range : fitur ini mengelompokan CreditScore/skor kredit, menyatakan kualitas kartu kredit nasabah <br>
d.	Tenure_Category : fitur ini mengelompokan Tenure/jumlah tahun menjadi nasabah <br>
e.	NumOfProducts_Category : merupakan fitur yang mengelompokan NumOfProduct/jumlah produk yang telah dibeli nasabah melalui bank <br>
f.	Salary_Range : fitur ini mengelompokan Salary/estimasi gaji nasabah <br>
g.	NumOfProducts_Exited : mengelompokan customer yang membeli produk pada jumlah tertentu terhadap potensi churn <br>
h.	CrCard_Active : menggabungkan IsActiveMember dan HasCrCard untuk melihat customer yang aktif mengunakan CC <br>
i.	Geography_Balance_Interact : menggabungkan Geography dengan Balance dan Exited untuk melihat saldo/tabungan nasabah berdasarkan region <br>
6.	Feature Encoding : Pada tahap ini kami melakukan label encoding pada 7 fitur dan one hot encoding pada 1 fitur dengan detail sebagai berikut : <br>
a.	Label encoding <br>
	Fitur gender menjadi ‘0’ untuk ‘male’ dan ‘1’ untuk ‘female’. <br>
	Fitur age_group menjadi ‘1’ untuk ‘young’, ‘2’ untuk ‘middle aged’, ‘3’ untuk ‘senior’ dan ‘4’ untuk ‘elderly’. <br>
	Fitur balance_category menjadi ‘1’ untuk ‘low’, ‘2’ untuk ‘medium’, ‘3’ untuk ‘high’ dan ‘4’ untuk ‘very high’. <br>
	Fitur tenure_category menjadi ‘1’ untuk ‘short term’, ‘2’ untuk ‘medium term’ dan ‘3’ untuk ‘long term’. <br>
	Fitur creditscore_range menjadi ‘1’ untuk ‘poor’, ‘2’ untuk ‘pair’, ‘3’ untuk ‘good’ dan ‘4’ untuk ‘excellent’. <br>
	Fitur numofproducts_category menjadi ‘1’ untuk ‘low’, ‘2’ untuk ‘medium’ dan ‘3’ untuk ‘high’. <br>
	Fitur salary_range menjadi ‘1’ untuk ‘low’, ‘2’ untuk ‘medium’, ‘3’ untuk ‘high’ dan ‘4’ untuk ‘very high’. <br>
b.	One hot encoding <br>
	Fitur geography dengan menambahkan 3 fitur baru yaitu ‘is_spain’, ‘is_germany’ dan ‘is_france’ dan menghapus kolom aslinya. <br>
7.	Tambahan Fitur : diantara fitur yang kami anggap penting dan dibutuhkan sebagai tambahan yaitu : <br>
a.	Jenis produk atau layanan yang digunakan nasabah missal rekening giro, kartu kredit dan deposito <br>
b.	Status pernikahan berupa married atau single sebab hal ini biasanya berpengaruh pada keuangan nasabah <br>
c.	Tingkat kepuasan nasabah pada pelayanan dan produk bank <br>
d.	Aktivitas churn terdahulu, sebab jika nasabah sudah pernah berpindah itu bisa menjadi indicator potensi churn di masa depan <br>
8.	Uji Multikolinearitas : Sebelumnya pada tahap EDA kami menemukan 2 fitur yang memiliki korelasi negatif sebesar -0,31. oleh karena itu pada tahap ini kami memutuskan untuk melakukan uji moultikolinearitas untuk kedua fitur tersebut. Berdasarkan hasil uji multikolinearitas dengan VIF dapat dilihat bahwa nilai VIF kedua fitur sangatlah kecil sehingga dalam hal ini kedua fitur belum bisa dikatakan memiliki korelasi kuat dan tidak perlu mendapatkan tindakan apapun.
9.	Train-Test Split : melakukan train-test split dan menyimpan keduanya dalam 2 dataset baru yang terpisah
10.	Handling imbalance data : kami melakukan resample dengan metode oversampling SMOTE sehingga label yang sebelumnya memiliki baris sekitar 1:6 menjadi balance.
11.	Feature Transformation : kami melakukan feature transformation dengan metode normalisasi untuk 5 fitur numerik yaitu CreditScore, Age, Tenure, Balance dan EstimatedSalary.
