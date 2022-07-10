# Mobile Price Classification

### Dokumentasi dataset
https://www.kaggle.com/datasets/iabhishekofficial/mobile-price-classification

### Train Model Awal
Sebelum melakukan EDA kami membuat model terlebih dahulu dengan Algoritma `Decision Tree`, `Random Forest Classifier` dan `Super Vector Classifier` untuk mengukur seberapa performa sebelum melakukan EDA\
Dan akurasi dari model memiliki perbedaan masing masing yaitu
1. Decission Tree  84 %
2. Random Forest Classifier 86 %
3. Super Vector Classifier 87 %\

## Exploratory Data Analisyst
### Korelasi Antara Fitur dengan Target
Dari semua fitur yang ada hanya terdapat 4 fitur yang memiliki korelasi diatas 10%, dimana fitur itulah yang akan di ambil sebagai variabel input. Alasan mengambil fitur dengan korelasi diatas 10% karena berpedoman pada pendapat dari Jonathan Sarwono Direktur Penjaminan Mutu di International Women University dalam artikel
http://www.databee.id/2020/12/jenis-uji-korelasi.html, 4 fitur itu adalah kolom
1. RAM = 91%
2. BATTERY_POWER = 20%
3. PX_WIDTH ( Resolusi lebar ) = 16%
4. PX_HEIGHT ( Resolusi tinggi ) = 14%

### Analisis Deskriptif
Dalam analisis ini ditemukan pada kolom `px_height` nilai minimum 0, setelah di telusuri lebih lanjut ternyata banyak informasi yang aneh dari baris yang memiliki nilai 0 tersebut dimana terdapat:
1. Kualitas HP berada di peringkat ke 3
2. Tidak memiliki bluetooth
3. Dan memiliki ram yang cukup besar
4. Memiliki battry_power yang besar
5. sc_width = 0\
*Akhirnya* kami menghapus baris tersebut karena informasi yang ada sangat ambigu

## Visualisasi Data
Visualisasi yang di digunakan hanya untuk melihat distribusi dari fitur untuk menemukan adanya outlier
![vis](https://user-images.githubusercontent.com/90812378/178136303-83d8771c-ea81-402f-bc60-142d4b933a3e.png)
#### visualisasi
Juga untuk melihat `Target` Apakah balance dari setiap class nya

![bal](https://user-images.githubusercontent.com/90812378/178136436-dbd17a6e-1e73-4cb4-96ab-699cbef436a3.png)

## Train Model 
![model](https://user-images.githubusercontent.com/90812378/178136466-e58d3586-f4cf-4ef3-a98e-7eb55ab8540a.png)
#### performa model
Perbedaan performa sebelum EDA dan setelahnya sangat jauh bahkan SVC mencapai 95%

## Hyperparameter Tuning
![hyper](https://user-images.githubusercontent.com/90812378/178136543-272aa6d6-fbae-4172-bec6-5a9ed7232e7c.png)

## Evaluation
Dari ketiga model setelah di lakukan `Hyperparameter Tuning` terjadi perbedaan yang cukup signifikan:
1. Decission Tree 88% accuaracy
2. Random Forest Classifier 90% accuracy
3. Super vektor Classifier 97% accuracy\
Berdasarkan hasil tersebut tentunya `Super Vektor Classifier lebih memiliki performa yang jauh lebih baik dibandingkan dengan yang lain. Maka kami lakukan test terakhir dengan `confussion matrix`
### Heatmap Confusion Matrix
![svc](https://user-images.githubusercontent.com/90812378/178136712-5885537b-5ff7-436f-80e1-03545b5a0c82.png)
#### Super Vektor Classifier Performa
Dimana dari `Heatmap Confusion Matrix` ini `Super Vektor` memprediksi melebihi kapasitas dari data test yang digunakan, dimana seharusnya data test nya berjumlah `400 mobile` namun di malah di prediksi `402 mobile` `perhitungan 99+1+2+87+4+3+97+5+2+102 = 402`
#### Random Forest Classifier Performa
Berbeda dengan `Random Forest` meskipun performanya kurang di bandingkan dengan `Super vektor` namun prediksinya tidak melewati batas

![rf](https://user-images.githubusercontent.com/90812378/178136898-622a4df2-97fe-477c-b5ac-342abca68bd6.png)


Maka model akhir yang layak digunakan adalah `Random Forest classifier` untuk melakukan klasifikasi pada dataset pada kasus tersebut.

#### Web Application
https://snakesystem-data-science-exploration-app-bfwrze.streamlitapp.com/




