# Machine-Learning-Based-Network-Intrusion-Detection-System

## Deskripsi Proyek

Proyek ini bertujuan untuk menganalisis serta membangun model deteksi intrusi jaringan menggunakan beberapa algoritma Machine Learning pada tiga dataset keamanan jaringan, yaitu:

* UNSW-NB15
* NSL-KDD
* CICIDS 2019

Model dikembangkan untuk mengidentifikasi lalu lintas jaringan normal, serangan siber, dan aktivitas anomali berdasarkan karakteristik data jaringan.

Penelitian ini membandingkan performa beberapa algoritma klasifikasi pada dataset dan rasio pembagian data yang berbeda. Hasil penelitian dapat digunakan sebagai dasar pengembangan sistem Intrusion Detection System atau IDS berbasis Machine Learning.

## Tujuan Penelitian

Tujuan utama proyek ini adalah:

1. Menganalisis karakteristik dataset deteksi intrusi jaringan.
2. Melakukan pembersihan dan pra-pemrosesan data.
3. Membangun model klasifikasi untuk mendeteksi serangan jaringan.
4. Membandingkan performa beberapa algoritma Machine Learning.
5. Menganalisis pengaruh rasio pembagian data terhadap kinerja model.
6. Menyimpan model terbaik agar dapat digunakan pada aplikasi web atau sistem inferensi.


## Dataset

Penelitian ini menggunakan tiga dataset publik yang banyak digunakan dalam penelitian Network Intrusion Detection System (NIDS).

### 1. UNSW-NB15

UNSW-NB15 merupakan dataset yang dikembangkan oleh University of New South Wales (UNSW) dan berisi lalu lintas jaringan normal serta sembilan kategori serangan modern.

**Sumber Resmi:**
https://www.kaggle.com/code/getanmolgupta01/unsw-nb15-cybersecurity-threat-detection-ann/input

---

### 2. NSL-KDD

NSL-KDD merupakan pengembangan dari dataset KDD Cup 1999 yang dirancang untuk mengurangi data duplikat dan meningkatkan kualitas evaluasi model.

**Sumber Resmi:**
https://www.kaggle.com/datasets/kiranmahesh/nslkdd

---

### 3. CICIDS 2019

CICIDS 2019 merupakan dataset keamanan jaringan modern yang dikembangkan oleh Canadian Institute for Cybersecurity (CIC) dan mencakup berbagai skenario serangan yang realistis.

**Sumber Resmi:**
https://www.kaggle.com/datasets/tarundhamor/cicids-2019-dataset?select=syn_data.csv

---

## Tahapan Penelitian

### 1. Eksplorasi Data

Tahap awal dilakukan untuk memahami struktur dataset, tipe data, distribusi kelas, jumlah fitur, serta kondisi data sebelum digunakan untuk pelatihan model.

Proses eksplorasi mencakup:

* Menampilkan informasi dataset.
* Memeriksa jumlah baris dan kolom.
* Memeriksa tipe data.
* Mengidentifikasi nilai yang hilang.
* Mengidentifikasi data duplikat.
* Menganalisis distribusi kelas target.

### 2. Pra-pemrosesan Data

Pra-pemrosesan dilakukan agar data dapat digunakan oleh algoritma Machine Learning.

Tahapan yang dilakukan meliputi:

* Membersihkan data yang tidak valid.
* Menangani nilai kosong atau missing values.
* Menghapus data duplikat jika diperlukan.
* Mengubah fitur kategorikal menjadi numerik menggunakan `LabelEncoder`.
* Melakukan normalisasi fitur numerik menggunakan `MinMaxScaler`.
* Memisahkan fitur prediktor dan variabel target.

### 3. Pembagian Data

Dataset dibagi menjadi data latih dan data uji menggunakan beberapa rasio `train_test_split`, antara lain:

* 90% data latih dan 10% data uji.
* 80% data latih dan 20% data uji.
* 70% data latih dan 30% data uji.

Penggunaan beberapa rasio pembagian data bertujuan untuk mengetahui pengaruh jumlah data latih dan data uji terhadap performa model.

### 4. Implementasi Model

Algoritma Machine Learning yang digunakan dalam penelitian ini adalah:

#### K-Nearest Neighbors

K-Nearest Neighbors melakukan klasifikasi berdasarkan kedekatan suatu data dengan data lain di sekitarnya.

#### Random Forest Classifier

Random Forest merupakan algoritma ensemble yang membangun sejumlah decision tree dan menentukan hasil klasifikasi berdasarkan keputusan mayoritas.

#### XGBoost Classifier

XGBoost merupakan algoritma boosting yang membangun model secara bertahap dengan memperbaiki kesalahan model sebelumnya.

## Evaluasi Model

Setiap model dievaluasi menggunakan beberapa metrik klasifikasi, yaitu:

* Accuracy
* Precision
* Recall
* F1-score
* Classification report
* Confusion matrix

### Accuracy

Accuracy menunjukkan proporsi prediksi yang benar dibandingkan dengan keseluruhan data pengujian.

### Precision

Precision menunjukkan tingkat ketepatan model ketika memprediksi suatu kelas sebagai serangan.

### Recall

Recall menunjukkan kemampuan model dalam menemukan seluruh data serangan yang sebenarnya.

### F1-Score

F1-score merupakan rata-rata harmonis antara precision dan recall.

### Confusion Matrix

Confusion matrix digunakan untuk melihat jumlah prediksi benar dan salah pada masing-masing kelas.

## Struktur Proyek

```text
network-intrusion-detection/
│
├── notebooks/
│   └── pipeline_final.ipynb
│
├── models/
│   ├── model_random_forest.pkl
│   └── scaler.pkl
│
├── datasets/
│   ├── UNSW-NB15/
│   ├── NSL-KDD/
│   └── CICIDS2019/
│
├── images/
│   ├── confusion_matrix/
│   └── model_comparison/
│
├── requirements.txt
├── .gitignore
└── README.md
```

## Teknologi yang Digunakan

Proyek ini dikembangkan menggunakan:

* Python
* Google Colab
* Pandas
* NumPy
* Scikit-learn
* XGBoost
* Matplotlib
* Joblib

## Penyimpanan Model

Model dan scaler yang telah dilatih disimpan menggunakan pustaka `joblib`.

Contoh penyimpanan model:

```python
import joblib

joblib.dump(model, "model_random_forest.pkl")
joblib.dump(scaler, "scaler.pkl")
```

Contoh memuat kembali model:

```python
import joblib

model = joblib.load("model_random_forest.pkl")
scaler = joblib.load("scaler.pkl")
```

Model yang telah disimpan dapat digunakan untuk:

* Melakukan prediksi terhadap data baru.
* Mengembangkan aplikasi web deteksi intrusi.
* Mengintegrasikan model dengan backend API.
* Melakukan deployment menggunakan Streamlit, Flask, atau FastAPI.

## Simulasi Implementasi Aplikasi Web

Proyek ini juga mencakup simulasi penggunaan model pada aplikasi web. Model terbaik dan scaler disimpan agar dapat digunakan untuk memproses input pengguna dan menghasilkan prediksi jenis lalu lintas jaringan.

Alur implementasi aplikasi adalah:

1. Pengguna memasukkan data karakteristik jaringan.
2. Data diproses menggunakan encoder dan scaler.
3. Model melakukan prediksi.
4. Sistem menampilkan hasil berupa lalu lintas normal atau serangan.
5. Hasil prediksi dapat ditampilkan melalui dashboard aplikasi.

## Hasil yang Diharapkan

Penelitian ini diharapkan dapat:

* Menghasilkan model deteksi intrusi dengan performa yang baik.
* Menentukan algoritma terbaik pada masing-masing dataset.
* Menunjukkan pengaruh pembagian data terhadap performa model.
* Memberikan dasar bagi pengembangan sistem keamanan jaringan otomatis.
* Mempermudah implementasi model Machine Learning pada aplikasi web.

## Pengembangan Selanjutnya

Beberapa pengembangan yang dapat dilakukan pada penelitian berikutnya meliputi:

* Menambahkan algoritma Machine Learning lainnya.
* Menerapkan feature selection.
* Menangani ketidakseimbangan data menggunakan SMOTE.
* Melakukan hyperparameter tuning.
* Mengembangkan klasifikasi multikelas untuk jenis serangan.
* Mengimplementasikan deteksi serangan secara real-time.
* Mengintegrasikan model dengan sistem monitoring jaringan.
* Mengembangkan dashboard analitik berbasis web.

## Kesimpulan

Proyek ini menyediakan alur kerja yang terstruktur untuk membangun sistem deteksi intrusi jaringan berbasis Machine Learning. Proses yang dilakukan mencakup eksplorasi data, pembersihan, transformasi fitur, normalisasi, pelatihan model, evaluasi performa, serta penyimpanan model.

Dengan menggunakan dataset UNSW-NB15, NSL-KDD, dan CICIDS 2019, penelitian ini dapat memberikan gambaran mengenai kemampuan beberapa algoritma Machine Learning dalam mendeteksi serangan dan anomali pada lalu lintas jaringan.

## Penulis

**Salman Alfaris**

Proyek penelitian Machine Learning untuk deteksi intrusi dan keamanan jaringan.
