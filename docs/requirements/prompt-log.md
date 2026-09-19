# LOG PENGEMBANGAN REQUIREMENTS

## Sistem Analisis Kedisiplinan Pegawai Berbasis K-Means

**Dokumen terkait:**
- `prd.md` — Product Requirement Document
- `srs.md` — Software Requirement Specification
- `log.md` — Log perubahan dan keputusan requirements

---

# 1. Informasi Dokumen

| Item | Keterangan |
|---|---|
| Nama Produk | Sistem Analisis Kedisiplinan Pegawai Berbasis K-Means |
| Dokumen Acuan | `prd.md` dan `srs.md` |
| Platform | Website `[ASUMSI-13]` |
| Metode Analisis | K-Means Clustering |
| Evaluasi Clustering | Silhouette Score |
| Prioritas | MoSCoW |
| Acuan Kualitas | ISO/IEC 25010 |
| Status | Draft |
| Durasi Prototype | 1 semester |

---

# 2. Tujuan Log

`log.md` digunakan untuk mencatat:

1. Perubahan requirements.
2. Keputusan yang diambil selama pengembangan.
3. Asumsi yang masih perlu divalidasi.
4. Hasil validasi terhadap PRD dan SRS.
5. Perubahan prioritas fitur.
6. Permasalahan requirements yang ditemukan.
7. Hubungan antara kebutuhan, fitur, dan bukti riset.

Log ini tidak digunakan untuk mencatat detail implementasi seperti struktur database, source code, API, atau arsitektur sistem.

---

# 3. Baseline Requirements

Requirements awal yang menjadi dasar pengembangan berasal dari `prd.md` dan kemudian diturunkan menjadi `srs.md`.

## 3.1 Problem Utama

Pihak pengelola kepegawaian membutuhkan cara yang lebih terstruktur untuk memahami tingkat kedisiplinan pegawai berdasarkan data presensi, karena data presensi yang tersedia belum dimanfaatkan secara optimal untuk menghasilkan informasi pengelompokan kedisiplinan.

Status:

**Ditetapkan sebagai baseline problem statement.**

---

# 4. Fitur Utama

| ID | Fitur | Prioritas | Status |
|---|---|---|---|
| F-01 | Login pengguna | Must | Draft |
| F-02 | Pengelolaan data presensi | Must | Draft |
| F-03 | ★ K-Means Clustering | Must | Draft |
| F-04 | ★ Hasil pengelompokan | Must | Draft |
| F-05 | ★ Silhouette Score | Must | Draft |
| F-06 | Tampilan hasil analisis | Must | Draft |
| F-07 | Filter periode | Should | Draft |
| F-08 | Rekap hasil klaster | Should | Draft |
| F-09 | Riwayat analisis | Should | Draft |
| F-10 | Export hasil analisis | Could | Draft |
| F-11 | Grafik sederhana | Could | Draft |

---

# 5. Log Keputusan Requirements

## LOG-001 — Penetapan Fokus Produk

**Tanggal:** `[ISI TANGGAL]`

### Keputusan

Produk difokuskan pada analisis tingkat kedisiplinan pegawai menggunakan data presensi.

### Alasan

PRD menetapkan permasalahan utama berupa belum optimalnya pemanfaatan data presensi untuk menghasilkan informasi pengelompokan kedisiplinan.

### Dampak

Scope produk tidak diperluas menjadi sistem informasi kepegawaian secara keseluruhan.

**Status:** Disetujui

---

## LOG-002 — Penetapan K-Means sebagai Fitur AI

**Tanggal:** `[ISI TANGGAL]`

### Keputusan

K-Means digunakan sebagai metode utama untuk melakukan pengelompokan data kedisiplinan.

### Alasan

Penelitian sumber menggunakan K-Means untuk mengelompokkan pegawai berdasarkan data persentase kehadiran dan pemenuhan jam kerja.

### Dampak

K-Means menjadi fitur:

**★ F-03 — K-Means Clustering**

**Status:** Disetujui

---

## LOG-003 — Penetapan Variabel Input AI

**Tanggal:** `[ISI TANGGAL]`

### Keputusan

Variabel minimum yang digunakan untuk analisis adalah:

1. Persentase kehadiran.
2. Persentase pemenuhan jam kerja.

### Sumber

Penelitian sumber menggunakan kedua variabel tersebut sebagai variabel clustering.

### Dampak

Dataset minimum untuk fitur AI harus menyediakan kedua variabel tersebut.

**Status:** Disetujui

---

## LOG-004 — Penetapan Jumlah Klaster

**Tanggal:** `[ISI TANGGAL]`

### Keputusan

Prototype menggunakan tiga kelompok hasil clustering:

1. Tinggi.
2. Sedang.
3. Rendah.

### Sumber

Penelitian sumber menghasilkan tiga cluster tingkat kedisiplinan.

### Catatan

Penamaan kelompok tidak boleh dianggap sebagai keputusan mutlak mengenai kualitas pegawai.

**Status:** Disetujui sebagai baseline penelitian

---

## LOG-005 — Penetapan Evaluasi AI

**Tanggal:** `[ISI TANGGAL]`

### Keputusan

Kualitas hasil clustering dievaluasi menggunakan **Silhouette Score**.

### Alasan

K-Means merupakan metode clustering, sehingga evaluasi tidak menggunakan akurasi klasifikasi seperti pada supervised learning.

### Nilai Acuan

Penelitian sumber memperoleh:

```text
Silhouette Score = 0,500844
