# Kebijakan publikasi dan redaksi

Repositori ini adalah **edisi publik tersanitasi** dari dokumentasi internal. Tujuannya adalah membagikan keputusan arsitektur dan hasil yang dapat diverifikasi tanpa mengekspos bahan operasional, data pribadi, atau detail internal yang tidak perlu.

## 1. Prinsip publikasi

- **Minimal necessary detail.** Tampilkan informasi yang diperlukan untuk memahami keputusan dan status.
- **Evidence tanpa kebocoran.** Ringkasan hasil boleh tampil; log mentah dan checksum artefak tidak.
- **Konteks sebelum klaim.** Setiap angka atau status harus disertai batas interpretasinya.
- **Redaksi eksplisit.** Informasi yang sengaja ditahan diberi tanda `[Redacted 0xnhsec]`.
- **Tidak ada payload.** Dokumentasi tidak memuat contoh eksploitasi, kredensial, atau perintah ofensif yang dapat langsung dipakai.

## 2. Matriks exposure

| Area | Publik | Disensor / ditahan |
|---|---|---|
| Tujuan dan arsitektur | Ya | Detail implementasi internal |
| Nama modul dan domain | Ya | Path lokal dan identitas build |
| Lisensi | Ya | Lokasi paket dan checksum artefak |
| Jumlah reference | Ya | Isi reference dan payload |
| Hasil test | Ringkasan | Log mentah dan perintah internal |
| Scanner | Kelas risiko dan status review | Detail finding dan contoh temuan |
| Instalasi | Status dan gate | Konfigurasi dan path profil |
| Runtime | Alur discovery dan view | Konfigurasi runtime dan identifier host |
| `red-ctf` | Status paket terpisah | Nama artefak, isi paket, checksum |
| Roadmap | Ya | Target tanggal internal dan detail engagement |

## 3. Token redaksi

String `[Redacted 0xnhsec]` berarti:

- informasi ada di evidence internal, tetapi tidak dipublikasikan;
- informasi tidak diperlukan untuk memahami keputusan publik;
- informasi tidak boleh direkonstruksi dari dokumen ini;
- menghapus token tidak otomatis membuat informasi layak dipublikasikan.

Token ini bukan TODO dan bukan tanda dokumen belum selesai. Dokumen dianggap lengkap untuk tingkat exposure yang dipilih.

## 4. Kategori yang ditahan

### 4.1 Identitas dan lingkungan

- Path absolut dan nama direktori rumah.
- Nama host, nama profil, dan identifier mesin.
- Build identity lengkap dan konfigurasi runtime.
- Kredensial, token, dan materi autentikasi.

### 4.2 Bukti mentah

- Log test dan install mentah.
- Output scanner per finding.
- Checksum artefak internal.
- File evidence yang dapat dipakai untuk merekonstruksi lingkungan.

### 4.3 Bahan operasional

- Payload, exploit, dan contoh command ofensif.
- Konfigurasi target dan hasil engagement.
- Detail challenge atau flag.
- Paket distribusi dan isi reference yang tidak tersanitasi.

## 5. Yang boleh dipublikasikan

- Ringkasan arsitektur dan pembagian domain.
- Nama modul, lisensi, dan status adopsi.
- Jumlah reference dan cakupan domain.
- Ringkasan hasil test tanpa log mentah.
- Status trust tier dan alasan pemisahan lisensi.
- Alur kerja, gate, dan rollback.
- Roadmap dengan exit criteria.

## 6. Checklist sebelum publikasi

- [ ] Tidak ada path absolut atau nama host.
- [ ] Tidak ada kredensial, token, atau identifier pribadi.
- [ ] Tidak ada payload atau perintah ofensif yang dapat langsung dipakai.
- [ ] Tidak ada log mentah atau detail finding scanner.
- [ ] Tidak ada checksum atau artefak paket internal.
- [ ] Semua klaim punya batas interpretasi.
- [ ] Token `[Redacted 0xnhsec]` hanya dipakai untuk informasi yang memang ditahan.
- [ ] Lisensi dan pemisahan MIT/GPL dijelaskan dengan benar.
- [ ] Dokumen tidak mengklaim seluruh roadmap selesai.
- [ ] Link internal dan diagram Mermaid valid.

## 7. Review perubahan

Setiap perubahan dokumen publik harus melewati review berikut:

1. **Akurasi.** Apakah status sesuai evidence internal?
2. **Redaksi.** Apakah ada data yang seharusnya ditahan?
3. **Konsistensi.** Apakah angka dan istilah sama dengan dokumen lain?
4. **Batas klaim.** Apakah pembaca bisa salah menyimpulkan capability?
5. **Lisensi.** Apakah tidak ada pencampuran MIT dan GPL?

Jika salah satu gagal, perubahan tidak dipublikasikan.

## 8. Lisensi dan distribusi

Dokumen ini mengikuti `LICENSE` repositori. Modul yang dibahas mempertahankan lisensi asalnya. Publikasi dokumen tidak memberikan lisensi tambahan atas paket, payload, atau source skill yang tidak disertakan.

## 9. Kontak dan koreksi

Koreksi faktual dapat diajukan melalui issue di repositori. Jangan meminta atau mengirim ulang data yang sudah ditandai `[Redacted 0xnhsec]` melalui issue publik.
