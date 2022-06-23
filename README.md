# EpsilonParty_JC_DS_LS_01_FinalProject

## **Ecommerce Customer Churn Analysis and Prediction**

Created By: 

- (https://github.com/irfanulzuhdi) - irfanulzuhdi@gmail.com
- Nadya Sindi Safitri

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

- Berdasarkan permasalahan tersebut, perusahaan ingin memiliki kemampuan untuk memprediksi kecenderungan tinggi untuk seorang customer akan churn atau meninggalkan perusahaan. sehingga akan memudahkan perusahaan untuk Menyusun strategi untuk mengurangi kerugian berupa kehilangan custumer tersebut dengan memberikan mereka beberapa penawaran yang positif. 

**Analytic Approach:**

- Jadi yang akan kita lakukan adalah menganalisis data untuk menemukan pola yang membedakan pelanggan yang churn atau tidak. Selanjutnya kita akan membangun model klasifikasi yang akan membantu perusahaan untuk dapat memprediksi customer yang akan churn atau tidak.

**Metric Evaluation:**

![Confusion Matrix](confusion.jpeg)

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
