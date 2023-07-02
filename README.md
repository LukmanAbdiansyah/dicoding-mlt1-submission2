# Project Overview
## Project Overview

Dalam era digital yang semakin maju, sistem rekomendasi telah menjadi elemen yang tidak terpisahkan dari berbagai aplikasi dan platform online. Dengan meningkatnya volume konten yang tersedia, pengguna sering kali menghadapi kesulitan dalam menemukan informasi yang relevan dan bermanfaat. Sistem rekomendasi hadir sebagai solusi untuk mengatasi masalah ini dengan memberikan rekomendasi yang dipersonalisasi berdasarkan minat, preferensi, dan perilaku pengguna. Dengan bantuan algoritma cerdas dan teknik analisis data, sistem rekomendasi dapat mempercepat dan mempermudah proses penemuan konten, memperluas pengetahuan pengguna, dan meningkatkan pengalaman pengguna secara keseluruhan.

Dalam industri buku, terdapat jumlah yang melimpah dari judul-judul yang tersedia di pasar. Bagi penggemar buku, ini dapat menjadi tantangan untuk menemukan bacaan baru yang sesuai dengan minat mereka di tengah keragaman yang ada. Dalam konteks ini, sistem rekomendasi *online bookstore* menjadi alat yang berharga untuk membantu pengguna menemukan buku-buku yang relevan, memperluas pengetahuan mereka, dan meningkatkan pengalaman membaca secara keseluruhan[1],[2].

Sistem rekomendasi merupakan teknologi yang sangat membantu pengguna dalam menemukan barang yang ingin mereka beli. Penggunaan sistem rekomendasi secara luas digunakan untuk merekomendasikan produk-produk yang paling sesuai kepada pengguna akhir. Saat ini, situs web penjualan buku *online* saling bersaing dengan mempertimbangkan berbagai atribut. Sistem rekomendasi merupakan salah satu alat terkuat untuk meningkatkan keuntungan dan mempertahankan pembeli. Namun, sistem-sistem yang sudah ada sering kali mengakibatkan ekstraksi informasi yang tidak relevan dan mengakibatkan kurangnya kepuasan pengguna. Dalam proyek ini, disajikan sebuah *Book Recommendation System* (BRS) yang didasarkan pada fitur kombinasi dari *Content Based Filtering* (CBF) dan*Collaborative Filtering* (CF) untuk menghasilkan rekomendasi yang efisien dan efektif[3]. 

# Business Understanding
## Problem Statement
Berdasarkan latar belakang sebelumnya maka ada beberapa yang dapat di pertanyakan yaitu:
* Bagaimana metode *Content Based Filtering dan Collaborative* memberikan dampak kepada pengguna?
* Apa keunggulan dan kekurangan dari metode *Collaborative Filtering* (CF) dan *Content-Based Filtering* (CBF) dalam sistem rekomendasi?
* Bagaimana hasil dari metode *Collaborative Filtering* (CF) dan *Content-Based Filtering* (CBF)?

## Goals
Berdasarkan problem statement yang dijabarkan sebelumnya maka tujuan dari proyek ini adalah :

* Mampu menampilkan, menjelaskan, dan mengimplementasikan hasil dari sistem rekomendasi dari metode Collaborative Filtering* (CF) dan *Content-Based Filtering* (CBF) 
* Mebandingkan keunggulan dan kekurangan dari metode *Collaborative Filtering* (CF) dan *Content-Based Filtering* (CBF) dalam sistem rekomendasi
* Analisis hasil dari metode *Collaborative Filtering* (CF) dan *Content-Based Filtering* (CBF)

## Solution Statement
Berdasarkan goal yang dimiliki maka ada beberapa solusi yang dapat diberikan yaitu:
* Menerapkan metode *Content Based Filtering* menggunakan *Cosine Similarity Measurement*
* Menerapkan *Collaborative filtering* yang di kombinasikan dengan *deep learning*
* Membandingkan kinerja pada metode CBF and CF
* Pada CBF akan menghitung *Precision* pada sistem
* Sedangkan untuk metode CF akan dievaluasi menggunakan *Root Mean Squared Error* (RMSE)

# Data Understanding
Dataset yang digunakan pada proyek ini diambil dari website kaggle [Book-Crossing: User review ratings](https://www.kaggle.com/datasets/ruchi798/bookcrossing-dataset) . Pada proyek ini digunakan 2 dataset yaitu *Book Data with Categories.csv* dan *BX-Book-Ratings.csv*.
## Data Variabel

Tabel 1 : Dataset Books
| Column              | Dtype   |
|---------------------|---------|
| user_id             | int64   |
| location            | object  |
| age                 | float64 |
| isbn                | object  |
| rating              | int64   |
| book_title          | object  |
| book_author         | object  |
| year_of_publication | float64 |
| publisher           | object  |
| img_s               | object  |
| img_m               | object  |
| img_l               | object  |
| Summary             | object  |
| Language            | object  |
| Category            | object  |
| city                | object  |
| state               | object  |
| country             | object  |

Dataset pertama yaitu  _Book Data with Categories.csv_  mempunyai total 1.031.175 data dan 18 kolom dengan informasi sebagai berikut :

-   user_id : merupakan id dari user
-   location : merupakan lokasi user tinggal
-   age : merupakan umur dari user
-   isbn : merupakan kode pengidentifikasi buku
-   rating : merupakan rating yang user berikan untuk buku
-   book_title : merupakan judul dari buku
-   book_author : merupakan penulis dari buku
-   year_of_publication : merupakan tahun publikasi buku
-   publisher : merupakan penerbit buku
-   img_s/img_m/img_l : merupakan gambar cover dari buku
-   summary : merupakan sinopsis dari buku
-   language : merupakan bahasa terjemahan buku
-   category : merupakan kategori buku
-   city : merupakan kota buku tersebut dibeli
-   state : merupakan provinsi buku tersebut dibeli
-   country : merupakan negara buku tersebut dibeli

Tabel 2 : Dataset Book Ratings
| **Column**  | **Dtype** |
|-------------|-----------|
| User-ID     | int64     |
| ISBN        | object    |
| Book-Rating | int64     |

Dataset kedua yaitu  _BX-Book-Ratings.csv_  memiliki total 1.149.780 data dan 3 kolom dengan informasi sebagai berikut :

-   User-ID : merupakan id dari user yang memberikan rating
-   ISBN : merupakan kode pengidentifikasi buku
-   Book-Rating : merupakan rating yang diberikan pada buku

## Sample dataset

### Rating Dataset

Tabel 3 : Book Ratings Sample

| **User-ID** |  **ISBN**  | **Book-Rating** |
|:-----------:|:----------:|:---------------:|
|      276725 | 034545104X |               0 |
|      276726 | 0155061224 |               5 |
|      276727 | 0446520802 |               0 |
|      276729 | 052165615X |               3 |
|      276729 | 0521795028 |               6 |

Pada dataset book ratings terdapat 3 kolom yang terdiri dari User-ID, ISBN dan Book-Rating. Dataset ini berisi tentang buku yang telah dirating oleh pengguna yang dapat dilihat pada tabel 3.

### Books Dataset

Tabel 4 : Books Dataset

| user_id |                  location |     age |       isbn | rating |          book_title |          book_author | year_of_publication |               publisher |                                             img_s |                                             img_m |                                             img_l |                                           Summary | Language |           Category |     city |      state | country |
|--------:|--------------------------:|--------:|-----------:|-------:|--------------------:|---------------------:|--------------------:|------------------------:|--------------------------------------------------:|--------------------------------------------------:|--------------------------------------------------:|--------------------------------------------------:|---------:|-------------------:|---------:|-----------:|--------:|
|       2 | stockton, california, usa | 18.0000 | 0195153448 |      0 | Classical Mythology |   Mark P. O. Morford |              2002.0 | Oxford University Press | http://images.amazon.com/images/P/0195153448.0... | http://images.amazon.com/images/P/0195153448.0... | http://images.amazon.com/images/P/0195153448.0... | Provides an introduction to classical myths pl... |       en | ['Social Science'] | stockton | california |     usa |
|       8 |  timmins, ontario, canada | 34.7439 | 0002005018 |      5 |        Clara Callan | Richard Bruce Wright |              2001.0 |   HarperFlamingo Canada | http://images.amazon.com/images/P/0002005018.0... | http://images.amazon.com/images/P/0002005018.0... | http://images.amazon.com/images/P/0002005018.0... | In a small town in Canada, Clara Callan reluct... |       en |      ['Actresses'] |  timmins |    ontario |  canada |
|   11400 |   ottawa, ontario, canada | 49.0000 | 0002005018 |      0 |        Clara Callan | Richard Bruce Wright |              2001.0 |   HarperFlamingo Canada | http://images.amazon.com/images/P/0002005018.0... | http://images.amazon.com/images/P/0002005018.0... | http://images.amazon.com/images/P/0002005018.0... | In a small town in Canada, Clara Callan reluct... |       en |      ['Actresses'] |   ottawa |    ontario |  canada |
|   11676 |             n/a, n/a, n/a | 34.7439 | 0002005018 |      8 |        Clara Callan | Richard Bruce Wright |              2001.0 |   HarperFlamingo Canada | http://images.amazon.com/images/P/0002005018.0... | http://images.amazon.com/images/P/0002005018.0... | http://images.amazon.com/images/P/0002005018.0... | In a small town in Canada, Clara Callan reluct... |       en |      ['Actresses'] |      NaN |        NaN |     NaN |
|   41385 |  sudbury, ontario, canada | 34.7439 | 0002005018 |      0 |        Clara Callan | Richard Bruce Wright |              2001.0 |   HarperFlamingo Canada | http://images.amazon.com/images/P/0002005018.0... | http://images.amazon.com/images/P/0002005018.0... | http://images.amazon.com/images/P/0002005018.0... | In a small town in Canada, Clara Callan reluct... |       en |      ['Actresses'] |  sudbury |    ontario |  canada |

Pada Books dataset terdapat 18 kolom yang dapat dilihat pada tabel 4.

## Langkah-Langkah Data Understanding
* Melakukan load dataset untuk seluruh menggunakan Pandas
* Mengecek Tipe data pada setiap dataset dengan fungsi .info()
* Melakukan .dropna() pada dataset untung *handling missing value*
* Mengecek nilai *unique* pada dataset terhadap kolom kategori
* Mengambil dataset sample karena keterbatasan resource perangkat google colab

### Hasil EDA

Tabel 5 : Table Info Dataset Books

|      **Column**     | **Non-Null Count** | **Dtype** |
|:-------------------:|:------------------:|:---------:|
| user_id             | 1031175 non-null   | int64     |
| location            | 1031175 non-null   | object    |
| age                 | 1031175 non-null   | float64   |
| isbn                | 1031175 non-null   | object    |
| rating              | 1031175 non-null   | int64     |
| book_title          | 1031175 non-null   | object    |
| book_author         | 1031175 non-null   | object    |
| year_of_publication | 1031175 non-null   | float64   |
| publisher           | 1031175 non-null   | object    |
| img_s               | 1031175 non-null   | object    |
| img_m               | 1031175 non-null   | object    |
| img_l               | 1031175 non-null   | object    |
| Summary             | 1031175 non-null   | object    |
| Language            | 1031175 non-null   | object    |
| Category            | 1031175 non-null   | object    |
| city                | 1017072 non-null   | object    |
| state               | 1008377 non-null   | object    |
| country             | 995801 non-null    | object    |

Keseluruhan tipe data pada dataset books adalah object kecuali pada kolom rating, user_id, age, dan year_of_publication. terlihat juga terdapat missing value pada kolom *city, state,* dan *country*. sementara itu untuk kolom kategori terdapat 6008 nilai unik, ketika dilakukan visualisasi ternyata terdapat *category* yang nilainya hanya sedikit sekali dan terdapat *category* yang namanya sama akan tetapi terdapat perbedaan pada hurufnya.

Tabel 6 : Info dataset Ratings

|   Column      | Non-Null Count | Dtype   |
|--------------|----------------|---------|
| User-ID      | 1149780        | int64   |
| ISBN         | 1149780        | object  |
| Book-Rating  | 1149780        | int64   |


Pada tabel dataset Rating memiliki dua kolom numerik *integer* dan satu tipe data *object* dan juga tidak ada indikasi nilai *null*.

Tabel 7 : Statistik Rating

|       |   Book-Rating |
|------:|--------------:|
| count | 340556.000000 |
|  mean |      3.010941 |
|  std  |      3.872787 |
|  min  |      0.000000 |
|  25%  |      0.000000 |
|  50%  |      0.000000 |
|  75%  |      7.000000 |
|  max  |     10.000000 |

Pada kolom *book rating* memiliki jumlah 340.556 setelah di clean yang memiliki rata-rata *rating* 3.01, dengan nilai minimal 1 dan maximal *rating* 10.

# Data Preparation

## Content Based Filtering


### Data Processing
* mengambil kolom memberikan informasi penting pada buku, seperti _book_title, book_author, publisher_ dan _category_, sehingga kita dapat menghapus semua kolom kecuali kolom-kolom tersebut.
* Membersihkan data dari duplikasi menggunakan fungsi drop_duplicates().
* Membersihkan data dari nilai null dengan menggunakan fungsi dropna().
* Merging dataset books dan rating pada nilai isbn dengan *left join*.

Tabel 8 : Hasil Merging
|    isbn    |                     book_title                    |      book_author     |        publisher        |      Category      | User-ID | Book-Rating |   |
|:----------:|:-------------------------------------------------:|:--------------------:|:-----------------------:|:------------------:|:-------:|:-----------:|:-:|
| 0195153448 |                               Classical Mythology |   Mark P. O. Morford | Oxford University Press | ['Social Science'] |       2 |           0 |   |
| 0002005018 |                                      Clara Callan | Richard Bruce Wright |   HarperFlamingo Canada |      ['Actresses'] |       8 |           5 |   |
| 0060973129 |                              Decision in Normandy |         Carlo D'Este |         HarperPerennial |      ['1940-1949'] |       8 |           0 |   |
| 0374157065 | Flu: The Story of the Great Influenza Pandemic... |     Gina Bari Kolata |    Farrar Straus Giroux |        ['Medical'] |       8 |           0 |   |
| 0393045218 |                            The Mummies of Urumchi |      E. J. W. Barber |  W. W. Norton & Company |         ['Design'] |       8 |           0 |   |

* membersihkan fitur *category* dari simbol, menghapus *category* yang memiliki jumlah data kurang dari 200 dan yang lebih dari 800 untuk mengurangi jumlah data sehingga mempercepat komputasi, kemudian menambahkan kolom baru dengan nama clean_category.

Tabel 9 : Hasil Cleaning Kolom Category
|     |                     book_title                    |     book_author    |          publisher          | Book-Rating |         clean_category        |
|----:|:-------------------------------------------------:|:------------------:|:---------------------------:|:-----------:|:-----------------------------:|
|  3  | Flu: The Story of the Great Influenza Pandemic... |   Gina Bari Kolata |        Farrar Straus Giroux |           0 |                       Medical |
|  16 | More Cunning Than Man: A Social History of Rat... | Robert Hendrickson | Kensington Publishing Corp. |           6 |                        Nature |
|  22 | If I'd Known Then What I Know Now: Why Not Lea... |      J. R. Parrish |               Cypress House |          10 |                     Reference |
|  94 | The Right Man : The Surprise Presidency of Geo... |         DAVID FRUM |                Random House |           8 |             Political Science |
| 241 | The Case of the Lost Look-Alike (An Avon Camel... |    Carol J. Farley |                  Avon Books |           0 | Detective and mystery stories |


### Alasan Penggunaan
* Mengambil dataset books dan rating karena CBF memberikan rekomendasi berdasarkan kemiripan konten yang terkandung
* Membersihkan data dari nilai null dan duplicates untuk menghindari bias dan kesalahan analisa pada model
* Melakukan *merging* untung mengambil kolom *rating*.
* Melakukan *cleaning category* karena terdapat *category* yang muncul berulang-ulang dan memiliki simbol.

## Collaborative FIltering
### Data Processing
* Menggunakan *Dataset Rating* untuk *modelling*
* Melakukan *Encode User-ID* dan ISBN menggunakan fungsi enumerate pada python
* Mapping Hasil encode ke dataframe menggunakan fungsi map()
* Mengacak dataset
* Membagikan dataset menjadi data training dan data testing menggunakan fungsi train_test_split pada *library* sklearn dengan perbandingan 80:20

### Alasan Penggunaan
* Menggunakan dataset Rating dikarenakan model akan memberikan rekomendasi berdasarkan rating yang diberikan user
* Proses encoding dilakukan agar model nantinya mudah dipahami dan di proses oleh algoritma. serta untuk mengubah data kategorikal menjadi data numerikal
* Membagi dataset bertujuan agar model dapat di evaluasi setelah melakukan *training*


# Modeling
## Modeling Content Based Filtering
### Proses yang Dilakukan
* Melakukan perhitungan tf-idf dengan Tfidfvectorizer pada *library* sklearn
* Perhitungan dilakukan dengan fungsi .fit() agar perhitungan dapat dilakukan
* Kemudian mentransformasikan hasil perhitungan kedalam bentuk skor pada data dengan fungsi fit_transform()
* Fitur yang ditransformasikan adalah isbn
* Setelah itu maka dilakukan *consine similarity measurement* menggunakan *library* sklearn
* Hasil dari perhitungan di masukkan kedalam *dataframe* 
* Membuat fungsi rekomendasi buku untuk melakukan perhitungan dan menampilkan rekomendasi buku berdasarkan judul buku
* Input paramater pada fungsi adalah judul_buku, similiarity_data,index,k dimana judul_buku yang merupakan input judul buku yang akan diperhitungkan, similiarity data merupakan dataframe hasil perhitungan consine_similiarity, index yang merupakan list judul buku dan nama pengarang buku dan k merupakan kelipatan yang akan ditampilkan sebanyak k.
* Untuk proses pada fungsi tersebut, judul_sebagai input akan masuk kedalam pencarian pada df hasil cosine_similiarity dengan menggunakan argpartition dan juga merubah dataframe menjadi numpy dengan rentang -1,-k,-1
* Kemudian mengambil similiarity terbesar dari index yang ada
* Selanjutnya hasil akan disimpan dan drop judul buku yang sebagai input
* Dan terakhir hasil disimpan kedalam dataframe dengan menampilkan top k

 ### Input data untuk Evaluasi
 
 Tabel  10 : Data Input Testing Untuk Evaluasi
 
|              **book_title**              |  **book_author**  |     **publisher**     | **Book-Rating** | **clean_category** |
|:----------------------------------------:|:-----------------:|:---------------------:|:---------------:|:------------------:|
| From Conception to Birth: A Life Unfolds | Alexander Tsiaras | Bantam Dell Pub Group |              10 |            Medical |


Pada data input adalah  rating 8 pada judul buku From Conception to Birth: A Life Unfolds dengan author Alexander Tsiaras.

### Output Data 

Tabel 11 : Hasil Prediksi System Rekomendasi CBF

|   |                   **book_title**                  |     **book_author**    |          **publisher**         | **clean_category** | **Book-Rating** |
|--:|:-------------------------------------------------:|:----------------------:|:------------------------------:|:------------------:|:---------------:|
| 1 | Caring for the Parkinson Patient: A Practical ... |       J. Thomas Hutton |               Prometheus Books |            Medical |               8 |
| 2 | Parkinson's Disease: A Complete Guide for Pati... | William J., Md. Weiner | Johns Hopkins University Press |            Medical |               8 |
| 0 | Flu: The Story of the Great Influenza Pandemic... |       Gina Bari Kolata |           Farrar Straus Giroux |            Medical |               0 |
| 3 | Positive Lives: Responses to HIV : A Photodocu... |            Steve Mayes |                        Cassell |            Medical |               0 |
| 4 | The Youngest Science: Notes of a Medicine-Watc... |           Lewis Thomas |                    Penguin USA |            Medical |               0 |

Pada tabel 11 dapat dilihat bahwa sistem rekomendasi berhasil melakukan prediksi dengan book author yang sama secara keseluruhan

## Modeling Collaborative FIltering
### Proses yang dilakukan
* Melakukan proses embedding terhadap data **user** dan **book**. Selanjutnya, lakukan operasi perkalian dot product antara embedding user dan book. Selain itu, kita juga dapat menambahkan bias untuk setiap user dan resto. Skor kecocokan ditetapkan dalam skala [0,1] dengan fungsi aktivasi sigmoid.
* Model ini menggunakan Binary Crossentropy untuk menghitung loss function, Adam (*Adaptive Moment Estimation*) sebagai optimizer dengan *learning rate* sebesar 0.001, dan *root mean squared error* (RMSE) sebagai metrics evaluation.
* Kemudian Inisialisasi nilai awal untuk embedding. Dalam kasus ini, 'he_normal' digunakan, yang merupakan metode inisialisasi yang biasa digunakan dalam *deep learning* dan juga Regularisasi yang diterapkan pada *embedding*. Dalam kasus ini, regularisasi L2 dengan parameter 1e-6 untuk membantu mengurangi kompleksitas model dan menghindari *overfitting*.
* Kemudian model masuk ke tahapan *training* dengan fungsi .fit() menggunakan epoch 50 dan batch_size 160

### Hasil Testing System Rekomendasi Menggunakan CF

Untuk data input adalah user-id 98391 dimana rating tertinggi yang diberikan adalah pada judul dibawah ini 

Tabel 12 : Top 10 High Rating *User book*

|                     **Top 10 book recommendation**                     |
|:----------------------------------------------------------------------:|
|      You're a Disgrace, Daisy (Definitely Daisy) By Jenny Oldfield     |
|                   Richard III By William Shakespeare                   |
|               Mrs. Fixit Easy Home Repair By Terri McGraw              |
|                   Roses for Dummies By Lance Walheim                   |
| Don't Roll Your Eyes At Me, Young Man! A Zits Sketchbook 3 Jerry Scott |
|                        Classic Rock By Gary Cee                        |
|                     Chessplayer By William Pearson                     |
|        The Compact Oxford English Dictionary By Edmund S. Weiner       |
|                 Introducing Nietzsche By Laurence Gane                 |
|            Roger Ebert's Movie Yearbook 2003 By Roger Ebert            |


Tabel diatas merupakan buku dengan rating terbaik yang diberikan oleh *user* 98391 yang dapat dilihat pada tabel diatas. 

## Perbandingan Kelebihan dan Kekurangan pada metode CBF dan CF
|                                        |                                        **Content-Based Filtering**                                       |                                                             **Collaborative Filtering**                                                            |
|----------------------------------------|:--------------------------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------:|
|              **Kelebihan**             | - Tidak memerlukan data pengguna lain atau informasi tentang perilaku pengguna                           | - Menggunakan informasi dari pengguna lain untuk memberikan rekomendasi                                                                            |
|                                        | - Dapat memberikan rekomendasi personalisasi berdasarkan karakteristik item dan preferensi pengguna      | - Mampu menemukan kesamaan antara pengguna berdasarkan preferensi mereka                                                                           |
|                                        | - Tidak terpengaruh oleh "cold start problem"                                                            | - Efektif dalam menghadapi "cold start problem"                                                                                                    |
|             **Kekurangan**             | - Terbatas pada kesamaan konten                                                                          | - Membutuhkan data pengguna yang cukup untuk memberikan rekomendasi yang akurat                                                                    |
|                                        |                                                                                                          | - Tidak efektif dalam menghadapi item baru atau jarang terjadi                                                                                     |
|                                        |                                                                                                          | - Mungkin terjadi masalah sparsitas, yaitu ketika matriks item-pengguna sangat jarang atau tidak lengkap, sulit memberikan rekomendasi yang akurat |
| **Metode yang Digunakan pada Situasi** | - Berguna ketika informasi yang relevan tentang item tersedia                                            | - Berguna ketika data pengguna yang cukup tersedia dan keterhubungan antar pengguna penting untuk memberikan rekomendasi                           |
|                                        | - Cocok untuk merekomendasikan item yang serupa berdasarkan karakteristik tertentu                       | - Cocok untuk merekomendasikan item berdasarkan preferensi pengguna yang serupa                                                                    |
|                                        | - Tidak tergantung pada perilaku pengguna atau keputusan pengguna sebelumnya                             | - Tergantung pada informasi perilaku pengguna sebelumnya dalam menemukan kesamaan                                                                  |
|                                        | - Cocok untuk mengatasi "cold start problem" karena dapat memberikan rekomendasi berdasarkan konten item | - Tidak cocok untuk mengatasi "cold start problem" karena membutuhkan data pengguna yang cukup                                                     |

# Evaluation
## Content Based Filtering

Untuk evaluasi dari sistem rekomendasi dengan pendekatan  _content based filtering_  kita dapat menggunakan salah satu metric yaitu  _precision@K_. Apa itu  _precision_?  _Precision_  adalah perbandingan antara  _True Positive (TP)_  dengan banyaknya data yang diprediksi positif. Atau juga bisa ditulis secara matematis sebagai berikut :

_precision = TP / (TP + FP)_

dimana : TP =  _True Positive_  atau positif yang sebenarnya FP =  _False Positive_  atau positif yang salah dari hasil prediksi

Namun pada sistem rekomendasi kita tidak akan menggunakan  _True positive_  atau  _False Positive_  melainkan  _rating_  yang diberikan pada buku untuk menentukan buku yang direkomendasikan relevan atau tidak. Dengan rumus sebagai berikut :

_precision@K = (# of recommended item that relevan) / (# of recommended item)_

Lalu apa definisi relevan? Bisa kita definisikan sebagai berikut :

Relevan :  _Rating_  > 5 Tidak relevan :  _Rating_  < 5

Angka 5 tersebut merupakan nilai arbiter dimana kita mengatakan bahwa nilai yang berada diatas akan dianggap relevan. Ada banyak metode untuk memilih nilai itu, tetapi untuk proek ini, kita akan menggunakan angka 5 sebagai ambang batas, yang berarti setiap buku yang memiliki rating di atas 5, akan dianggap relevan dan di bawahnya tidak akan relevan.

-   Pertama kita memilih nilai K yaitu 5 (sesuai total hasil rekomendasi)
-   Lalu kita akan menentukan relevansi  _threshold_  yaitu 5
-   Kemudian kita akan memfilter semua buku rekomendasi sesuai  _threshold_
-   Terakhir hitung dengan rumus  _precision@K_  di atas

Dari hasil rekomendasi yang dihasilkan, didapatkan  _precision_  sebagai berikut :

_precision@10 = 2 / 5_  _precision@10 = 40%_

Karena terdapat 5 buku yang memiliki rating di atas  _threshold_  maka didapatkan 50%  _precision_  dari model sistem rekomendasi dengan pendekatan  _content based filtering_.

## Collaborative Filtering
* Dalam Collaborative Filtering, metrik evaluasi yang digunakan adalah RMSE (Root Mean Squared Error), yang sering digunakan dalam masalah regresi atau prediksi kontinu.
* Nilai RMSE yang lebih kecil menunjukkan bahwa model memberikan performa yang lebih baik.

RMSE = $$\sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2}$$

* Untuk hasil performa learning pada model dapat dilihat pada gambar berikut
![image](https://github.com/LukmanAbdiansyah/dicoding-mlt1-submission2/assets/74924298/f972ca95-9e0e-40e2-ab7f-efa2c0bfa012)

Gambar 1 : Hasil Performa Training Model

Pada gambar 1 terlihat bahwa model memiliki performa yang cukup bagus dengan nilai RMSE sebesar 0.336 untuk train dan 0.329 untuk testing pada epoch ke 50. akan tetapi model tesebut sudah cukup baik pada di epoch ke 30, karena di titik tersebut kurva train dan test berpotongan, hal ini menandakan bahwa model tidak overfitting maupun underfitting.
# Kesimpulan
* Proyek System rekomendasi buku dapat menggunakan metode Content Based Filtering maupun Collaborative Filtering
* Untuk masing-masing sistem memiliki keunggulan dan kekurangan masing-masing
* Pada Sistem Content Based Filtering mampu memberikan system rekomendasi dengan tingkat evaluasi akurasi, presisi sebesar 40%
* Sedangkan pada Collaborative Filtering Memberikan hasil nilai evaluasi RMSE sebesar 0.336 dan Validasi RMSE 0.329 dimana model mengalami overfitting
* Apabila ingin membuat sistem dengan berdasarkan Content atau atribut pada item, maka CBF dapat menjadi solusi
* Metode CF dapat menjadi solusi  jika ingin membuat sistem rekomendasi berdasarkan rating yang diberikan pengguna
 
Dalam proyek ini terdapat beberapa kekurangan yaitu :

* Untuk sistem CBF saat ini dapat di eksplor dengan based lain seperti User based yang mungkin bisa memberikan preferensi rekomendasi yang lebih baik sehingga dapat meningkatkan presisi
* Perlu adanya penelitian lebih lanjut dalam penerapan model *Collaborative Filtering* dengan Teknik *Deep Learning*


# Referensi

* [1] Kurmashov, N., Latuta, K., & Nussipbekov, A. (2015). Online book recommendation system. _2015 Twelve International Conference on Electronics Computer and Computation (ICECCO)_. https://doi.org/10.1109/icecco.2015.7416895
* [2] Devika, P., Jyothisree, K., Rahul, P., Arjun, S., & Narayanan, J. (2021). Book recommendation system. _2021 12th International Conference on Computing Communication and Networking Technologies (ICCCNT)_. https://doi.org/10.1109/icccnt51525.2021.9579647
* [3] P. Mathew, B. Kuriakose and V. Hegde, "Book Recommendation System through content based and collaborative filtering method," 2016 International Conference on Data Mining and Advanced Computing (SAPIENCE), Ernakulam, India, 2016, pp. 47-52.
https://doi.org/10.1109/SAPIENCE.2016.7684166.
