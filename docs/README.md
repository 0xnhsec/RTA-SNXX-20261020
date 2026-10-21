<p align="center">
  <img src="../snxx-project.png" alt="SNXX logo" width="140">
</p>

# Dokumentasi RTA-SNXX

<p align="center">
  <a href="en/README.md">English</a> · <strong>Bahasa Indonesia</strong>
</p>

Dokumentasi ini menjelaskan bagaimana modul red-team dari beberapa repositori sumber dipetakan, dikonsolidasikan, diadopsi, diverifikasi, dan dipublikasikan ke SNXX.

## Urutan baca

| Urutan | Dokumen | Pertanyaan yang dijawab |
|---:|---|---|
| 0 | [Scope dan otorisasi](00-SCOPE.md) | Apa batas pekerjaan dan klaim yang tidak diizinkan? |
| 1 | [Laporan adopsi](01-ADOPTION-REPORT.md) | Apa yang diadopsi, apa hasilnya, dan apa batas klaimnya? |
| 2 | [Workflow](02-WORKFLOW.md) | Bagaimana alur kerja dan gate keputusannya? |
| 3 | [Arsitektur](03-ARCHITECTURE.md) | Bagaimana lapisan sistem dan batas kepercayaannya? |
| 4 | [Verifikasi](04-VERIFICATION.md) | Bukti apa yang mendukung status saat ini? |
| 5 | [Publikasi](05-PUBLICATION.md) | Apa yang boleh tampil di GitHub dan apa yang disensor? |
| 6 | [Roadmap](06-ROADMAP.md) | Apa yang belum selesai dan apa exit criteria-nya? |

## Diagram

File Mermaid mentah tersedia di [`diagrams/`](diagrams/):

- [`01-adoption-workflow.mmd`](diagrams/01-adoption-workflow.mmd) — alur adopsi dari inventaris sampai publikasi.
- [`02-verification-workflow.mmd`](diagrams/02-verification-workflow.mmd) — alur verifikasi dan evidence handling.
- [`03-runtime-load-flow.mmd`](diagrams/03-runtime-load-flow.mmd) — alur pemuatan modul saat runtime.

Diagram yang sama juga disematkan di [workflow](02-WORKFLOW.md) agar langsung dirender oleh GitHub.

## Konvensi redaksi

String `[Redacted 0xnhsec]` menandai informasi yang sengaja tidak dipublikasikan. Ini bukan placeholder yang belum diisi. Detail kategori dan alasannya ada di [kebijakan publikasi](05-PUBLICATION.md).

## Status dokumen

- **Versi:** 1.0
- **Tanggal:** 21 Oktober 2026
- **Cakupan:** Phase 1 adopsi dan dokumentasi publiknya
- **Sifat:** dokumentasi; bukan distribusi kode atau paket operasional
