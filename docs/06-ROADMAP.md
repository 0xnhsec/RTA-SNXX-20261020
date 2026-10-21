# Roadmap dan gap

Dokumen ini mencatat pekerjaan yang **belum** diklaim selesai. Tujuannya mencegah Phase 1 dibaca sebagai penyelesaian seluruh roadmap.

## 1. Posisi saat ini

| Area | Status | Catatan |
|---|---|---|
| Adopsi lima modul MIT | Selesai | Tree optional, kontrak dan test lulus |
| Pilot `re-code` | Selesai | Kontrak dan test lulus |
| Merge `web-pentest` | Selesai | Evidence-led merge |
| `red-ctf` load-path | Selesai | Ditemukan dan dibaca lewat `external_dirs` |
| `red-ctf` solve end-to-end | Belum | Perlu sandbox dan scope eksplisit |
| `red-reverse` Phase 2 | Belum | 12 reference tambahan |
| Wave 2/3 | Belum | Skill inti yang belum termodul |
| Branding sweep | Belum | Locale, docs, desktop |
| Arsip log lama | Belum | Lokasi internal `[Redacted 0xnhsec]` |

## 2. Gap dan exit criteria

### 2.1 `red-ctf` end-to-end

**Gap:** load-path proof hanya membuktikan modul dapat ditemukan dan dibaca.

**Exit criteria:**

- satu challenge CTF dijalankan di sandbox;
- scope dan otorisasi tercatat;
- langkah solve dapat direproduksi;
- hasil dan keterbatasan dicatat sebagai evidence;
- tidak ada klaim kemampuan di luar challenge yang diuji.

**Status:** open.

### 2.2 `red-reverse` Phase 2

**Gap:** Phase 1 belum mencakup seluruh domain reverse engineering.

**Cakupan yang belum ada:**

- macOS dan Mach-O;
- JavaScript dan runtime web;
- DSL/VM;
- protocol reverse engineering;
- thick client;
- browser extension;
- dynamic analysis dan anti-analysis;
- deep-dive per bahasa.

**Exit criteria:**

- reference baru ditambahkan dan dirutekan dari `SKILL.md`;
- kontrak dan test modul diperbarui;
- discovery dan reference reading diverifikasi;
- cakupan yang belum ada tetap dinyatakan terbuka.

**Status:** open.

### 2.3 Wave 2/3

**Gap:** enam modul Phase 1 bukan pengganti seluruh katalog sumber.

**Exit criteria:**

- skill inti yang belum termodul dipetakan;
- setiap modul mengikuti kontrak authoring yang sama;
- tidak ada duplikasi semantik;
- test kontrak dan invariant lulus;
- prompt index diukur ulang;
- status adopsi diperbarui di manifest internal dan dokumen publik.

**Status:** open.

### 2.4 Branding sweep

**Gap:** masih ada sisa branding lama di locale, dokumentasi, dan desktop.

**Exit criteria:**

- istilah lama tidak muncul di surface publik;
- locale dan dokumen konsisten;
- build desktop diperiksa;
- tidak ada regresi fungsi.

**Status:** open.

### 2.5 Arsip log lama

**Gap:** sebagian log runtime lama masih berada di lokasi sementara internal `[Redacted 0xnhsec]`.

**Exit criteria:**

- log yang masih diperlukan dipindahkan ke evidence store;
- log yang tidak diperlukan dihapus sesuai kebijakan retensi;
- checksum evidence diperbarui;
- tidak ada path sementara yang dirujuk dokumen publik.

**Status:** open.

## 3. Prioritas

| Prioritas | Pekerjaan | Alasan |
|---:|---|---|
| P1 | `red-ctf` end-to-end | Menutup gap capability yang paling mudah disalahpahami |
| P1 | `red-reverse` Phase 2 | Melengkapi domain yang belum tercakup |
| P2 | Wave 2/3 | Memperluas cakupan tanpa mengulang kesalahan authoring |
| P2 | Branding sweep | Konsistensi produk dan dokumentasi |
| P3 | Arsip log lama | Housekeeping dan retensi |

## 4. Non-goals

- Mengadopsi seluruh 128 skill sekaligus.
- Menyalin `red-ctf` ke tree MIT.
- Mengaktifkan modul ofensif di profil default.
- Mengklaim solve capability tanpa uji end-to-end.
- Mempublikasikan payload, log mentah, atau checksum artefak.
- Menjadikan dokumentasi publik sebagai paket distribusi.

## 5. Aturan pembaruan roadmap

1. Status hanya berubah jika ada evidence baru.
2. Gap yang selesai dipindahkan ke bagian status dengan tanggal.
3. Gap baru harus punya exit criteria.
4. Dokumen publik tidak boleh memuat target tanggal internal yang belum disetujui.
5. Jika evidence dicabut, status harus dikembalikan ke open.

## 6. Ringkasan satu kalimat

Phase 1 sudah cukup untuk dipakai sebagai fondasi opt-in, tetapi belum cukup untuk mengklaim cakupan penuh, kemampuan CTF end-to-end, atau penyelesaian seluruh roadmap.
