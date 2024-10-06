# Analisis Data Eksploratif pada Dataset Penjualan Pizza

**Mata Kuliah**: Infrastruktur dan Platform Sains Data  
**Pertemuan**: 2  
**Topik**: Analisis Data Eksploratif (EDA)

Proyek ini berfokus pada melakukan **Analisis Data Eksploratif (EDA)** pada dataset penjualan pizza sebagai bagian dari pertemuan kedua dalam mata kuliah *Infrastruktur dan Platform Sains Data*. Tujuan dari eksplorasi ini adalah untuk memahami dataset dengan lebih baik melalui proses pembersihan, analisis, dan visualisasi data.

## Tujuan Proyek
Tujuan utama dari proyek ini adalah mengeksplorasi dataset menggunakan berbagai teknik EDA, yang memungkinkan kita untuk mendapatkan wawasan dan memahami data yang ada. Poin-poin utama yang dibahas adalah sebagai berikut:

### 1. Memuat Data
Dataset yang berisi informasi penjualan pizza dimuat ke dalam lingkungan. Dataset ini mencakup detail seperti:
- pizza_id
- order_id
- pizza_name_id
- quantity
- order_date
- order_time
- unit_price
- total_price
- pizza_size
- pizza_category
- pizza_ingredients
- pizza_name

### 2. Informasi Dasar tentang Dataset
Pada langkah ini, kita memperoleh informasi dasar seperti:
- Jumlah baris dan kolom dalam dataset.
- Nama kolom, tipe data, dan pratinjau data.
- Gambaran tentang nilai yang hilang, jika ada.
- Duplikasi data

### 3. Memeriksa Nilai Duplikat dan Unik
- **Nilai Duplikat**: Dataset diperiksa untuk menemukan entri yang duplikat.
- **Nilai Unik**: Dataset dianalisis untuk menemukan jumlah nilai unik pada kolom tertentu, seperti jenis pizza, kategori, dan ukuran.

### 4. Memvisualisasikan Nilai Unik
Visualisasi (misalnya, diagram batang) dibuat untuk menunjukkan distribusi nilai unik pada fitur kategori tertentu, seperti:
- `pizza_category`
- `pizza_size`
- `quantity`

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
- Jenis pizza yang dipesan.
- Size pizza yang dipesan.
- Jumlah pizza yang di pesan.

### 9. Membuat Box Plot
Sebuah **box plot** dibuat untuk memvisualisasikan distribusi dan penyebaran fitur numerik, seperti:
- `pizza_category` dan `quantity`: Ini membantu mengetahui seberapa banyak pizza dipesan berdasarkan jenis pizza.

### 10. Analisis Korelasi
Korelasi antara fitur numerik (misalnya, `quantity`, `total_price`). Ada hubungan positif yang sedang antara jumlah pizza yang dipesan dan total harga. Semakin banyak pizza yang dipesan, semakin tinggi total harga yang dibayarkan, meskipun hubungan ini tidak 100% langsung (ada faktor lain yang mungkin mempengaruhi, seperti harga per satuan).

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

```python
# Mengimpor library yang diperlukan
import numpy as np                     # NumPy untuk komputasi numerik
import pandas as pd                    # Pandas untuk manipulasi dan analisis data
import matplotlib.pyplot as plt        # Matplotlib untuk visualisasi data
import seaborn as sns                 # Seaborn untuk visualisasi yang lebih menarik

```

```python
# Membaca dataset dari file CSV
df = pd.read_csv('E:/semester 3/IPUSD/archive/pizza_sales.csv')  # Memuat data penjualan pizza ke dalam DataFrame
```


# Menampilkan lima baris pertama dari DataFrame untuk melihat struktur data
```python
df.head()
```
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>pizza_id</th>
      <th>order_id</th>
      <th>pizza_name_id</th>
      <th>quantity</th>
      <th>order_date</th>
      <th>order_time</th>
      <th>unit_price</th>
      <th>total_price</th>
      <th>pizza_size</th>
      <th>pizza_category</th>
      <th>pizza_ingredients</th>
      <th>pizza_name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>1.0</td>
      <td>hawaiian_m</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:38:36</td>
      <td>13.25</td>
      <td>13.25</td>
      <td>M</td>
      <td>Classic</td>
      <td>Sliced Ham, Pineapple, Mozzarella Cheese</td>
      <td>The Hawaiian Pizza</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2.0</td>
      <td>2.0</td>
      <td>classic_dlx_m</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:57:40</td>
      <td>16.00</td>
      <td>16.00</td>
      <td>M</td>
      <td>Classic</td>
      <td>Pepperoni, Mushrooms, Red Onions, Red Peppers,...</td>
      <td>The Classic Deluxe Pizza</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3.0</td>
      <td>2.0</td>
      <td>five_cheese_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:57:40</td>
      <td>18.50</td>
      <td>18.50</td>
      <td>L</td>
      <td>Veggie</td>
      <td>Mozzarella Cheese, Provolone Cheese, Smoked Go...</td>
      <td>The Five Cheese Pizza</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.0</td>
      <td>2.0</td>
      <td>ital_supr_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:57:40</td>
      <td>20.75</td>
      <td>20.75</td>
      <td>L</td>
      <td>Supreme</td>
      <td>Calabrese Salami, Capocollo, Tomatoes, Red Oni...</td>
      <td>The Italian Supreme Pizza</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5.0</td>
      <td>2.0</td>
      <td>mexicana_m</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:57:40</td>
      <td>16.00</td>
      <td>16.00</td>
      <td>M</td>
      <td>Veggie</td>
      <td>Tomatoes, Red Peppers, Jalapeno Peppers, Red O...</td>
      <td>The Mexicana Pizza</td>
    </tr>
  </tbody>
</table>
</div>

# Menampilkan statistik deskriptif dari kolom numerik dalam DataFrame
```python
df.describe()
```
<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>pizza_id</th>
      <th>order_id</th>
      <th>quantity</th>
      <th>unit_price</th>
      <th>total_price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>48620.000000</td>
      <td>48620.000000</td>
      <td>48620.000000</td>
      <td>48620.000000</td>
      <td>48620.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>24310.500000</td>
      <td>10701.479761</td>
      <td>1.019622</td>
      <td>16.494132</td>
      <td>16.821474</td>
    </tr>
    <tr>
      <th>std</th>
      <td>14035.529381</td>
      <td>6180.119770</td>
      <td>0.143077</td>
      <td>3.621789</td>
      <td>4.437398</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>9.750000</td>
      <td>9.750000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>12155.750000</td>
      <td>5337.000000</td>
      <td>1.000000</td>
      <td>12.750000</td>
      <td>12.750000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>24310.500000</td>
      <td>10682.500000</td>
      <td>1.000000</td>
      <td>16.500000</td>
      <td>16.500000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>36465.250000</td>
      <td>16100.000000</td>
      <td>1.000000</td>
      <td>20.250000</td>
      <td>20.500000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>48620.000000</td>
      <td>21350.000000</td>
      <td>4.000000</td>
      <td>35.950000</td>
      <td>83.000000</td>
    </tr>
  </tbody>
</table>
</div>

# Menampilkan informasi tentang DataFrame, termasuk tipe data dan jumlah non-null
```python
df.info()  
```
## Informasi Dataset

| No | Column             | Non-Null Count | Dtype  |
|----|--------------------|----------------|--------|
| 0  | pizza_id           | 48620          | float64|
| 1  | order_id           | 48620          | float64|
| 2  | pizza_name_id      | 48620          | object |
| 3  | quantity           | 48620          | float64|
| 4  | order_date         | 48620          | object |
| 5  | order_time         | 48620          | object |
| 6  | unit_price         | 48620          | float64|
| 7  | total_price        | 48620          | float64|
| 8  | pizza_size         | 48620          | object |
| 9  | pizza_category     | 48620          | object |
| 10 | pizza_ingredients   | 48620          | object |
| 11 | pizza_name         | 48620          | object |

# Memeriksa apakah ada duplikat dalam DataFrame dan mengembalikan boolean untuk setiap baris
```python
df.duplicated()  
```
## Nilai Duplikat dalam Dataset

Dataset ini memiliki **X** nilai duplikat.

| No | Indeks Baris | Duplikat |
|----|--------------|----------|
| 0  | 0            | False    |
| 1  | 1            | False    |
| 2  | 2            | False    |
| 3  | 3            | False    |
| 4  | 4            | False    |
| ...| ...          | ...      |
| N  | 48619        | False    |

**Catatan**: `False` menunjukkan bahwa baris tersebut tidak merupakan duplikat.

# Menghapus baris yang duplikat berdasarkan kolom 'pizza_ingredients' dan 'pizza_name'
```python
data_unik = df.drop_duplicates(subset=['pizza_ingredients', 'pizza_name'])  # Membuat DataFrame baru tanpa duplikat
```
<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>pizza_id</th>
      <th>order_id</th>
      <th>pizza_name_id</th>
      <th>quantity</th>
      <th>order_date</th>
      <th>order_time</th>
      <th>unit_price</th>
      <th>total_price</th>
      <th>pizza_size</th>
      <th>pizza_category</th>
      <th>pizza_ingredients</th>
      <th>pizza_name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>1.0</td>
      <td>hawaiian_m</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:38:36</td>
      <td>13.25</td>
      <td>13.25</td>
      <td>M</td>
      <td>Classic</td>
      <td>Sliced Ham, Pineapple, Mozzarella Cheese</td>
      <td>The Hawaiian Pizza</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2.0</td>
      <td>2.0</td>
      <td>classic_dlx_m</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:57:40</td>
      <td>16.00</td>
      <td>16.00</td>
      <td>M</td>
      <td>Classic</td>
      <td>Pepperoni, Mushrooms, Red Onions, Red Peppers,...</td>
      <td>The Classic Deluxe Pizza</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3.0</td>
      <td>2.0</td>
      <td>five_cheese_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:57:40</td>
      <td>18.50</td>
      <td>18.50</td>
      <td>L</td>
      <td>Veggie</td>
      <td>Mozzarella Cheese, Provolone Cheese, Smoked Go...</td>
      <td>The Five Cheese Pizza</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.0</td>
      <td>2.0</td>
      <td>ital_supr_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:57:40</td>
      <td>20.75</td>
      <td>20.75</td>
      <td>L</td>
      <td>Supreme</td>
      <td>Calabrese Salami, Capocollo, Tomatoes, Red Oni...</td>
      <td>The Italian Supreme Pizza</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5.0</td>
      <td>2.0</td>
      <td>mexicana_m</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:57:40</td>
      <td>16.00</td>
      <td>16.00</td>
      <td>M</td>
      <td>Veggie</td>
      <td>Tomatoes, Red Peppers, Jalapeno Peppers, Red O...</td>
      <td>The Mexicana Pizza</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6.0</td>
      <td>2.0</td>
      <td>thai_ckn_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:57:40</td>
      <td>20.75</td>
      <td>20.75</td>
      <td>L</td>
      <td>Chicken</td>
      <td>Chicken, Pineapple, Tomatoes, Red Peppers, Tha...</td>
      <td>The Thai Chicken Pizza</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8.0</td>
      <td>3.0</td>
      <td>prsc_argla_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>12:12:28</td>
      <td>20.75</td>
      <td>20.75</td>
      <td>L</td>
      <td>Supreme</td>
      <td>Prosciutto di San Daniele, Arugula, Mozzarella...</td>
      <td>The Prosciutto and Arugula Pizza</td>
    </tr>
    <tr>
      <th>10</th>
      <td>11.0</td>
      <td>6.0</td>
      <td>bbq_ckn_s</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>12:29:36</td>
      <td>12.75</td>
      <td>12.75</td>
      <td>S</td>
      <td>Chicken</td>
      <td>Barbecued Chicken, Red Peppers, Green Peppers,...</td>
      <td>The Barbecue Chicken Pizza</td>
    </tr>
    <tr>
      <th>11</th>
      <td>12.0</td>
      <td>6.0</td>
      <td>the_greek_s</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>12:29:36</td>
      <td>12.00</td>
      <td>12.00</td>
      <td>S</td>
      <td>Classic</td>
      <td>Kalamata Olives, Feta Cheese, Tomatoes, Garlic...</td>
      <td>The Greek Pizza</td>
    </tr>
    <tr>
      <th>12</th>
      <td>13.0</td>
      <td>7.0</td>
      <td>spinach_supr_s</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>12:50:37</td>
      <td>12.50</td>
      <td>12.50</td>
      <td>S</td>
      <td>Supreme</td>
      <td>Spinach, Red Onions, Pepperoni, Tomatoes, Arti...</td>
      <td>The Spinach Supreme Pizza</td>
    </tr>
    <tr>
      <th>15</th>
      <td>16.0</td>
      <td>9.0</td>
      <td>green_garden_s</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>12:52:01</td>
      <td>12.00</td>
      <td>12.00</td>
      <td>S</td>
      <td>Veggie</td>
      <td>Spinach, Mushrooms, Tomatoes, Green Olives, Fe...</td>
      <td>The Green Garden Pizza</td>
    </tr>
    <tr>
      <th>16</th>
      <td>17.0</td>
      <td>9.0</td>
      <td>ital_cpcllo_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>12:52:01</td>
      <td>20.50</td>
      <td>20.50</td>
      <td>L</td>
      <td>Classic</td>
      <td>Capocollo, Red Peppers, Tomatoes, Goat Cheese,...</td>
      <td>The Italian Capocollo Pizza</td>
    </tr>
    <tr>
      <th>20</th>
      <td>21.0</td>
      <td>9.0</td>
      <td>spicy_ital_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>12:52:01</td>
      <td>20.75</td>
      <td>20.75</td>
      <td>L</td>
      <td>Supreme</td>
      <td>Capocollo, Tomatoes, Goat Cheese, Artichokes, ...</td>
      <td>The Spicy Italian Pizza</td>
    </tr>
    <tr>
      <th>21</th>
      <td>22.0</td>
      <td>9.0</td>
      <td>spin_pesto_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>12:52:01</td>
      <td>20.75</td>
      <td>20.75</td>
      <td>L</td>
      <td>Veggie</td>
      <td>Spinach, Artichokes, Tomatoes, Sun-dried Tomat...</td>
      <td>The Spinach Pesto Pizza</td>
    </tr>
    <tr>
      <th>22</th>
      <td>23.0</td>
      <td>9.0</td>
      <td>veggie_veg_s</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>12:52:01</td>
      <td>12.00</td>
      <td>12.00</td>
      <td>S</td>
      <td>Veggie</td>
      <td>Mushrooms, Tomatoes, Red Peppers, Green Pepper...</td>
      <td>The Vegetables + Vegetables Pizza</td>
    </tr>
    <tr>
      <th>24</th>
      <td>25.0</td>
      <td>10.0</td>
      <td>southw_ckn_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>13:00:15</td>
      <td>20.75</td>
      <td>20.75</td>
      <td>L</td>
      <td>Chicken</td>
      <td>Chicken, Tomatoes, Red Peppers, Red Onions, Ja...</td>
      <td>The Southwest Chicken Pizza</td>
    </tr>
    <tr>
      <th>26</th>
      <td>27.0</td>
      <td>11.0</td>
      <td>cali_ckn_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>13:02:59</td>
      <td>20.75</td>
      <td>20.75</td>
      <td>L</td>
      <td>Chicken</td>
      <td>Chicken, Artichoke, Spinach, Garlic, Jalapeno ...</td>
      <td>The California Chicken Pizza</td>
    </tr>
    <tr>
      <th>28</th>
      <td>29.0</td>
      <td>11.0</td>
      <td>pepperoni_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>13:02:59</td>
      <td>15.25</td>
      <td>15.25</td>
      <td>L</td>
      <td>Classic</td>
      <td>Mozzarella Cheese, Pepperoni</td>
      <td>The Pepperoni Pizza</td>
    </tr>
    <tr>
      <th>31</th>
      <td>32.0</td>
      <td>12.0</td>
      <td>ckn_pesto_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>13:04:41</td>
      <td>20.75</td>
      <td>20.75</td>
      <td>L</td>
      <td>Chicken</td>
      <td>Chicken, Tomatoes, Red Peppers, Spinach, Garli...</td>
      <td>The Chicken Pesto Pizza</td>
    </tr>
    <tr>
      <th>35</th>
      <td>36.0</td>
      <td>15.0</td>
      <td>big_meat_s</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>13:33:00</td>
      <td>12.00</td>
      <td>12.00</td>
      <td>S</td>
      <td>Classic</td>
      <td>Bacon, Pepperoni, Italian Sausage, Chorizo Sau...</td>
      <td>The Big Meat Pizza</td>
    </tr>
    <tr>
      <th>37</th>
      <td>38.0</td>
      <td>15.0</td>
      <td>soppressata_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>13:33:00</td>
      <td>20.75</td>
      <td>20.75</td>
      <td>L</td>
      <td>Supreme</td>
      <td>Soppressata Salami, Fontina Cheese, Mozzarella...</td>
      <td>The Soppressata Pizza</td>
    </tr>
    <tr>
      <th>39</th>
      <td>40.0</td>
      <td>16.0</td>
      <td>four_cheese_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>13:34:07</td>
      <td>17.95</td>
      <td>17.95</td>
      <td>L</td>
      <td>Veggie</td>
      <td>Ricotta Cheese, Gorgonzola Piccante Cheese, Mo...</td>
      <td>The Four Cheese Pizza</td>
    </tr>
    <tr>
      <th>40</th>
      <td>41.0</td>
      <td>16.0</td>
      <td>napolitana_s</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>13:34:07</td>
      <td>12.00</td>
      <td>12.00</td>
      <td>S</td>
      <td>Classic</td>
      <td>Tomatoes, Anchovies, Green Olives, Red Onions,...</td>
      <td>The Napolitana Pizza</td>
    </tr>
    <tr>
      <th>43</th>
      <td>44.0</td>
      <td>17.0</td>
      <td>calabrese_m</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>13:53:00</td>
      <td>16.25</td>
      <td>16.25</td>
      <td>M</td>
      <td>Supreme</td>
      <td>?duja Salami, Pancetta, Tomatoes, Red Onions, ...</td>
      <td>The Calabrese Pizza</td>
    </tr>
    <tr>
      <th>47</th>
      <td>48.0</td>
      <td>17.0</td>
      <td>ital_veggie_s</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>13:53:00</td>
      <td>12.75</td>
      <td>12.75</td>
      <td>S</td>
      <td>Veggie</td>
      <td>Eggplant, Artichokes, Tomatoes, Zucchini, Red ...</td>
      <td>The Italian Vegetables Pizza</td>
    </tr>
    <tr>
      <th>48</th>
      <td>49.0</td>
      <td>17.0</td>
      <td>mediterraneo_m</td>
      <td>2.0</td>
      <td>1/1/2015</td>
      <td>13:53:00</td>
      <td>16.00</td>
      <td>32.00</td>
      <td>M</td>
      <td>Veggie</td>
      <td>Spinach, Artichokes, Kalamata Olives, Sun-drie...</td>
      <td>The Mediterranean Pizza</td>
    </tr>
    <tr>
      <th>50</th>
      <td>51.0</td>
      <td>17.0</td>
      <td>peppr_salami_s</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>13:53:00</td>
      <td>12.50</td>
      <td>12.50</td>
      <td>S</td>
      <td>Supreme</td>
      <td>Genoa Salami, Capocollo, Pepperoni, Tomatoes, ...</td>
      <td>The Pepper Salami Pizza</td>
    </tr>
    <tr>
      <th>51</th>
      <td>52.0</td>
      <td>17.0</td>
      <td>spinach_fet_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>13:53:00</td>
      <td>20.25</td>
      <td>20.25</td>
      <td>L</td>
      <td>Veggie</td>
      <td>Spinach, Mushrooms, Red Onions, Feta Cheese, G...</td>
      <td>The Spinach and Feta Pizza</td>
    </tr>
    <tr>
      <th>54</th>
      <td>55.0</td>
      <td>19.0</td>
      <td>sicilian_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>13:59:09</td>
      <td>20.25</td>
      <td>20.25</td>
      <td>L</td>
      <td>Supreme</td>
      <td>Coarse Sicilian Salami, Tomatoes, Green Olives...</td>
      <td>The Sicilian Pizza</td>
    </tr>
    <tr>
      <th>73</th>
      <td>74.0</td>
      <td>28.0</td>
      <td>ckn_alfredo_s</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>15:35:46</td>
      <td>12.75</td>
      <td>12.75</td>
      <td>S</td>
      <td>Chicken</td>
      <td>Chicken, Red Onions, Red Peppers, Mushrooms, A...</td>
      <td>The Chicken Alfredo Pizza</td>
    </tr>
    <tr>
      <th>86</th>
      <td>87.0</td>
      <td>35.0</td>
      <td>pep_msh_pep_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>16:32:04</td>
      <td>17.50</td>
      <td>17.50</td>
      <td>L</td>
      <td>Classic</td>
      <td>Pepperoni, Mushrooms, Green Peppers</td>
      <td>The Pepperoni, Mushroom, and Peppers Pizza</td>
    </tr>
    <tr>
      <th>427</th>
      <td>428.0</td>
      <td>182.0</td>
      <td>brie_carre_s</td>
      <td>1.0</td>
      <td>3/1/2015</td>
      <td>18:50:10</td>
      <td>23.65</td>
      <td>23.65</td>
      <td>S</td>
      <td>Supreme</td>
      <td>Brie Carre Cheese, Prosciutto, Caramelized Oni...</td>
      <td>The Brie Carre Pizza</td>
    </tr>
  </tbody>
</table>
</div>

# Menghapus duplikat berdasarkan 'pizza_name_id'
```python
unik_data = df.drop_duplicates(subset=['pizza_name_id'])  # Data unik berdasarkan pizza_name_id
```
<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>pizza_id</th>
      <th>order_id</th>
      <th>pizza_name_id</th>
      <th>quantity</th>
      <th>order_date</th>
      <th>order_time</th>
      <th>unit_price</th>
      <th>total_price</th>
      <th>pizza_size</th>
      <th>pizza_category</th>
      <th>pizza_ingredients</th>
      <th>pizza_name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>1.0</td>
      <td>hawaiian_m</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:38:36</td>
      <td>13.25</td>
      <td>13.25</td>
      <td>M</td>
      <td>Classic</td>
      <td>Sliced Ham, Pineapple, Mozzarella Cheese</td>
      <td>The Hawaiian Pizza</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2.0</td>
      <td>2.0</td>
      <td>classic_dlx_m</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:57:40</td>
      <td>16.00</td>
      <td>16.00</td>
      <td>M</td>
      <td>Classic</td>
      <td>Pepperoni, Mushrooms, Red Onions, Red Peppers,...</td>
      <td>The Classic Deluxe Pizza</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3.0</td>
      <td>2.0</td>
      <td>five_cheese_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:57:40</td>
      <td>18.50</td>
      <td>18.50</td>
      <td>L</td>
      <td>Veggie</td>
      <td>Mozzarella Cheese, Provolone Cheese, Smoked Go...</td>
      <td>The Five Cheese Pizza</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.0</td>
      <td>2.0</td>
      <td>ital_supr_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:57:40</td>
      <td>20.75</td>
      <td>20.75</td>
      <td>L</td>
      <td>Supreme</td>
      <td>Calabrese Salami, Capocollo, Tomatoes, Red Oni...</td>
      <td>The Italian Supreme Pizza</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5.0</td>
      <td>2.0</td>
      <td>mexicana_m</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:57:40</td>
      <td>16.00</td>
      <td>16.00</td>
      <td>M</td>
      <td>Veggie</td>
      <td>Tomatoes, Red Peppers, Jalapeno Peppers, Red O...</td>
      <td>The Mexicana Pizza</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>591</th>
      <td>592.0</td>
      <td>260.0</td>
      <td>the_greek_l</td>
      <td>1.0</td>
      <td>5/1/2015</td>
      <td>12:06:27</td>
      <td>20.50</td>
      <td>20.50</td>
      <td>L</td>
      <td>Classic</td>
      <td>Kalamata Olives, Feta Cheese, Tomatoes, Garlic...</td>
      <td>The Greek Pizza</td>
    </tr>
    <tr>
      <th>617</th>
      <td>618.0</td>
      <td>271.0</td>
      <td>soppressata_m</td>
      <td>1.0</td>
      <td>5/1/2015</td>
      <td>14:22:19</td>
      <td>16.50</td>
      <td>16.50</td>
      <td>M</td>
      <td>Supreme</td>
      <td>Soppressata Salami, Fontina Cheese, Mozzarella...</td>
      <td>The Soppressata Pizza</td>
    </tr>
    <tr>
      <th>621</th>
      <td>622.0</td>
      <td>273.0</td>
      <td>soppressata_s</td>
      <td>1.0</td>
      <td>5/1/2015</td>
      <td>14:28:00</td>
      <td>12.50</td>
      <td>12.50</td>
      <td>S</td>
      <td>Supreme</td>
      <td>Soppressata Salami, Fontina Cheese, Mozzarella...</td>
      <td>The Soppressata Pizza</td>
    </tr>
    <tr>
      <th>768</th>
      <td>769.0</td>
      <td>334.0</td>
      <td>calabrese_l</td>
      <td>1.0</td>
      <td>6/1/2015</td>
      <td>14:24:18</td>
      <td>20.25</td>
      <td>20.25</td>
      <td>L</td>
      <td>Supreme</td>
      <td>?duja Salami, Pancetta, Tomatoes, Red Onions, ...</td>
      <td>The Calabrese Pizza</td>
    </tr>
    <tr>
      <th>3447</th>
      <td>3448.0</td>
      <td>1528.0</td>
      <td>the_greek_xxl</td>
      <td>1.0</td>
      <td>26-01-2015</td>
      <td>15:24:38</td>
      <td>35.95</td>
      <td>35.95</td>
      <td>XXL</td>
      <td>Classic</td>
      <td>Kalamata Olives, Feta Cheese, Tomatoes, Garlic...</td>
      <td>The Greek Pizza</td>
    </tr>
  </tbody>
</table>
<p>91 rows × 12 columns</p>
</div>

# Membuat bar chart untuk menunjukkan jumlah order pizza unik
```python
plt.bar(unik_data['pizza_category'], unik_data['pizza_size'])  # Menggunakan pizza_category dan pizza_size
plt.xlabel('Jenis Pizza')  # Label sumbu x
plt.ylabel('Jumlah Order')  # Label sumbu y
plt.title('Jumlah Order Pizza Unik')  # Judul grafik
plt.show()  # Menampilkan grafik
```
![image](https://github.com/user-attachments/assets/3cc68c7f-1cbf-409d-af44-c6db2022eb2d)

# Menampilkan tipe data untuk setiap kolom dalam DataFrame
```python
for kolom in df.columns:
    print(kolom, type(df[kolom].values[0]))  # Menampilkan nama kolom dan tipe data
```
## Tipe Data Setiap Kolom

Dataset ini memiliki tipe data sebagai berikut:

| No | Column             | Data Type             |
|----|--------------------|-----------------------|
| 1  | pizza_id           | numpy.float64         |
| 2  | order_id           | numpy.float64         |
| 3  | pizza_name_id      | str                   |
| 4  | quantity           | numpy.float64         |
| 5  | order_date         | str                   |
| 6  | order_time         | str                   |
| 7  | unit_price         | numpy.float64         |
| 8  | total_price        | numpy.float64         |
| 9  | pizza_size         | str                   |
| 10 | pizza_category     | str                   |
| 11 | pizza_ingredients   | str                   |
| 12 | pizza_name         | str                   |


# Menghitung korelasi antara unit_price dan quantity
```python
corr_matrix = df[['unit_price', 'quantity']].corr()  # Menghitung matriks korelasi
```
<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>unit_price</th>
      <th>quantity</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>unit_price</th>
      <td>1.000000</td>
      <td>0.007142</td>
    </tr>
    <tr>
      <th>quantity</th>
      <td>0.007142</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>
# Menyaring DataFrame berdasarkan unit_price
```python
df_filter = df[df['unit_price'] > 15]  # Memfilter DataFrame untuk harga unit lebih dari 15
df_filter  # Menampilkan DataFrame yang telah difilter
```
<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>pizza_id</th>
      <th>order_id</th>
      <th>pizza_name_id</th>
      <th>quantity</th>
      <th>order_date</th>
      <th>order_time</th>
      <th>unit_price</th>
      <th>total_price</th>
      <th>pizza_size</th>
      <th>pizza_category</th>
      <th>pizza_ingredients</th>
      <th>pizza_name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>2.0</td>
      <td>2.0</td>
      <td>classic_dlx_m</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:57:40</td>
      <td>16.00</td>
      <td>16.00</td>
      <td>M</td>
      <td>Classic</td>
      <td>Pepperoni, Mushrooms, Red Onions, Red Peppers,...</td>
      <td>The Classic Deluxe Pizza</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3.0</td>
      <td>2.0</td>
      <td>five_cheese_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:57:40</td>
      <td>18.50</td>
      <td>18.50</td>
      <td>L</td>
      <td>Veggie</td>
      <td>Mozzarella Cheese, Provolone Cheese, Smoked Go...</td>
      <td>The Five Cheese Pizza</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.0</td>
      <td>2.0</td>
      <td>ital_supr_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:57:40</td>
      <td>20.75</td>
      <td>20.75</td>
      <td>L</td>
      <td>Supreme</td>
      <td>Calabrese Salami, Capocollo, Tomatoes, Red Oni...</td>
      <td>The Italian Supreme Pizza</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5.0</td>
      <td>2.0</td>
      <td>mexicana_m</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:57:40</td>
      <td>16.00</td>
      <td>16.00</td>
      <td>M</td>
      <td>Veggie</td>
      <td>Tomatoes, Red Peppers, Jalapeno Peppers, Red O...</td>
      <td>The Mexicana Pizza</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6.0</td>
      <td>2.0</td>
      <td>thai_ckn_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:57:40</td>
      <td>20.75</td>
      <td>20.75</td>
      <td>L</td>
      <td>Chicken</td>
      <td>Chicken, Pineapple, Tomatoes, Red Peppers, Tha...</td>
      <td>The Thai Chicken Pizza</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>48612</th>
      <td>48613.0</td>
      <td>21347.0</td>
      <td>ital_supr_m</td>
      <td>1.0</td>
      <td>31-12-2015</td>
      <td>21:14:37</td>
      <td>16.50</td>
      <td>16.50</td>
      <td>M</td>
      <td>Supreme</td>
      <td>Calabrese Salami, Capocollo, Tomatoes, Red Oni...</td>
      <td>The Italian Supreme Pizza</td>
    </tr>
    <tr>
      <th>48614</th>
      <td>48615.0</td>
      <td>21347.0</td>
      <td>southw_ckn_l</td>
      <td>1.0</td>
      <td>31-12-2015</td>
      <td>21:14:37</td>
      <td>20.75</td>
      <td>20.75</td>
      <td>L</td>
      <td>Chicken</td>
      <td>Chicken, Tomatoes, Red Peppers, Red Onions, Ja...</td>
      <td>The Southwest Chicken Pizza</td>
    </tr>
    <tr>
      <th>48615</th>
      <td>48616.0</td>
      <td>21348.0</td>
      <td>ckn_alfredo_m</td>
      <td>1.0</td>
      <td>31-12-2015</td>
      <td>21:23:10</td>
      <td>16.75</td>
      <td>16.75</td>
      <td>M</td>
      <td>Chicken</td>
      <td>Chicken, Red Onions, Red Peppers, Mushrooms, A...</td>
      <td>The Chicken Alfredo Pizza</td>
    </tr>
    <tr>
      <th>48616</th>
      <td>48617.0</td>
      <td>21348.0</td>
      <td>four_cheese_l</td>
      <td>1.0</td>
      <td>31-12-2015</td>
      <td>21:23:10</td>
      <td>17.95</td>
      <td>17.95</td>
      <td>L</td>
      <td>Veggie</td>
      <td>Ricotta Cheese, Gorgonzola Piccante Cheese, Mo...</td>
      <td>The Four Cheese Pizza</td>
    </tr>
    <tr>
      <th>48618</th>
      <td>48619.0</td>
      <td>21349.0</td>
      <td>mexicana_l</td>
      <td>1.0</td>
      <td>31-12-2015</td>
      <td>22:09:54</td>
      <td>20.25</td>
      <td>20.25</td>
      <td>L</td>
      <td>Veggie</td>
      <td>Tomatoes, Red Peppers, Jalapeno Peppers, Red O...</td>
      <td>The Mexicana Pizza</td>
    </tr>
  </tbody>
</table>
<p>32604 rows × 12 columns</p>
</div>

# Membuat box plot untuk harga pizza
```python
plt.figure(figsize=(10,6))  # Menentukan ukuran grafik
sns.boxplot(x='pizza_category', y='unit_price', data=df)  # Membuat box plot
plt.title('Box Plot Harga Pizza')  # Judul box plot
plt.xlabel('Kategori Pizza')  # Label sumbu x
plt.ylabel('Harga')  # Label sumbu y
plt.show()  # Menampilkan box plot
```
![image](https://github.com/user-attachments/assets/7a2ea1fe-44a5-4e60-b3f8-e82a14af306a)


# Menghitung dan menampilkan heatmap korelasi antara quantity dan total_price
```python
corr_matrix = df[['quantity', 'total_price']].corr()  # Menghitung matriks korelasi
plt.figure(figsize=(10,6))  # Menentukan ukuran grafik
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm', square=True)  # Membuat heatmap
plt.title('Heatmap Korelasi')  # Judul heatmap
plt.show()  # Menampilkan heatmap
```
![image](https://github.com/user-attachments/assets/afaaec5d-96fa-495d-8cb5-580664d81d4b)

