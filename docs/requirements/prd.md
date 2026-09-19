# DRAF PRODUCT REQUIREMENT DOCUMENT (PRD)

## Nama Produk
**[ASUMSI-01] Sistem Analisis Kedisiplinan Pegawai Berbasis K-Means**

---

# 1. Ringkasan Eksekutif

Produk ini merupakan aplikasi **[ASUMSI-02] berbasis website** yang digunakan untuk membantu pihak pengelola kepegawaian menganalisis data presensi dan memperoleh informasi mengenai tingkat kedisiplinan pegawai.

Permasalahan yang menjadi dasar pengembangan adalah data presensi yang dapat digunakan untuk kebutuhan administratif, tetapi belum tentu dimanfaatkan untuk menghasilkan informasi analitis mengenai kedisiplinan.

Artikel yang digunakan sebagai bukti riset menunjukkan kasus pada Sistem Kepegawaian STMIK El Rahma Yogyakarta, di mana data presensi sebelumnya masih terbatas pada pencatatan administratif dan belum dioptimalkan untuk menghasilkan informasi analitis mengenai kedisiplinan pegawai.

Produk akan memiliki fitur **★ klasterisasi tingkat kedisiplinan menggunakan K-Means** berdasarkan data presensi. Pada penelitian sumber, data berupa persentase kehadiran dan pemenuhan jam kerja dikelompokkan menjadi tiga klaster, yaitu tinggi, sedang, dan rendah.

---

# 2. Problem Statement & Bukti

## 2.1 Problem Statement

**[ASUMSI-03]** Pihak pengelola kepegawaian membutuhkan cara yang lebih terstruktur untuk memahami tingkat kedisiplinan pegawai berdasarkan data presensi, karena data presensi yang tersedia belum dimanfaatkan secara optimal untuk menghasilkan informasi pengelompokan kedisiplinan.

Problem statement ini berfokus pada permasalahan, bukan solusi teknis.

## 2.2 Fakta

| Fakta | Bukti |
|---|---|
| Data presensi dapat digunakan sebagai indikator kedisiplinan melalui kehadiran dan pemenuhan jam kerja. | Artikel menjelaskan bahwa presensi merupakan salah satu indikator yang dapat merepresentasikan tingkat kedisiplinan. |
| Pada kasus penelitian, data presensi masih terbatas untuk pencatatan administratif. | Artikel menyebutkan bahwa data presensi belum dioptimalkan untuk menghasilkan informasi analitis mengenai kedisiplinan. |
| Evaluasi yang hanya bersifat deskriptif dapat menyulitkan klasifikasi kedisiplinan secara sistematis. | Dijelaskan pada bagian pendahuluan penelitian. |
| K-Means digunakan untuk mengelompokkan data berdasarkan kemiripan karakteristik. | Dijelaskan pada bagian K-Means Clustering. |
| Penelitian menghasilkan tiga kelompok kedisiplinan. | Kelompok terdiri dari kedisiplinan tinggi, sedang, dan rendah. |
| Penelitian memperoleh rata-rata Silhouette Score sebesar 0,500844. | Digunakan untuk mengevaluasi kualitas hasil klasterisasi. |

## 2.3 Asumsi

- **[ASUMSI-04]** Pengguna utama produk adalah pihak pengelola kepegawaian atau manajemen.
- **[ASUMSI-05]** Pengguna membutuhkan informasi tingkat kedisiplinan untuk membantu monitoring dan evaluasi.
- **[ASUMSI-06]** Data presensi yang tersedia memiliki informasi kehadiran dan pemenuhan jam kerja.
- **[ASUMSI-07]** Produk digunakan pada satu institusi/organisasi sebagai prototype selama satu semester.
- **[ASUMSI-08]** Belum dilakukan wawancara atau survei langsung terhadap calon pengguna.

> **Catatan:** Artikel sumber merupakan penelitian pada STMIK El Rahma Yogyakarta. Fakta tersebut tidak boleh dianggap sebagai bukti bahwa masalah yang sama pasti terjadi pada calon pengguna produk ini.

---

# 3. Target User & Stakeholder

| Peran | Kebutuhan | Pengaruh |
|---|---|---|
| Pengelola kepegawaian **[ASUMSI-09]** | Melihat dan memahami tingkat kedisiplinan pegawai berdasarkan data presensi. | Tinggi |
| Manajemen/pimpinan **[ASUMSI-10]** | Mendapatkan informasi untuk membantu monitoring dan evaluasi. | Tinggi |
| Pegawai **[ASUMSI-11]** | Mengetahui informasi tingkat kedisiplinannya. | Sedang |
| Administrator sistem **[ASUMSI-12]** | Mengelola data yang digunakan oleh sistem. | Sedang |
| Peneliti/pengembang | Memastikan fitur analisis berjalan sesuai kebutuhan prototype. | Sedang |

## Target User Utama

**[ASUMSI-13] Pengelola kepegawaian**, karena informasi yang dihasilkan berkaitan dengan evaluasi tingkat kedisiplinan pegawai.

---

# 4. Value Proposition

## 4.1 Pain yang Dikurangi

1. Kesulitan memahami pola kedisiplinan hanya dari data presensi mentah.
2. Evaluasi kedisiplinan yang masih membutuhkan interpretasi manual.
3. Kesulitan mengelompokkan pegawai berdasarkan karakteristik presensi secara sistematis.

## 4.2 Gain yang Diciptakan

1. Pegawai dapat dikelompokkan berdasarkan karakteristik data presensi.
2. Pengelola mendapatkan informasi tingkat kedisiplinan dalam bentuk kelompok yang lebih mudah dipahami.
3. Proses monitoring dan evaluasi dapat didukung oleh informasi berbasis data.

## 4.3 Mengapa Fitur AI Bukan Gimmick?

Fitur **★ K-Means** mempunyai fungsi langsung terhadap masalah karena digunakan untuk mengelompokkan data presensi berdasarkan kemiripan karakteristik.

Fitur ini bukan sekadar penambahan label AI karena hasil proses digunakan untuk mengubah data presensi menjadi informasi kelompok tingkat kedisiplinan.

Dalam penelitian sumber, dua variabel utama yang digunakan adalah:

- Persentase pemenuhan jam kerja
- Persentase kehadiran

Data tersebut kemudian dikelompokkan menjadi tiga klaster.

---

# 5. Tujuan Produk & KPI Terukur

| Tujuan | KPI | Cara Mengukur |
|---|---|---|
| Menghasilkan pengelompokan kedisiplinan | 100% data valid yang diproses menghasilkan label klaster | Membandingkan jumlah data yang diproses dengan data yang memperoleh hasil klaster |
| Menyediakan tiga kelompok kedisiplinan | 3 kategori klaster tersedia | Memeriksa hasil proses K-Means |
| Menilai kualitas hasil klasterisasi | Silhouette Score dapat dihitung | Menghitung Silhouette Score setelah proses clustering |
| Memastikan fungsi utama sistem berjalan | 100% skenario fungsi utama berhasil pada pengujian prototype | Blackbox testing |
| Mengurangi proses pengelompokan manual **[ASUMSI-14]** | Waktu proses pengelompokan lebih rendah dibandingkan baseline | Membandingkan waktu proses manual dengan waktu menggunakan sistem |

> **Catatan:** Target pengurangan waktu belum dapat ditentukan karena belum tersedia data baseline dari calon pengguna.

---

# 6. Scope Fitur 3 Bulan — MoSCoW

| Prioritas | Fitur | Keterangan |
|---|---|---|
| **Must Have** | Login pengguna **[ASUMSI-15]** | Membatasi akses pengguna sistem. |
| **Must Have** | Pengelolaan data presensi | Menyediakan data yang akan dianalisis. |
| **Must Have** | ★ Proses K-Means | Mengelompokkan data berdasarkan karakteristik presensi. |
| **Must Have** | ★ Hasil klasterisasi | Menampilkan kelompok kedisiplinan hasil analisis. |
| **Must Have** | ★ Silhouette Score | Mengukur kualitas hasil klasterisasi. |
| **Must Have** | Tampilan data hasil analisis | Menampilkan informasi hasil clustering. |
| **Should Have** | Filter periode presensi | Memungkinkan pengguna memilih periode data. |
| **Should Have** | Rekap hasil klaster | Menampilkan jumlah pegawai pada setiap kelompok. |
| **Should Have** | Riwayat hasil analisis **[ASUMSI-16]** | Menyimpan hasil analisis sebelumnya. |
| **Could Have** | Export hasil analisis **[ASUMSI-17]** | Menghasilkan laporan hasil analisis. |
| **Could Have** | Grafik sederhana **[ASUMSI-18]** | Membantu membaca distribusi hasil klaster. |
| **Won't Have** | Prediksi kedisiplinan masa depan | Tidak menjadi bagian prototype 3 bulan. |
| **Won't Have** | Sistem penilaian kinerja otomatis | K-Means hanya digunakan untuk pengelompokan. |
| **Won't Have** | Pengambilan keputusan otomatis terhadap pegawai | Keputusan tetap dilakukan oleh pihak yang berwenang. |
| **Won't Have** | Analisis di luar data presensi | Tidak termasuk dalam scope awal. |

---

# 7. Non-Goals

Produk **tidak bertujuan untuk**:

1. Menentukan sanksi atau penghargaan pegawai secara otomatis.
2. Menggantikan keputusan manajemen.
3. Menilai keseluruhan kinerja pegawai.
4. Memprediksi perilaku pegawai pada masa depan.
5. Menentukan apakah seorang pegawai layak mendapatkan promosi.
6. Menggunakan data di luar kebutuhan analisis kedisiplinan pada prototype.
7. Menjadi sistem kepegawaian lengkap.
8. Membuat keputusan berdasarkan hasil clustering tanpa interpretasi manusia.

Hasil K-Means digunakan sebagai informasi pengelompokan berdasarkan karakteristik data, bukan sebagai keputusan final mengenai kualitas atau kinerja seseorang.

---

# 8. Asumsi & Risiko Utama + Mitigasi

| Asumsi/Risiko | Dampak | Mitigasi |
|---|---|---|
| **[ASUMSI-19]** Data presensi tersedia dalam format yang dapat dianalisis. | Data tidak dapat diproses. | Menentukan format data minimum sejak awal. |
| **[ASUMSI-20]** Data memiliki informasi kehadiran dan pemenuhan jam kerja. | Variabel utama clustering tidak tersedia. | Melakukan pengecekan dataset sebelum analisis. |
| Data tidak lengkap atau tidak konsisten. | Hasil clustering dapat terganggu. | Melakukan validasi dan pembersihan data sebelum analisis. |
| Jumlah data prototype terbatas. | Hasil belum tentu mewakili kondisi sebenarnya. | Menyatakan hasil sebagai hasil prototype dan tidak menggeneralisasikannya. |
| Pemilihan jumlah klaster tidak sesuai kebutuhan. | Hasil pengelompokan sulit diinterpretasikan. | Menentukan jumlah klaster berdasarkan kebutuhan penelitian dan mengevaluasinya menggunakan metrik clustering. |
| Hasil clustering disalahartikan sebagai penilaian mutlak. | Dapat menghasilkan keputusan yang tidak tepat. | Menampilkan hasil sebagai informasi pendukung, bukan keputusan otomatis. |
| **[ASUMSI-21]** Pengguna belum pernah menggunakan fitur clustering. | Pengguna dapat kesulitan memahami hasil. | Menggunakan istilah dan tampilan kategori yang sederhana serta memberikan penjelasan hasil. |
| Waktu pengembangan hanya satu semester. | Fitur terlalu banyak dan tidak selesai. | Membatasi prototype pada fitur Must Have terlebih dahulu. |
| Data dan biaya AI terbatas. | Pengembangan fitur AI yang kompleks sulit dilakukan. | Menggunakan metode clustering pada data numerik yang tersedia dan membatasi scope analisis. |

---

# 9. Review Checklist PRD

| Checklist | Status | Keterangan |
|---|---|---|
| Problem statement konsisten dengan Tugas 2 | ✅ | Fokus pada pemanfaatan data presensi untuk analisis kedisiplinan. |
| Problem statement bebas kata solusi | ✅ | K-Means tidak dimasukkan sebagai masalah. |
| KPI terukur | ✅ | Terdapat indikator jumlah data, kategori, Silhouette Score, dan pengujian. |
| Fitur AI memberikan nilai nyata | ✅ | K-Means digunakan untuk mengelompokkan data presensi. |
| Non-goals jelas | ✅ | Keputusan otomatis, prediksi, dan penilaian kinerja dikeluarkan. |
| Tidak ada klaim tanpa bukti | ✅ | Fakta dipisahkan dari asumsi. |
| Setiap informasi yang belum tersedia diberi label asumsi | ✅ | Menggunakan format `[ASUMSI-XX]`. |
| Tidak memasukkan arsitektur/solusi teknis | ✅ | Tidak membahas HLD, LLD, database, API, dan arsitektur. |
| Scope 3 bulan jelas | ✅ | Menggunakan prioritas MoSCoW. |
| Risiko dan mitigasi tersedia | ✅ | Risiko data, interpretasi, waktu, dan keterbatasan prototype dicantumkan. |

---

# 10. Kesimpulan

Produk berfokus pada pemanfaatan data presensi untuk menghasilkan informasi mengenai pengelompokan tingkat kedisiplinan pegawai.

Fitur utama yang menjadi pembeda adalah **★ K-Means Clustering**, yang digunakan untuk mengelompokkan data berdasarkan karakteristik presensi. Pada penelitian sumber, variabel yang digunakan adalah persentase kehadiran dan persentase pemenuhan jam kerja, dengan tiga kelompok yaitu kedisiplinan tinggi, sedang, dan rendah.

Karena data mengenai calon pengguna, hasil wawancara, observasi, survei, platform, dan kebutuhan organisasi belum tersedia dalam konteks, bagian tersebut masih ditandai sebagai **[ASUMSI-XX]** dan perlu divalidasi sebelum PRD dijadikan dasar untuk SRS.
