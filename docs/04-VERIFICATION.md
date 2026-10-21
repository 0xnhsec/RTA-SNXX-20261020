# Verifikasi dan bukti

Dokumen ini merangkum model verifikasi Phase 1 dan hasil yang boleh dipublikasikan. Log mentah, perintah internal, path absolut, dan checksum artefak disimpan secara privat dan diganti dengan `[Redacted 0xnhsec]` di edisi ini.

## 1. Model verifikasi

Verifikasi tidak berhenti pada “file berhasil dipasang”. Ada lima lapisan pemeriksaan:

| Lapisan | Pertanyaan | Bukti yang diharapkan |
|---|---|---|
| Struktur | Apakah `SKILL.md` dan reference lengkap? | Inspeksi struktur dan routing |
| Kontrak | Apakah frontmatter, trigger, prerequisite, dan tool mapping sesuai? | Test kontrak per modul |
| Policy | Apakah modul boleh dipasang pada tier yang dipilih? | Verdict dan keputusan policy |
| Runtime | Apakah modul ditemukan, dibaca, dan reference-nya dapat diakses? | `skills list` dan `skill_view` |
| Integritas | Apakah evidence konsisten dan tidak berubah? | Checksum dan audit ulang |

## 2. Hasil ringkas

| Pemeriksaan | Hasil | Interpretasi |
|---|---:|---|
| Suite skill | 1888 pass, 1 skip | Tidak ada kegagalan |
| Kontrak adopsi | 90/90 pass | Tujuh entri kontrak terpenuhi |
| Invariant opt-out | 12/12 pass | Contoh disable dan larangan prosa pra-adopsi |
| Test modul | 90/90 pass | Struktur dan authoring modul |
| Lint | Bersih | Tidak ada dependency baru |
| Install opt-in | Diizinkan | Hanya di profil sementara |
| Profil default | 54 enabled | Tidak ada `red-*` |
| `red-ctf` di tree MIT | 0 file | Pemisahan lisensi terjaga |

Satu skip pada suite skill adalah test kontrak khusus Windows yang dijalankan pada host Linux. Skip ini bukan kegagalan modul.

## 3. Cakupan test

### 3.1 Kontrak adopsi

Kontrak mencakup:

- deskripsi pendek dan tidak bertabrakan dengan index;
- trigger di body;
- prerequisite dan tool mapping;
- routing reference dari `SKILL.md`;
- contoh opt-out yang menunjuk nama modul sendiri;
- metadata lisensi dan provenance.

### 3.2 Invariant opt-out

Invariant memeriksa dua hal yang mudah regresi:

1. Contoh `skills.disabled` harus menunjuk nama modul yang benar.
2. `SKILL.md` tidak boleh memuat prosa pra-adopsi.

Invariant ini membuat perbaikan teks tidak hanya bersifat sekali jalan.

### 3.3 Test modul

Test modul memeriksa struktur, reference, dan kontrak authoring. Test ini melengkapi suite skill utama, bukan menggantikannya.

## 4. Verifikasi runtime

### 4.1 Modul MIT

Modul MIT diverifikasi melalui:

1. Install di profil sementara.
2. `skills list` untuk memastikan modul muncul.
3. `skill_view` untuk membaca `SKILL.md`.
4. Pembacaan reference utama.
5. Pemeriksaan bahwa profil default tidak berubah.

### 4.2 `red-ctf` GPL

`red-ctf` diverifikasi sebagai paket terpisah melalui `external_dirs`:

- modul ditemukan sebagai external/local;
- `SKILL.md` dapat dibaca;
- reference orchestrator dapat dibaca;
- paket tidak muncul di tree `optional-skills/`;
- tidak ada klaim solve challenge.

Load-path proof menjawab pertanyaan “apakah modul dapat dimuat dan dibaca?”. Ia tidak menjawab “apakah modul berhasil menyelesaikan challenge?”.

## 5. Policy dan instalasi

| Pemeriksaan | Hasil publik |
|---|---|
| Review policy | Selesai |
| Detail finding scanner | `[Redacted 0xnhsec]` |
| Verdict per modul | Diringkas sebagai kelas risiko, bukan detail finding |
| Install official | Diizinkan untuk modul yang lolos gate |
| Install project tier | Tidak dipakai untuk modul ofensif |
| Default profile | Tidak berubah |

Modul ofensif tetap memerlukan opt-in eksplisit. Keberhasilan install tidak berarti modul boleh diaktifkan untuk engagement normal.

## 6. Integritas evidence

Evidence internal mencakup:

- hasil suite dan kontrak;
- hasil test modul;
- audit prosa dan header;
- status install di profil sementara;
- status profil default;
- load-path `red-ctf`;
- checksum folder evidence.

Untuk edisi publik:

- jumlah dan ringkasan hasil boleh ditampilkan;
- log mentah tidak ditampilkan;
- path absolut dan nama host diganti;
- checksum artefak diganti `[Redacted 0xnhsec]`;
- detail finding scanner tidak ditampilkan.

## 7. Batas bukti

Verifikasi ini membuktikan:

- modul adopted berada di tree yang benar;
- kontrak dan invariant lulus;
- instalasi opt-in berhasil;
- modul dapat ditemukan dan dibaca;
- batas lisensi tidak dilanggar;
- profil default tetap bersih.

Verifikasi ini **tidak** membuktikan:

- seluruh 128 skill sudah diadopsi;
- `red-ctf` dapat menyelesaikan challenge;
- `red-reverse` sudah lengkap;
- modul bebas dari semua risiko operasional;
- performa atau kualitas hasil pada target nyata.

## 8. Audit ulang

Audit ulang dilakukan dengan urutan:

1. Periksa checksum evidence internal.
2. Jalankan suite dan kontrak pada lingkungan terisolasi.
3. Verifikasi status profil default.
4. Verifikasi load-path modul GPL.
5. Periksa ulang dokumen publik terhadap aturan redaksi.
6. Perbarui [roadmap](06-ROADMAP.md) jika ada perubahan status.

Jika salah satu langkah gagal, status “selesai” pada dokumen publik harus dicabut sampai evidence baru tersedia.
