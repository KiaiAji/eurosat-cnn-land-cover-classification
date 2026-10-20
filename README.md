# Klasifikasi Tutupan Lahan EuroSAT Menggunakan CNN

Proyek *deep learning* untuk mengklasifikasikan citra satelit ke dalam 10 kategori tutupan lahan menggunakan **Convolutional Neural Network (CNN)** dan dataset EuroSAT RGB.

## 1. Deskripsi Proyek

Klasifikasi tutupan lahan merupakan salah satu penerapan penginderaan jauh (*remote sensing*) dan kecerdasan buatan dalam analisis citra satelit. Informasi tutupan lahan dapat digunakan untuk memahami distribusi kawasan hutan, lahan pertanian, permukiman, jalan, dan berbagai jenis penggunaan lahan lainnya.

Proyek ini bertujuan membangun model CNN yang mampu mengklasifikasikan citra satelit berdasarkan karakteristik visualnya. Studi ini menjadi langkah awal untuk memahami pemanfaatan *deep learning* dalam analisis tutupan lahan serta pengembangan sistem pemantauan deforestasi.

## 2. Tujuan

- Mengklasifikasikan citra satelit ke dalam 10 kategori tutupan lahan.
- Membangun dan melatih model CNN menggunakan TensorFlow dan Keras.
- Mengevaluasi performa model menggunakan akurasi, precision, recall, F1-score, dan confusion matrix.
- Memahami penerapan *deep learning* dalam bidang penginderaan jauh.
- Menjadi dasar pengembangan penelitian lanjutan terkait pemantauan hutan dan perubahan tutupan lahan.

## 3. Dataset

**Nama dataset:** EuroSAT RGB

**Sumber dataset:** [EuroSAT RGB di Hugging Face](https://huggingface.co/datasets/timm/eurosat-rgb)

Dataset EuroSAT berisi citra satelit yang digunakan untuk klasifikasi tutupan lahan. Dalam proyek ini, versi RGB diakses menggunakan pustaka Hugging Face `datasets` dengan metode *streaming* untuk mengurangi kebutuhan mengunduh seluruh dataset terlebih dahulu.

### Kategori tutupan lahan

Model dirancang untuk mengklasifikasikan citra ke dalam 10 kategori berikut:

1. `AnnualCrop` — tanaman semusim
2. `Forest` — hutan
3. `HerbaceousVegetation` — vegetasi herba
4. `Highway` — jalan raya
5. `Industrial` — kawasan industri
6. `Pasture` — padang rumput untuk penggembalaan
7. `PermanentCrop` — tanaman tahunan
8. `Residential` — kawasan permukiman
9. `River` — sungai
10. `SeaLake` — laut dan danau

## 4. Metodologi

Tahapan penelitian dalam proyek ini adalah:

1. Memuat dataset EuroSAT RGB.
2. Mengambil sebagian data untuk eksperimen awal.
3. Melakukan prapemrosesan citra dan normalisasi nilai piksel ke rentang 0–1.
4. Membangun arsitektur CNN.
5. Melatih model menggunakan data pelatihan.
6. Memantau performa menggunakan data validasi.
7. Menguji model menggunakan data pengujian.
8. Menganalisis hasil klasifikasi dan mengevaluasi performa model.

## 5. Arsitektur Model

Model CNN menggunakan beberapa lapisan berikut:

- **Conv2D:** mengekstraksi fitur visual dari citra.
- **MaxPooling2D:** mengurangi dimensi fitur.
- **Dense:** mempelajari hubungan antarfitur untuk klasifikasi.
- **Dropout:** membantu mengurangi risiko *overfitting*.
- **Softmax:** menghasilkan probabilitas prediksi untuk 10 kelas tutupan lahan.

### Konfigurasi pelatihan

| Parameter | Nilai |
|---|---|
| Framework | TensorFlow dan Keras |
| Algoritma | Convolutional Neural Network |
| Optimizer | Adam |
| Fungsi loss | Sparse categorical cross-entropy |
| Ukuran batch | 32 |
| Epoch maksimum | 10 |
| Early stopping | Digunakan |

## 6. Pembagian Data

Eksperimen awal menggunakan sebagian dataset agar kebutuhan komputasi lebih ringan.

| Subset | Jumlah citra |
|---|---:|
| Data pelatihan (*training*) | 2.000 |
| Data validasi (*validation*) | 500 |
| Data pengujian (*testing*) | 500 |
| **Total** | **3.000** |

Jumlah di atas merupakan target konfigurasi eksperimen. Jumlah aktual perlu diperiksa setelah kode berhasil dijalankan.

## 7. Evaluasi Model

Performa model dievaluasi menggunakan beberapa metrik:

- **Accuracy:** persentase prediksi yang benar dari seluruh data pengujian.
- **Precision:** mengukur ketepatan prediksi pada setiap kelas.
- **Recall:** mengukur kemampuan model mengenali sampel dari suatu kelas.
- **F1-score:** menggabungkan precision dan recall.
- **Confusion matrix:** menunjukkan perbandingan kelas aktual dengan kelas hasil prediksi.

Hasil evaluasi akan dicatat setelah eksperimen dijalankan. Nilai akurasi tidak ditetapkan sebelumnya agar laporan mencerminkan hasil pengujian yang sebenarnya.

## 8. Struktur Repositori

```text
eurosat-cnn-land-cover-classification/
├── README.md
├── eurosat_cnn_classification.ipynb
├── eurosat_cnn_model.keras
├── accuracy_curve.png
├── loss_curve.png
├── confusion_matrix.png
├── classification_report.csv
└── experiment_results.json
```

File hasil eksperimen akan tersedia setelah program berhasil dijalankan dan file terkait diunggah ke repositori.

## 9. Teknologi yang Digunakan

- Python
- TensorFlow dan Keras
- Hugging Face Datasets
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- Google Colab
- GitHub

### Instalasi pustaka

Jalankan perintah berikut di Google Colab atau lingkungan Python yang sesuai:

```bash
pip install datasets tensorflow scikit-learn matplotlib seaborn pandas
```

## 10. Cara Menjalankan Proyek

1. Buka [Google Colab](https://colab.research.google.com/).
2. Buat notebook baru.
3. Instal pustaka yang dibutuhkan.
4. Jalankan kode untuk memuat dataset EuroSAT RGB.
5. Lakukan prapemrosesan data.
6. Bangun dan latih model CNN.
7. Evaluasi model menggunakan data pengujian.
8. Simpan grafik, laporan evaluasi, dan model jika diperlukan.
9. Unggah notebook dan hasil eksperimen ke repositori GitHub.

Koneksi internet diperlukan untuk mengakses dataset melalui Hugging Face.

## 11. Keterbatasan Penelitian

Proyek ini berfokus pada **klasifikasi tutupan lahan, bukan deteksi deforestasi secara langsung**.

Model mengklasifikasikan citra berdasarkan kategori tutupan lahan, tetapi belum dirancang untuk:

- Mendeteksi perubahan hutan antara dua waktu pengamatan.
- Menentukan lokasi dan luas area deforestasi.
- Mengidentifikasi penyebab langsung deforestasi, seperti ekspansi pertanian, penebangan, pertambangan, atau kebakaran.
- Menghasilkan peringatan deforestasi secara berkala.

Untuk mengembangkan sistem deteksi deforestasi, diperlukan pendekatan tambahan seperti analisis citra multitemporal, deteksi perubahan (*change detection*), serta data referensi yang sesuai.

## 12. Pengembangan Selanjutnya

Beberapa pengembangan yang dapat dilakukan:

- Menggunakan lebih banyak data untuk meningkatkan evaluasi model.
- Menerapkan augmentasi citra dan *transfer learning*.
- Membandingkan CNN dengan arsitektur *deep learning* lainnya.
- Mengintegrasikan citra Sentinel-1 dan Sentinel-2.
- Menganalisis perubahan tutupan hutan dari waktu ke waktu.
- Menguji model menggunakan data independen dari wilayah studi tertentu.
- Mengembangkan sistem pemantauan perubahan hutan sebagai tahap penelitian berikutnya.

## 13. Kesimpulan

Proyek ini menunjukkan penerapan CNN untuk klasifikasi tutupan lahan berbasis citra satelit EuroSAT RGB. Eksperimen ini memberikan dasar untuk memahami pemrosesan citra satelit, pelatihan model *deep learning*, dan evaluasi hasil klasifikasi.

Hasil dan pendekatan yang diperoleh dapat menjadi landasan untuk penelitian lebih lanjut dalam bidang penginderaan jauh, pemetaan tutupan lahan, dan pengembangan sistem pemantauan deforestasi.

## 14. Referensi

- Dataset: [EuroSAT RGB — Hugging Face](https://huggingface.co/datasets/timm/eurosat-rgb)
- TensorFlow: [https://www.tensorflow.org/](https://www.tensorflow.org/)
- Scikit-learn: [https://scikit-learn.org/](https://scikit-learn.org/)

**Tujuan proyek:** Studi kasus akademik klasifikasi tutupan lahan menggunakan citra satelit.
