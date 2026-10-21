<p align="center">
  <img src="snxx-project.png" alt="SNXX logo" width="220">
</p>

<h1 align="center">RTA-SNXX</h1>

<p align="center">
  Dokumentasi publik adopsi modul red-team ke runtime SNXX: keputusan arsitektur, batas lisensi, alur kerja, ringkasan verifikasi, dan roadmap yang masih terbuka.
</p>

<p align="center">
  <a href="README.en.md">English</a> · <strong>Bahasa Indonesia</strong>
</p>

> **Repositori:** `RTA-SNXX-20261020`

> **Edisi publik tersanitasi.** Path lokal, identitas build, log mentah, detail temuan scanner, checksum artefak, dan konfigurasi internal diganti dengan `[Redacted 0xnhsec]`. Repositori ini **tidak** mendistribusikan source skill, payload, atau paket operasional.

## Nama proyek

| Bagian | Arti |
|---|---|
| **RTA** | *Red Team Agent* |
| **SNXX** | Nama diri (*noun*), bukan akronim |
| **20261020** | Tanggal dalam format `YYMMDD`: 20 Oktober 2026 |

Nama lengkap: **RTA-SNXX-20261020** — *Red Team Agent — SNXX — 20 October 2026*.

Logo proyek: [`snxx-project.png`](snxx-project.png).

## Ringkasan

Proyek ini mendokumentasikan Phase 1 adopsi empat sumber skill ke SNXX. Lima modul MIT diadopsi ke tier optional, dua pilot (`re-code` dan `web-pentest`) masuk melalui jalur yang sama, dan `red-ctf` dipisahkan sebagai paket GPL-3.0 di luar tree MIT. Modul ofensif tetap opt-in; profil default tidak diisi otomatis.

Hasil verifikasi Phase 1: **1888 pass, 1 skip** pada suite skill, **90/90** kontrak adopsi, **12/12** invariant opt-out, **90/90** test modul, dan pemeriksaan lint bersih. Satu skip berasal dari test khusus Windows yang dijalankan di host Linux.

## Status

| Area | Status |
|---|---|
| Adopsi 5 modul MIT | Selesai dan terverifikasi |
| Pilot `re-code` | Selesai dan terverifikasi |
| Merge `web-pentest` | Selesai dan terverifikasi |
| `red-ctf` GPL-3.0 | Paket terpisah; load-path terverifikasi, solve end-to-end belum |
| Profil default | 54 skill aktif; tidak ada `red-*` |
| Dokumentasi publik | Edisi tersanitasi, tersedia di repositori ini |
| Fase berikutnya | `red-reverse` Phase 2, Wave 2/3, branding sweep |

## Peta dokumentasi

| Dokumen | Isi |
|---|---|
| [Scope dan otorisasi](docs/00-SCOPE.md) | Batas pekerjaan, network profile, dan klaim yang tidak diizinkan |
| [Laporan adopsi](docs/01-ADOPTION-REPORT.md) | Laporan utama, hasil, evidence chain, batas klaim |
| [Workflow](docs/02-WORKFLOW.md) | Alur kerja end-to-end, gate, exception, rollback |
| [Arsitektur](docs/03-ARCHITECTURE.md) | Lapisan sistem, trust tier, batas lisensi, runtime lifecycle |
| [Verifikasi](docs/04-VERIFICATION.md) | Model verifikasi, hasil ringkas, integritas bukti |
| [Publikasi dan redaksi](docs/05-PUBLICATION.md) | Matriks exposure, aturan redaksi, checklist publikasi |
| [Roadmap dan gap](docs/06-ROADMAP.md) | Pekerjaan yang belum diklaim selesai |
| [Diagram Mermaid](docs/diagrams/) | File `.mmd` mentah untuk alur adopsi, verifikasi, dan runtime |

## Mulai membaca

1. Baca [scope dan otorisasi](docs/00-SCOPE.md) untuk memahami batas pekerjaan.
2. Baca [laporan adopsi](docs/01-ADOPTION-REPORT.md) untuk hasil dan batas klaim.
3. Baca [workflow](docs/02-WORKFLOW.md) untuk urutan kerja dan gate keputusan.
4. Baca [arsitektur](docs/03-ARCHITECTURE.md) untuk memahami trust tier dan pemisahan lisensi.
5. Gunakan [roadmap](docs/06-ROADMAP.md) untuk melihat apa yang masih terbuka.

## Cakupan

**Termasuk dalam dokumentasi publik:**

- Ringkasan arsitektur dan katalog modul.
- Alur adopsi, verifikasi, dan penggunaan opt-in.
- Ringkasan hasil test dan status instalasi.
- Kebijakan redaksi dan batas klaim.
- Diagram alur dalam format Mermaid.

**Tidak termasuk:**

- Source code atau payload skill.
- Path absolut, nama host, kredensial, dan konfigurasi runtime.
- Log mentah, detail finding scanner, dan checksum artefak internal.
- Paket distribusi GPL dan petunjuk operasional yang tidak tersanitasi.
- Klaim performa atau hasil penyelesaian target nyata.

## Prinsip

- **Opt-in by default.** Modul ofensif tidak boleh aktif otomatis.
- **License boundary is a hard gate.** MIT dan GPL-3.0 tidak dicampur dalam satu tree distribusi.
- **Evidence before claim.** Setiap klaim status harus punya jejak verifikasi.
- **Public means sanitized.** Detail yang tidak perlu untuk memahami keputusan tidak dipublikasikan.
- **Phase 1 bukan seluruh roadmap.** Enam modul bukan pengganti seluruh katalog sumber.

## Lisensi

Repositori dokumentasi ini mengikuti `LICENSE` di root repositori. Modul yang diadopsi mempertahankan lisensi asalnya: MIT untuk lima modul inti dan pilot, GPL-3.0 untuk `red-ctf` yang dipisahkan. Dokumen ini tidak mengubah lisensi kode pihak ketiga.
