# DRAFT USE CASE

## Sistem Analisis Kedisiplinan Pegawai Berbasis K-Means

---

# 1. Informasi Dokumen

| Item | Keterangan |
|---|---|
| Produk | Sistem Analisis Kedisiplinan Pegawai Berbasis K-Means |
| Dokumen Acuan | `prd.md`, `srs.md`, `user-stories.md` |
| Fokus | Use Case prioritas Must dan Should |
| Fokus AI | ★ K-Means Clustering |
| Platform | Website `[ASUMSI-01]` |
| Layanan AI | K-Means Clustering `[ASUMSI-02]` |
| Database | Penyimpanan data presensi dan hasil analisis `[ASUMSI-03]` |
| Status | Draft |

> **Catatan:** SRS yang tersedia tidak menetapkan API AI eksternal, model AI berbasis server, nilai confidence threshold, maupun angka batas latensi final. Oleh karena itu, informasi tersebut tidak dibuat-buat dalam dokumen ini.

---

# 2. Aktor

## 2.1 Aktor Utama

### Pengelola Kepegawaian `[ASUMSI]`

Pengelola kepegawaian merupakan persona utama yang menggunakan sistem untuk mengelola data presensi dan memperoleh informasi hasil pengelompokan kedisiplinan.

---

## 2.2 Aktor Pendukung

| Aktor | Peran |
|---|---|
| **Layanan K-Means ★** | Melakukan proses clustering berdasarkan data persentase kehadiran dan persentase pemenuhan jam kerja. |
| **Database `[ASUMSI]`** | Menyimpan data presensi dan hasil analisis. |

> **Catatan:** K-Means pada SRS merupakan metode clustering. SRS belum menyatakan bahwa K-Means dijalankan melalui layanan AI eksternal/API. Karena itu, istilah **Layanan K-Means** digunakan sebagai aktor pendukung logis untuk kebutuhan Use Case, bukan klaim mengenai arsitektur implementasi.

---

# 3. Batas Waktu dan Penanganan AI

SRS menetapkan bahwa waktu proses clustering harus dapat diukur, tetapi belum menetapkan angka target latensi final.

| Parameter | Ketentuan |
|---|---|
| Latensi clustering | `[ASUMSI-04]` Target ditentukan setelah baseline dataset prototype tersedia. |
| Timeout layanan AI | `[ASUMSI-05]` Nilai timeout belum ditentukan dalam SRS. |
| Toleransi error | `[ASUMSI-06]` SRS menetapkan target keberhasilan proses valid sebesar ≥ 95%, tetapi belum menetapkan toleransi khusus untuk layanan AI eksternal. |
| Low confidence | Tidak ditetapkan pada SRS karena K-Means menghasilkan cluster, bukan probabilitas confidence klasifikasi. |
| Evaluasi model | Silhouette Score. |
| Nilai acuan penelitian | 0,500844. |

---

# 4. Daftar Use Case

| ID | Nama Use Case | User Story | FR Asal | Prioritas |
|---|---|---|---|---|
| UC-01 | Memasukkan Data Presensi | US-02 | FR-02 | Must |
| UC-02 | Menyiapkan Data Kehadiran | US-03 | FR-03 | Must |
| UC-03 | Menyiapkan Data Pemenuhan Jam Kerja | US-04 | FR-04 | Must |
| UC-04 | Menjalankan K-Means ★ | US-05 | FR-05 | Must |
| UC-05 | Memperoleh Hasil Pengelompokan ★ | US-06 | FR-06 | Must |
| UC-06 | Melihat Hasil Analisis ★ | US-07 | FR-07, FR-09 | Must |
| UC-07 | Mengevaluasi Hasil Clustering ★ | US-08 | FR-08 | Must |
| UC-08 | Memilih Periode Analisis | US-09 | FR-10 | Should |
| UC-09 | Melihat Rekap Hasil Clustering ★ | US-10 | FR-11 | Should |
| UC-10 | Melihat Riwayat Analisis ★ | US-11 | FR-12 | Should |

---

# 5. Use Case UC-01 — Memasukkan Data Presensi

## 5.1 Identitas

| Item | Keterangan |
|---|---|
| ID | UC-01 |
| Nama | Memasukkan Data Presensi |
| Aktor Utama | Pengelola Kepegawaian `[ASUMSI]` |
| Aktor Pendukung | Database `[ASUMSI]` |
| User Story | US-02 |
| FR | FR-02 |
| Prioritas | Must |

## 5.2 Precondition

1. Pengelola kepegawaian telah memiliki data presensi.
2. Sistem dapat menerima data presensi.
3. Data memiliki informasi yang diperlukan untuk analisis.

## 5.3 Postcondition

Data presensi tersedia sebagai sumber data untuk proses analisis.

## 5.4 Alur Utama

1. Pengelola kepegawaian memberikan data presensi.
2. Sistem menerima data presensi.
3. Sistem memeriksa keberadaan data yang diperlukan.
4. Sistem menyimpan data yang valid.
5. Sistem menyatakan data tersedia untuk proses analisis.
6. Use Case selesai.

## 5.5 Alur Alternatif

### A1 — Sebagian Data Tidak Lengkap

1. Sistem menemukan sebagian data tidak memiliki informasi yang diperlukan.
2. Sistem menandai data tersebut sebagai tidak valid.
3. Sistem mempertahankan data valid.
4. Sistem memberikan informasi bahwa sebagian data tidak dapat digunakan.
5. Pengelola kepegawaian memperbaiki atau melengkapi data.
6. Proses dapat dilanjutkan setelah data valid tersedia.

## 5.6 Alur Eksepsi AI

Use Case ini belum melakukan inferensi AI.

Jika data akan digunakan untuk proses AI dan kualitas input rendah:

1. Sistem mendeteksi bahwa data yang diperlukan tidak valid atau tidak lengkap.
2. Sistem tidak mengirim data tersebut ke proses K-Means.
3. Sistem memberikan informasi mengenai data yang perlu diperbaiki.
4. Pengelola kepegawaian memperbaiki data.
5. Proses analisis dapat dilakukan kembali.

**Catatan:** istilah "buram" tidak relevan dengan data presensi numerik pada SRS. Tidak terdapat bukti bahwa sistem menerima gambar sebagai input AI.

---

# 6. Use Case UC-02 — Menyiapkan Data Kehadiran

## 6.1 Identitas

| Item | Keterangan |
|---|---|
| ID | UC-02 |
| Nama | Menyiapkan Data Kehadiran |
| Aktor Utama | Pengelola Kepegawaian `[ASUMSI]` |
| Aktor Pendukung | Database `[ASUMSI]` |
| User Story | US-03 |
| FR | FR-03 |
| Prioritas | Must |

## 6.2 Precondition

1. Data presensi tersedia.
2. Data memiliki informasi yang dapat digunakan untuk memperoleh persentase kehadiran.

## 6.3 Postcondition

Persentase kehadiran tersedia sebagai variabel analisis.

## 6.4 Alur Utama

1. Pengelola kepegawaian menyediakan data presensi.
2. Sistem mengambil data yang berkaitan dengan kehadiran.
3. Sistem menggunakan persentase kehadiran sebagai variabel analisis.
4. Sistem menandai variabel sebagai tersedia.
5. Use Case selesai.

## 6.5 Alur Alternatif

### A1 — Data Kehadiran Tidak Tersedia

1. Sistem memeriksa data presensi.
2. Sistem tidak menemukan informasi yang diperlukan.
3. Sistem menyatakan data belum memenuhi kebutuhan analisis.
4. Sistem tidak melanjutkan proses K-Means.
5. Pengelola kepegawaian melengkapi data.

## 6.6 Alur Eksepsi AI

Karena Use Case belum menjalankan inferensi:

- Tidak ada permintaan ke layanan AI.
- Tidak ada confidence score.
- Tidak ada timeout layanan AI.

---

# 7. Use Case UC-03 — Menyiapkan Data Pemenuhan Jam Kerja

## 7.1 Identitas

| Item | Keterangan |
|---|---|
| ID | UC-03 |
| Nama | Menyiapkan Data Pemenuhan Jam Kerja |
| Aktor Utama | Pengelola Kepegawaian `[ASUMSI]` |
| Aktor Pendukung | Database `[ASUMSI]` |
| User Story | US-04 |
| FR | FR-04 |
| Prioritas | Must |

## 7.2 Precondition

1. Data presensi tersedia.
2. Data memiliki informasi pemenuhan jam kerja.

## 7.3 Postcondition

Persentase pemenuhan jam kerja tersedia sebagai variabel analisis.

## 7.4 Alur Utama

1. Pengelola kepegawaian menyediakan data presensi.
2. Sistem mengambil data pemenuhan jam kerja.
3. Sistem menggunakan persentase pemenuhan jam kerja sebagai variabel analisis.
4. Sistem memastikan variabel tersedia.
5. Use Case selesai.

## 7.5 Alur Alternatif

### A1 — Data Pemenuhan Jam Kerja Tidak Tersedia

1. Sistem memeriksa data.
2. Sistem menemukan informasi pemenuhan jam kerja tidak tersedia.
3. Sistem menyatakan data belum memenuhi kebutuhan analisis.
4. Sistem tidak melanjutkan proses K-Means.
5. Pengelola kepegawaian melengkapi data.

## 7.6 Alur Eksepsi AI

Tidak ada inferensi AI pada tahap ini.

---

# 8. Use Case UC-04 — Menjalankan K-Means ★

## 8.1 Identitas

| Item | Keterangan |
|---|---|
| ID | UC-04 |
| Nama | Menjalankan K-Means |
| Aktor Utama | Pengelola Kepegawaian `[ASUMSI]` |
| Aktor Pendukung | Layanan K-Means ★ |
| Aktor Pendukung | Database `[ASUMSI]` |
| User Story | US-05 |
| FR | FR-05 |
| Prioritas | Must |

## 8.2 Precondition

1. Data presensi tersedia.
2. Persentase kehadiran tersedia.
3. Persentase pemenuhan jam kerja tersedia.
4. Data memenuhi syarat minimum untuk proses clustering.
5. Layanan K-Means tersedia `[ASUMSI]`.

## 8.3 Postcondition

Data memperoleh hasil pengelompokan dari proses K-Means.

## 8.4 Alur Utama

1. Pengelola kepegawaian meminta sistem melakukan analisis.
2. Sistem memeriksa ketersediaan data.
3. Sistem mengambil persentase kehadiran.
4. Sistem mengambil persentase pemenuhan jam kerja.
5. Sistem menyiapkan kedua variabel sebagai input clustering.
6. Sistem mengirimkan input ke layanan K-Means `[ASUMSI]`.
7. Layanan K-Means memproses data.
8. Layanan K-Means menghasilkan kelompok data.
9. Sistem menerima hasil clustering.
10. Sistem menyimpan hasil analisis.
11. Sistem melanjutkan ke proses evaluasi hasil.
12. Use Case selesai.

## 8.5 Alur Alternatif

### A1 — Data Valid Tetapi Sebagian Data Tidak Dapat Digunakan

1. Sistem menemukan sebagian data tidak memenuhi kebutuhan.
2. Sistem memisahkan data yang tidak valid.
3. Sistem menggunakan data yang memenuhi syarat `[ASUMSI]`.
4. Sistem menjalankan proses clustering terhadap data yang valid.
5. Sistem menyimpan hasil analisis.
6. Sistem memberikan informasi bahwa sebagian data tidak digunakan.

---

## 8.6 Alur Eksepsi Khusus AI

### E1 — Kualitas Input Rendah atau Data Tidak Valid

1. Sistem memeriksa kualitas data sebelum dikirim ke layanan K-Means.
2. Sistem menemukan data tidak lengkap, tidak valid, atau tidak dapat digunakan.
3. Sistem tidak mengirim data yang bermasalah ke layanan K-Means.
4. Sistem memberikan informasi bahwa data belum memenuhi syarat analisis.
5. Pengelola kepegawaian memperbaiki data.
6. Pengelola kepegawaian menjalankan analisis kembali.

### E2 — Timeout Layanan AI

1. Sistem mengirimkan data ke layanan K-Means.
2. Sistem tidak menerima respons dalam batas waktu yang ditentukan `[ASUMSI-04]`.
3. Sistem menghentikan penantian terhadap respons.
4. Sistem tidak menyimpan hasil clustering sebagai hasil yang berhasil.
5. Sistem memberikan informasi bahwa proses analisis belum berhasil.
6. Pengelola kepegawaian dapat mencoba kembali.

### E3 — Gagal Koneksi ke Layanan AI

1. Sistem mencoba mengirimkan data ke layanan K-Means.
2. Koneksi ke layanan gagal.
3. Sistem tidak menerima hasil clustering.
4. Sistem tidak menggunakan hasil yang tidak lengkap sebagai hasil analisis.
5. Sistem memberikan informasi kegagalan proses.
6. Pengelola kepegawaian dapat mencoba kembali setelah layanan tersedia.

### E4 — Low Confidence

K-Means pada SRS tidak menghasilkan skor keyakinan klasifikasi. Oleh karena itu, **low confidence tidak dapat diterapkan secara langsung berdasarkan kebutuhan yang tersedia**.

Jika implementasi AI nantinya menyediakan confidence score:

1. Sistem menerima hasil clustering beserta confidence score.
2. Sistem membandingkan confidence score dengan threshold yang telah ditentukan `[ASUMSI-07]`.
3. Jika confidence berada di bawah threshold, sistem tidak langsung menggunakan hasil sebagai hasil final.
4. Sistem menandai hasil sebagai membutuhkan pemeriksaan.
5. Pengelola kepegawaian dapat melakukan analisis ulang atau pemeriksaan data.

> **Catatan:** Threshold confidence belum ditentukan dalam SRS sehingga tidak boleh diisi dengan angka tanpa validasi.

---

# 9. Use Case UC-05 — Memperoleh Hasil Pengelompokan ★

## 9.1 Identitas

| Item | Keterangan |
|---|---|
| ID | UC-05 |
| Nama | Memperoleh Hasil Pengelompokan |
| Aktor Utama | Pengelola Kepegawaian `[ASUMSI]` |
| Aktor Pendukung | Layanan K-Means ★ |
| Aktor Pendukung | Database `[ASUMSI]` |
| User Story | US-06 |
| FR | FR-06 |
| Prioritas | Must |

## 9.2 Precondition

1. Proses K-Means telah selesai.
2. Hasil clustering tersedia.

## 9.3 Postcondition

Tiga kelompok hasil clustering tersedia untuk digunakan sebagai informasi pengelompokan kedisiplinan.

## 9.4 Alur Utama

1. Sistem menerima hasil clustering.
2. Sistem memeriksa keberadaan hasil untuk data yang diproses.
3. Sistem mengidentifikasi tiga kelompok hasil.
4. Sistem menginterpretasikan kelompok sesuai aturan bisnis yang ditetapkan.
5. Sistem menyimpan hasil.
6. Sistem menyediakan hasil untuk proses berikutnya.
7. Use Case selesai.

## 9.5 Alur Alternatif

### A1 — Hasil Tidak Lengkap

1. Sistem menerima hasil clustering.
2. Sistem menemukan sebagian data tidak memperoleh kelompok.
3. Sistem menandai hasil sebagai tidak lengkap.
4. Sistem tidak menyatakan proses sebagai berhasil sepenuhnya.
5. Pengelola kepegawaian dapat menjalankan analisis kembali.

## 9.6 Alur Eksepsi AI

### E1 — Input Berkualitas Rendah

Jika hasil menunjukkan bahwa data yang diproses tidak memenuhi kualitas minimum:

1. Sistem menolak hasil sebagai hasil final.
2. Sistem memberikan informasi bahwa data perlu diperbaiki.
3. Pengelola kepegawaian memperbaiki data.
4. Analisis dijalankan kembali.

### E2 — Timeout/Gagal Koneksi

Jika layanan K-Means tidak menghasilkan respons:

1. Sistem tidak membuat hasil pengelompokan.
2. Sistem mencatat proses sebagai gagal.
3. Pengelola kepegawaian diberi kesempatan untuk mencoba kembali.

### E3 — Low Confidence

Tidak berlaku pada K-Means standar karena SRS tidak mendefinisikan confidence score.

Jika layanan AI yang digunakan nantinya menyediakan confidence score, penanganannya mengikuti aturan pada **UC-04 E4**.

---

# 10. Use Case UC-06 — Melihat Hasil Analisis ★

## 10.1 Identitas

| Item | Keterangan |
|---|---|
| ID | UC-06 |
| Nama | Melihat Hasil Analisis |
| Aktor Utama | Pengelola Kepegawaian `[ASUMSI]` |
| Aktor Pendukung | Database `[ASUMSI]` |
| User Story | US-07 |
| FR | FR-07, FR-09 |
| Prioritas | Must |

## 10.2 Precondition

1. Hasil clustering tersedia.
2. Hasil analisis tersimpan.

## 10.3 Postcondition

Pengelola kepegawaian memperoleh informasi hasil pengelompokan untuk mendukung monitoring dan evaluasi.

## 10.4 Alur Utama

1. Pengelola kepegawaian meminta hasil analisis.
2. Sistem mengambil hasil analisis.
3. Sistem memeriksa kelengkapan hasil.
4. Sistem menyediakan informasi kelompok kedisiplinan.
5. Pengelola kepegawaian memperoleh informasi hasil analisis.
6. Use Case selesai.

## 10.5 Alur Alternatif

### A1 — Belum Ada Hasil Analisis

1. Pengelola kepegawaian meminta hasil analisis.
2. Sistem tidak menemukan hasil analisis.
3. Sistem menyatakan belum tersedia hasil.
4. Pengelola kepegawaian menjalankan proses analisis terlebih dahulu.

## 10.6 Alur Eksepsi AI

Use Case ini tidak melakukan inferensi AI secara langsung.

Jika hasil sebelumnya ditandai gagal atau tidak valid:

1. Sistem tidak menampilkan hasil sebagai hasil analisis yang valid.
2. Sistem memberikan informasi bahwa analisis perlu dilakukan kembali.

---

# 11. Use Case UC-07 — Mengevaluasi Hasil Clustering ★

## 11.1 Identitas

| Item | Keterangan |
|---|---|
| ID | UC-07 |
| Nama | Mengevaluasi Hasil Clustering |
| Aktor Utama | Pengelola Kepegawaian `[ASUMSI]` |
| Aktor Pendukung | Layanan K-Means ★ |
| User Story | US-08 |
| FR | FR-08 |
| Prioritas | Must |

## 11.2 Precondition

1. Hasil clustering tersedia.
2. Data hasil clustering dapat dievaluasi.

## 11.3 Postcondition

Nilai Silhouette Score tersedia sebagai informasi evaluasi kualitas clustering.

## 11.4 Alur Utama

1. Sistem menerima hasil clustering.
2. Sistem menggunakan data hasil clustering untuk evaluasi.
3. Sistem menghitung Silhouette Score.
4. Sistem memperoleh nilai evaluasi.
5. Sistem menyimpan nilai evaluasi bersama hasil analisis.
6. Pengelola kepegawaian dapat mengetahui nilai evaluasi.
7. Use Case selesai.

## 11.5 Alur Alternatif

### A1 — Clustering Tidak Dapat Dievaluasi

1. Sistem mencoba melakukan evaluasi.
2. Data tidak memenuhi syarat untuk perhitungan Silhouette Score.
3. Sistem tidak menghasilkan nilai evaluasi.
4. Sistem memberikan informasi bahwa evaluasi tidak dapat dilakukan.
5. Pengelola kepegawaian dapat memeriksa kembali data dan hasil clustering.

## 11.6 Alur Eksepsi AI

### E1 — Input Tidak Memadai

1. Sistem memeriksa data clustering.
2. Data tidak memenuhi syarat evaluasi.
3. Sistem menghentikan proses evaluasi.
4. Sistem memberikan informasi kegagalan evaluasi.

### E2 — Layanan AI Tidak Tersedia

Jika evaluasi bergantung pada layanan eksternal `[ASUMSI]`:

1. Sistem mencoba meminta proses evaluasi.
2. Layanan tidak merespons atau koneksi gagal.
3. Sistem tidak menyatakan nilai evaluasi berhasil diperoleh.
4. Sistem mencatat evaluasi sebagai gagal.
5. Pengelola kepegawaian dapat mencoba kembali.

### E3 — Low Confidence

Silhouette Score bukan confidence score model.

Oleh karena itu, tidak ada mekanisme low confidence khusus pada SRS saat ini.

---

# 12. Use Case UC-08 — Memilih Periode Analisis

## 12.1 Identitas

| Item | Keterangan |
|---|---|
| ID | UC-08 |
| Nama | Memilih Periode Analisis |
| Aktor Utama | Pengelola Kepegawaian `[ASUMSI]` |
| Aktor Pendukung | Database `[ASUMSI]` |
| User Story | US-09 |
| FR | FR-10 |
| Prioritas | Should |

## 12.2 Precondition

Data presensi tersedia untuk lebih dari satu periode `[ASUMSI]`.

## 12.3 Postcondition

Data yang digunakan untuk analisis dibatasi pada periode yang dipilih.

## 12.4 Alur Utama

1. Pengelola kepegawaian menentukan periode analisis.
2. Sistem memeriksa ketersediaan data pada periode tersebut.
3. Sistem mengambil data yang sesuai.
4. Sistem menyediakan data tersebut untuk proses analisis.
5. Use Case selesai.

## 12.5 Alur Alternatif

### A1 — Data Tidak Tersedia

1. Sistem memeriksa periode yang dipilih.
2. Tidak ditemukan data.
3. Sistem memberikan informasi bahwa data tidak tersedia.
4. Pengelola kepegawaian memilih periode lain.

## 12.6 Alur Eksepsi AI

Tidak ada inferensi AI langsung pada Use Case ini.

---

# 13. Use Case UC-09 — Melihat Rekap Hasil Clustering ★

## 13.1 Identitas

| Item | Keterangan |
|---|---|
| ID | UC-09 |
| Nama | Melihat Rekap Hasil Clustering |
| Aktor Utama | Pengelola Kepegawaian `[ASUMSI]` |
| Aktor Pendukung | Database `[ASUMSI]` |
| User Story | US-10 |
| FR | FR-11 |
| Prioritas | Should |

## 13.2 Precondition

Hasil clustering tersedia.

## 13.3 Postcondition

Jumlah anggota setiap kelompok dapat diketahui.

## 13.4 Alur Utama

1. Pengelola kepegawaian meminta rekap hasil.
2. Sistem mengambil hasil clustering.
3. Sistem menghitung jumlah anggota setiap kelompok.
4. Sistem menyediakan rekap hasil.
5. Pengelola kepegawaian memperoleh informasi distribusi kelompok.
6. Use Case selesai.

## 13.5 Alur Alternatif

### A1 — Hasil Clustering Tidak Tersedia

1. Sistem mencari hasil clustering.
2. Sistem tidak menemukan hasil.
3. Sistem memberikan informasi bahwa rekap belum tersedia.
4. Pengelola kepegawaian menjalankan analisis terlebih dahulu.

## 13.6 Alur Eksepsi AI

Tidak ada inferensi AI baru.

Jika hasil clustering berasal dari proses yang gagal:

1. Sistem tidak menggunakan hasil gagal sebagai sumber rekap.
2. Sistem meminta hasil clustering yang valid.

---

# 14. Use Case UC-10 — Melihat Riwayat Analisis ★

## 14.1 Identitas

| Item | Keterangan |
|---|---|
| ID | UC-10 |
| Nama | Melihat Riwayat Analisis |
| Aktor Utama | Pengelola Kepegawaian `[ASUMSI]` |
| Aktor Pendukung | Database `[ASUMSI]` |
| User Story | US-11 |
| FR | FR-12 |
| Prioritas | Should |

## 14.2 Precondition

Terdapat hasil analisis yang telah disimpan `[ASUMSI]`.

## 14.3 Postcondition

Pengelola kepegawaian dapat menelusuri hasil analisis sebelumnya.

## 14.4 Alur Utama

1. Pengelola kepegawaian meminta riwayat analisis.
2. Sistem mengambil hasil analisis yang tersimpan.
3. Sistem memeriksa validitas hasil.
4. Sistem menyediakan hasil analisis sebelumnya.
5. Pengelola kepegawaian memilih hasil yang ingin ditelusuri.
6. Sistem memberikan hasil analisis tersebut.
7. Use Case selesai.

## 14.5 Alur Alternatif

### A1 — Riwayat Tidak Tersedia

1. Pengelola kepegawaian meminta riwayat.
2. Sistem tidak menemukan hasil analisis sebelumnya.
3. Sistem memberikan informasi bahwa riwayat belum tersedia.
4. Use Case selesai.

## 14.6 Alur Eksepsi AI

### E1 — Hasil Analisis Sebelumnya Tidak Valid

1. Sistem menemukan hasil analisis dengan status gagal.
2. Sistem tidak memperlakukan hasil tersebut sebagai hasil valid.
3. Sistem memberikan informasi status hasil kepada pengelola kepegawaian.
4. Pengelola kepegawaian dapat menjalankan analisis baru.

### E2 — Low Confidence

Tidak berlaku pada hasil K-Means standar karena SRS tidak menetapkan confidence score.

Jika layanan AI nantinya menyediakan confidence score:

1. Sistem membaca confidence score yang tersimpan.
2. Sistem membandingkan dengan threshold `[ASUMSI-07]`.
3. Hasil di bawah threshold ditandai membutuhkan pemeriksaan.
4. Hasil tidak digunakan sebagai dasar keputusan otomatis.

---

# 15. Aturan Umum Penanganan Kegagalan AI

## 15.1 Input Berkualitas Rendah

Sistem harus memeriksa kelayakan data sebelum proses AI dilakukan.

Jika data tidak memenuhi kebutuhan:

1. Data tidak dikirim ke layanan AI.
2. Sistem memberikan informasi kegagalan validasi.
3. Pengguna memperbaiki data.
4. Proses dapat diulang.

---

## 15.2 Timeout

Jika layanan AI tidak memberikan respons dalam batas waktu yang ditentukan:

1. Sistem menghentikan proses menunggu.
2. Sistem tidak menggunakan hasil yang tidak lengkap.
3. Sistem mencatat proses sebagai gagal.
4. Sistem memberikan informasi kepada pengguna.
5. Pengguna dapat mencoba kembali.

Nilai timeout final:

`[ASUMSI-05]`

---

## 15.3 Gagal Koneksi

Jika koneksi ke layanan AI gagal:

1. Sistem tidak menganggap proses berhasil.
2. Sistem tidak membuat hasil clustering berdasarkan data yang tidak lengkap.
3. Sistem memberikan informasi kegagalan.
4. Pengguna dapat mencoba kembali.

---

## 15.4 Low Confidence

Pada SRS saat ini, K-Means tidak memiliki confidence score.

Karena itu:

- Tidak ada threshold confidence yang dapat ditetapkan.
- Tidak boleh mengarang threshold.
- Tidak boleh menyebut Silhouette Score sebagai confidence score.

Jika layanan AI yang dipilih pada tahap berikutnya menyediakan confidence score, kebutuhan tersebut harus ditambahkan atau direvisi dalam SRS sebelum implementasi.

---

# 16. Matriks Traceability

| Use Case | User Story | FR | Fitur PRD |
|---|---|---|---|
| UC-01 | US-02 | FR-02 | Pengelolaan data presensi |
| UC-02 | US-03 | FR-03 | Data presensi |
| UC-03 | US-04 | FR-04 | Data presensi |
| UC-04 | US-05 | FR-05 | ★ K-Means Clustering |
| UC-05 | US-06 | FR-06 | ★ Hasil klasterisasi |
| UC-06 | US-07 | FR-07, FR-09 | Hasil analisis |
| UC-07 | US-08 | FR-08 | ★ Silhouette Score |
| UC-08 | US-09 | FR-10 | Filter periode |
| UC-09 | US-10 | FR-11 | Rekap hasil klaster |
| UC-10 | US-11 | FR-12 | Riwayat hasil analisis |

---

# 17. Checklist Review Tahap 2

## Aktor

- [x] Aktor utama berasal dari persona pada tahap sebelumnya.
- [ ] Persona masih perlu divalidasi karena masih berstatus `[ASUMSI]`.
- [x] Layanan K-Means dicatat sebagai aktor pendukung logis.
- [x] Database dicatat sebagai aktor pendukung.

## Alur AI

- [x] Alur utama K-Means dijelaskan secara berurutan.
- [x] Validasi input sebelum AI dilakukan.
- [x] Timeout AI ditangani.
- [x] Gagal koneksi AI ditangani.
- [x] Low confidence dibahas.
- [x] Tidak menganggap Silhouette Score sebagai confidence score.
- [x] Tidak membuat threshold confidence tanpa sumber.

## Kualitas Input

- [x] Data tidak valid/tidak lengkap ditangani sebelum proses AI.
- [x] Sistem tidak menggunakan hasil AI yang tidak lengkap.
- [ ] Penanganan input "buram" tidak diterapkan karena input yang didukung SRS berupa data numerik presensi, bukan gambar.

## Alur Use Case

- [x] Setiap alur memiliki precondition.
- [x] Setiap alur memiliki postcondition.
- [x] Langkah utama diberi nomor.
- [x] Alur alternatif dipisahkan dari alur utama.
- [x] Eksepsi AI dipisahkan dari alur alternatif.
- [x] Tidak membahas desain UI.
- [x] Tidak membahas source code.
- [x] Tidak membahas arsitektur HLD/LLD.

---

# 18. Status Dokumen

**Status: DRAFT**

Dokumen Use Case masih membutuhkan validasi terhadap:

1. Persona pengguna sebenarnya.
2. Layanan AI yang benar-benar digunakan.
3. Apakah K-Means dijalankan sebagai layanan eksternal atau bagian dari sistem.
4. Target latensi final.
5. Nilai timeout.
6. Mekanisme dan threshold confidence apabila layanan AI menyediakan confidence score.
7. Dataset aktual.
8. Kebutuhan fitur Should dari stakeholder.

> **Catatan penting:** SRS saat ini hanya mendukung K-Means dengan input persentase kehadiran dan persentase pemenuhan jam kerja. Karena itu, skenario "data buram" dan "low confidence" tidak dapat dianggap sebagai karakteristik aktual sistem tanpa adanya perubahan requirement pada SRS.
