# PROMPT LOG

## Praktikum Prompt AI · Intelligent Mobile and Web Application Development

**Teknik Informatika — Praktikum PRD → SRS → HLD → LLD**

---

# 1. Informasi Dokumen

| Item           | Keterangan                                            |
| -------------- | ----------------------------------------------------- |
| Nama Produk    | Sistem Analisis Kedisiplinan Pegawai Berbasis K-Means |
| Dokumen        | Prompt Log                                            |
| Platform       | Website `[SESUAIKAN DENGAN PRD]`                      |
| Fitur AI Utama | ★ K-Means Clustering                                  |
| Tim            | `[NAMA TIM]`                                          |
| Anggota        | `[NAMA ANGGOTA]`                                      |
| Tanggal        | `[TANGGAL]`                                           |
| Status         | Draft                                                 |

---

# 2. Tujuan Prompt Log

Dokumen ini digunakan untuk mencatat proses penggunaan AI selama penyusunan kebutuhan sistem.

Setiap tahapan mencatat:

1. Prompt yang dikirimkan ke AI.
2. Konteks atau input yang diberikan.
3. Draf awal hasil generate AI.
4. Koreksi atau perubahan manual dari tim.
5. Alasan dilakukan koreksi.
6. Hasil akhir yang digunakan pada dokumen proyek.
7. Status validasi terhadap dokumen sebelumnya.

Dokumen ini bertujuan menjaga **keterlacakan proses penggunaan AI** sehingga perubahan dari hasil generate awal sampai hasil final dapat ditinjau kembali.

---

# 3. Konvensi Status

| Status      | Arti                                    |
| ----------- | --------------------------------------- |
| `GENERATED` | Hasil pertama dari AI                   |
| `REVIEWED`  | Sudah diperiksa oleh tim                |
| `REVISED`   | Sudah dikoreksi secara manual           |
| `VALIDATED` | Sudah dibandingkan dengan dokumen acuan |
| `REJECTED`  | Hasil AI tidak digunakan                |
| `FINAL`     | Hasil telah dipilih sebagai versi final |

---

# 4. Log Tahap PRD

## Prompt PRD

### Metadata

| Item      | Keterangan                                                                                            |
| --------- | ----------------------------------------------------------------------------------------------------- |
| ID Prompt | PROMPT-PRD-01                                                                                         |
| Tahap     | PRD                                                                                                   |
| Tanggal   | `[TANGGAL]`                                                                                           |
| Tujuan    | Menghasilkan draf Product Requirements Document                                                       |
| Input     | Problem statement, target user, stakeholder, persona, bukti riset, platform, fitur AI, dan constraint |
| Output    | `prd.md`                                                                                              |
| Status    | `[GENERATED / REVISED / FINAL]`                                                                       |

### Prompt yang Dikirim

```text
[Peran]
Kamu adalah product manager senior untuk produk Mobile/Web berfitur AI.

[Tugas]
Susun DRAF PRD ringkas untuk "<nama produk>" berdasarkan kasus berikut.

[Konteks]
Problem statement : <problem statement>
Target user : <target user>
Stakeholder lain : <stakeholder>
Persona ringkas : <persona>
Bukti riset : <kutipan/fakta wawancara-observasi-survey>
Platform & stack : <platform>
Fitur AI inti : <fitur AI>
Konstrain : prototype 1 semester; data & biaya AI terbatas

[Format output]
1) Ringkasan eksekutif;
2) Problem statement & bukti;
3) Target user & stakeholder;
4) Value proposition;
5) Tujuan produk & KPI;
6) Scope fitur 3 bulan: MoSCoW;
7) Non-goals;
8) Asumsi & risiko.

[Aturan]
Hanya gunakan data pada konteks.
Bila kurang, tulis [ASUMSI-XX].
Jangan menulis solusi teknis/arsitektur.
```

### Draf Awal AI

```text
[Tempel hasil generate AI pertama di sini]
```

### Koreksi Manual Tim

| Bagian            | Hasil AI     | Koreksi Tim | Alasan     |
| ----------------- | ------------ | ----------- | ---------- |
| Problem Statement | `[HASIL AI]` | `[KOREKSI]` | `[ALASAN]` |
| Target User       | `[HASIL AI]` | `[KOREKSI]` | `[ALASAN]` |
| KPI               | `[HASIL AI]` | `[KOREKSI]` | `[ALASAN]` |
| Scope             | `[HASIL AI]` | `[KOREKSI]` | `[ALASAN]` |
| Risiko            | `[HASIL AI]` | `[KOREKSI]` | `[ALASAN]` |

### Hasil Akhir

**Dokumen:** `prd.md`

**Status:** `FINAL / REVISED`

**Catatan validasi:**

```text
- Problem statement diperiksa agar tidak mengandung solusi.
- KPI diperiksa agar dapat diukur.
- Fitur AI diperiksa agar memiliki nilai nyata.
- Asumsi diberi penanda [ASUMSI-XX].
```

---

# 5. Log Tahap SRS

## Prompt SRS

### Metadata

| Item      | Keterangan                                          |
| --------- | --------------------------------------------------- |
| ID Prompt | PROMPT-SRS-01                                       |
| Tahap     | SRS                                                 |
| Acuan     | `prd.md`                                            |
| Tujuan    | Mengubah PRD menjadi kebutuhan sistem yang testable |
| Output    | `srs.md`                                            |
| Status    | `[GENERATED / REVISED / FINAL]`                     |

### Prompt yang Dikirim

```text
[Peran]
Kamu adalah requirements analyst senior.

[Tugas]
Ubah PRD berikut menjadi DRAF SRS ringkas.

[Konteks]
PRD hasil revisi : <tempel PRD>
Acuan kualitas : ISO/IEC 25010
Prioritas : MoSCoW
Platform & stack : <platform>

[Format output]
1) Tujuan, scope, definisi istilah;
2) User & stakeholder;
3) Lingkungan operasi;
4) Asumsi & dependensi;
5) FR;
6) NFR;
7) Kebutuhan data minimum fitur AI;
8) Aturan bisnis;
9) Matriks traceability.

[Aturan]
Setiap FR/NFR harus dapat ditelusuri ke PRD.
Dilarang menambah kebutuhan tanpa bukti.
Bila masuk arsitektur/UI, hentikan.
```

### Draf Awal AI

```text
[Tempel hasil generate AI pertama di sini]
```

### Koreksi Manual Tim

| ID     | Masalah pada Hasil AI | Koreksi     | Alasan        |
| ------ | --------------------- | ----------- | ------------- |
| FR-XX  | `[MASALAH]`           | `[KOREKSI]` | `[BUKTI PRD]` |
| NFR-XX | `[MASALAH]`           | `[KOREKSI]` | `[BUKTI PRD]` |
| NFR-AI | `[MASALAH]`           | `[KOREKSI]` | `[BUKTI PRD]` |

### Hasil Akhir

**Dokumen:** `srs.md`

**Status:** `FINAL / REVISED`

---

# 6. Log Tahap User Stories

## Prompt User Stories

### Metadata

| Item      | Keterangan                      |
| --------- | ------------------------------- |
| ID Prompt | PROMPT-US-01                    |
| Tahap     | User Stories                    |
| Acuan     | `srs.md`                        |
| Fokus     | FR Must dan Should              |
| Fitur AI  | ★ K-Means Clustering            |
| Output    | `user-stories.md`               |
| Status    | `[GENERATED / REVISED / FINAL]` |

### Prompt yang Dikirim

```text
[Peran]
Kamu adalah agile product owner dan business analyst.

[Tugas]
Ubah daftar Functional Requirements pada SRS menjadi DRAF User Stories
untuk fitur prioritas Must dan Should, termasuk fitur AI ★.

[Konteks]
SRS : <tempel FR Must/Should>
Persona : <tempel persona>
Fitur AI : <nama dan fungsi fitur AI>
Platform : <platform>

[Format output]
1) Tabel User Story;
2) Evaluasi INVEST;
3) Pecah story yang terlalu besar.

[Aturan]
Peran harus berasal dari persona.
Manfaat harus menjelaskan nilai nyata.
Jangan menulis detail UI atau coding.
```

### Draf Awal AI

```text
[Tempel hasil generate AI pertama di sini]
```

### Koreksi Manual Tim

| Story   | Koreksi     | Alasan     |
| ------- | ----------- | ---------- |
| US-01   | `[KOREKSI]` | `[ALASAN]` |
| US-02   | `[KOREKSI]` | `[ALASAN]` |
| US-05 ★ | `[KOREKSI]` | `[ALASAN]` |

### Hasil Akhir

**Dokumen:** `user-stories.md`

**Status:** `FINAL / REVISED`

---

# 7. Log Tahap Use Case

## Prompt Use Case

### Metadata

| Item      | Keterangan                      |
| --------- | ------------------------------- |
| ID Prompt | PROMPT-UC-01                    |
| Tahap     | Use Case                        |
| Acuan     | User Story                      |
| Fokus     | Fitur AI ★                      |
| Output    | Use Case                        |
| Status    | `[GENERATED / REVISED / FINAL]` |

### Prompt yang Dikirim

```text
[Peran]
Kamu adalah system analyst aplikasi cerdas.

[Tugas]
Buat DRAFT Use Case formal untuk User Story prioritas,
fokus pada fitur berbasis AI ★ dan alur penanganan kegagalannya.

[Konteks]
User Story : <tempel User Story>
Rincian Layanan AI : <model/API AI dan batasannya>
Batas Waktu Respon : <NFR>

[Format]
- ID dan Nama Use Case
- Aktor Utama
- Aktor Pendukung
- Precondition
- Postcondition
- Alur Utama
- Alur Alternatif
- Eksepsi AI
- Kaitan User Story dan FR

[Aturan]
Fokus pada alur logika dan interaksi.
Jangan membahas layout UI.
```

### Draf Awal AI

```text
[Tempel hasil generate AI pertama di sini]
```

### Koreksi Manual Tim

| Bagian       | Koreksi     | Alasan     |
| ------------ | ----------- | ---------- |
| Aktor        | `[KOREKSI]` | `[ALASAN]` |
| Precondition | `[KOREKSI]` | `[ALASAN]` |
| Alur Utama   | `[KOREKSI]` | `[ALASAN]` |
| Timeout      | `[KOREKSI]` | `[ALASAN]` |
| AI Failure   | `[KOREKSI]` | `[ALASAN]` |

---

# 8. Log Tahap User Flow

## Prompt User Flow

### Metadata

| Item      | Keterangan                      |
| --------- | ------------------------------- |
| ID Prompt | PROMPT-UF-01                    |
| Tahap     | User Flow                       |
| Fokus     | Fitur AI ★ dan fitur utama      |
| Output    | User Flow                       |
| Status    | `[GENERATED / REVISED / FINAL]` |

### Prompt yang Dikirim

```text
[Peran]
Kamu adalah UX designer dan interaction analyst produk cerdas.

[Tugas]
Susun DRAFT User Flow terstruktur untuk fitur AI ★
dan satu fitur utama lainnya.

[Konteks]
Persona & Skenario : <persona>
Use Case : <use case>
NFR Respon Waktu : <NFR>

[Format]
1) Langkah alur pengguna.
2) Empat status sistem:
   - Validasi awal
   - Pemrosesan AI
   - Penanganan hasil
   - Fallback
3) Diagram Mermaid atau teks.
4) Tabel kaitan alur ke Use Case.

[Aturan]
Jangan mengasumsikan AI selalu berhasil.
```

### Draf Awal AI

```text
[Tempel diagram dan hasil generate AI di sini]
```

### Koreksi Manual Tim

```text
[Tempel flowchart atau koreksi manual di sini]

Contoh:
Input Data
    ↓
Validasi
    ↓
AI Processing
    ↓
Hasil / Timeout
    ↓
Review
    ↓
Simpan
```

### Alasan Koreksi

* `[ALASAN 1]`
* `[ALASAN 2]`
* `[ALASAN 3]`

---

# 9. Log Tahap Acceptance Criteria

## Prompt Acceptance Criteria

### Metadata

| Item      | Keterangan                      |
| --------- | ------------------------------- |
| ID Prompt | PROMPT-AC-01                    |
| Tahap     | Acceptance Criteria             |
| Acuan     | User Story + Use Case + SRS     |
| Format    | Given-When-Then                 |
| Output    | Acceptance Criteria             |
| Status    | `[GENERATED / REVISED / FINAL]` |

### Prompt yang Dikirim

```text
[Peran]
Kamu adalah QA engineer dan test analyst.

[Tugas]
Tulis DRAFT Acceptance Criteria berpola Given-When-Then
untuk setiap User Story.

[Konteks]
User Story : <tempel User Story>
Use Case & Eksepsi : <tempel Use Case>
NFR : <tempel angka batas waktu, akurasi, pesan error>

[Format]
Scenario: [nama skenario]
Given [kondisi awal]
When [aksi]
Then [hasil terukur]

Untuk fitur AI wajib:
- Happy path
- Edge case
- Failure/timeout

Sertakan metode uji.
```

### Draf Awal AI

```text
[Tempel hasil generate AI pertama di sini]
```

### Koreksi Manual Tim

| User Story | Scenario    | Koreksi     | Alasan     |
| ---------- | ----------- | ----------- | ---------- |
| US-01      | Login valid | `[KOREKSI]` | `[ALASAN]` |
| US-05 ★    | Happy path  | `[KOREKSI]` | `[ALASAN]` |
| US-05 ★    | Timeout     | `[KOREKSI]` | `[ALASAN]` |
| US-08 ★    | Evaluasi AI | `[KOREKSI]` | `[ALASAN]` |

### Hasil Akhir

**Dokumen:** `user-stories.md`

**Status:** `FINAL / REVISED`

---

# 10. Log Integrasi Dokumen

Setelah setiap tahap selesai, hasil AI dibandingkan dengan dokumen sebelumnya.

| Tahap               | Dokumen Acuan               | Dokumen Hasil     | Status Validasi |
| ------------------- | --------------------------- | ----------------- | --------------- |
| PRD                 | Riset / Tugas 2             | `prd.md`          | `[STATUS]`      |
| SRS                 | `prd.md`                    | `srs.md`          | `[STATUS]`      |
| User Story          | `srs.md`                    | `user-stories.md` | `[STATUS]`      |
| Use Case            | User Story                  | `user-stories.md` | `[STATUS]`      |
| User Flow           | Use Case                    | `user-stories.md` | `[STATUS]`      |
| Acceptance Criteria | User Story + Use Case + SRS | `user-stories.md` | `[STATUS]`      |

---

# 11. Rekap Koreksi Manual Tim

Bagian ini mencatat perubahan penting yang dilakukan manusia terhadap hasil AI.

| No. | Tahap               | Bagian            | Masalah Hasil AI | Perubahan Tim | Alasan     |
| --- | ------------------- | ----------------- | ---------------- | ------------- | ---------- |
| 1   | PRD                 | Problem Statement | `[MASALAH]`      | `[PERUBAHAN]` | `[ALASAN]` |
| 2   | PRD                 | KPI               | `[MASALAH]`      | `[PERUBAHAN]` | `[ALASAN]` |
| 3   | SRS                 | FR                | `[MASALAH]`      | `[PERUBAHAN]` | `[ALASAN]` |
| 4   | SRS                 | NFR               | `[MASALAH]`      | `[PERUBAHAN]` | `[ALASAN]` |
| 5   | User Story          | US                | `[MASALAH]`      | `[PERUBAHAN]` | `[ALASAN]` |
| 6   | Use Case            | Alur              | `[MASALAH]`      | `[PERUBAHAN]` | `[ALASAN]` |
| 7   | User Flow           | Flow              | `[MASALAH]`      | `[PERUBAHAN]` | `[ALASAN]` |
| 8   | Acceptance Criteria | Scenario          | `[MASALAH]`      | `[PERUBAHAN]` | `[ALASAN]` |

---

# 12. Catatan Halusinasi / Klaim Tanpa Bukti

Setiap informasi yang muncul dari AI tetapi tidak memiliki dukungan dari PRD, SRS, atau hasil riset dicatat di sini.

| No. | Klaim AI  | Sumber yang Seharusnya | Status             | Tindakan            |
| --- | --------- | ---------------------- | ------------------ | ------------------- |
| 1   | `[KLAIM]` | `[SUMBER]`             | Tidak ditemukan    | Dihapus             |
| 2   | `[KLAIM]` | `[SUMBER]`             | Belum diverifikasi | Ditandai `[ASUMSI]` |
| 3   | `[KLAIM]` | `[SUMBER]`             | Terverifikasi      | Dipertahankan       |

---

# 13. Keputusan Tim

| ID     | Keputusan     | Tahap               | Alasan     | Diputuskan Oleh | Tanggal     |
| ------ | ------------- | ------------------- | ---------- | --------------- | ----------- |
| DEC-01 | `[KEPUTUSAN]` | PRD                 | `[ALASAN]` | `[NAMA]`        | `[TANGGAL]` |
| DEC-02 | `[KEPUTUSAN]` | SRS                 | `[ALASAN]` | `[NAMA]`        | `[TANGGAL]` |
| DEC-03 | `[KEPUTUSAN]` | User Story          | `[ALASAN]` | `[NAMA]`        | `[TANGGAL]` |
| DEC-04 | `[KEPUTUSAN]` | Use Case            | `[ALASAN]` | `[NAMA]`        | `[TANGGAL]` |
| DEC-05 | `[KEPUTUSAN]` | User Flow           | `[ALASAN]` | `[NAMA]`        | `[TANGGAL]` |
| DEC-06 | `[KEPUTUSAN]` | Acceptance Criteria | `[ALASAN]` | `[NAMA]`        | `[TANGGAL]` |

---

# 14. Ringkasan Perubahan Versi

| Versi | Tanggal     | Tahap               | Perubahan                | Penanggung Jawab |
| ----- | ----------- | ------------------- | ------------------------ | ---------------- |
| v0.1  | `[TANGGAL]` | PRD                 | Generate awal            | `[NAMA]`         |
| v0.2  | `[TANGGAL]` | PRD                 | Koreksi manual           | `[NAMA]`         |
| v0.3  | `[TANGGAL]` | SRS                 | Generate awal            | `[NAMA]`         |
| v0.4  | `[TANGGAL]` | SRS                 | Koreksi manual           | `[NAMA]`         |
| v0.5  | `[TANGGAL]` | User Story          | Generate awal            | `[NAMA]`         |
| v0.6  | `[TANGGAL]` | Use Case            | Generate awal            | `[NAMA]`         |
| v0.7  | `[TANGGAL]` | User Flow           | Generate awal            | `[NAMA]`         |
| v0.8  | `[TANGGAL]` | Acceptance Criteria | Generate awal            | `[NAMA]`         |
| v1.0  | `[TANGGAL]` | Final               | Validasi seluruh dokumen | `[NAMA TIM]`     |

---

# 15. Checklist Akhir Prompt Log

* [ ] Semua prompt utama terdokumentasi.
* [ ] Draf awal AI disimpan.
* [ ] Koreksi manual tim dicatat.
* [ ] Alasan setiap koreksi penting dicatat.
* [ ] Klaim AI tanpa bukti dicatat dan ditangani.
* [ ] Perubahan requirement dapat ditelusuri.
* [ ] User Story dapat ditelusuri ke SRS.
* [ ] Use Case dapat ditelusuri ke User Story.
* [ ] User Flow dapat ditelusuri ke Use Case.
* [ ] Acceptance Criteria dapat ditelusuri ke User Story dan SRS.
* [ ] Placeholder `[ASUMSI]` dan `[BELUM DITENTUKAN]` tidak diisi tanpa bukti.
* [ ] Tim melakukan validasi akhir terhadap hasil generate AI.

---

# 16. Kesimpulan

`prompt-log.md` menjadi catatan audit proses penggunaan AI dalam pengembangan requirement.

Alur dokumentasi:

```text
Prompt
   ↓
Draf Awal AI
   ↓
Review Tim
   ↓
Koreksi Manual
   ↓
Validasi terhadap Sumber
   ↓
Hasil Final
```

AI digunakan sebagai alat bantu penyusunan draf, sedangkan keputusan akhir mengenai requirement, koreksi, prioritas, dan validasi tetap dilakukan oleh tim.

**Status Dokumen:** `[DRAFT / FINAL]`
