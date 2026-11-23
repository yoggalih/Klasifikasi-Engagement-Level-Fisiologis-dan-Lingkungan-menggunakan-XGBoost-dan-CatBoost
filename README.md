# Klasifikasi-Engagement-Level-Fisiologis-dan-Lingkungan-menggunakan-XGBoost-dan-CatBoost
# Klasifikasi Engagement Level Berdasarkan Parameter Fisiologis dan Kondisi Lingkungan Menggunakan XGBoost dan CatBoost

## Deskripsi Proyek

Proyek ini merupakan penelitian klasifikasi *Engagement Level* (tingkat keterlibatan) berdasarkan parameter fisiologis dan kondisi lingkungan menggunakan algoritma Machine Learning **XGBoost** dan **CatBoost**.

Penelitian ini bertujuan untuk menganalisis bagaimana kombinasi parameter fisiologis dan kondisi lingkungan dapat digunakan untuk mengklasifikasikan tingkat keterlibatan ke dalam tiga kategori, yaitu:

- **Highly Engaged** – Tingkat keterlibatan tinggi.
- **Moderately Engaged** – Tingkat keterlibatan sedang.
- **Disengaged** – Tingkat keterlibatan rendah.

Eksperimen dilakukan dengan membandingkan performa kedua algoritma pada tiga skenario penggunaan fitur, yaitu fisiologis, lingkungan, dan multimodal.

## Tujuan Penelitian

1. Menganalisis karakteristik dataset berdasarkan parameter fisiologis dan kondisi lingkungan.
2. Mengidentifikasi hubungan statistik antara fitur numerik dan Engagement Level.
3. Membangun model klasifikasi menggunakan algoritma XGBoost dan CatBoost.
4. Membandingkan performa model berdasarkan tiga skenario kombinasi fitur.
5. Mengevaluasi kemampuan model menggunakan metrik klasifikasi dan Stratified Cross-Validation.

## Dataset

Dataset yang digunakan adalah **Emotional Monitoring Dataset** dari Kaggle.

Dataset memiliki karakteristik sebagai berikut:

| Keterangan | Jumlah |
|---|---:|
| Total observasi | 1.000 |
| Total kolom awal | 14 |
| Fitur yang digunakan | 11 |
| Variabel target | 1 |
| Kategori target | 3 |

### Kelompok Fitur

**1. Parameter Fisiologis (9 fitur)**

| Fitur | Deskripsi |
|---|---|
| HeartRate | Detak jantung |
| SkinConductance | Konduktivitas kulit |
| EEG | Aktivitas listrik otak |
| Temperature | Suhu tubuh |
| PupilDiameter | Diameter pupil |
| SmileIntensity | Intensitas senyuman |
| FrownIntensity | Intensitas kerutan dahi |
| CortisolLevel | Tingkat kortisol |
| ActivityLevel | Tingkat aktivitas |

**2. Parameter Lingkungan (2 fitur)**

| Fitur | Deskripsi |
|---|---|
| AmbientNoiseLevel | Tingkat kebisingan lingkungan |
| LightingLevel | Intensitas pencahayaan |

**3. Variabel Target**

`EngagementLevel` merupakan variabel target yang digunakan dalam proses klasifikasi dengan tiga kategori tingkat keterlibatan.

> Catatan: Dataset merupakan dataset simulasi, sehingga hasil penelitian menggambarkan performa model pada data yang digunakan dan tidak secara langsung merepresentasikan kondisi pengukuran fisiologis di dunia nyata.

## Metodologi

Penelitian dilakukan melalui beberapa tahapan berikut:

### 1. Exploratory Data Analysis (EDA)

Analisis awal dilakukan untuk memahami karakteristik dan kualitas dataset, meliputi:

- Pemeriksaan missing values.
- Validasi tipe data.
- Statistik deskriptif.
- Deteksi outlier menggunakan metode Interquartile Range (IQR).
- Pemeriksaan data duplikat.
- Analisis distribusi kelas target.
- Pengujian perbedaan fitur menggunakan Kruskal-Wallis.

### 2. Data Preprocessing

Tahapan preprocessing meliputi:

- Menghapus fitur `EmotionalState` dan `CognitiveState` yang tidak digunakan dalam eksperimen.
- Memisahkan variabel fitur dan target.
- Menyesuaikan label target agar sesuai dengan kebutuhan algoritma.
- Mengelompokkan fitur berdasarkan skenario eksperimen.

### 3. Skenario Eksperimen

Terdapat tiga skenario pengujian:

| Skenario | Jumlah Fitur | Keterangan |
|---|---:|---|
| Fisiologis | 9 | Menggunakan parameter fisiologis |
| Lingkungan | 2 | Menggunakan parameter lingkungan |
| Multimodal | 11 | Menggabungkan parameter fisiologis dan lingkungan |

### 4. Pembagian Data

Dataset dibagi menjadi:

- 80% data training.
- 20% data testing.

Pembagian menggunakan `train_test_split` dengan `stratify` untuk mempertahankan proporsi kelas pada data training dan testing.

Parameter random state ditetapkan sebesar 42 untuk menjaga konsistensi pembagian data.

### 5. Model Machine Learning

Dua algoritma digunakan dalam penelitian ini:

**XGBoost (Extreme Gradient Boosting)**

Algoritma berbasis gradient boosting yang membangun model secara bertahap untuk meningkatkan kemampuan prediksi melalui kombinasi sejumlah decision tree.

Konfigurasi eksperimen menggunakan 100 estimators.

**CatBoost (Categorical Boosting)**

Algoritma gradient boosting berbasis decision tree yang menggunakan pendekatan Ordered Boosting untuk membantu mengurangi prediction shift.

Konfigurasi eksperimen menggunakan 1.000 iterations.

Kedua algoritma diuji pada seluruh skenario fitur untuk memperoleh perbandingan performa yang konsisten.

### 6. Evaluasi Model

Evaluasi dilakukan menggunakan beberapa metrik:

- **Accuracy:** Mengukur proporsi prediksi yang benar.
- **Precision:** Mengukur ketepatan prediksi pada setiap kelas.
- **Recall:** Mengukur kemampuan model dalam menemukan seluruh data pada setiap kelas.
- **F1-Score:** Mengukur keseimbangan antara precision dan recall.
- **Confusion Matrix:** Mengidentifikasi distribusi prediksi benar dan salah pada setiap kelas.

Selain pengujian data testing, dilakukan validasi tambahan menggunakan **5-Fold Stratified Cross-Validation** dengan metrik:

- Accuracy
- Macro Precision
- Macro Recall
- Macro F1-Score

Hasil evaluasi divisualisasikan untuk membandingkan performa XGBoost dan CatBoost pada setiap skenario.

## Teknologi dan Tools

| Teknologi | Penggunaan |
|---|---|
| Python | Bahasa pemrograman |
| Google Colab | Lingkungan pengembangan dan eksperimen |
| Pandas | Manipulasi dan pengolahan data |
| NumPy | Operasi numerik |
| Matplotlib | Visualisasi data |
| Seaborn | Visualisasi statistik |
| Scikit-learn | Data splitting dan evaluasi model |
| XGBoost | Algoritma klasifikasi |
| CatBoost | Algoritma klasifikasi |
| SciPy | Pengujian statistik Kruskal-Wallis |

## Struktur Repository

```text
Klasifikasi-Engagement-Level/
│
├── BISMILLAHFIKS.ipynb
├── emotional_monitoring_dataset_with_target.csv
└── README.md
```

*Catatan: Struktur di atas menggambarkan file utama yang digunakan dalam eksperimen. Pastikan file CSV tersedia sebelum menjalankan notebook.*

## Cara Menjalankan Proyek

Proyek dikembangkan menggunakan Google Colab sehingga dapat dijalankan tanpa konfigurasi lingkungan Python secara lokal.

**1. Buka Notebook**

Klik tombol berikut untuk membuka notebook di Google Colab:

[Open in Google Colab](https://colab.research.google.com/github/yoggalih/Klasifikasi-Engagement-Level-Fisiologis-dan-Lingkungan-menggunakan-XGBoost-dan-CatBoost/blob/main/BISMILLAHFIKS.ipynb)

**2. Siapkan Dataset**

Pastikan file `emotional_monitoring_dataset_with_target.csv` tersedia dan dapat diakses oleh notebook.

**3. Instalasi Library**

Jalankan cell instalasi library:

```python
!pip install xgboost catboost
```

**4. Jalankan Notebook**

Jalankan seluruh cell secara berurutan mulai dari proses import library, pemuatan dataset, EDA, preprocessing, pelatihan model, hingga evaluasi.

## Hasil dan Analisis

Eksperimen menghasilkan perbandingan performa XGBoost dan CatBoost berdasarkan tiga skenario penggunaan fitur:

1. Skenario fisiologis.
2. Skenario lingkungan.
3. Skenario multimodal.

Hasil pengujian dianalisis melalui metrik evaluasi klasifikasi pada data testing dan validasi 5-Fold Stratified Cross-Validation.

Pendekatan ini digunakan untuk melihat perbedaan performa algoritma berdasarkan kelompok fitur yang digunakan, sekaligus mengevaluasi konsistensi model melalui beberapa pembagian data.

## Batasan Penelitian

- Dataset yang digunakan merupakan dataset simulasi, bukan hasil pengukuran langsung terhadap individu.
- Penelitian berfokus pada klasifikasi berdasarkan fitur yang tersedia dalam dataset.
- Hasil eksperimen tidak dimaksudkan sebagai sistem monitoring engagement secara real-time.
- Performa model bergantung pada karakteristik dan distribusi dataset yang digunakan.

## Referensi

- Dataset: [Emotional Monitoring Dataset – Kaggle](https://www.kaggle.com/datasets/ziya07/emotional-monitoring-dataset)
- [XGBoost Documentation](https://xgboost.readthedocs.io/)
- [CatBoost Documentation](https://catboost.ai/docs/)
- [Scikit-learn Documentation](https://scikit-learn.org/stable/)

## Author

**Galih Yoga Kurniawan**

Informatika – Universitas Ahmad Dahlan

GitHub: [@yoggalih](https://github.com/yoggalih)

---

*Project ini merupakan bagian dari penelitian akademik mengenai klasifikasi Engagement Level berdasarkan parameter fisiologis dan kondisi lingkungan menggunakan algoritma Machine Learning.*
