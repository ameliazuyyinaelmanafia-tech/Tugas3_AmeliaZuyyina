# DRAF USER STORIES

## Sistem Analisis Kedisiplinan Pegawai Berbasis K-Means

---

# 1. Tabel User Story

> **Catatan:** Persona utama pada dokumen sebelumnya masih berstatus `[ASUMSI]`. Oleh karena itu, peran di bawah ini perlu divalidasi kembali melalui wawancara atau konfirmasi stakeholder.

| ID Story | Narasi User Story | FR Asal | Prioritas | Kategori |
|---|---|---|---|---|
| US-01 | Sebagai **pengelola kepegawaian [ASUMSI]**, saya ingin masuk ke sistem menggunakan akun yang valid, agar saya dapat mengakses fungsi yang berkaitan dengan pengelolaan dan analisis data presensi. | FR-01 | Must | Fitur Inti |
| US-02 | Sebagai **pengelola kepegawaian [ASUMSI]**, saya ingin memasukkan data presensi pegawai, agar data tersebut dapat digunakan sebagai dasar analisis kedisiplinan. | FR-02 | Must | Fitur Inti |
| US-03 | Sebagai **pengelola kepegawaian [ASUMSI]**, saya ingin menggunakan persentase kehadiran sebagai data analisis, agar tingkat kehadiran pegawai dapat menjadi bagian dari pengelompokan kedisiplinan. | FR-03 | Must | Fitur Inti |
| US-04 | Sebagai **pengelola kepegawaian [ASUMSI]**, saya ingin menggunakan persentase pemenuhan jam kerja sebagai data analisis, agar pemenuhan jam kerja dapat menjadi bagian dari pengelompokan kedisiplinan. | FR-04 | Must | Fitur Inti |
| US-05 | Sebagai **pengelola kepegawaian [ASUMSI]**, saya ingin menjalankan **K-Means Clustering ★** pada data presensi, agar data pegawai dapat dikelompokkan berdasarkan kemiripan karakteristik kehadiran dan pemenuhan jam kerja. | FR-05 | Must | Fitur AI ★ |
| US-06 | Sebagai **pengelola kepegawaian [ASUMSI]**, saya ingin memperoleh kelompok hasil K-Means **★**, agar saya dapat mengetahui pengelompokan tingkat kedisiplinan pegawai. | FR-06 | Must | Fitur AI ★ |
| US-07 | Sebagai **pengelola kepegawaian [ASUMSI]**, saya ingin melihat hasil pengelompokan kedisiplinan, agar saya dapat menggunakan informasi tersebut untuk membantu monitoring dan evaluasi. | FR-07, FR-09 | Must | Fitur AI ★ |
| US-08 | Sebagai **pengelola kepegawaian [ASUMSI]**, saya ingin melihat nilai **Silhouette Score ★**, agar saya dapat mengetahui kualitas hasil pengelompokan yang dihasilkan. | FR-08 | Must | Fitur AI ★ |
| US-09 | Sebagai **pengelola kepegawaian [ASUMSI]**, saya ingin memilih periode data presensi yang akan dianalisis, agar hasil pengelompokan sesuai dengan periode yang ingin saya evaluasi. | FR-10 | Should | Fitur Inti |
| US-10 | Sebagai **pengelola kepegawaian [ASUMSI]**, saya ingin melihat jumlah pegawai pada setiap kelompok, agar saya dapat mengetahui distribusi hasil pengelompokan kedisiplinan. | FR-11 | Should | Fitur AI ★ |
| US-11 | Sebagai **pengelola kepegawaian [ASUMSI]**, saya ingin melihat kembali hasil analisis sebelumnya, agar saya dapat membandingkan atau menelusuri hasil pengelompokan yang pernah dilakukan. | FR-12 | Should | Fitur AI ★ |

---

# 2. Pemecahan Epic

Beberapa FR pada SRS memiliki cakupan yang cukup besar sehingga perlu dipecah menjadi beberapa User Story agar lebih kecil dan dapat diuji secara mandiri.

## 2.1 FR-02 — Pengelolaan Data Presensi

FR-02 memiliki cakupan pengelolaan data yang cukup luas.

Untuk User Story, kebutuhan utama difokuskan terlebih dahulu pada penyediaan data presensi untuk analisis.

### US-02 — Menyediakan Data Presensi

> Sebagai pengelola kepegawaian `[ASUMSI]`, saya ingin memasukkan data presensi pegawai, agar data tersebut dapat digunakan sebagai dasar analisis kedisiplinan.

**Status:** Cukup kecil untuk prototype.

---

## 2.2 FR-05 — K-Means Clustering ★

FR-05 merupakan fitur AI utama dan dapat dianggap sebagai Epic apabila mencakup seluruh proses analisis.

Untuk menjaga story tetap kecil, prosesnya dipisahkan menjadi beberapa story.

### US-05 — Menjalankan Analisis ★

> Sebagai pengelola kepegawaian `[ASUMSI]`, saya ingin menjalankan K-Means Clustering pada data presensi, agar data pegawai dapat dikelompokkan berdasarkan kemiripan karakteristik kehadiran dan pemenuhan jam kerja.

### US-06 — Mendapatkan Hasil Cluster ★

> Sebagai pengelola kepegawaian `[ASUMSI]`, saya ingin memperoleh kelompok hasil K-Means, agar saya dapat mengetahui pengelompokan tingkat kedisiplinan pegawai.

### US-08 — Mengevaluasi Hasil ★

> Sebagai pengelola kepegawaian `[ASUMSI]`, saya ingin melihat nilai Silhouette Score, agar saya dapat mengetahui kualitas hasil pengelompokan yang dihasilkan.

Ketiga story tersebut memiliki tujuan yang berbeda dan dapat diuji secara terpisah.

---

# 3. Evaluasi Prinsip INVEST

| ID | Independent | Negotiable | Valuable | Estimable | Small | Testable | Evaluasi |
|---|---|---|---|---|---|---|---|
| US-01 | Ya | Ya | Ya | Ya | Ya | Ya | Memenuhi INVEST |
| US-02 | Ya | Ya | Ya | Ya | Ya | Ya | Memenuhi INVEST |
| US-03 | Ya | Ya | Ya | Ya | Ya | Ya | Memenuhi INVEST |
| US-04 | Ya | Ya | Ya | Ya | Ya | Ya | Memenuhi INVEST |
| US-05 | Cukup | Ya | Ya | Ya | Ya | Ya | Cukup kecil untuk prototype, tetapi perlu batasan dataset |
| US-06 | Ya | Ya | Ya | Ya | Ya | Ya | Memenuhi INVEST |
| US-07 | Ya | Ya | Ya | Ya | Ya | Ya | Memenuhi INVEST |
| US-08 | Ya | Ya | Ya | Ya | Ya | Ya | Memenuhi INVEST |
| US-09 | Ya | Ya | Ya | Ya | Ya | Ya | Memenuhi INVEST |
| US-10 | Ya | Ya | Ya | Ya | Ya | Ya | Memenuhi INVEST |
| US-11 | Ya | Ya | Ya | Ya | Ya | Ya | Memenuhi INVEST |

### Kesimpulan INVEST

Secara umum, User Story sudah cukup **Small** dan **Testable** untuk kebutuhan prototype satu semester.

Story yang paling perlu diperhatikan adalah **US-05 (K-Means)** karena merupakan fitur AI utama. Story tersebut harus tetap dibatasi pada fungsi pengelompokan data presensi dan tidak diperluas menjadi prediksi, penilaian kinerja, atau pengambilan keputusan otomatis.

---

# 4. Kriteria Testability

## US-01 — Login

**Kondisi:** Akun valid digunakan.

**Hasil yang diharapkan:** Pengelola kepegawaian dapat mengakses fungsi sistem.

---

## US-02 — Data Presensi

**Kondisi:** Data presensi diberikan.

**Hasil yang diharapkan:** Data tersedia untuk digunakan dalam proses analisis.

---

## US-03 — Persentase Kehadiran

**Kondisi:** Data memiliki persentase kehadiran.

**Hasil yang diharapkan:** Persentase kehadiran dapat digunakan sebagai variabel analisis.

---

## US-04 — Persentase Pemenuhan Jam Kerja

**Kondisi:** Data memiliki persentase pemenuhan jam kerja.

**Hasil yang diharapkan:** Persentase pemenuhan jam kerja dapat digunakan sebagai variabel analisis.

---

## US-05 — K-Means ★

**Kondisi:** Data presensi yang diperlukan tersedia.

**Hasil yang diharapkan:** Proses K-Means menghasilkan pengelompokan data.

---

## US-06 — Hasil Cluster ★

**Kondisi:** Proses K-Means selesai.

**Hasil yang diharapkan:** Tersedia tiga kelompok hasil clustering sesuai baseline penelitian.

---

## US-07 — Hasil Pengelompokan ★

**Kondisi:** Hasil clustering tersedia.

**Hasil yang diharapkan:** Pengelola kepegawaian dapat mengetahui hasil pengelompokan kedisiplinan.

---

## US-08 — Silhouette Score ★

**Kondisi:** Hasil clustering tersedia.

**Hasil yang diharapkan:** Nilai Silhouette Score dapat diperoleh.

---

## US-09 — Filter Periode

**Kondisi:** Periode analisis dipilih.

**Hasil yang diharapkan:** Data yang digunakan sesuai dengan periode yang dipilih.

---

## US-10 — Rekap Cluster ★

**Kondisi:** Hasil clustering tersedia.

**Hasil yang diharapkan:** Jumlah anggota pada setiap kelompok dapat diketahui.

---

## US-11 — Riwayat Analisis ★

**Kondisi:** Hasil analisis sebelumnya tersedia.

**Hasil yang diharapkan:** Hasil analisis sebelumnya dapat ditelusuri kembali.

---

# 5. Hubungan User Story dengan Fitur AI

## Fitur AI Utama

**K-Means Clustering ★**

Fungsinya adalah mengelompokkan data berdasarkan karakteristik:

1. Persentase kehadiran.
2. Persentase pemenuhan jam kerja.

## User Story yang Berkaitan dengan AI

| User Story | Fungsi AI |
|---|---|
| US-03 | Menyediakan persentase kehadiran sebagai data analisis |
| US-04 | Menyediakan persentase pemenuhan jam kerja sebagai data analisis |
| US-05 | Menjalankan K-Means |
| US-06 | Menghasilkan kelompok |
| US-07 | Melihat hasil pengelompokan |
| US-08 | Mengevaluasi hasil dengan Silhouette Score |
| US-10 | Melihat distribusi anggota kelompok |
| US-11 | Menelusuri hasil analisis sebelumnya |

Fitur AI dipisahkan dari fitur pengelolaan data biasa agar fungsi analitik dapat dibedakan dari fungsi CRUD.

---

# 6. Traceability User Story

| User Story | FR SRS | Fitur PRD |
|---|---|---|
| US-01 | FR-01 | Login pengguna |
| US-02 | FR-02 | Pengelolaan data presensi |
| US-03 | FR-03 | Data presensi |
| US-04 | FR-04 | Data presensi |
| US-05 | FR-05 | ★ K-Means Clustering |
| US-06 | FR-06 | ★ Hasil klasterisasi |
| US-07 | FR-07, FR-09 | Hasil analisis |
| US-08 | FR-08 | ★ Silhouette Score |
| US-09 | FR-10 | Filter periode |
| US-10 | FR-11 | Rekap hasil klaster |
| US-11 | FR-12 | Riwayat hasil analisis |

---

# 7. Checklist Review Tahap 1

## 7.1 Persona

- [ ] Peran pengguna sudah divalidasi melalui wawancara/observasi.
- [x] Peran tidak menggunakan istilah umum seperti "pengguna".
- [ ] Peran final perlu dikonfirmasi karena persona pada PRD/SRS masih `[ASUMSI]`.

## 7.2 Manfaat

- [x] Setiap story menggunakan format "agar".
- [x] Manfaat tidak sekadar mengulang aksi fitur.
- [x] Manfaat berhubungan dengan monitoring, evaluasi, atau pemanfaatan data.

## 7.3 Fitur AI

- [x] Fitur AI diberi tanda ★.
- [x] K-Means dipisahkan dari fitur CRUD.
- [x] Silhouette Score dipisahkan sebagai kebutuhan evaluasi AI.
- [x] Input AI berasal dari variabel yang didukung penelitian.
- [x] Tidak ada story untuk prediksi atau keputusan otomatis.

## 7.4 INVEST

- [x] Story memiliki tujuan yang jelas.
- [x] Story dapat diuji.
- [x] Story cukup kecil untuk prototype.
- [x] Epic K-Means sudah dipecah menjadi story yang lebih kecil.

---

# 8. Status Dokumen

**Status:** DRAFT

User Stories masih perlu divalidasi berdasarkan:

1. Persona pengguna yang sebenarnya.
2. Hasil wawancara atau observasi stakeholder.
3. Data presensi yang tersedia.
4. Platform final.
5. Kebutuhan fitur Should yang benar-benar diperlukan.
6. Batasan prototype satu semester.

Sebelum validasi selesai, story yang menggunakan `[ASUMSI]` belum dapat dianggap sebagai kebutuhan pengguna yang final.
