# Scope dan otorisasi

Dokumen ini menetapkan batas pekerjaan yang dilaporkan di repositori ini. Fokusnya adalah adopsi skill dan dokumentasi, bukan engagement terhadap target eksternal.

## 1. Identitas proyek

| Atribut | Nilai |
|---|---|
| Nama proyek | `RTA-SNXX-20261020` |
| RTA | *Red Team Agent* |
| SNXX | Nama diri (*noun*), bukan akronim |
| 20261020 | Tanggal `YYMMDD`: 20 Oktober 2026 |
| Jenis | Adopsi skill, verifikasi, dan dokumentasi arsitektur |
| Objek | Modul red-team dan tree skill SNXX |
| Lingkungan | Lokal dan terisolasi |
| Tanggal laporan | 21 Oktober 2026 |
| Klasifikasi | Publik tersanitasi |

Nama lengkap proyek: **Red Team Agent — SNXX — 20 October 2026**.

## 2. In scope

- Inventaris empat repositori sumber dan 128 skill unik.
- Konsolidasi domain menjadi modul yang dapat dipilih secara opt-in.
- Kontrak authoring, routing reference, dan metadata lisensi.
- Policy review dan trust tier.
- Instalasi opt-in di profil sementara.
- Verifikasi discovery, `skill_view`, dan pembacaan reference.
- Pemisahan paket GPL dari tree MIT.
- Dokumentasi publik yang tersanitasi.

## 3. Out of scope

- Pengujian terhadap target, host, atau jaringan tanpa scope tertulis.
- Redistribusi source skill, payload, atau paket operasional.
- Klaim performa atau penyelesaian target nyata.
- Publikasi log mentah, path absolut, kredensial, dan checksum artefak.
- Skill common/engineering yang tidak termasuk Phase 1.
- Gap fungsional yang belum memiliki evidence baru.

## 4. Network profile

Pekerjaan yang didokumentasikan tidak menggunakan network profile untuk menyerang target. Semua verifikasi instalasi dan pembacaan modul dilakukan di lingkungan lokal atau sementara yang terisolasi. Tidak ada host eksternal yang menjadi sasaran dalam laporan ini.

## 5. Otorisasi

Perubahan yang diizinkan pada Phase 1:

- menambah atau memperbarui modul di `optional-skills/`;
- menambah test kontrak dan invariant;
- memperbarui dokumentasi, manifest, dan evidence;
- membuat paket GPL terpisah untuk `red-ctf`;
- melakukan instalasi uji di profil sementara.

Perubahan yang tidak dilakukan:

- mengubah core runtime SNXX;
- menyalin `red-ctf` ke tree MIT;
- mengaktifkan modul ofensif di profil default;
- mempublikasikan data internal tanpa redaksi;
- melakukan push atau sinkronisasi otomatis ke repositori publik.

## 6. Publication boundary

Edisi ini adalah dokumentasi publik. Informasi yang tidak diperlukan untuk memahami keputusan dan status diganti dengan `[Redacted 0xnhsec]`. Kategori yang ditahan dijelaskan di [kebijakan publikasi](05-PUBLICATION.md).

## 7. Batas klaim

Scope ini tidak mengizinkan klaim berikut:

- seluruh 128 skill sudah diadopsi;
- `red-ctf` sudah menyelesaikan challenge end-to-end;
- `red-reverse` sudah lengkap;
- seluruh roadmap sudah selesai;
- dokumentasi ini adalah distribusi paket operasional.
