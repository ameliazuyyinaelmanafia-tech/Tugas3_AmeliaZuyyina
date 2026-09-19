# DRAF SOFTWARE REQUIREMENTS SPECIFICATION (SRS)

## Sistem Analisis Kedisiplinan Pegawai Berbasis K-Means

---

# 1. Tujuan, Scope, dan Definisi Istilah

## 1.1 Tujuan

Sistem ini bertujuan membantu pihak pengelola kepegawaian dalam memperoleh informasi pengelompokan tingkat kedisiplinan pegawai berdasarkan data presensi.

Sistem menggunakan fitur **K-Means Clustering** untuk mengelompokkan data berdasarkan karakteristik presensi. Pada penelitian yang menjadi acuan, variabel yang digunakan adalah persentase kehadiran dan persentase pemenuhan jam kerja.

Hasil pengelompokan digunakan sebagai informasi pendukung dalam proses monitoring dan evaluasi, bukan sebagai keputusan otomatis terhadap pegawai.

---

## 1.2 Scope

### Termasuk dalam scope

1. Login pengguna **[ASUMSI-01]**.
2. Pengelolaan data presensi.
3. Pemrosesan data presensi untuk analisis.
4. **K-Means Clustering** untuk mengelompokkan tingkat kedisiplinan.
5. Penampilan hasil pengelompokan.
6. Perhitungan **Silhouette Score**.
7. Filter berdasarkan periode **[ASUMSI-02]**.
8. Rekap hasil klaster **[ASUMSI-03]**.
9. Riwayat hasil analisis **[ASUMSI-04]**.
10. Export hasil analisis **[ASUMSI-05]**.
11. Grafik sederhana hasil klaster **[ASUMSI-06]**.

### Di luar scope

1. Prediksi tingkat kedisiplinan pada masa mendatang.
2. Penilaian keseluruhan kinerja pegawai.
3. Penentuan sanksi secara otomatis.
4. Penentuan penghargaan secara otomatis.
5. Penentuan promosi pegawai.
6. Pengambilan keputusan otomatis berdasarkan hasil clustering.
7. Sistem informasi kepegawaian secara keseluruhan.

---

## 1.3 Definisi Istilah

| Istilah | Definisi |
|---|---|
| Presensi | Data yang menunjukkan kehadiran pegawai. |
| K-Means | Metode clustering yang digunakan untuk mengelompokkan data berdasarkan kemiripan karakteristik. |
| Clustering | Proses mengelompokkan data berdasarkan karakteristik tertentu. |
| Klaster | Kelompok data yang memiliki karakteristik relatif serupa. |
| Silhouette Score | Nilai yang digunakan untuk mengevaluasi kualitas hasil clustering. |
| Data Mining | Proses menemukan pola atau informasi dari data. |
| KDD | Tahapan pengolahan data yang mencakup selection, preprocessing, transformation, data mining, dan evaluation. |
| Tingkat Kedisiplinan | Kelompok hasil analisis yang pada penelitian sumber terdiri dari tinggi, sedang, dan rendah. |

---

# 2. User & Stakeholder, Lingkungan Operasi, Asumsi & Dependensi

## 2.1 User

| User | Kebutuhan |
|---|---|
| Pengelola kepegawaian **[ASUMSI-07]** | Memperoleh informasi pengelompokan kedisiplinan pegawai. |
| Manajemen/pimpinan **[ASUMSI-08]** | Menggunakan hasil analisis sebagai informasi pendukung monitoring dan evaluasi. |
| Administrator **[ASUMSI-09]** | Mengelola data yang digunakan dalam proses analisis. |

## 2.2 Stakeholder

| Stakeholder | Kepentingan |
|---|---|
| Pengelola kepegawaian **[ASUMSI-10]** | Analisis dan monitoring kedisiplinan. |
| Manajemen/pimpinan **[ASUMSI-11]** | Informasi pendukung evaluasi. |
| Pegawai **[ASUMSI-12]** | Data kedisiplinan yang berkaitan dengan dirinya. |
| Pengembang/peneliti | Pengembangan dan pengujian prototype. |

---

## 2.3 Lingkungan Operasi

- Platform: **Website [ASUMSI-13]**
- Stack: **[ASUMSI-14]**
- Prototype dikembangkan dalam periode satu semester.
- Sistem menggunakan data presensi sebagai sumber data analisis.

> **Catatan:** Platform dan stack belum diberikan secara konkret dalam PRD sehingga masih ditandai sebagai asumsi.

---

## 2.4 Asumsi

| ID | Asumsi |
|---|---|
| ASUMSI-01 | Sistem menggunakan mekanisme login pengguna. |
| ASUMSI-02 | Pengguna membutuhkan filter periode data. |
| ASUMSI-03 | Pengguna membutuhkan rekap jumlah hasil klaster. |
| ASUMSI-04 | Pengguna membutuhkan riwayat hasil analisis. |
| ASUMSI-05 | Pengguna membutuhkan export hasil analisis. |
| ASUMSI-06 | Grafik sederhana membantu membaca distribusi hasil klaster. |
| ASUMSI-07 | Pengelola kepegawaian merupakan user utama. |
| ASUMSI-08 | Manajemen/pimpinan menggunakan hasil analisis untuk monitoring. |
| ASUMSI-09 | Administrator diperlukan untuk pengelolaan data. |
| ASUMSI-10 | Pengelola kepegawaian menjadi stakeholder utama. |
| ASUMSI-11 | Manajemen/pimpinan berkepentingan terhadap hasil analisis. |
| ASUMSI-12 | Pegawai menjadi pihak yang berkaitan dengan hasil pengelompokan. |
| ASUMSI-13 | Sistem dikembangkan berbasis website. |
| ASUMSI-14 | Stack teknologi belum ditentukan. |

---

## 2.5 Dependensi

1. Sistem bergantung pada ketersediaan data presensi.
2. Data harus memiliki variabel yang diperlukan untuk proses clustering.
3. Hasil analisis bergantung pada kualitas data yang digunakan.
4. Kualitas hasil clustering bergantung pada data yang diproses dan parameter clustering.

---

# 3. Functional Requirements (FR)

## 3.1 Daftar Functional Requirements

| ID | Functional Requirement | Prioritas | Metode Verifikasi |
|---|---|---|---|
| FR-01 | Sistem harus dapat melakukan autentikasi pengguna saat pengguna mengakses sistem → pengguna yang valid dapat masuk ke sistem. | Must | Black-box testing |
| FR-02 | Sistem harus dapat menerima dan menyimpan data presensi saat data presensi diberikan → data presensi tersedia untuk proses analisis. | Must | Black-box testing |
| FR-03 | Sistem harus dapat menggunakan data persentase kehadiran saat proses analisis dilakukan → persentase kehadiran digunakan sebagai data analisis. | Must | Uji data |
| FR-04 | Sistem harus dapat menggunakan data persentase pemenuhan jam kerja saat proses analisis dilakukan → persentase pemenuhan jam kerja digunakan sebagai data analisis. | Must | Uji data |
| FR-05 | Sistem harus dapat melakukan proses K-Means saat data yang dibutuhkan tersedia → setiap data memperoleh kelompok hasil clustering. | Must | Black-box testing + perbandingan hasil |
| FR-06 | Sistem harus dapat menghasilkan tiga kelompok hasil clustering saat proses K-Means selesai → tersedia kelompok kedisiplinan tinggi, sedang, dan rendah. | Must | Uji hasil |
| FR-07 | Sistem harus dapat menampilkan hasil pengelompokan saat proses clustering selesai → pengguna dapat melihat kelompok hasil analisis. | Must | Black-box testing |
| FR-08 | Sistem harus dapat menghitung Silhouette Score saat hasil clustering tersedia → nilai Silhouette Score ditampilkan sebagai ukuran evaluasi clustering. | Must | Perhitungan + uji hasil |
| FR-09 | Sistem harus dapat menampilkan informasi hasil analisis saat hasil clustering tersedia → informasi kelompok kedisiplinan dapat diperiksa pengguna. | Must | Black-box testing |
| FR-10 | Sistem harus dapat memfilter data berdasarkan periode saat pengguna memilih periode analisis → sistem menampilkan data pada periode yang dipilih. | Should | Black-box testing |
| FR-11 | Sistem harus dapat menampilkan rekap jumlah data pada setiap klaster saat hasil clustering tersedia → jumlah anggota setiap kelompok ditampilkan. | Should | Black-box testing |
| FR-12 | Sistem harus dapat menyimpan riwayat hasil analisis saat proses analisis selesai → hasil analisis sebelumnya dapat ditelusuri kembali. | Should | Black-box testing |
| FR-13 | Sistem harus dapat mengekspor hasil analisis saat pengguna meminta export → file hasil analisis tersedia. | Could | Black-box testing |
| FR-14 | Sistem harus dapat menampilkan grafik sederhana saat hasil clustering tersedia → distribusi hasil klaster dapat dilihat secara visual. | Could | Black-box testing |

> **Catatan:** FR-10 sampai FR-14 berasal dari fitur **Should Have/Could Have** pada PRD dan masih mengandung asumsi yang perlu divalidasi.

---

# 4. Non-Functional Requirements (NFR)

Acuan kualitas yang digunakan adalah karakteristik **ISO/IEC 25010** yang relevan dengan prototype, yaitu:

- Functional suitability
- Performance efficiency
- Security
- Usability
- Reliability
- Maintainability

Khusus sistem AI/data mining, kebutuhan akurasi dan latensi dicantumkan sebagai kebutuhan pengukuran prototype.

| ID | Kategori ISO/IEC 25010 | NFR | Metrik | Target | Kondisi Ukur |
|---|---|---|---|---|---|
| NFR-01 | Functional suitability | Sistem harus menghasilkan label klaster untuk seluruh data valid yang diproses → tidak ada data valid yang kehilangan hasil klaster. | Persentase data memperoleh label | 100% | Dataset valid dimasukkan ke sistem. |
| NFR-02 | Functional suitability | Sistem harus menghitung Silhouette Score ketika hasil clustering tersedia → nilai evaluasi dapat diperoleh. | Ketersediaan nilai Silhouette Score | 100% proses clustering berhasil menghasilkan nilai | Dataset berhasil diproses dan memiliki lebih dari satu klaster. |
| NFR-03 | Performance efficiency | Sistem harus menyelesaikan proses clustering setelah data valid diberikan → hasil clustering dapat digunakan oleh pengguna. | Waktu proses clustering | **[ASUMSI-15] Ditentukan setelah baseline pengujian** | Dataset prototype dengan ukuran yang ditetapkan saat pengujian. |
| NFR-04 | Performance efficiency | Sistem harus mencatat waktu proses analisis → waktu proses dapat dibandingkan dengan baseline. | Waktu dalam detik | Terukur pada setiap pengujian | Pengujian dilakukan menggunakan dataset prototype. |
| NFR-05 | AI/Model evaluation | Sistem harus menghasilkan hasil clustering yang dapat dievaluasi → Silhouette Score tersedia untuk setiap proses analisis. | Silhouette Score | ≥ 0,500844 **[acuan penelitian sumber]** | Dataset dan konfigurasi pengujian prototype. |
| NFR-06 | AI/Model evaluation | Sistem harus menghasilkan hasil clustering yang konsisten ketika dataset dan parameter yang sama digunakan → hasil dapat dibandingkan dengan hasil pengujian acuan. | Persentase kesamaan hasil | **[ASUMSI-16] Ditentukan melalui pengujian** | Dataset, parameter, dan kondisi pengujian dibuat sama. |
| NFR-07 | Security | Sistem harus membatasi akses fungsi sistem kepada pengguna yang berhasil melakukan autentikasi → fungsi yang dilindungi tidak dapat diakses tanpa login. | Persentase skenario akses tidak sah yang ditolak | 100% | Pengujian akses tanpa autentikasi. |
| NFR-08 | Security | Sistem harus membatasi akses data sesuai hak pengguna **[ASUMSI-17]** → pengguna tanpa hak tidak dapat mengakses data yang dibatasi. | Persentase skenario akses tidak sah yang ditolak | 100% | Pengujian menggunakan akun dengan hak berbeda. |
| NFR-09 | Privacy | Sistem harus menjaga data presensi agar hanya dapat diakses oleh pengguna yang memiliki hak akses → data tidak ditampilkan kepada pengguna tidak berwenang. | Persentase skenario akses tidak sah yang ditolak | 100% | Pengujian akses terhadap data presensi. |
| NFR-10 | Usability | Sistem harus menyediakan hasil clustering dalam bentuk informasi kelompok yang dapat dibaca pengguna → pengguna dapat mengetahui hasil kelompok yang dihasilkan sistem. | Persentase tugas pengujian yang berhasil | **[ASUMSI-18] ≥ 80%** | Pengujian task-based terhadap calon pengguna. |
| NFR-11 | Usability | Sistem harus menggunakan istilah kelompok yang konsisten pada hasil analisis → label kelompok tidak berubah pada tampilan hasil yang sama. | Konsistensi label | 100% | Pengujian beberapa hasil clustering. |
| NFR-12 | Reliability | Sistem harus menghasilkan hasil analisis tanpa kegagalan pada data valid → proses analisis selesai atau memberikan informasi kesalahan yang dapat diketahui pengguna. | Persentase proses berhasil | **[ASUMSI-19] ≥ 95%** | Pengujian berulang menggunakan dataset valid. |
| NFR-13 | Maintainability | Sistem harus memisahkan fungsi analisis dari fitur lain sehingga proses pengujian K-Means dapat dilakukan secara terpisah → proses analisis dapat diuji tanpa menjalankan seluruh fungsi sistem. | Keberhasilan pengujian fungsi analisis | 100% skenario pengujian | Pengujian fungsi K-Means secara terpisah. |

> **Catatan penting:** Target NFR yang belum memiliki dasar dari PRD/riset diberi tanda **[ASUMSI-XX]**. Nilainya harus divalidasi sebelum SRS final.

---

# 5. Kebutuhan Data Minimum Fitur AI

## 5.1 Input Model

Berdasarkan penelitian yang menjadi acuan, fitur K-Means menggunakan dua variabel utama:

| Data Input | Keterangan |
|---|---|
| Persentase kehadiran | Persentase kehadiran pegawai pada periode yang dianalisis. |
| Persentase pemenuhan jam kerja | Persentase pemenuhan jam kerja pegawai pada periode yang dianalisis. |

## 5.2 Alur Input → Output

```text
Data Presensi
     │
     ├── Persentase Kehadiran
     │
     └── Persentase Pemenuhan Jam Kerja
              │
              ▼
      Data untuk Analisis
              │
              ▼
        K-Means Clustering
              │
              ▼
        Hasil Pengelompokan
              │
       ┌──────┼──────┐
       ▼      ▼      ▼
     Tinggi  Sedang  Rendah
              │
              ▼
      Silhouette Score
