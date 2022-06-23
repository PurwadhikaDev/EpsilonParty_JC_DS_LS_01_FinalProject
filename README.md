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
- Mengetahui faktor apa saja yang mempengaruhi customer akan churn dari e-commerce.
- Mengetahui insight yang didapatkan dari analisis data untuk menjawab permasalahan bisnis perusahaan.

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

### **Satisfaction Score**
![satisfaction](https://user-images.githubusercontent.com/51298939/175254844-3ac3af38-720f-4825-b8ee-467f2a4c1c97.png)

### **Complain**

![complain](https://user-images.githubusercontent.com/51298939/175253139-c9e39487-cd1b-468f-aa8f-262e5d9b5371.png)

### **Coupon Used**

![Coupon](https://user-images.githubusercontent.com/51298939/175253387-218afc87-0435-405a-a746-fa2e1128368f.png)

### **Tenure**

![image](https://user-images.githubusercontent.com/51298939/175253604-1c491cec-3ca6-4e1b-863d-a2eca6c5aeea.png)

### **Cashback Amount**

![cashback](https://user-images.githubusercontent.com/51298939/175254360-51b3aa6f-ee00-4e27-b301-b0f326f18ca4.png)

### **Analysis insight**

1. Pada Feature Satisfaction Score, Customer yang memberikan Score 5 tidak bisa dikatakan Customer yang tidak akan Churn.
2. Customer yang melakukan complain churn ratenya tinggi.
3. Customer yang menggunakan kupon 8 kali tidak bisa dikatakan Customer yang tidak akan churn, karena banyak Customer yang hanya ingin menggunakan promo saja. 
4. Pada Feature Tenure, Mayoritas Customer memiliki umur tenure yang pendek. Customer yang sudah lama menggunakan layanan maka cenderung untuk tidak churn.
5. Customer yang memiliki churn rate tinggi akan berkurang dengan bertambah tinggi Cashback yang diterima Customer.




## **Modeling & Evaluation**

**XGBClassifier**

- XGboost adalah implementasi lanjutan dari algoritma peningkatan gradien (Gradient Boosting). XGboost menggunakan prinsip ensemble yaitu menggabungkan beberapa set pembelajar (tree) yang lemah menjadi sebuah model yang kuat sehingga menghasilkan prediksi yang kuat.

![Recap score](https://user-images.githubusercontent.com/51298939/175260897-318bd8ff-73ed-4609-9b3e-21dcd8cbe26d.png)

**Informasi score:**
- Terlihat bahwa score yang dihasilkan menggunakan training set dan test set tidak jauh berbeda, ini menandakan proses modeling sudah benar. Hasil score yang didapatkan cukup baik setelah dilakukan hyperparameter tuning dan diuji performa model dalam test set, kita mendapatkan nilai f1_score = 0.8896 atau 89% tingkat akurasi model. Selain itu untuk PR AUC score setelah tuning didapatkan 0.903 atau 90% model sudah dapat membedakan kedua kelas.

Berdasarkan grafik di atas, kita dapat melihat fitur-fitur yang memberikan pengaruh penting (signifikan) terhadap customer churn. Kita dapat menjadikan feature importance sebagai acuan untuk memberikan rekomendasi kepada stakeholder.

![Importance](https://user-images.githubusercontent.com/51298939/175260388-fcad316a-4614-4af6-bb79-0971c3f51337.png)

Berikut merupakan fitur-fitur yang signifikan berpengaruh terhadap customer churn:
- Tenure
- Complain
- PreferedOrderCat (X3)
- PreferredLoginDevice (X0)
- PreferredPaymentMode (X1)
- NumberOfAddress
- MaritalStatus (X3)

## **Shapley Additive Explanations (SHAP) Values**

![Shapvalue](https://user-images.githubusercontent.com/51298939/175260104-8d32d0d7-384c-477c-86ad-7674f83dab56.png)

**Berdasarkan SHAP value:**
1. **Tenure** : Customer dengan Tenure kecil berpengaruh secara positif dengan target atau kemungkinan besar akan churn.
2. **Complain** : Complain hanya memiliki dua value (0 dan 1), `complain == 1` berpengaruh positif dengan target atau customer yang complain kemungkinan besar churn daripada `complain == 0`.
3. **NumberOfAddress** : Jika customer mendaftarkan banyak alamatnya pada e-commerce berpengaruh positif terhadap target (Churn).
4. **CashbackAmount**, **DaySinceLastOrder**, : Memiliki kemungkinan besar akan churn ketika value nya kecil.
5. **WarehouseToHome**, **OrderCount**, **SatisfactionScore** : Memiliki kemungkinan besar akan churn ketika value nya besar.

## **Conclusion & Recommendation**

![Confusion Matrix](https://user-images.githubusercontent.com/51298939/175259512-ea9e9de3-cb78-4226-bfdd-f8f18e1157fe.png)

**Informasi:**

Bedasarkan data Revenue E-commerce di Indonesia dari : https://ecommercedb.com/en/markets/id/all
- Pada tahun 2021, salah satu e-commerce dengan revenue sebesar USD 390 million.
- Kita akan menggunakan data tersebut untuk menganalisis performa model yang telah dibangun

Perhitungan Keuangan:
- Revenue tahun 2021 = USD 390 million
- Kita asumsi pendapatan (Revenue) didapatkan dari:
    - 80% dari customer
    - 20% dari others
- Asumsi customer tahun 2021 = 1.000.000 orang
- Revenue per customer = (USD 390 m x 80%) / 1.000.000 (customer) = `USD 312` per customer dalam satu tahun.
- Dana campaign (5% dari revenue) =  USD 19.500.000
- Dana campaign per customer = USD 19.500.000 / 1.000.000 (customer) = `USD 19.5` per customer

Kesimpulan:
1. Berdasarkan campaign cost, kita mengalami kerugian karena memberikan promo yang salah sebesar 1,5%.
2. Berdasarkan perhitungan yang telah dilakukan, kita dapat melakukan saving keuangan hingga 86% dengan loss 13,8%. ini menandakan modeling dapat saving money bagi perusahaan akibat kehilangan customer karena memperkecil prediksi yang salah.
3. Keuntungan yang didapatkan setelah dikurangi dana untuk campaign kepada customer tetap adalah USD 226.746

![Classification Report](https://user-images.githubusercontent.com/51298939/175259744-dcc27795-114a-43eb-a2e5-15e956e6bdbe.png)

![PRAUCscore](https://user-images.githubusercontent.com/51298939/175259880-46dc820e-43c6-4466-9b99-e8937eae8817.png)

**Berdasarkan classification Report:**
- Final model yang digunakan adalah model XGBoost yang telah dilakukan optimize threshold.
- Berdasarkan `f1_score`, terdapat 89% pelanggan perlu diberikan perhatian lebih besar dengan memberikan layanan yang positif karena customer akan churn, dan terdapat 98% customer yang tidak perlu diberikan lebih layanan yang positif karena customer tidak akan churn.

**Informasi kurva:**
1. Kurva PR untuk final model sudah menjelaskan bahwa metrics dapat membedakan antara kelas positif dan kelas negatif atau dapat dikatakan sudah mengklasifikasikan dengan baik karena nilai yang dihasilkan 90% presisi tinggi dengan kurva condong ke sudut kanan atas.
2. PR Curve Tuned bekerja dengan threshold 0.33 atau dapat dikatakan kelas positif dengan probabilitas > 0.33 dan kelas negatif dengan probabilitas < 0,33. Dengan PR curve tuned merupakan threshold terbaik untuk masalah ini.

**Konklusi secara general:**
- Berdasarkan dataset yang ada, terdapat 83% customer tidak churn dan 17% customer churn.
- Dari EDA category features kita dapat mengetahui bahwa tingkat Customer yang Churnnya tinggi yaitu 
Customer yang lebih banyak menggunakan Computer, metode pembayarannya menggunakan Cash on Delivery, banyak memesan kategori elektronik, gendernya male dan statusnya single.

## **Recommendation**

**Berdasarkan Feature Importance yang didapatkan dari Final Model:**
-  `Tenure` merupakan fitur paling penting dalam menentukan customer akan churn. Jika dilihat dari EDA, customer yang memiliki nilai Tenure kecil (0-5 bulan pemakaian) paling banyak dan tingkat churn juga paling besar. Maka kita dapat melakukan:
    - Memberikan layanan yang positif secara besar kepada customer baru (0-5 bulan) penggunaan agar tetap bertahan menggunakan layanan E-commerce ini.
    - Layanan positif yang diberikan dapat berupa promo gratis ongkir tanpa ada minimal jarak, cashback pembelian barang, dan pemotongan harga yang dibeli.
- `Complain` merupakan bagian penting lain yang harus diperhatikan, karena customer yang memberikan complain (1) terhadap e-commerce tingkat churnnya tinggi. Customer yang complain tidak puas dengan layanan yang diberikan ataupun ada masalah yang terjadi ketika customer menggunakan layanan.
    - Hal yang dapat dilakukan untuk kedepannya, dapat mengumpulkan hasil complain tahun lalu terhadap layanan e-commerce, setelah itu menyusun memperbaiki layanan dengan mempertimbangkan complain yang diberikan oleh customer.
- `PreferedOrderCat` kategori grocery merupakan salah satu kategori order yang berpengaruh signifikan, maka kita dapat memaksimalkan layanan terhadap customer yang melakukan pembelian pada kategori grocery.


**Berdasarkan EDA:**
1. Customer yang menggunakan computer lebih sedikit dan tingkat churnnya tinggi, oleh karena itu kita perlu menurunkan churn rate dengan meningkatkan layanan pada computer.
2. Penggunaan layanan pembayaran berupa Cash on Delivery memiliki tingkat churn yang tinggi. Sebelum kita memperbaiki layanan, kita dapat meminta feedback kekurangan terhadap layanan dari Customer yang menggunakan agar kita dapat memperbaiki layanan dan menurunkan churn rate Customer.
3. Customer yang membeli kategori elektronik pada layanan e commerce paling tinggi churnnya (63%). Oleh karena itu, kita dapat meningkatkan keamanan transaksi,pengiriman dan proteksi produk (dapat berupa asuransi rusak dan kecurian).
4. Customer Single memiliki churn tinggi. Jika ingin menurunkan Churn ratenya, kita bisa meningkatkan terhadap layanan feature lain. Karena Customer Single termasuk dalam kategori dengan churn rate tinggi pada feature lain.
5. Perlu diperhatikan terhadap `satisfaction score` yang diberikan customer. Satisfaction score sama dengan 3 merupakan penilaian paling banyak diberikan oleh customer diikuti score sama dengan 1. Ini menandakan bahwa customer tidak puas terhadap layanan yang diberikan. Sedangkan, tingkat churn customer tinggi dengan score 5. Terdapat dua hal yang perlu diperhatikan dan diberikan rekomendasi.
    - Untuk customer yang memberikan score buruk (< 3) namun, tingkat churn rendah. Kita dapat meningkatkan layanan yang positif seperti, memberikan kupon promo, atau meningkatkan keamanan dalam bertransaksi dan pengiriman barang, dan cepat respon ketika customer memberikan complain.
    - Untuk customer yang memberikan score paling baik (5), secara logika customer yang memberikan nilai paling baik, tingkat churn-nya seharusnya kecil. Berdasarkan hasil EDA dan observasi terhadap fitur lain, ternyata customer tersebut merupakan golongan customer baru (0-5 bulan) yang hanya melakukan order paling banyak 1 hingga 2 kali dan menggunakan kupon sedikit. Sehingga, dapat memberikan treatment positif kedepannya untuk customer yang memberikan score paling baik (5) agar tetap menjadi customer yang loyal seperti memberikan promo apapun.
6. Berdasarkan `CouponUsed` yang didapatkan dan digunakan oleh customer, customer yang menggunakan kupon sebanyak 8 kali memiliki tingkat churn tinggi, namun jumlah customernya paling sedikit. Oleh karena itu, kita dapat mengasumsikan bahwa customer tersebut merupakan 'Coupon seeker' atau orang-orang yang hanya menggunakan layanan karena ada promo, setelah promo digunakan mereka akan berhenti menggunakan layanan dan berpindah ke kompetitor. Maka, kita dapat merekomendasikan untuk selalu intens memberikan informasi promo kepada customer tersebut.

**Hal-hal yang dapat dilakukan untuk memaksimalkan model:**
1. Mencoba model algoritma klasifikasi lain yang lebih tinggi tingkat akurasinya atau lebih cocok terhadap costumer churn.
2. Melakukan banyak percobaan terhadap hyperparameter tuning agar mendapatkan parameter yang paling baik.
3. Mencoba metode handling imbalance lainnya yang dapat mengatasi imbalance klasifikasi.

**Limitasi Model**
- Jumlah data setelah drop outlier = 4735 baris
- Warehouse to Home: 5 - 36 km
- Hour Spend on App: 0.5 - 4.5 jam
- Number of Address: 1 - 12 alamat
- Cashback amount : 81 - 324.73
