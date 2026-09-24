# High Level Design (HLD)

## Sistem Klasterisasi Tingkat Kedisiplinan Pegawai Berbasis K-Means

> **Status:** Draft  
> **Versi:** 1.0  
> **Platform:** Web  
> **Fitur AI Utama:** K-Means Clustering  
> **Metode:** Knowledge Discovery in Databases (KDD)  
> **Normalisasi:** Min-Max  
> **Evaluasi:** Silhouette Score  
> **Target:** Prototype 1 Semester

---

# 1. Pendahuluan

## 1.1 Tujuan

Sistem dirancang untuk memanfaatkan data presensi pegawai agar dapat dianalisis untuk memperoleh informasi mengenai tingkat kedisiplinan pegawai.

Fitur AI utama menggunakan algoritma **K-Means Clustering** untuk mengelompokkan pegawai berdasarkan data presensi.

Dua variabel utama yang digunakan adalah:

1. Persentase kehadiran.
2. Persentase pemenuhan jam kerja.

Hasil proses clustering digunakan untuk membentuk tiga kelompok tingkat kedisiplinan:

- Kedisiplinan Tinggi
- Kedisiplinan Sedang
- Kedisiplinan Rendah

---

# 2. Ruang Lingkup

## 2.1 In Scope

- Pengolahan data presensi pegawai.
- Pemilihan periode data.
- Selection data.
- Preprocessing data.
- Transformasi data.
- Normalisasi Min-Max.
- Clustering menggunakan K-Means.
- Pembentukan tiga cluster.
- Evaluasi menggunakan Silhouette Score.
- Interpretasi hasil cluster.
- Penyajian hasil tingkat kedisiplinan.

## 2.2 Out of Scope

Fitur berikut tidak termasuk dalam rancangan:

- Prediksi kedisiplinan masa depan.
- Pemberian sanksi otomatis.
- Penilaian kinerja otomatis.
- Payroll.
- Sistem penggajian.
- Notifikasi otomatis.
- Facial recognition.
- Pengambilan keputusan kepegawaian otomatis.

---

# 3. Arsitektur Sistem

## 3.1 High Level Architecture

```mermaid
flowchart LR
    USER[User / Admin]
    CLIENT[Web Client]
    API[Backend API]
    DB[(Database)]
    PRE[Preprocessing]
    NORM[Min-Max Normalization]
    AI[K-Means Clustering]
    EVAL[Silhouette Score]
    RESULT[Hasil Klasterisasi]

    USER --> CLIENT
    CLIENT -->|HTTPS| API

    API --> DB
    DB --> API

    API --> PRE
    PRE --> NORM
    NORM --> AI
    AI --> EVAL
    EVAL --> RESULT

    RESULT --> DB
    RESULT --> API

    API --> CLIENT
    CLIENT --> USER
