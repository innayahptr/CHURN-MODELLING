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
