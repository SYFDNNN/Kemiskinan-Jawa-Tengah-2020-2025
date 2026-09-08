# Data

`raw/` berisi enam ZIP data indikator BPS yang digunakan notebook. `processed/` berisi data gabungan tingkat kabupaten/kota dan tahun yang dibuat setelah notebook berhasil dijalankan.

Dataset gabungan diharapkan memiliki 175 observasi (35 kabupaten/kota × 5 tahun, 2020–2024) dengan target `persentase_penduduk_miskin` dan fitur `uhh`, `hls`, `rls`, `pengeluaran_per_kapita_disesuaikan`, serta `tpt`.

## Sumber data BPS

| Variabel | Tabel statistik resmi |
|---|---|
| Persentase penduduk miskin | [Kemiskinan Menurut Kabupaten/Kota di Provinsi Jawa Tengah](https://jateng.bps.go.id/id/statistics-table/2/MzQjMg%3D%3D/kemiskinan.html) |
| Umur harapan hidup (UHH) | [[Metode Baru] Umur Harapan Hidup Saat Lahir (UHH) Hasil Long Form SP2020 Menurut Kabupaten/Kota](https://jateng.bps.go.id/id/statistics-table/2/MjAzNSMy/-metode-baru--umur-harapan-hidup-saat-lahir--uhh--hasil-long-form-sp2020-menurut-kabupaten-kota.html) |
| Harapan lama sekolah (HLS) | [[Indikator Strategis] [IPM] Harapan Lama Sekolah Menurut Kabupaten/Kota di Provinsi Jawa Tengah](https://jateng.bps.go.id/id/statistics-table/2/MjQxMyMy/-indikator-strategis---ipm--harapan-lama-sekolah-menurut-kabupaten-kota-di-provinsi-jawa-tengah.html) |
| Rata-rata lama sekolah (RLS) | [[Indikator Strategis] [IPM] Rata-rata Lama Sekolah Menurut Kabupaten/Kota di Provinsi Jawa Tengah](https://jateng.bps.go.id/id/statistics-table/2/MjQxNCMy/-indikator-strategis---ipm--rata-rata-lama-sekolah--menurut-kabupaten-kota-di-provinsi-jawa-tengah.html) |
| Pengeluaran per kapita disesuaikan | [[Indikator Strategis] [IPM] Pengeluaran per Kapita Disesuaikan Menurut Kabupaten/Kota di Provinsi Jawa Tengah](https://jateng.bps.go.id/id/statistics-table/2/MjQxNSMy/-indikator-strategis-ipm-pengeluaran-per-kapita-disesuaikan-menurut-kabupaten-kota-di-provinsi-jawa-tengah.html) |
| Tingkat pengangguran terbuka (TPT) | [Tingkat Pengangguran Terbuka (TPT) Menurut Kabupaten/Kota di Provinsi Jawa Tengah](https://jateng.bps.go.id/id/statistics-table/2/NjQjMg%3D%3D/tingkat-pengangguran-terbuka--tpt--di-provinsi-jawa-tengah.html) |

Tanggal akses seluruh tabel: **8 September 2026**.

## Struktur data

- `raw/` menyimpan enam ZIP indikator yang diunduh dari BPS, masing-masing berisi lima CSV tahunan.
- `processed/kemiskinan_jateng_2020_2024.csv` adalah hasil penggabungan yang dibuat oleh notebook.
- Baris agregat Provinsi Jawa Tengah (`3300`) dikeluarkan sehingga tersisa 35 kabupaten/kota.
