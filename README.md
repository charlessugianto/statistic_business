# statistic_business
Link youtube: abc.com

# 1. Background dan Tujuan Analisa
Dalam project kali ini, peneliti akan mengolah dataset yang menggambarkan pendapatan individu berdasarkan berbagai faktor seperti usia, jenis kelamin, pendidikan, posisi pekerjaan, dan pengalaman kerja. Peneliti ingin memahami bagaimana faktor-faktor ini mempengaruhi pendapatan seseorang dan juga untuk melakukan prediksi mengenai pendapatan individu.

# 2. Dataset dan Tools
Dataset: https://www.kaggle.com/datasets/rkiattisak/salaly-prediction-for-beginer
Tools: Jupyter Notebook
Dataset terdiri dari 375 baris data yang mencakup informasi tentang usia, jenis kelamin, tingkat pendidikan, jabatan, lama pengalaman kerja, dan besaran gaji. Sebelum dilakukan pengolahan lebih lanjut, tahapan persiapan dilakukan dengan menghilangkan nilai yang hilang dan data yang duplikat.

A.	Missing Value dan Duplicated Data
Dalam proses pengolahannya terdapat 3 point penting yang menjadi perhatian peneliti, sebagai berikut:
-	Data Job Title tidak akan digunakan dalam pemodelan regresi karena terlalu bervariasi.
-	Data jenis kelamin (Gender) akan diubah dari data kategorikal menjadi data numerik dengan Male = 0 dan Female = 1.
-	Data tingkat pendidikan (Education Level) akan diubah dari data kategorikal menjadi data numerik dengan Bachelor’s = 0, Master’s = 1, dan PhD = 2.

# 3 Deskripsi Data
3.1 Deskripsi Data Numerik
Penelitian ini mengungkapkan bahwa terdapat suatu korelasi yang signifikan antara variabel usia, lama pengalaman kerja, dan besaran gaji dalam konteks populasi yang diamati. Hasil analisis statistik menunjukkan adanya hubungan positif yang kuat antara usia dan lama pengalaman kerja dengan besaran gaji yang diterima oleh individu-individu dalam sampel studi ini. Korelasi positif ini menunjukkan bahwa semakin tinggi usia dan semakin lama pengalaman kerja, semakin tinggi pula besaran gaji yang cenderung diterima oleh individu-individu dalam studi ini.

3.2 Deskripsi Data Kategorik
Secara statistik, terdapat perbedaan yang signifikan dalam rata-rata gaji antara individu berjenis kelamin laki-laki dan perempuan, dengan rata-rata gaji laki-laki secara konsisten lebih tinggi dibandingkan dengan rata-rata gaji perempuan. Selain itu, terdapat pola yang menunjukkan bahwa rata-rata gaji meningkat seiring dengan peningkatan tingkat pendidikan, yang mengindikasikan adanya hubungan positif antara tingkat pendidikan yang lebih tinggi dan besaran rata-rata gaji dalam populasi yang diteliti.

# 4. Visualisasi
Dalam konteks penelitian ini, temuan menunjukkan bahwa terdapat suatu hubungan positif antara masa kerja individu dan besaran gaji yang diterimanya. Artinya, semakin lama seseorang telah bekerja, semakin tinggi pula besaran gaji yang cenderung diterimanya. Selain itu, temuan ini menunjukkan bahwa terdapat hubungan positif antara usia individu dan masa kerja yang dimilikinya. Ini mengindikasikan bahwa semakin tua seseorang, semakin banyak pengalaman kerja yang biasanya telah diakumulasinya. Namun, berdasarkan analisis yang dilakukan, jenis kelamin tidak memainkan peran yang signifikan dalam menentukan besaran gaji seseorang. Artinya, perbedaan gender tidak memiliki dampak yang cukup besar dalam memengaruhi besaran gaji individu dalam sampel yang diteliti.

# 5. Uji Statistik 
Dataset ini mencakup dua kategori jenis kelamin, yaitu male dan female. Peneliti ingin melakukan pengujian statistik untuk menentukan apakah terdapat perbedaan yang signifikan antara rata-rata gaji laki-laki dan rata-rata gaji Perempuan, dengan taraf signifikansi sebesar 10%. Selain itu, standar deviasi populasi tidak diketahui sehingga pengujian digunakan t-test.
H0: µa = µb
H1: µa > µb

-	Uji Varians
Ada bukti yang cukup kuat menunjukkan bahwa terdapat perbedaan yang signifikan antara rata-rata gaji individu berjenis kelamin laki-laki dan perempuan. Rata-rata gaji laki-laki cenderung lebih tinggi daripada rata-rata gaji perempuan.

-	Derajat Kebebasan dan Confidence Level
Berdasarkan hasil analisis, dapat disimpulkan bahwa dengan tingkat keyakinan sebesar 90%, terdapat bukti yang kuat bahwa rata-rata gaji laki-laki melebihi rata-rata gaji perempuan. Selain itu, hasil dari interval kepercayaan (confidence interval) menunjukkan bahwa dengan tingkat kepercayaan sebesar 90%, perkiraan interval untuk perbedaan rata-rata gaji adalah dari -1535 hingga 16208.

# 6. Model Regresi
6.1 Single Predictor
Terkait dengan prediksi gaji seseorang dari lama pengalaman kerjanya.
Salary = 31960 + 6763 × Years of Experience
Hasil analisis menghasilkan model regresi yang memiliki tingkat R-squared yang cukup tinggi sebesar 85,46%. Dalam konteks perbandingan dua individu dengan perbedaan pengalaman kerja selama satu tahun, model ini memprediksi bahwa individu dengan pengalaman kerja lebih lama 1 tahun akan memiliki perbedaan pendapatan sekitar 6763. 
Residual Plot
Normality of Error Assumption
 
6.2 Single Predictor with Log Transormation
Terkait dengan  gaji seseorang dari lama pengalaman kerjanya, serta transformasi logaritmik pada variabel prediktor.
Dalam hasil analisis, tercatat bahwa nilai R-squared yang diperoleh adalah sekitar 0,76. Nilai ini menunjukkan bahwa kemampuan model untuk menjelaskan variasi dalam data tidak sekuat pada model sebelumnya yang memiliki R-squared sebesar 0,85, yang tidak menggunakan transformasi logaritmik. Oleh karena itu, dalam konteks pemodelan regresi dengan satu variabel prediktor, lebih disarankan untuk menggunakan model regresi tanpa transformasi logaritmik.

6.3 Multiple Predictors with One Interaction
Dalam analisis, peneliti akan menggunakan semua variabel prediktor, termasuk interaksi usia dan lama pengalaman kerja, dengan tingkat pendidikan sebagai variabel kategorikal.

6.3.1 Evaluasi model dengan K-Fold cross validation
Nilai rata-rata R-squared yang ditemukan adalah sekitar 0,88, mengindikasikan bahwa model ini memiliki kualitas yang baik dan mampu menjelaskan sekitar 88% variasi dalam besaran gaji.

6.3.2 Fitting Model
Koefisien persamaan regresi di atas menghasilkan intercept yang kurang optimal, karena interpretasinya tidak sesuai (gaji tidak dapat bernilai negatif) dan umumnya usia kerja tidak dimulai dari nol, sehingga variabel usia dicentering.

6.3.3 Centering Variabel Usia
Average = 37 tahun, digunakan sebagai dasar perhitungan

6.3.4 K Fold Cross Validation
Tercapai nilai R-squared rata-rata sekitar 0,89, yang mengindikasikan bahwa model ini memiliki kualitas yang baik dan mampu menjelaskan sekitar 89% variasi dalam besaran gaji.

Gaji Bachelor = 68396+3042 ×(Age - 37)−9311×Gender+2561×YearsOfExperience+3×(Age - 37)×YearsOfExperience

Gaji Master = 68396+19574+3042×(Age - 37)−9311×Gender+2561×YearsOfExperience+3×(Age - 37)×YearsOfExperience

Gaji PhD = 68396+26339+3042×(Age - 37)−9311×Gender+2561×YearsOfExperience+3×(Age - 37)×YearsOfExperience

# 7. Penjelasan
-	Jenis kelamin: Perempuan diperkirakan memiliki gaji 9,311 dollar lebih rendah daripada laki-laki dengan kondisi yang sama.
-	Lama pengalaman kerja: Lama pengalaman kerja tambahan 1 tahun diperkirakan meningkatkan gaji sebesar 2,561 dollar.
-	Intercept: Seorang laki-laki berusia 37 tahun dengan gelar Bachelor’s tanpa pengalaman kerja diperkirakan memiliki gaji sebesar 68,396 dollar.
-	Tingkat pendidikan: Seseorang dengan gelar Master’s diperkirakan memiliki gaji 19,574 dollar lebih tinggi daripada yang memiliki gelar Bachelor’s.
-	Usia: Usia 1 tahun lebih tua dari 37 tahun diperkirakan berarti gaji lebih tinggi sebesar 3,042 dollar.
Residual Plot
Normality of Error Assumption
 
# 8 Kesimpulan 
Berdasarkan hasil Analisa, maka dapat disimpulkan usia, jenis kelamin, lama pengalaman kerja, dan tingkat pendidikan memengaruhi gaji dan dapat digunakan dalam prediksi. Model regresi dengan lama pengalaman kerja sebagai satu-satunya predictor memiliki R-squared 0,85, sementara model dengan transformasi logaritmik memiliki R-squared 0,76. Model regresi dengan semua predictor dan interaksi usia dan lama pengalaman kerja memiliki R-squared 0,89, dengan centering pada variabel usia.

# 9 Referensi
Anderson, D.R., Sweeney, D.J., Williams, T.A., Camm, J.D. and Cochran, J.J., 2016. Statistics for business & economics. Cengage Learning.
Ellis, P.D., 2010. The essential guide to effect sizes: Statistical power, meta-analysis, and the interpretation of research results. Cambridge university press.
