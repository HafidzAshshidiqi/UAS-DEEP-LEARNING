# UAS-DEEP-LEARNING
NAMA KELOMPOK :

AKRAM ANALIS (G1A022004)

M. HAFIDZ ASHSHIDIQI (G1A022079)

# IoT Temperature Anomaly Detection using CNN-LSTM

Proyek ini bertujuan untuk mengembangkan **sistem deteksi anomali pada data sensor suhu IoT** menggunakan arsitektur **Hybrid Convolutional Neural Network (CNN) dan Long Short-Term Memory (LSTM)**. Model dirancang untuk mendeteksi pola suhu abnormal secara otomatis berdasarkan data time-series, serta dioptimalkan agar dapat diterapkan pada perangkat edge menggunakan **TensorFlow Lite (TFLite)**.

---

## 📌 Latar Belakang
Perkembangan Internet of Things (IoT) memungkinkan pengumpulan data sensor secara kontinu dan real-time. Salah satu data penting dalam sistem monitoring adalah data suhu, yang sering digunakan pada smart building, greenhouse, data center, dan sistem industri. Namun, data sensor IoT rentan terhadap anomali akibat kerusakan perangkat, gangguan lingkungan, atau kesalahan sistem.

Metode tradisional sering kali kurang efektif dalam menangkap **pola temporal kompleks** pada data time-series. Oleh karena itu, penelitian ini mengusulkan penggunaan **arsitektur CNN-LSTM**, yang menggabungkan kemampuan CNN dalam mengekstraksi fitur lokal dan LSTM dalam memodelkan ketergantungan waktu.

---

## 📂 Dataset
Dataset yang digunakan adalah **IoT Temperature Sensor Dataset** yang diperoleh dari Kaggle.

**Karakteristik Dataset:**
- Jumlah data: ±97.606 baris
- Tipe data: Time-series
- Fitur utama:
  - `temp` : nilai suhu
  - `noted_date` : waktu pencatatan
- Data bersifat **imbalanced**, dengan jumlah data normal jauh lebih banyak dibandingkan data anomali


---

## 🧠 Metodologi

### 1. Pra-Pemrosesan Data
- Parsing dan pengurutan data berdasarkan waktu
- Normalisasi nilai suhu (Min-Max Scaling)
- Segmentasi data menggunakan **window temporal (30 timestep)**
- Pelabelan anomali menggunakan pendekatan threshold statistik

### 2. Arsitektur Model
Model utama menggunakan **Hybrid CNN-LSTM**:
- **1D-CNN**: Ekstraksi fitur lokal dari setiap window data
- **LSTM**: Pemodelan ketergantungan temporal
- **Dense + Sigmoid**: Klasifikasi biner (normal vs anomali)

### 3. Baseline Model
Sebagai pembanding digunakan:
- **Support Vector Machine (SVM)**
- **Autoencoder**

---

## 🏋️ Pelatihan Model
- Framework: TensorFlow & Keras
- Optimizer: Adam
- Loss function: Binary Cross-Entropy
- Callback:
  - Early Stopping
  - Model Checkpoint
- Pembagian data:
  - Train: 70%
  - Validation: 15%
  - Test: 15%

---

## 📊 Evaluasi Model
Evaluasi dilakukan menggunakan metrik berikut:
- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Confusion Matrix
- ROC Curve

Hasil menunjukkan bahwa **CNN-LSTM memberikan performa terbaik** dibandingkan baseline, dengan nilai **akurasi dan ROC-AUC yang tinggi**, meskipun dataset memiliki ketidakseimbangan kelas.

---

## 🚀 Deployment (Edge Computing)
Model terbaik diekspor ke format **TensorFlow Lite (TFLite)** untuk mendukung deployment pada perangkat edge atau embedded system.

Proses deployment meliputi:
- Konversi model Keras ke TFLite
- Pengujian inference menggunakan data contoh
- Simulasi prediksi anomali secara real-time

Model hasil deployment tersimpan pada:

