# Laporan Proyek Machine Learning Prediksi Harga Rumah - Mellania Permata Sylvie
---
 
## Domain Problem
Rumah atau tempat tinggal merupakan salah satu kebutuhan primer bagi manusia. Maka dari itu, penting bagi kita untuk membuat perencanaan agar kelak dapat memiliki tempat tinggal pribadi. Agar bisa membuat perencanaan yang baik, salah satunya yaitu kita harus bisa memprediksi berapa harga rumah yang akan kita beli. Seiring berjalannya waktu, harga rumah selalu berubah-ubah. Ada beberapa faktor yang mempengaruhi harga rumah, diantaranya yaitu letak rumah, usia bangunan, jumlah ruangan, jumlah kamar, dan sebagainya.

Proyek ini berfokus pada domain Ekonomi dan Bisnis. Dengan memanfaatkan data yang ada, peneliti menerapkan model regresi untuk memprediksi berapakah harga rumah di masa yang akan datang. Dengan mengetahui prediksi harga rumah, pembeli dapat mendapatkan harga yang bagus dan investor juga dapat memprediksi potensi pengembalian investasi mereka. 
Dalam mengerjakan proyek ini, peneliti memulai dengan studi literatur. Adapun referensi yang digunakan oleh peneliti diantaranya :
- [Jurnal 1]  -  California House’s Price Prediction using Machine Learning 
- [Jurnal 2]  -  Research on Ensemble Learning-based Housing Price Prediction Model
- [Jurnal 3]  -  Prediksi Harga Rumah Menggunakan Web Scrapping Dan Machine Learning Dengan Algoritma Linear Regression

## Business Understanding
### Problem Statements
Seperti yang dijelaskan sebelumnya, proyek ini akan membuat program prediksi harga rumah. Sehingga permasalahan yang perlu untuk diselesaikan yaitu sebagai berikut.
- Berapakah prediksi harga nilai rumah berdasarkan fitur yang sudah ada ?
- Fitur-fitur apa sajakah yang paling berpengaruh terhadap harga rumah ?

### Goals
Sesuai dengan permasalahan yang ada, maka goals dalam proyek ini diantaranya sebagai berikut.
- Model dapat memprediksi harga rumah dengan hasil yang seakurat mungkin.
- Mengetahui fitur-fitur yang paling berpengaruh besar terhadap harga rumah.

### Solution Statements
Agar bisa menjawab masalah di atas dan mencapai goals yang sudah ditentukan, maka solusi yang dilakukan yaitu membuat model regresi dengan harga rumah (median house value) sebagai target. Algoritma yang digunakan dalam model development ini yaitu KNN, Random Forest, dan algoritma Boosting. Berikut penjelasannya.
- **K-Nearest Neighbor**
Algoritma K-Nearest Neighbor merupakan algoritma yang menggunakan ‘kesamaan fitur’ untuk memprediksi nilai dari setiap data yang baru. Dengan kata lain, setiap data baru diberi nilai berdasarkan seberapa mirip titik tersebut dalam set pelatihan. algoritma KNN ini relatif sederhana, mudah dipahami dan digunakan.
- **Random Forest**
Algoritma random forest adalah salah satu algoritma supervised learning yang dapat menyelesaikan masalah klasifikasi dan regresi. Random forest termasuk ke dalam kelompok model ensemble yang merupakan model prediksi yang terdiri dari beberapa model dan bekerja secara bersama-sama. Random forest termasuk dalam algoritma yang sering digunakan karena cukup sederhana tetapi memiliki stabilitas yang mumpuni.
- **Boosting Algorithm**
Algoritma boosting merupakan algoritma yang bekerja dengan membangun model dari data latih. Kemudian ia membuat model kedua yang bertugas memperbaiki kesalahan dari model pertama. Model ditambahkan sampai data latih terprediksi dengan baik atau telah mencapai jumlah maksimum model untuk ditambahkan. algoritma ini bertujuan untuk meningkatkan performa atau akurasi prediksi.

## Data Understanding
Proyek ini menggunakan dataset California Housing Prices. Dataset ini berisi mengenai Harga rumah rata-rata untuk distrik California berasal dari sensus 1990. Dataset ini berisi 20640 data dan terdapat 10 fitur, berikut penjelasannya.
1. **longitude** : Ukuran seberapa jauh ke barat sebuah rumah, nilai yang lebih tinggi lebih jauh ke barat
2. **latitude** : Ukuran seberapa jauh ke utara sebuah rumah, nilai yang lebih tinggi lebih jauh ke utara
3. **housing_median_age** : Usia rata-rata sebuah rumah dalam satu blok, angka yang lebih rendah adalah bangunan yang lebih baru
4. **total_rooms** : Jumlah total kamar dalam satu blok
5. **total_bedrooms** : Jumlah total kamar tidur dalam satu blok
6. **population** : Jumlah total orang yang tinggal dalam satu blok
7. **households** : Jumlah total rumah tangga, sekelompok orang yang tinggal dalam satu unit rumah, untuk satu blok
8. **median_income** : Pendapatan rata-rata untuk rumah tangga dalam satu blok rumah (diukur dalam puluhan ribu Dolar AS)
9. **median_house_value**: Nilai median rumah untuk rumah tangga dalam satu blok (diukur dalam Dolar AS)
10. **ocean_proximity** : Lokasi rumah dengan laut/laut

Dataset ini bisa diunduh di Kaggle. Berikut linknya [Klik Disini].

## Data Preparation
Dalam proyek ini, tahapan data preparation yang digunakan yaitu ada 4, yaitu encoding fitur kategori, reduksi dimensi dengan PCA, membagi dataset, dan standarisasi. Berikut merupakan penjelasannya :
- **Encoding Fitur Kategori**
Pada tahap Encoding Fitur Kategori ini teknik yang digunakan adalah teknik one-hot-encoding. Proses ini dilakukan dengan library pandas dengan fitur get_dummies. Pada proses ini, kita mengubah variabel kategori menjadi variabel numerik. Tujuan dari teknik ini yaitu dengan mendapatkan fitur baru yang sesuai, sehingga dapat mewakili variabel kategori.
- **Reduksi Dimensi dengan PCA**
Teknik selanjutnya yang digunakan yaitu teknik reduksi dimensi. Teknik ini menggunakan Principal Component Analysis (PCA). Prosedur teknik ini yaitu mengurangi jumlah fitur dengan tetap mempertahankan informasi pada data. Proses yang dilakukan pertama yaitu mengecek fitur yang berkorelasi tinggi dengan fungsi pairplot. Setelah itu membuat class PCA dengan library scikit learn. lalu mereduksi fiturnya, disini membuat fitur baru bernama factor yang menggantikan fitur total_rooms, total_bedrooms, population, dan households.
- **Membagi Dataset**
Sebelum membuat model, penting bagi kita untuk membagi dataset menjadi data latih (train) dan data uji (test). Proses membagi dataset ini menggunakan library Scikitlearn. Disini datasetnya dibagi menjadi 80% data train dan 20% data test.
- **Standarisasi**
Teknik standarisasi ini dilakukan dengan tujuan untuk membantu membuat fitur data menjadi bentuk yang lebih mudah diolah dengan algoritma, sehingga modelnya memiliki performa lebih baik. Proses standarisasi ini menggunakan teknik StandarScaler dari library Scikitlearn.

## Modeling
Proyek ini menggunakan 3 jenis model development. pertama yaitu model algoritma K-Nearest Neighbor (KNN), kedua model algoritma Random Forest, dan ketiga yaitu model boosting algorithm.
Proses modeling yang digunakan dalam proyek ini yaitu menggunakan 3 model algoritma berbeda kemudian membandingkan hasil performanya. Dengan begini kita dapat mengetahui model mana yang performanya paling baik.
Setelah dilakukan model development dengan 3 algoritme berbeda, berikut merupakan hasil perbandingannya :
![perbandingan model](https://picc.io/ZoCt4P2.jpg "Perbandingan model")
Untuk mengetahui algoritma mana yang dapat memprediksi lebih baik, maka berikut disajikan hasil prediksi dengan ketiga model berbeda.
![hasil prediksi](https://picc.io/HffIp9Y.jpg "hasil prediksi")
Berdasarkan hasil di atas dapat diketahui bahwa prediksi dari model Random Forest yang paling mendekati dengan data yang diprediksi. Jadi, model yang performanya bekerja paling baik yaitu model dengan algoritma Random Forest.

## Evaluation
Karena proyek ini termasuk dalam kasus regresi, maka metrik yang digunakan yaitu Mean Squared Error (MSE). Metrik ini menghitung selisih rata-rata nilai sebenarnya dengan nilai prediksi. Berikut merupakan rumus dari MSE :
![rumus mse](https://picc.io/2gIFsmX.jpg "Rumus MSE")
Keterangan:
N = jumlah dataset
yi = nilai sebenarnya
y_pred = nilai prediksi

Kelebihan dari metrik ini yaitu metrik ini berguna jika kita memiliki nilai tak terduga yang harus kita pedulikan. Nilai sangat tinggi atau rendah yang harus kita perhatikan. Sedangkan kekurangan dari metrik ini yaitu Jika kita membuat satu prediksi yang sangat buruk, kuadrat akan membuat kesalahan lebih buruk dan itu mungkin membuat metrik cenderung melebih-lebihkan keburukan model.

cara menerapkan metrik ini ke dalam kode yaitu dengan kode berikut :
```sh
mse = pd.DataFrame(columns=['train', 'test'], index=['KNN','RF','Boosting'])
model_dict = {'KNN': model_knn, 'RF': model_RF, 'Boosting': model_boosting}
for name, model in model_dict.items():
    mse.loc[name, 'train'] = mean_squared_error(y_true=y_train, y_pred=model.predict(X_train))/1e3 
    mse.loc[name, 'test'] = mean_squared_error(y_true=y_test, y_pred=model.predict(X_test))/1e3
 
mse
```

---

[//]: # (berikut merupakan daftar link yang digunakan)

[Jurnal 1]: <http://www.ijics.com/gallery/j26.pdf>
[Jurnal 2]: <https://pdfs.semanticscholar.org/77ba/361f1375441f9d9b928967cfb0dbcd3e8432.pdf>
[Jurnal 3]: <https://jurnal.mdp.ac.id/index.php/jatisi/article/download/701/219/>
[Klik Disini]: <https://www.kaggle.com/camnugent/california-housing-prices>


