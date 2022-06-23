# EpsilonParty_JC_DS_LS_01_FinalProject

## **Ecommerce Customer Churn Analysis and Prediction**
***

![Epsilon Party](https://user-images.githubusercontent.com/51298939/175247657-db60f8ca-58ad-4c25-98ff-e521c0c1ea09.png)

Team Members: 

- [Irfanul Zuhdi.N](https://github.com/irfanulzuhdi) - irfanulzuhdi@gmail.com
- [Nadya Sindi Safitri](https://github.com/nadya32) - nadyasindi5@gmail.com

Dataset = E Commerce Dataset (link: https://www.kaggle.com/code/ankitverma2010/e-commercecustomerchurn/data)

***
## **Business Problem Understanding**

**Contex:**

- Dalam dunia E-commerce, perusahaan harus berusaha keras tidak hanya untuk meyakinkan customer tetapi juga untuk mempertahankan customer yang sudah ada. Suatu perusahaan E-commerce harus mampu memprediksi perilaku customer apakah seorang customer akan berhenti/tidak menggunakan E-commerce(churn). Churn merupakan orang yang berhenti menggunakan layanan E-commerce dikarenakan beberapa alasan. Salah satu bukti customer bisa dikatakan churn adalah ketika dia sudah lama tidak melakukan transaksi ataupun sudah lama tidak menggunakan layanan E-commerce. Semakin banyak yang churn akan mengakibatkan kerugian cukup besar untuk perusahaan. Karena biasanya, bahwa sebagian besar keuntungan perusahaan diperoleh dari customer yang tetap dan lebih banyak biaya untuk menarik customer baru daripada mempertahankan yang lama. Oleh karena itu, perusahaan ingin menemukan customer churn agar membantu perusahaan mempertahankan customer mereka dan mempertahankan hubungan dengan customer lama merupakan hal yang sangat penting, salah satunya mengurangi tingkat kerugian akibat kehilangan customer dengan memberikan promo yang sesuai kepada customer. 

- Target :

        0 : Customer tidak Churn 

        1 : Customer Churn


**Problem Statement:**

- Salah satu dampak dari persaingan di dunia E-commerce adalah kondisi dimana customer berhenti menggunakan ecommerce dengan alasan tidak ada kepuasan terhadap layanan dana customer lebih tertarik dengan layanan yang diberikan pesaing. Pada perusahaan bisnis ecommerce lebih menguntungkan untuk mempertahankan hubungan dengan customer dalam hal retensi dibandingkan dengan mendapatkan customer baru. Oleh karena itu perusahaan ingin mengetahui customer yang ingin churn atau tidak untuk mengurangi tingkat kerugiaan yang sangat besar. Ketika memperoleh customer yang baru biasanya akan menghabiskan biaya lima sampai enam kali lebih mahal daripada mempertahankan yang sudah ada.

**Goals:**

- Berdasarkan permasalahan tersebut, perusahaan ingin memiliki kemampuan untuk memprediksi kecenderungan tinggi untuk seorang customer akan churn atau meninggalkan perusahaan. sehingga akan memudahkan perusahaan untuk menyusun strategi dalam mengurangi kerugian berupa kehilangan custumer tersebut dengan memberikan mereka beberapa layanan yang positif. 
- Mengetahui faktor apa saja yang mempengaruhi customer akan churn dari e-commerce
- Mengetahui insight yang didapatkan dari analisis data untuk menjawab permasalahan bisnis perusahaan

**Analytic Approach:**

- Jadi yang akan kita lakukan adalah menganalisis data untuk menemukan pola yang membedakan pelanggan yang churn atau tidak. Selanjutnya kita akan membangun model klasifikasi yang akan membantu perusahaan untuk dapat memprediksi customer yang akan churn atau tidak.

**Metric Evaluation:**

![confusion](https://user-images.githubusercontent.com/51298939/175247978-b98c3867-569d-4deb-8e9f-d250b00f5db9.jpeg)

*Type 1 error : False Positive*
<br>Konsekuensi: membuang-buang biaya dan waktu untuk mengadakan promo yang diberikan

*Type 2 error : False Negative*
<br>Konsekuensi: Kehilangan customer

Berdasarkan konsekuensinya, maka kita akan membuat model yang dapat meminimalisir 2 hal:
1. Jumlah biaya mengadakan promo yang diberikan kepada pelanggan sehingga harga yang keluar lebih efisien.
2. Jumlah pelanggan yang dianggap akan bertahan tetapi justru Churn, sehingga perusahaan akan kehilangan pelanggan dan menjadi rugi.

Maka sebisa mungkin kita akan membuat model yang dapat meminimalisir dari 2 konsekuensi tersebut. Oleh karena itu, metric utama yang kita gunakan adalah F1 score dan PR score.
- Alasan utama menggunakan metrics f1_score dan PR curve karena dapat digunakan untuk data imbalance seperti kasus ini.
- Precision-Recall curve secara khusus dirancang ketika kelas positif (churn) lebih menarik daripada kelas negatif (not churn), dan PR curve tidak terpengaruh oleh ketidakseimbangan data.
- f1_score digunakan ketika kita fokus pada kelas positif (churn) dan mempertimbangan kedua bagian False Negative (FN) dan False Positive (FP).

## **Data Understanding**

**Unit Analysis**
Berdasarkan *problem statement* ini merupakan permasalahan mengenai E-commerce (Company online retail) Customer Churn. Data ini disebarkan secara public di Kaggle. Data ini berisikan setiap baris data mempresentasikan satu customer yang di mana terdapat 5630 baris data dengan 20 kolom termasuk kolom 'CustomerID'.


**Attribute Information**

| Attribute | Data Type, Length | Description |
| --- | --- | --- |
| CustomerID | Int | ID tiap Customer yang belanja|
| Churn | Int | Pelanggan melakukan Churn dan tidak Churn |
| Tenure | Float | durasi(bulan) dalam menggunakan layanan ecommers  |
| PreferredLoginDevice | Object | Perangkat login pilihan pelanggan|
| CityTier | Int | Tingkatan Pengelompokan Daerah dalam satu negara |
| WarehouseToHome | Float | Jarak antara gudang ke rumah pelanggan |
| PreferredPaymentMode | Object | Metode pembayaran pilihan pelanggan|
| Gender | Object | Jenis kelamin pelanggan|
| HourSpendOnApp | Float | Jumlah durasi(jam) yang dihabiskan pelanggan dalam  menggunakan e-commerce|
| NumberOfDeviceRegistered | Int | Jumlah perangkat yang terdaftar oleh pelanggan |
| PreferedOrderCat | Object | Kategori pesanan pilihan pelanggan bulan lalu|
| SatisfactionScore | Int | Tingkat kepuasan pelanggan pada layanan|
| MaritalStatus | Object | Status pernikahan pelanggan|
| NumberOfAddress | Int | Jumlah alamat per pelanggan yang terdaftar pada e-commerce |
| Complain | Int | Keluhan yang telah diajukan oleh pelanggan pada bulan lalu |
| OrderAmountHikeFromlastYear | Float | Persentase volume jumlah kenaikan pesanan dari tahun lalu |
| CouponUsed | Float | kupon yang telah pengguna gunakan bulan lalu|
| OrderCount | Float | Jumlah pesanan per pelanggan di bulan lalu|
| DaySinceLastOrder | Float | Hari Sejak pesanan terakhir dipesan oleh pelanggan|
| CashbackAmount | Float | Rata-rata cashback bulan lalu|

## **Data Preprocessing (Cleaning)**

Sebelum kita melakukan Exploratory Data Analysis (EDA), sebaiknya kita melakukan Data Preprocessing atau Data Cleaning. Pada tahapan ini, kita akan melakukan pengecekan terhadap dataset apakah memiliki anomali. Jika terdapat anomali pada dataset, maka akan mempengaruhi hasil analisis yang kita lakukan. Data yang dapat mengganggu proses analisis dapat dilihat jika memiliki missing value, kesalahan dalam penulisan atau pengulangan penulisan untuk satu kata yang sama, data yang duplikat, tipe data yang tidak sesuai, dan data outlier. Oleh karena itu, perlu adanya penanganan terhadap beberapa data yang bermasalah tersebut. Sehingga, Data yang sudah bersih yang akan kita gunakan untuk lanjut ke tahap analisis. 

- Langkah Pertama, kita melakukan drop pada kolom `CustomerID`. Karena kolom tersebut merupakan ID unik setiap customer yang tidak akan mempengaruhi target (tidak dapat digunakan untuk analisa data dan pembuatan model machine learning).

**Check Target (Churn)**

Dari dataset, data target atau 'Churn' merupakan data imbalance. Hal ini dilihat dari jumlah customer yang tidak churn sebesar 83% (4682 customer), sedangkan customer yang churn sebesar 17% (948 customer).

![Data imbalance](https://user-images.githubusercontent.com/51298939/175250935-5833f119-a2b2-48ce-bd44-a246db53d653.png)

1. Missing Value Treatment
2. Data Duplicate
3. Non-standard Value (Categorical Features)
4. Handling Outliers (Numerical Features)

## **Data Analysis/Exploratory Data Analysis (EDA)**

**Satisfaction Score**



