# DRAFT ACCEPTANCE CRITERIA

## Sistem Analisis Kedisiplinan Pegawai Berbasis K-Means

---

# 1. Informasi Dokumen

| Item | Keterangan |
|---|---|
| Produk | Sistem Analisis Kedisiplinan Pegawai Berbasis K-Means |
| Dokumen | Acceptance Criteria Tahap 4 |
| Acuan | User Story, Use Case, dan SRS |
| Fokus | Given-When-Then / Gherkin |
| Fitur AI | ★ K-Means Clustering |
| Status | Draft |

> **Catatan:** Nilai numerik NFR seperti batas waktu respons, target akurasi, threshold, dan pesan error final belum tersedia pada konteks sumber. Placeholder `[NFR-XX]` dipertahankan agar tidak membuat angka yang tidak didukung SRS.

---

# 2. User Story dan Acceptance Criteria

## US-01 — Login

**FR Asal:** FR-01  
**Prioritas:** Must  
**Kategori:** Fitur Inti

### Scenario 1: Login dengan akun valid

**Given** sistem tersedia dan pengguna memiliki akun dengan kredensial yang valid  
**When** pengelola kepegawaian memasukkan kredensial yang valid dan melakukan autentikasi  
**Then** sistem memberikan akses ke fungsi yang diizinkan untuk pengelola kepegawaian

**Metode uji:** Integration Test / User Acceptance Test

### Scenario 2: Login dengan kredensial tidak valid

**Given** sistem tersedia dan kredensial yang diberikan tidak valid  
**When** pengelola kepegawaian melakukan autentikasi  
**Then** sistem menolak autentikasi dan menampilkan pesan kesalahan sesuai `[NFR-PESAN-ERROR-01]`

**Metode uji:** Integration Test

---

# US-02 — Memasukkan Data Presensi

**FR Asal:** FR-02  
**Prioritas:** Must  
**Kategori:** Fitur Inti

### Scenario 1: Data presensi valid

**Given** data presensi memiliki seluruh informasi yang diperlukan untuk analisis  
**When** pengelola kepegawaian memasukkan data presensi  
**Then** sistem menerima dan menyimpan data tersebut sebagai data yang dapat digunakan untuk analisis

**Metode uji:** Integration Test

### Scenario 2: Data presensi tidak lengkap

**Given** data presensi tidak memiliki salah satu informasi yang diperlukan  
**When** pengelola kepegawaian memasukkan data tersebut  
**Then** sistem menolak data yang tidak memenuhi syarat dan menampilkan pesan perbaikan sesuai `[NFR-PESAN-ERROR-02]`

**Metode uji:** Unit Test / Integration Test

---

# US-03 — Menggunakan Persentase Kehadiran

**FR Asal:** FR-03  
**Prioritas:** Must  
**Kategori:** Fitur Inti

### Scenario 1: Persentase kehadiran tersedia

**Given** data presensi memiliki data yang diperlukan untuk memperoleh persentase kehadiran  
**When** sistem menyiapkan data untuk analisis  
**Then** persentase kehadiran tersedia sebagai variabel analisis

**Metode uji:** Unit Test

### Scenario 2: Data kehadiran tidak tersedia

**Given** data presensi tidak memiliki informasi yang diperlukan untuk memperoleh persentase kehadiran  
**When** sistem melakukan validasi data analisis  
**Then** sistem menandai data sebagai tidak memenuhi kebutuhan analisis dan tidak melanjutkan proses K-Means

**Metode uji:** Unit Test / Integration Test

---

# US-04 — Menggunakan Persentase Pemenuhan Jam Kerja

**FR Asal:** FR-04  
**Prioritas:** Must  
**Kategori:** Fitur Inti

### Scenario 1: Data pemenuhan jam kerja tersedia

**Given** data presensi memiliki informasi pemenuhan jam kerja  
**When** sistem menyiapkan data untuk analisis  
**Then** persentase pemenuhan jam kerja tersedia sebagai variabel analisis

**Metode uji:** Unit Test

### Scenario 2: Data pemenuhan jam kerja tidak tersedia

**Given** data presensi tidak memiliki informasi pemenuhan jam kerja  
**When** sistem melakukan validasi data analisis  
**Then** sistem menandai data sebagai tidak memenuhi kebutuhan analisis dan tidak melanjutkan proses K-Means

**Metode uji:** Unit Test / Integration Test

---

# US-05 — Menjalankan K-Means ★

**FR Asal:** FR-05  
**Prioritas:** Must  
**Kategori:** Fitur AI ★

### Scenario 1: Happy Path — K-Means berhasil

**Given** data persentase kehadiran dan persentase pemenuhan jam kerja tersedia dan valid  
**When** pengelola kepegawaian menjalankan analisis K-Means  
**Then** sistem menghasilkan pengelompokan data dan proses selesai dalam waktu <= `[NFR-LATENSI-AI]`

**Metode uji:** Integration Test

### Scenario 2: Edge Case — Data tidak memenuhi syarat

**Given** sebagian data analisis tidak lengkap atau tidak valid  
**When** pengelola kepegawaian menjalankan K-Means  
**Then** sistem tidak mengirim data yang tidak valid untuk proses analisis, menampilkan pesan perbaikan `[NFR-PESAN-ERROR-03]`, dan tidak menyatakan analisis berhasil

**Metode uji:** Unit Test / Integration Test

### Scenario 3: Timeout layanan AI

**Given** data analisis valid dan proses K-Means telah dimulai  
**When** layanan K-Means tidak memberikan respons sampai batas `[NFR-TIMEOUT-AI]`  
**Then** sistem menghentikan penantian, menandai proses sebagai gagal, dan menampilkan pesan error sesuai `[NFR-PESAN-ERROR-04]`

**Metode uji:** Integration Test

### Scenario 4: Koneksi layanan AI gagal

**Given** data analisis valid  
**When** sistem gagal terhubung ke layanan K-Means  
**Then** sistem tidak menyimpan hasil sebagai hasil analisis berhasil dan menawarkan mekanisme fallback yang ditentukan pada SRS

**Metode uji:** Integration Test

---

# US-06 — Memperoleh Hasil Pengelompokan ★

**FR Asal:** FR-06  
**Prioritas:** Must  
**Kategori:** Fitur AI ★

### Scenario 1: Hasil clustering tersedia

**Given** proses K-Means berhasil dilakukan terhadap data yang valid  
**When** sistem menerima hasil clustering  
**Then** sistem menyediakan hasil pengelompokan untuk digunakan dalam analisis kedisiplinan

**Metode uji:** Integration Test

### Scenario 2: Hasil clustering tidak lengkap

**Given** proses K-Means menghasilkan data pengelompokan yang tidak lengkap  
**When** sistem memvalidasi hasil clustering  
**Then** sistem menandai hasil sebagai tidak lengkap dan tidak menyatakannya sebagai hasil analisis yang berhasil

**Metode uji:** Integration Test

### Scenario 3: Proses AI timeout

**Given** sistem telah mengirim data valid untuk proses K-Means  
**When** respons tidak diterima sampai `[NFR-TIMEOUT-AI]`  
**Then** sistem tidak menghasilkan hasil clustering final dan menampilkan pesan error `[NFR-PESAN-ERROR-04]`

**Metode uji:** Integration Test

---

# US-07 — Melihat Hasil Analisis ★

**FR Asal:** FR-07, FR-09  
**Prioritas:** Must  
**Kategori:** Fitur AI ★

### Scenario 1: Hasil analisis tersedia

**Given** hasil clustering telah berhasil disimpan  
**When** pengelola kepegawaian meminta hasil analisis  
**Then** sistem menampilkan informasi hasil pengelompokan yang tersimpan

**Metode uji:** Integration Test / User Acceptance Test

### Scenario 2: Hasil analisis belum tersedia

**Given** belum terdapat hasil clustering yang valid  
**When** pengelola kepegawaian meminta hasil analisis  
**Then** sistem menyatakan bahwa hasil analisis belum tersedia dan tidak menampilkan hasil yang tidak valid

**Metode uji:** Integration Test

### Scenario 3: Hasil analisis berasal dari proses gagal

**Given** proses K-Means sebelumnya berstatus gagal  
**When** pengelola kepegawaian meminta hasil analisis  
**Then** sistem tidak memperlakukan proses gagal sebagai hasil analisis valid

**Metode uji:** Integration Test

---

# US-08 — Melihat Silhouette Score ★

**FR Asal:** FR-08  
**Prioritas:** Must  
**Kategori:** Fitur AI ★

### Scenario 1: Silhouette Score berhasil dihitung

**Given** hasil clustering valid dan memenuhi syarat evaluasi  
**When** sistem melakukan evaluasi hasil clustering  
**Then** sistem menghasilkan dan menyimpan nilai Silhouette Score

**Metode uji:** Unit Test / Integration Test

### Scenario 2: Data tidak dapat dievaluasi

**Given** hasil clustering tidak memenuhi syarat untuk perhitungan Silhouette Score  
**When** sistem melakukan evaluasi  
**Then** sistem tidak menghasilkan nilai Silhouette Score yang tidak valid dan menampilkan pesan sesuai `[NFR-PESAN-ERROR-05]`

**Metode uji:** Unit Test

### Scenario 3: Evaluasi gagal

**Given** proses clustering telah menghasilkan data tetapi proses evaluasi mengalami kegagalan  
**When** sistem mencoba menghitung Silhouette Score  
**Then** sistem mencatat evaluasi sebagai gagal dan tidak menampilkan nilai evaluasi sebagai hasil yang valid

**Metode uji:** Integration Test

> **Catatan:** Silhouette Score merupakan metrik evaluasi clustering dan bukan confidence score.

---

# US-09 — Memilih Periode Analisis

**FR Asal:** FR-10  
**Prioritas:** Should  
**Kategori:** Fitur Inti

### Scenario 1: Periode memiliki data

**Given** data presensi tersedia pada periode yang dipilih  
**When** pengelola kepegawaian memilih periode tersebut  
**Then** sistem menggunakan data dari periode tersebut sebagai data analisis

**Metode uji:** Integration Test / User Acceptance Test

### Scenario 2: Periode tidak memiliki data

**Given** tidak terdapat data presensi pada periode yang dipilih  
**When** pengelola kepegawaian memilih periode tersebut  
**Then** sistem menyatakan bahwa data tidak tersedia dan tidak menjalankan analisis

**Metode uji:** Integration Test

---

# US-10 — Melihat Rekap Hasil Clustering ★

**FR Asal:** FR-11  
**Prioritas:** Should  
**Kategori:** Fitur AI ★

### Scenario 1: Rekap berhasil ditampilkan

**Given** hasil clustering valid tersedia  
**When** pengelola kepegawaian meminta rekap hasil  
**Then** sistem menampilkan jumlah anggota pada setiap kelompok berdasarkan hasil clustering

**Metode uji:** Integration Test / User Acceptance Test

### Scenario 2: Hasil clustering tidak tersedia

**Given** tidak terdapat hasil clustering yang valid  
**When** pengelola kepegawaian meminta rekap  
**Then** sistem tidak menampilkan rekap dari data yang tidak valid dan memberikan informasi bahwa rekap belum tersedia

**Metode uji:** Integration Test

### Scenario 3: Hasil clustering tidak lengkap

**Given** hasil clustering tidak memiliki data anggota yang lengkap  
**When** sistem menghitung rekap  
**Then** sistem tidak menyatakan rekap sebagai hasil final dan memberikan informasi mengenai kegagalan tersebut

**Metode uji:** Integration Test

---

# US-11 — Melihat Riwayat Analisis ★

**FR Asal:** FR-12  
**Prioritas:** Should  
**Kategori:** Fitur AI ★

### Scenario 1: Riwayat analisis tersedia

**Given** terdapat hasil analisis yang telah tersimpan  
**When** pengelola kepegawaian meminta riwayat analisis  
**Then** sistem menyediakan hasil analisis sebelumnya untuk ditelusuri

**Metode uji:** Integration Test / User Acceptance Test

### Scenario 2: Riwayat belum tersedia

**Given** belum terdapat hasil analisis yang tersimpan  
**When** pengelola kepegawaian meminta riwayat  
**Then** sistem menyatakan bahwa riwayat analisis belum tersedia

**Metode uji:** Integration Test

### Scenario 3: Riwayat memiliki hasil gagal

**Given** terdapat proses analisis sebelumnya dengan status gagal  
**When** pengelola kepegawaian membuka riwayat  
**Then** sistem mempertahankan status gagal dan tidak memperlakukan hasil tersebut sebagai hasil analisis valid

**Metode uji:** Integration Test

---

# 3. Matriks Acceptance Criteria terhadap FR

| User Story | FR | Happy Path | Edge Case | Timeout/Gagal | Metode Utama |
|---|---|---:|---:|---:|---|
| US-01 | FR-01 | ✓ | ✓ | - | Integration Test |
| US-02 | FR-02 | ✓ | ✓ | - | Integration Test |
| US-03 | FR-03 | ✓ | ✓ | - | Unit Test |
| US-04 | FR-04 | ✓ | ✓ | - | Unit Test |
| US-05 ★ | FR-05 | ✓ | ✓ | ✓ | Integration Test |
| US-06 ★ | FR-06 | ✓ | ✓ | ✓ | Integration Test |
| US-07 ★ | FR-07, FR-09 | ✓ | ✓ | ✓ | Integration/UAT |
| US-08 ★ | FR-08 | ✓ | ✓ | ✓ | Unit/Integration |
| US-09 | FR-10 | ✓ | ✓ | - | Integration/UAT |
| US-10 ★ | FR-11 | ✓ | ✓ | - | Integration/UAT |
| US-11 ★ | FR-12 | ✓ | ✓ | - | Integration/UAT |

---

# 4. Acceptance Criteria Khusus Fitur AI

## 4.1 Validasi Input

**Given** data akan digunakan untuk proses K-Means  
**When** sistem melakukan validasi awal  
**Then** data yang tidak memenuhi persyaratan tidak dikirim ke proses AI dan sistem menampilkan pesan `[NFR-PESAN-ERROR-03]`

---

## 4.2 Batas Latensi

**Given** data analisis valid dan layanan AI tersedia  
**When** sistem menjalankan proses K-Means  
**Then** sistem menerima hasil dalam waktu <= `[NFR-LATENSI-AI]`

---

## 4.3 Timeout

**Given** proses K-Means telah dimulai  
**When** layanan AI tidak memberikan respons sampai `[NFR-TIMEOUT-AI]`  
**Then** sistem menghentikan penantian dan menampilkan pesan `[NFR-PESAN-ERROR-04]`

---

## 4.4 Kegagalan Koneksi

**Given** data analisis valid  
**When** koneksi ke layanan AI gagal  
**Then** sistem menandai proses sebagai gagal, tidak menyimpan hasil sebagai hasil valid, dan menyediakan jalur pemulihan sesuai Use Case

---

## 4.5 Evaluasi Hasil

**Given** hasil clustering berhasil diperoleh  
**When** sistem melakukan evaluasi clustering  
**Then** sistem menghasilkan Silhouette Score apabila data memenuhi persyaratan perhitungan

---

# 5. Catatan tentang Akurasi dan Confidence

K-Means merupakan metode clustering. Berdasarkan requirement yang tersedia:

- Metrik evaluasi yang disebutkan adalah **Silhouette Score**.
- SRS tidak menetapkan accuracy dalam bentuk persentase untuk K-Means.
- SRS juga belum menetapkan confidence score.
- Karena itu, acceptance criteria tidak menetapkan angka accuracy atau confidence threshold yang tidak memiliki sumber.

Jika SRS final menetapkan target tertentu, acceptance criteria harus diperbarui menjadi:

```text
Then hasil memenuhi nilai [NFR-AKURASI] yang telah ditetapkan
