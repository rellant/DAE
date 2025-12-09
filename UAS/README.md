
📋 Pendahuluan
Proyek ini bertujuan untuk mengungkap pola tersembunyi di balik penentuan harga mobil bekas dan membangun sistem prediksi otomatis. Menggunakan workflow KNIME, kami menganalisis spesifikasi teknis dari 1.436 unit Toyota Corolla untuk mengklasifikasikan harga ke dalam dua kategori: High (Mahal) dan Low (Murah).

Variabel kunci yang diteliti meliputi:

Harga (Price) & Umur (Age)

Jarak Tempuh (KM) & Bahan Bakar (Fuel Type)

Fitur Fisik (HP, Berat, dll.)

🛠️ Alur Pengerjaan (Workflow)
Kami membagi proses teknis menjadi tiga tahapan strategis untuk memastikan data bersih dan model akurat:

1. Data Processing & Cleaning
Tahap ini mengubah data mentah menjadi format yang siap diolah mesin.

Penyaringan: Membuang kolom yang tidak relevan (seperti Id, Model, Cylinders) menggunakan node Column Filter.

Konversi Tipe Data: Mengubah angka yang terbaca teks menjadi numerik murni dengan String to Number agar korelasi dapat dihitung.

Labeling: Menggunakan Rule Engine untuk menetapkan target prediksi: Mobil dengan harga di atas median (€9.900) dilabeli "High", sisanya "Low".

2. Feature Engineering
Encoding: Mengubah data kategori (Bensin/Diesel) menjadi format biner menggunakan One to Many.

Splitting: Membagi data secara adil: 80% untuk Training (belajar) dan 20% untuk Testing (ujian) menggunakan Partitioning.

3. Modeling (Klasifikasi)
Algoritma: Menggunakan Random Forest Learner karena kemampuannya menangani banyak fitur sekaligus.

Anti-Curang: Kolom Price asli dihapus dari input model untuk mencegah kebocoran data (data leakage), sehingga model murni menebak berdasarkan spesifikasi mobil.

📊 Visualisasi & Eksplorasi Data
Berikut adalah interpretasi visual dari data yang telah diolah:

📉 Histogram (Sebaran Harga): Pasar didominasi oleh mobil segmen menengah ke bawah. Grafik menunjukkan kemiringan ke kanan (right-skewed), menandakan stok mobil "premium" jumlahnya sedikit.

🗓️ Scatter Plot (Umur vs Harga): Terlihat pola garis lurus menurun yang tajam. Semakin tua mobil, harga jatuh drastis. Ini adalah hubungan terkuat dalam dataset.

⛽ Box Plot (Bahan Bakar): Varian Diesel memiliki rentang harga yang sangat lebar (tidak stabil), sedangkan varian Bensin (Petrol) memiliki harga pasar yang jauh lebih konsisten.

💡 Temuan Utama (Key Insights)
Berdasarkan hasil visualisasi dan evaluasi model Scorer, berikut adalah kesimpulan akhirnya:

"Umur adalah Raja": Tahun pembuatan mobil adalah faktor penentu harga paling mutlak, mengalahkan fitur fisik seperti Power Steering atau Airbag.

Stabilitas Bensin: Mobil berbahan bakar bensin adalah komoditas paling aman untuk diperjualbelikan karena harganya stabil dan mudah diprediksi.

Pengaruh Berat Mobil: Mobil yang lebih berat cenderung masuk kategori harga "High", kemungkinan karena asosiasi dengan varian bodi yang lebih besar atau fitur yang lebih lengkap.

Akurasi Prediksi: Model Machine Learning berhasil mengenali kategori harga mobil (High/Low) dengan akurasi ~90%.

Peran Kilometer: Meskipun jarak tempuh (KM) berpengaruh negatif terhadap harga, efeknya tidak sekuat faktor umur. Mobil tua dengan KM rendah tetap dihargai murah.

Laporan ini disusun berdasarkan hasil eksekusi workflow KNIME pada dataset Toyota Corolla.
