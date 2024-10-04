# Analisis Data Eksploratif pada Dataset Penjualan Pizza

**Mata Kuliah**: Infrastruktur dan Platform Sains Data  
**Pertemuan**: 2  
**Topik**: Analisis Data Eksploratif (EDA)

Proyek ini berfokus pada melakukan **Analisis Data Eksploratif (EDA)** pada dataset penjualan pizza sebagai bagian dari pertemuan kedua dalam mata kuliah *Infrastruktur dan Platform Sains Data*. Tujuan dari eksplorasi ini adalah untuk memahami dataset dengan lebih baik melalui proses pembersihan, analisis, dan visualisasi data.

## Tujuan Proyek
Tujuan utama dari proyek ini adalah mengeksplorasi dataset menggunakan berbagai teknik EDA, yang memungkinkan kita untuk mendapatkan wawasan dan memahami data yang ada. Poin-poin utama yang dibahas adalah sebagai berikut:

### 1. Memuat Data
Dataset yang berisi informasi penjualan pizza dimuat ke dalam lingkungan. Dataset ini mencakup detail seperti:
- Jenis pizza
- Jumlah pesanan
- Harga
- Bahan-bahan
- Tanggal dan waktu pemesanan

### 2. Informasi Dasar tentang Dataset
Pada langkah ini, kita memperoleh informasi dasar seperti:
- Jumlah baris dan kolom dalam dataset.
- Nama kolom, tipe data, dan pratinjau data.
- Gambaran tentang nilai yang hilang, jika ada.

### 3. Memeriksa Nilai Duplikat dan Unik
- **Nilai Duplikat**: Dataset diperiksa untuk menemukan entri yang duplikat.
- **Nilai Unik**: Dataset dianalisis untuk menemukan jumlah nilai unik pada kolom tertentu, seperti jenis pizza, kategori, dan ukuran.

### 4. Memvisualisasikan Nilai Unik
Visualisasi (misalnya, diagram batang) dibuat untuk menunjukkan distribusi nilai unik pada fitur kategori tertentu, seperti:
- `pizza_category`
- `pizza_size`
- `pizza_ingredients`

### 5. Menemukan Nilai Kosong
Dataset dianalisis untuk mendeteksi nilai `null` atau yang hilang. Nilai kosong ini dapat mempengaruhi analisis, jadi penting untuk mengidentifikasinya sejak awal.

### 6. Mengganti Nilai Kosong
Semua nilai kosong atau hilang ditangani dan diganti berdasarkan konteks data:
- Untuk kolom numerik, imputasi rata-rata atau median dapat digunakan.
- Untuk kolom kategori, mode atau metode lain dipertimbangkan.

### 7. Memahami Tipe Data
Kami memeriksa tipe data dari setiap kolom untuk memastikan bahwa mereka sesuai untuk analisis lebih lanjut. Mengetahui tipe data membantu menentukan cara menangani data:
- `int64` untuk angka bulat (misalnya, jumlah pesanan).
- `float64` untuk harga.
- `object` untuk variabel kategori (misalnya, nama pizza, bahan-bahan).

### 8. Penyaringan Data
Dataset disaring berdasarkan kriteria tertentu untuk berfokus pada data tertentu. Misalnya:
- Pesanan dalam rentang tanggal tertentu.
- Kategori pizza tertentu (misalnya, hanya pizza "Veggie").

### 9. Membuat Box Plot
Sebuah **box plot** dibuat untuk memvisualisasikan distribusi dan penyebaran fitur numerik, seperti:
- `unit_price` dan `total_price`: Ini membantu mendeteksi outlier dan memahami distribusi harga antar jenis pizza.

### 10. Analisis Korelasi
Korelasi antara fitur numerik (misalnya, `quantity`, `unit_price`, `total_price`) dihitung untuk melihat bagaimana mereka saling berhubungan. Langkah ini membantu mengidentifikasi hubungan potensial antara variabel yang mungkin berguna untuk pemodelan atau analisis lebih lanjut.

---

## Contoh Dataset
Berikut adalah pratinjau dataset yang dieksplorasi:

| pizza_id | order_id | pizza_name_id | quantity | order_date | order_time | unit_price | total_price | pizza_size | pizza_category | pizza_ingredients                              | pizza_name               |
|----------|----------|---------------|----------|------------|------------|------------|-------------|------------|----------------|-----------------------------------------------|--------------------------|
| 1.0      | 1.0      | hawaiian_m    | 1.0      | 1/1/2015   | 11:38:36   | 13.25      | 13.25       | M          | Classic        | Sliced Ham, Pineapple, Mozzarella Cheese      | The Hawaiian Pizza        |
| 2.0      | 2.0      | classic_dlx_m | 1.0      | 1/1/2015   | 11:57:40   | 16.00      | 16.00       | M          | Classic        | Pepperoni, Mushrooms, Red Onions, Red Peppers | The Classic Deluxe Pizza  |
| 3.0      | 2.0      | five_cheese_l | 1.0      | 1/1/2015   | 11:57:40   | 18.50      | 18.50       | L          | Veggie         | Mozzarella Cheese, Provolone Cheese           | The Five Cheese Pizza     |

---

## Memulai

### Prasyarat
- Python 3.x
- Perpustakaan: `pandas`, `numpy`, `matplotlib`, `seaborn`

### Instalasi
1. Clone repositori ini
   ```bash
   git clone https://github.com/username/pizza-eda.git
