# DRAFT USER FLOW

## Sistem Analisis Kedisiplinan Pegawai Berbasis K-Means

---

# 1. Informasi Dokumen

| Item | Keterangan |
|---|---|
| Produk | Sistem Analisis Kedisiplinan Pegawai Berbasis K-Means |
| Dokumen | User Flow Tahap 3 |
| Fokus Utama | Fitur AI ★ |
| Fitur Pendukung | Pengelolaan/Input Data Presensi |
| Platform | Website `[ASUMSI-01]` |
| Status | Draft |

> **Catatan:** User Flow ini mengikuti Use Case dan User Story pada tahap sebelumnya. Detail yang belum ditetapkan pada PRD/SRS ditandai `[ASUMSI]`.

---

# 2. Tujuan User Flow

User Flow menggambarkan perjalanan pengguna ketika menggunakan fitur analisis berbasis AI, mulai dari:

1. Membuka fitur.
2. Memberikan data.
3. Melakukan validasi awal.
4. Menunggu proses AI.
5. Menerima hasil analisis.
6. Menangani hasil yang meragukan.
7. Menangani kegagalan AI.
8. Melakukan review hasil.
9. Menyimpan hasil analisis.

Alur dirancang agar pengguna tetap memperoleh jalur penyelesaian ketika proses AI gagal atau hasil tidak dapat langsung digunakan.

---

# 3. Persona dan Skenario

## 3.1 Persona

**Pengelola Kepegawaian `[ASUMSI]`**

Pengguna menggunakan sistem untuk mengolah data presensi dan memperoleh hasil pengelompokan kedisiplinan pegawai.

---

## 3.2 Skenario Utama

Pengelola kepegawaian ingin melakukan analisis data presensi menggunakan fitur **K-Means Clustering ★** untuk memperoleh pengelompokan berdasarkan:

- Persentase kehadiran.
- Persentase pemenuhan jam kerja.

---

# 4. Fitur yang Dicakup

## 4.1 Fitur AI ★

### K-Means Clustering

Fitur AI digunakan untuk mengelompokkan data pegawai berdasarkan karakteristik data presensi.

Input utama:

- Persentase kehadiran.
- Persentase pemenuhan jam kerja.

Output:

- Hasil pengelompokan/cluster.
- Informasi evaluasi clustering melalui Silhouette Score.

---

## 4.2 Fitur Utama Pendukung

### Input Data Presensi

Pengguna menyediakan data yang diperlukan sebelum proses analisis dilakukan.

---

# 5. User Flow Utama

## 5.1 Langkah Alur

| No. | Tahap | Aktor | Aktivitas | Status Sistem |
|---|---|---|---|---|
| 1 | Masuk fitur | Pengguna | Membuka fitur analisis | Siap |
| 2 | Input data | Pengguna | Memberikan data presensi | Input |
| 3 | Validasi | Sistem | Memeriksa kelayakan data | Validasi |
| 4 | Perbaikan | Pengguna | Memperbaiki data jika tidak valid | Perbaikan |
| 5 | Pemrosesan | Sistem/AI | Memulai proses K-Means | Loading |
| 6 | Pemeriksaan respons | Sistem | Memeriksa apakah AI merespons dalam batas waktu | Processing |
| 7A | AI berhasil | Sistem/AI | Menghasilkan hasil analisis | Hasil yakin |
| 7B | AI meragukan | Sistem/AI | Meminta konfirmasi pengguna | Hasil meragukan |
| 7C | AI gagal | Sistem | Menawarkan jalur fallback | Fallback |
| 8 | Review | Pengguna | Memeriksa hasil analisis | Review |
| 9 | Simpan | Pengguna/Sistem | Menyimpan hasil dan menyelesaikan proses | Selesai |

---

# 6. Diagram User Flow Mermaid

```mermaid
flowchart TD
    A([Buka Fitur]) --> B[Input Data / Foto]

    B --> C{Input Layak?}

    C -- Tidak --> D[Tampilkan Pesan Perbaikan]
    D --> B

    C -- Ya --> E[Tampilkan Loading: Memproses AI...]

    E --> F{Respon <= Batas Waktu?}

    F -- Timeout/Gagal --> G[Tawarkan Mode Manual / Fallback]
    G --> H[Layar Review Hasil]

    F -- Sukses --> I{Confidence Cukup?}

    I -- Rendah/Ragu --> J[Minta Konfirmasi Pengguna]
    I -- Tinggi/Yakin --> K[Tampilkan Hasil Analisis Otomatis]

    J --> H
    K --> H

    H --> L([Simpan & Selesai])
