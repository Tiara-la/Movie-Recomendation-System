# Laporan Proyek Machine Learning - Tiara Lailatul Nikmah
---
## Domain Proyek
----
Pada projek ini akan dibuat sistem rekomendasi film. Perkembangan   teknologi informasi   dan   komunikasi   telah   meningkat   dalam   berbagai bidang  seperti  bidang  ekonomi,  ilmu  pengetahuan,  industri  maupun  dalam  kehidupan  sosial. Dampak dari perkembangan ini juga semakin meningkatkan perkembangan industri per film-an. Sekarang ini film sangat banyak dipasaran. Tidak diherankan lagi karena setiap tahunnya film baru pasti akan rilis. Sekarang ini juga sekali aplikasi streaming film di internet. Aplikasi itu menawarkan pengguna untuk bisa menonton film secara online dimana saja dan kapan saja. Selain itu fitur terbaik dari aplikasi ini salah satunya adalah fitur rekomendasinya yang dapat memberikan rekomendasi film-film terbaik kepada pengguna. Salah satunya adalah aplikasi MovieLens.

Banyak dari penggemar film yang membutuhkan sistem rekomendasi yang bagus untuk mencari film yang bagus untuk mereka. Rekomendasi film bisa berdasarkan genre atau rating. Dengan jumlah  film  yang  banyak yang mempunyai berbagai macam genre,  maka dibuatlah  klasifikasi genre  film  untuk  membantu user dalam mencari dan memilih film yang tepat dilihat. Genre dalam  film  merupakan  elemen  utama  dalam  suatu sistem  rekomendasi, karena dengan  adanya  pengklasifikasian genre  dapat  memudahkan  sistem  dalam  mencari  sebuah  film berdasarkan tipe-tipe tertentu, penonton juga lebih mudah dalam mengidentifikasi film seperti apa yang  ditayangkan. Dan bagi penonton yang ingin menonton film yang bagus namun tidak berdasarkan genre tertentu bisa mencari rekomendasi film dengan rating tertinggi. 
Sumber Referensi : [Referensi 1](https://media.neliti.com/media/publications/103958-ID-rancang-bangun-aplikasi-rekomendasi-film.pdf), [Referensi 2](https://mpra.ub.uni-muenchen.de/83349/1/MPRA_paper_83349.pdf), [Referensi 3](http://ekonobis.unram.ac.id/index.php/ekonobis/article/view/47/44)

## Business Understanding
---
Latar belakang permasalahan ini adalah para penonton film yang ingin mendapat rekomendasi film terbaiknya di MovieLens. Mereka ingin menonton film yang mereka suka atau menonton film yang memiliki rating tertinggi. Jadi permasalahan yang dihadapi adalah bagaimana membuat sistem rekomendasi film dengan kategori sesuai dengan film yang disukai dan film terbaik yang memiliki rating tertinggi. Dan berikut uraian lebih lengkap mengenai penjelasan permasalahan tersebut :

### Problem Statements
Dari permasalahan yang sudah disebutkan diatas berikut ini merupakan rincian masalah yang perlu diselesaikan di proyek ini:
- Bagaimana cara melakukan pra-premosesan data film agar dapat digunakan untuk membuat model yang baik?
- Sistem rekomendasi apa yang baik untuk diterapkan pada kasus ini?
- Bagaimana cara membuat sistem rekomendasi film untuk pengguna MovieLens?

### Goals
Berikut adalah tujuan dari dibuatnya proyek ini:
- Melakukan pra-pemrosesan data film yang baik agar dapat digunakan dalam membuat model yang baik
- Membuat sistem rekomendasi film untuk pengguna MovieLens.
- Memberikan rekomendasi untuk film yang kemungkinan disukai pengguna MovieLens.

### Solution statements
Solusi yang dapat dilakukan untuk mencapai tujuan diatas adalah sebagai berikut :
- Untuk teknik pra-pemrosesan data dilakukan pada tahap Data Preparation dengan teknik berikut :
    - Mengatasi Missing Value 
    - Melakukan konversi data series menjadi list
    - membuat dictionary untuk menentukan pasangan key-value
    - Membersihkan data duplikasi.
    - Mengubah tipe data kolom rating menjadi float
- Untuk sistem rekomendasi yang dibuat, meggunakan sistem rekomendasi Content Based Filtering dan Collaborative Filtering. 
    - **Content Based Filtering**
     -Kelebihan: Teknik ini baik dipakai ketika skala user yang besar, Teknik ini dapat menemukan ketertarikan spesifik dari seorang user, dan dapat merekomendasikan item yang jarang disukai orang lain.
    -Kekurangan: Karena meta feature yang digunakan kita yang menentukan sendiri, kualitas dari rekomendasi tergantung kualitas dari meta feature itu sendiri.
    Beberapa teknik yang digunakan untuk membuat sistem rekomendasi Content Based Filtering di proyek ini diantaranya :
         - TF-IDF Vectorizer
         Teknik tersebut juga akan digunakan pada sistem rekomendasi untuk menemukan representasi fitur penting dari setiap kategori genre. Teknik ini menggunakan fungsi TfidfVectorizer() dari sklearn.  TfidfVectorizer akan melakukan proses tokenisasi pada teks, mempelajari kosa kata, melakukan pembobotan frekuensi dokumen secara terbalik (inverse), dan memungkinkan Anda untuk melakukan proses encoding teks baru.
         Berikut adalah definisi TF suatu term X pada dokumen :  
         ![Gambar Metotret](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202107291610325784de49f00104b077d2ccacea4d6ba5.jpeg)  
         IDF untuk suatu term X didefinisikan sebagai berikut:  
        ![Gambar Metotret](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2021072916103253d5e45cb6d14c5e11c5642c468976bf.jpeg)  
        Terakhir, untuk menghitung skor atau bobot untuk TF-IDF, kalikan nilai TF dengan IDF seperti di bawah ini:  
        ![Gambar Metotret](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210729161032371ea6d17d823e17c6967f0e74fb47f7.jpeg)  
        - Cosine Similarity
        Fungsi cosine_similarity digunakan untuk menghitung derajat kesamaan (similarity degree) antar film.
        Cara menghitungnya adalah dengan rumus berikut ini :
        ![Gambar Metotret](https://github.com/Tiara-la/Gambar-EDA/raw/main/cosine%20similarity.png)
        Keterangan :
        x, y = nilai vektor 
        k = nilai cosine similarity dari vektor x dan y
    - **Collaborative Filtering**
    Collaborative filtering bergantung pada pendapat komunitas pengguna. Ia tidak memerlukan atribut untuk setiap itemnya seperti pada sistem berbasis konten. Beberapa teknik yang digunakan untuk membuat sistem rekomendasi Collaborative Filtering di proyek ini diantaranya :
        - Teknik Embedding
        Proses ini dilakukan untuk menghitung skor kecocokan antara pengguna dan resto.
        - Binary Crossentropy untuk menghitung loss function.
        - Adam (Adaptive Moment Estimation) sebagai optimizer.
        - Root Mean Squared Error (RMSE) sebagai metrik evaluation.
- Untuk memberikan rekomendasi untuk film yang kemungkinan disukai pengguna MovieLens saya menggunakan beberapa teknik yaitu operator bitwise (~) dan fungsi model.predict().
    - Operator bitwise (~)
    Operasi ~ atau not, yang akan membalikkan nilai bit sebuah variabel dari 0 menjadi 1, dan 1 menjadi nol. Operator ini fungsinya untuk membuat variabel movie_not_visited yang berisi daftar film yang belum pernah ditonton oleh pengguna. Variabel ini nanti yang akan direkomendasikan untuk pengguna.
    - model.predict()
    Fungsi ini untuk memprediksi label set data baru pada data latih. Metode ini menerima satu argumen, data baru X_new (misalnya model.predict(X_new)), dan mengembalikan label yang dipelajari untuk setiap objek dalam array.

## Data Understanding
---
Dataset yang saya gunakan adalah dataset film di MovieLens. Dataset tersebut saya dapatkan dari [Kaggel](https://www.kaggle.com/grouplens/movielens-20m-dataset). 
 ![Gambar Metotret](https://github.com/Tiara-la/Gambar-EDA/raw/main/dataset.png)
 Didalam dataset ini terdapat 6 file csv yaitu: 
 - genome_scores.csv
 - genome_tags.csv
 - link.csv
 - movie.csv
 - rating.csv
 - tag.csv

Dari ke-6 file csv yang saya sebutkan diatas didalamnya berisi beberapa variabel sebagai berikut:
- genome_scores.csv : berisi informasi mengenai data relevansi tag film :
    - movieId : kode unik setiap film
    - tagId : kode unik dari tag film
    - relevance : relevansi dari tag film
- genome_tags.csv : yang berisi deskripsi tag : 
    - tagId : kode unik dari tag film
    - tag : kata yang berhubungan dengan film yang digunakan untuk menandai suatu film
- link.csv :yang berisi pengidentifikasi yang dapat digunakan untuk menautkan ke sumber lain
    - movieId : kode unik setiap film
    - imdbId : ID IMDB dari film
    - tmbdId : ID TMDB dari film
- movie.csv : yang berisi informasi film :
    - movieId : kode unik setiap film
    - title : nama judul film
    - genres : jenis genre film
- rating.csv : yang berisi peringkat film oleh pengguna :
    - userId : kode unik setiap user
    - movieId : kode unik setiap film
    - rating : data penilaian pengguna dari film dalam satuan range 1-5
    - timestamp : waktu ketika pengguna memberikan penilaian
- tag.csv : yang berisi tag yang diterapkan ke film oleh pengguna :
    - userId : kode unik setiap user
    - movieId : kode unik setiap film
    - tag : data penilaian pengguna dari film dalam satuan range 1-5
    - timestamp : waktu ketika pengguna memberikan penilaian
Tahapan yang dilakukan untuk memahami data adalah :
- **Data loading** untuk membaca file dataset dalam komputer atau local machine. upload dataset tersebut langsung ke file storage di Google Colab.
- **Data Preprocessing** 
    - Menggabungkan Data Film :  untuk mengidentifikasi berapa jumlah seluruh film pada dataset. Disini menggunakan library numpy dan fungsi concatenate untuk menggabungkan beberapa file (movie, link).
    - Menggabungkan Data User :  untuk mengidentifikasi berapa jumlah seluruh user pada dataset. Disini menggunakan library numpy dan fungsi concatenate untuk menggabungkan beberapa file (rating, tag).
    - Mengetahui Jumlah Rating : menggabungkan dataframe rating dengan movie_info berdasarkan nilai movieId dan mengecek missing value.
    - Menggabungkan Data dengan Fitur Nama dan Genre Film : menggabungkan rating dengan nama dan genre film berdasarkan movieId

Terakhir, inilah gambar visualisasi data dari data numerik dan kategorik :
- Data Kategorik
    - **Title**  
    ![Gambar Metotret](https://github.com/Tiara-la/Gambar-EDA/raw/main/title.png)  
    Dari grafik diatas bisa kita lihat karena data judul film terlalu banyak jadi terlalu sulit untuk membacanya. Namun kita masih bisa melihat beberapa data judul film melalui tabel berikut :
    ![Gambar Metotret](https://github.com/Tiara-la/Gambar-EDA/raw/main/title2.png)  
    - **Genre**  
     ![Gambar Metotret](https://github.com/Tiara-la/Gambar-EDA/raw/main/genres.png)  
    Dari grafik diatas bisa kita lihat karena data genre terlalu banyak jadi terlalu sulit untuk membacanya. Namun kita masih bisa melihat beberapa data genre melalui tabel berikut :
     ![Gambar Metotret](https://github.com/Tiara-la/Gambar-EDA/raw/main/genres2.png)
- Data Numerik
Berikut merupakan histogram data numerik :
 ![Gambar Metotret](https://github.com/Tiara-la/Gambar-EDA/raw/main/histo%20reco.png)
Dari histogram diatas kita bisa memperoleh beberapa informasi adalah:
- rata-rata rating film yang diberikan pengguna adalah 3 dan 4

## Data Preparation
Berikut merupakan solusi dari teknik pra-premosesan yang sudah disebutkan sebelumnya yang saya gunakan pada tahap data preparation adalah:
- **Content Based Filtering**
Tahapan data preparation yang dilakukan pada teknik ini adalah : 
    - **Mengatasi Missing Value** : Mengecek lagi dataset apakah ada missing value atau tidak dengan fungsi isnull().sum(). Jika terdapat missing value data bisa di-drop atau dihapus atau data yang hilang bisa diganti dengan modus atau rata-rata. Namun karena didataset ini tidak terdapat missing value jadi data sudah baik.
    - **Melakukan konversi data** : melakukan konversi data series menjadi list menggunakan fungsi tolist() dari library numpy.
    - **Membuat dictionary** : membuat dictionary untuk menentukan pasangan key-value pada data movie_id, movie_name, dan movie_genre
    - **Membersihkan data duplikasi** :  data unik digunakan untuk dimasukkan ke dalam proses pemodelan. Untuk mendpatkan data unik tersebut perlu menghapus data yang duplikat dengan fungsi drop_duplicates() pada kolom ‘movieId’.
- **Collaborative Filtering**
Tahapan data preparation yang dilakukan pada teknik ini adalah : 
    - **Memahami data rating** yang kita miliki
    - **Menyandikan (encode)** fitur ‘user’ dan ‘movieId’ ke dalam indeks integer.
    - **Memetakan data** ‘userID’ dan ‘movieId’ ke dataframe yang berkaitan.
    - **Mengecek data** beberapa hal dalam data seperti jumlah user, jumlah resto, 
    - **Mengubah type data** mengubah type data rating menjadi float.

## Modeling
Setelah dilakukan data preparation, selanjutnya adalah membuat sistem rekomendasi content based filtering dan Collaborative Filtering.
- Dalam teknik **Content Based Filtering**
    - TF-IDF Vectorizer
    Teknik ini digunakan pada sistem rekomendasi untuk menemukan representasi fitur penting dari setiap kategori genre.
    Berikut hasil dari proses TF-IDF Vectorizer :
    ![Gambar Metotret](https://github.com/Tiara-la/Gambar-EDA/raw/main/tfd.png)
    - Cosine Similarity
    Fungsi cosine_similarity digunakan untuk menghitung derajat kesamaan (similarity degree) antar film. Prosesnya adalah dengan memanggil fungsi cosine_similarity dengan argumen dataframe sebagai objeknya. Kemudian hasil dari perhitungannya disimpan pada dataframe baru. Lalu akan dilakukan pencarian kolom dari suatu nama film pada dataframe baru. Kemudian diurutkan nilainya berdasarkan nilai cosine similarity tertinggi dan juga urutannya. Setiap urutan ke 2 terakhir sampai ke n terakhir merupakan kandidat yang memiliki nilai cosine similarity yang sama maka akan ditampilkan sebagai hasil rekomendasinya. 
    Berikut hasil dari proses cosine_similarity :
    ![Gambar Metotret](https://github.com/Tiara-la/Gambar-EDA/raw/main/cosine_hasil.png)
    Hasil Rekomendasi :
    ![Gambar Metotret](https://github.com/Tiara-la/Gambar-EDA/raw/main/recomend2.png)
- Dalam teknik **Collaborative Filtering**
Beberapa teknik yang digunakan untuk membuat sistem rekomendasi Collaborative Filtering di proyek ini diantaranya :
    - Teknik Embedding
    Proses ini dilakukan untuk menghitung skor kecocokan antara pengguna dan resto
    - Binary Crossentropy untuk menghitung loss function 
    - Adam (Adaptive Moment Estimation) sebagai optimizer
    - Root Mean Squared Error (RMSE) sebagai metrics evaluation
Hasil Rekomendasi :
![Gambar Metotret](https://github.com/Tiara-la/Gambar-EDA/raw/main/rekomen_colla.png)
## Evaluation
Metrik evaluasi model yang saya gunakan pada projek ini adalah :
- Pada **Content Based Filtering**
    - **Precision**, Precision menggambarkan tingkat keakuratan antara data yang diminta dengan hasil prediksi yang diberikan oleh model. Atau bisa diartikan kita bisa mengecek seberapa akurat hasil rekomendasi yang kita berikan dengan permintaan penggunan. 
    Berikut cara untuk menghitung presisi di sistem rekomendasi :
    ![Gambar Metotret](https://github.com/Tiara-la/Gambar-EDA/raw/main/presisi.png)  
    Perhiungan Persisi : 
    ![Gambar Metotret](https://github.com/Tiara-la/Gambar-EDA/raw/main/recomend1.png)  
    ![Gambar Metotret](https://github.com/Tiara-la/Gambar-EDA/raw/main/recomend2.png)  
    Precision = 4/5  
    Precision = 80%  
    Jika dilihat dari gambar diatas, diketahui bahwa Film Fun and Fancy Free termasuk ke dalam kategori Animation|Childern|Musical. Dari 5 item yang direkomendasikan, 4 item memiliki kategori Animation|Childern|Musical dan satu kategori Animation|Childern|Drama|Musical. Artinya, precision sistem kita sebesar 80%.
- Pada **Collaborative Filtering**
    - **RMSE atau Root Mean Squared Error RMSE** adalah akar kuadrat dari MSE. Nilai RMSE digunakan untuk menggambarkan tingkat error data model yang digunakan. Semakin kecil nilai RMSE maka semakin tinggi nilai akurasi sistem.
        - Kelebihan : menghukum large error lebih sehingga bisa lebih tepat dalam beberapa kasus, menghindari penggunaan pengambilan nilai absolut, yang tidak diinginkan dalam banyak perhitungan matematis
        - Kekurangan : tidak mendeskripsikan kesalahan rata-rata saja dan memiliki implikasi lain yang lebih sulit untuk dipahami
Berikut merupakan hasil evaluasi dari metrik RSME :
![Gambar Metotret](https://github.com/Tiara-la/Gambar-EDA/raw/main/rsme_hasil.png)   
![Gambar Metotret](https://github.com/Tiara-la/Gambar-EDA/raw/main/rsme_metrik.png)  
MSE didefinisikan dalam persamaan berikut :  
![Gambar Metotret](https://github.com/Tiara-la/Gambar-EDA/raw/main/rsme.png)  
Keterangan :  
n = jumlah dataset  
Yi = nilai sebenarnya  
yi = nilai prediksi  

- **MSE atau Mean Squared Error**, Metrik ini menghitung selisih rata-rata nilai sebenarnya dengan nilai prediksi.
    - Kelebihan MSE yaitu sederhana dalam perhitungan.
    - Kelemahan yang dimiliki MSE adalah akurasi hasil peramalan sangat kecil karena tidak memperhatikan apakah hasil peramalan lebih besar atau lebih kecil dibandingkan kenyataannya. 
Berikut hasil evaluasi dengan metrik MSE :
![Gambar Metotret](https://github.com/Tiara-la/Gambar-EDA/raw/main/sme_hasil.png)  
![Gambar Metotret](https://github.com/Tiara-la/Gambar-EDA/raw/main/mse_metrik.png)  
MSE didefinisikan dalam persamaan berikut :   
![Gambar Metotret](https://github.com/Tiara-la/Gambar-EDA/raw/main/mse.jpg)  
Keterangan :  
N = jumlah dataset  
yi = nilai sebenarnya  
y_pred = nilai prediksi  

- **Mean Absolute Error (MAE)** MAE mengukur besarnya rata-rata kesalahan dalam serangkaian prediksi, tanpa mempertimbangkan arahnya. Ini adalah rata-rata di atas sampel uji dari perbedaan absolut antara prediksi dan observasi aktual di mana semua perbedaan individu memiliki bobot yang sama.
    - Kelebihan : MAE kuat terhadap outlier
    - Kekurangan : MAE tidak terdiferensiasi ketika nilai aktual = nilai prediksi
Berikut adalah hasil evaluasi dari MAE :   
![Gambar Metotret](https://github.com/Tiara-la/Gambar-EDA/raw/main/mae_hasil.png)  
![Gambar Metotret](https://github.com/Tiara-la/Gambar-EDA/raw/main/mae_metrik.png)  
MAE didefinisikan sebagai berikut :  
![Gambar Metotret](https://github.com/Tiara-la/Gambar-EDA/raw/main/mae.png)  
Keterangan :  
N = jumlah dataset  
yi = nilai sebenarnya  
y = nilai prediksi  

**---Ini adalah bagian akhir laporan---**

