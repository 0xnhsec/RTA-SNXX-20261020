# Laporan adopsi modul red-team ke SNXX

> **Dokumen:** laporan utama Phase 1
> **Proyek:** `RTA-SNXX-20261020` — *Red Team Agent — SNXX — 20 October 2026*
> **Tanggal:** 21 Oktober 2026
> **Status:** selesai untuk scope adopsi Phase 1; gap fungsional tercatat di [roadmap](06-ROADMAP.md)
> **Klasifikasi:** publik tersanitasi
> **Versi:** 1.0

## 1. Ringkasan eksekutif

Phase 1 menggabungkan skill keamanan dari empat repositori sumber menjadi enam modul yang lebih mudah dipilih, diaudit, dan dioperasikan di SNXX. Lima modul berlisensi MIT diadopsi ke tree `optional-skills/`, pilot `re-code` dan merge `web-pentest` diverifikasi melalui jalur yang sama, sedangkan `red-ctf` dipisahkan sebagai paket GPL-3.0 di luar tree MIT.

Hasil utamanya bukan sekadar penambahan jumlah skill. Perubahan yang paling penting adalah adanya kontrak authoring yang konsisten, pemisahan lisensi yang eksplisit, jalur instalasi opt-in, dan bukti verifikasi yang dapat diperiksa ulang. Profil default tetap bersih: 54 skill aktif dan tidak ada modul `red-*` yang dipasang otomatis.

Verifikasi Phase 1 menunjukkan **1888 pass, 1 skip** pada suite skill, **90/90** kontrak adopsi, **12/12** invariant opt-out, **90/90** test modul, dan lint yang bersih. Satu skip adalah test khusus Windows yang berjalan di host Linux.

Laporan ini tidak mengklaim bahwa seluruh 128 skill sumber sudah diadopsi. Enam modul Phase 1 mengonsolidasikan 88 skill dari `reverse-skill`; 40 skill lain tetap di luar cakupan. `red-reverse` juga baru mencapai Phase 1, dan `red-ctf` baru terbukti dapat ditemukan serta dibaca, belum diuji menyelesaikan challenge end-to-end.

## 2. Scope dan otorisasi

### 2.1 In scope

- Scope resmi dan batas klaim: [00-SCOPE.md](00-SCOPE.md).
- Inventaris dan klasifikasi skill dari empat repositori sumber.
- Konsolidasi domain ke modul yang dapat dipilih secara opt-in.
- Kontrak frontmatter, trigger, prerequisite, tool mapping, dan routing reference.
- Pemisahan lisensi MIT dan GPL-3.0.
- Verifikasi kontrak, invariant, discovery, `skill_view`, dan pembacaan reference.
- Dokumentasi publik yang tersanitasi.

### 2.2 Out of scope

- Redistribusi source skill atau paket operasional di repositori ini.
- Pengujian pada target tanpa scope tertulis.
- Klaim performa atau penyelesaian target nyata.
- Publikasi log mentah, detail finding scanner, dan artefak internal.
- Modul yang belum masuk Phase 1.

### 2.3 Publication boundary

Dokumen ini adalah **edisi publik**. Informasi yang tidak diperlukan untuk memahami keputusan arsitektur dan hasil verifikasi diganti dengan `[Redacted 0xnhsec]`. Detail kategori ada di [kebijakan publikasi](05-PUBLICATION.md).

## 3. Masalah dan keputusan

Empat repositori sumber memiliki gaya authoring, bahasa, lisensi, dan tingkat kedalaman yang berbeda. Menyalin semuanya sekaligus akan menghasilkan katalog yang ramai, tumpang tindih, dan sulit diaudit. Karena itu, keputusan yang diambil adalah:

| Keputusan | Alasan | Konsekuensi |
|---|---|---|
| Konsolidasi per domain | Mengurangi tumpang tindih dan biaya routing | Beberapa skill sumber digabung dalam satu modul |
| Lima modul MIT masuk tree | Modul inti dapat dipasang lewat tier official | Modul ofensif tetap opt-in |
| `red-ctf` dipisahkan | Lisensi GPL-3.0 berbeda dari tree MIT | Perlu paket dan jalur `external_dirs` sendiri |
| `re-code` sebagai pilot | Menguji skill tunggal yang dalam | Tidak semua skill perlu dikonsolidasikan |
| `web-pentest` di-merge | Menghindari duplikasi dengan skill existing | Perubahan dilakukan evidence-led, bukan copy-paste |
| Default profile bersih | Mengurangi risiko aktivasi yang tidak disengaja | Operator harus memilih modul secara eksplisit |

Prinsip yang dipakai adalah **adopsi bertahap, bukan migrasi total**. Modul yang belum matang tetap berada di roadmap dan tidak diklaim selesai.

## 4. Arsitektur adopsi

Alur besarnya:

```text
Repositori sumber
    -> inventaris dan klasifikasi
    -> modul domain
    -> kontrak authoring
    -> policy review
    -> install opt-in di profil sementara
    -> verifikasi dan evidence
    -> publikasi tersanitasi
```

Lapisan detail, trust tier, dan batas lisensi dijelaskan di [arsitektur](03-ARCHITECTURE.md). Diagram alur tersedia di [workflow](02-WORKFLOW.md) dan file Mermaid mentah di [`diagrams/`](diagrams/).

## 5. Hasil adopsi

### 5.1 Katalog Phase 1

| Modul | Lisensi | Fokus | Referensi | Status |
|---|---|---|---:|---|
| `red-reverse` | MIT | Reverse engineering binary, firmware, dan native code | 12 | Diadopsi |
| `red-offensive` | MIT | AD/identity, cloud, exploit, evasion, attack chain | 8 | Diadopsi; opt-in wajib |
| `red-web` | MIT | Web/API, AppSec, code audit, database, LLM, supply chain | 7 | Diadopsi; opt-in wajib |
| `red-forensics` | MIT | DFIR, malware, threat hunting, threat intelligence | 5 | Diadopsi |
| `red-hardware` | MIT | Mobile, firmware, hardware, OT/ICS, RF, Wi-Fi | 7 | Diadopsi |
| `re-code` | MIT | Reverse engineering terarah dan workflow evidence | 15 | Pilot; diadopsi |
| `web-pentest` | MIT | Web pentest yang sudah ada, diperkaya hasil merge | 17 + kartu taxonomy | Merge; diadopsi |
| `red-ctf` | GPL-3.0 | CTF/AWD orchestration dan domain child | 10 | Paket terpisah; tidak masuk tree MIT |

Enam modul inti (lima MIT + `red-ctf`) memiliki total 49 reference. `re-code` dan `web-pentest` adalah entri pilot yang mengikuti kontrak yang sama, bukan modul tambahan dari `reverse-skill`.

### 5.2 Yang diadopsi ke tree

Lima modul MIT dan dua pilot masuk ke `optional-skills/security/` pada kategori yang sesuai. Modul tersebut:

- memiliki deskripsi pendek yang tidak bertabrakan dengan index skill SNXX;
- menaruh trigger di body, bukan mengandalkan field yang tidak dibaca runtime;
- memiliki prerequisite dan tool mapping;
- merutekan seluruh reference dari `SKILL.md`;
- memiliki contoh opt-out yang menunjuk nama modul sendiri;
- memiliki kontrak test.

### 5.3 `red-ctf` sebagai paket terpisah

`red-ctf` tidak disalin ke tree MIT. Modul ini dikemas terpisah dengan `LICENSE` GPL-3.0 dan diuji melalui `external_dirs`. Hasil yang terbukti adalah **load-path proof**: modul ditemukan oleh `skills list`, `SKILL.md` dapat dibaca, dan reference orchestrator dapat dibuka.

Yang **belum** dibuktikan adalah kemampuan menyelesaikan challenge CTF end-to-end. Load-path proof tidak sama dengan solve proof.

### 5.4 Yang tidak diadopsi

- Seluruh 128 skill sumber: tidak.
- Seluruh 88 skill `reverse-skill`: belum; Phase 1 baru mengonsolidasikan domain utama.
- Skill common/engineering di luar red-team: tidak termasuk Phase 1.
- Modul yang masih memerlukan dependency tool pihak ketiga: prerequisite dicatat, tetapi tool tidak dipasang otomatis.

## 6. Ringkasan verifikasi

| Pemeriksaan | Hasil | Catatan |
|---|---:|---|
| Suite skill | 1888 pass, 1 skip | Skip adalah test khusus Windows di host Linux |
| Kontrak adopsi | 90/90 pass | Lima modul red, `re-code`, `web-pentest` |
| Invariant opt-out | 12/12 pass | Contoh `skills.disabled` dan larangan prosa pra-adopsi |
| Test modul | 90/90 pass | Test authoring dan struktur modul |
| Lint | Bersih | Tidak ada dependency baru yang ditulis ke repo |
| Install opt-in | Diizinkan | Dilakukan di profil sementara, bukan profil default |
| Profil default | 54 enabled | Tidak ada `red-*` |
| Header provenance | 39 adopted, 0 staging | Source module disinkronkan dengan tree adopted |
| `red-ctf` di tree MIT | 0 file | Paket GPL terpisah |

Detail model verifikasi dan batas bukti ada di [verifikasi](04-VERIFICATION.md).

## 7. Evidence -> Finding -> Path

### 7.1 Scope summary

- **Jenis pekerjaan:** adopsi skill dan dokumentasi arsitektur.
- **Target:** tree skill SNXX dan modul RedWolf.
- **Authorization:** perubahan hanya pada skill, dokumentasi, test, dan paket pendukung; core runtime tidak diubah.
- **Batas:** tidak ada engagement terhadap target eksternal.

### 7.2 Evidence

| ID | Source reference | Ringkasan | Integrity |
|---|---|---|---|
| E-01 | Inventaris internal, `[Redacted 0xnhsec]` | Empat repositori sumber, 128 skill unik, 129 `SKILL.md` | Hash `[Redacted 0xnhsec]` |
| E-02 | Kontrak test internal, `[Redacted 0xnhsec]` | 90/90 kontrak adopsi lulus | Hash `[Redacted 0xnhsec]` |
| E-03 | Suite skill internal, `[Redacted 0xnhsec]` | 1888 pass, 1 skip | Hash `[Redacted 0xnhsec]` |
| E-04 | Test modul internal, `[Redacted 0xnhsec]` | 90/90 test modul lulus | Hash `[Redacted 0xnhsec]` |
| E-05 | Policy dan install internal, `[Redacted 0xnhsec]` | Install opt-in diizinkan di profil sementara | Hash `[Redacted 0xnhsec]` |
| E-06 | Load-path `red-ctf`, `[Redacted 0xnhsec]` | `skills list` dan `skill_view` berhasil | Hash `[Redacted 0xnhsec]` |
| E-07 | Audit header dan prosa, `[Redacted 0xnhsec]` | 39 header adopted, 0 staging, 0 frasa pra-adopsi | Hash `[Redacted 0xnhsec]` |

### 7.3 Findings

| ID | Severity | Evidence | Confidence | Location | Status |
|---|---|---|---|---|---|
| F-01 | `n/a_re` | E-01, E-02, E-03 | High | Tree `optional-skills/security/` | Closed |
| F-02 | `n/a_re` | E-01, E-05 | High | Batas lisensi MIT/GPL | Closed |
| F-03 | `n/a_re` | E-05 | High | Profil default dan jalur opt-in | Closed |
| F-04 | Medium | E-01, E-06 | High | `red-ctf` dan cakupan Phase 2 | Open |
| F-05 | `n/a_re` | E-07 | High | Dokumentasi dan source module | Closed |

**F-01 — Adopsi Phase 1 berhasil.** Lima modul MIT, `re-code`, dan `web-pentest` masuk ke tree yang benar dan lulus kontrak.

**F-02 — Pemisahan lisensi berhasil.** Tidak ada `red-ctf` di tree MIT; paket GPL memiliki jalur distribusi sendiri.

**F-03 — Default aman.** Modul ofensif tidak aktif otomatis; profil default tetap 54 skill tanpa `red-*`.

**F-04 — Gap fungsional masih terbuka.** `red-ctf` belum diuji solve end-to-end; `red-reverse` baru Phase 1; Wave 2/3 belum selesai.

**F-05 — Dokumentasi konsisten.** Prosa pra-adopsi dan header staging sudah dibersihkan, termasuk sinkronisasi source module.

### 7.4 Path

| ID | Path type | Langkah | Evidence |
|---|---|---|---|
| P-01 | `callflow` | Inventaris -> klasifikasi -> konsolidasi -> kontrak -> policy -> install -> verifikasi -> publikasi | E-01..E-05, E-07 |
| P-02 | `callflow` | Paket GPL -> `external_dirs` -> `skills list` -> `skill_view` -> reference | E-06 |
| P-03 | `callflow` | Operator memilih modul -> tugas dalam scope -> evidence -> disable/rollback | E-05 |

Tidak ada `path_type=attack` dalam laporan ini karena pekerjaan yang didokumentasikan adalah adopsi dan verifikasi, bukan engagement ofensif terhadap target.

## 8. Timeline

| Tanggal | Kejadian |
|---|---|
| 2026-10-20/21 | Inventaris sumber dan pemetaan awal 128 skill |
| 2026-10-21 | Konsolidasi enam modul dan penulisan kontrak |
| 2026-10-21 | Perbaikan prosa pra-adopsi, opt-out, manifest, dan header |
| 2026-10-21 | Verifikasi kontrak, invariant, dan suite skill |
| 2026-10-21 | Install opt-in di profil sementara |
| 2026-10-21 | Pemisahan `red-ctf` sebagai paket GPL dan load-path proof |
| 2026-10-21 | Sinkronisasi source module dan audit akhir |
| 2026-10-21 | Publikasi dokumentasi tersanitasi |

## 9. Risiko, batas klaim, dan gap

### 9.1 Batas klaim

Yang **boleh** diklaim:

- Tujuh entri skill masuk ke tree `optional-skills/`: lima modul MIT, `re-code`, dan merge `web-pentest`.
- Kontrak adopsi, invariant opt-out, suite skill, dan test modul lulus.
- Jalur official mengizinkan instalasi modul berisiko tinggi di lingkungan terkontrol.
- Profil default tidak berisi modul `red-*`.
- `red-ctf` tidak berada di tree MIT dan dapat dimuat melalui `external_dirs`.
- Dokumentasi publik sudah disanitasi.

Yang **tidak boleh** diklaim:

- Seluruh 128 skill sudah diadopsi.
- `red-ctf` sudah menyelesaikan challenge CTF end-to-end.
- `red-reverse` sudah lengkap.
- Seluruh roadmap RedWolf sudah selesai.
- Dokumentasi publik ini adalah distribusi paket operasional.

### 9.2 Risiko utama

| Risiko | Dampak | Mitigasi |
|---|---|---|
| Aktivasi modul ofensif tanpa scope | Penyalahgunaan atau tindakan di luar otorisasi | Opt-in, gate scope, disable/rollback |
| Pencampuran lisensi | Masalah distribusi dan kepatuhan | Pemisahan tree dan paket GPL |
| Klaim berlebihan | Kepercayaan publik turun | Batas klaim eksplisit dan evidence chain |
| Data internal bocor | Risiko operasional dan privasi | Redaksi `[Redacted 0xnhsec]` dan review publikasi |
| Gap Phase 2 dianggap selesai | Ekspektasi yang salah | Roadmap dengan exit criteria |

## 10. Rekomendasi

1. Uji `red-ctf` pada satu challenge CTF di sandbox sebelum mengklaim solve capability.
2. Lanjutkan `red-reverse` Phase 2 dengan reference yang masih kurang.
3. Jalankan Wave 2/3 dengan kontrak dan test yang sama.
4. Pertahankan profil default bersih dan gunakan `skills.disabled` untuk opt-out.
5. Perbarui dokumen publik hanya setelah evidence internal berubah dan checksum diverifikasi.
6. Jangan mempublikasikan log mentah, payload, path lokal, atau checksum artefak.

## 11. Referensi

- [Workflow](02-WORKFLOW.md)
- [Arsitektur](03-ARCHITECTURE.md)
- [Verifikasi](04-VERIFICATION.md)
- [Publikasi dan redaksi](05-PUBLICATION.md)
- [Roadmap](06-ROADMAP.md)
- [Diagram Mermaid](diagrams/)
- `LICENSE` repositori ini

## 12. Glosarium

| Istilah | Arti |
|---|---|
| **Adopted** | Modul sudah berada di tree SNXX dan memiliki kontrak |
| **Opt-in** | Modul tidak aktif sampai operator memilihnya |
| **Official tier** | Jalur distribusi tepercaya dengan trust `builtin` |
| **Project tier** | Jalur project yang lebih ketat; tidak dipakai untuk modul ofensif |
| **Load-path proof** | Bukti modul ditemukan dan dibaca, bukan bukti solve |
| **Evidence chain** | Rantai E -> F -> P yang menghubungkan bukti, temuan, dan alur |
| **Phase 1** | Cakupan adopsi awal; bukan seluruh roadmap |
