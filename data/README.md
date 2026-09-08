# Dokumentasi Data

Dataset penelitian mencakup 35 kabupaten/kota di Jawa Tengah selama 2020–2025. Enam ZIP pada `raw/` masing-masing berisi enam CSV tahunan, sedangkan `processed/kemiskinan_jateng_2020_2025.csv` merupakan hasil penggabungan yang dapat direproduksi melalui notebook.

## Sumber data BPS

| Variabel | Tabel statistik resmi |
|---|---|
| Persentase penduduk miskin | [Kemiskinan Menurut Kabupaten/Kota di Provinsi Jawa Tengah](https://jateng.bps.go.id/id/statistics-table/2/MzQjMg%3D%3D/kemiskinan.html) |
| Umur harapan hidup (UHH) | [Umur Harapan Hidup Saat Lahir menurut Kabupaten/Kota](https://jateng.bps.go.id/id/statistics-table/2/MjAzNSMy/-metode-baru--umur-harapan-hidup-saat-lahir--uhh--hasil-long-form-sp2020-menurut-kabupaten-kota.html) |
| Harapan lama sekolah (HLS) | [Harapan Lama Sekolah menurut Kabupaten/Kota](https://jateng.bps.go.id/id/statistics-table/2/MjQxMyMy/-indikator-strategis---ipm--harapan-lama-sekolah-menurut-kabupaten-kota-di-provinsi-jawa-tengah.html) |
| Rata-rata lama sekolah (RLS) | [Rata-rata Lama Sekolah menurut Kabupaten/Kota](https://jateng.bps.go.id/id/statistics-table/2/MjQxNCMy/-indikator-strategis---ipm--rata-rata-lama-sekolah--menurut-kabupaten-kota-di-provinsi-jawa-tengah.html) |
| Pengeluaran per kapita disesuaikan | [Pengeluaran per Kapita Disesuaikan menurut Kabupaten/Kota](https://jateng.bps.go.id/id/statistics-table/2/MjQxNSMy/-indikator-strategis-ipm-pengeluaran-per-kapita-disesuaikan-menurut-kabupaten-kota-di-provinsi-jawa-tengah.html) |
| Tingkat pengangguran terbuka (TPT) | [TPT menurut Kabupaten/Kota di Provinsi Jawa Tengah](https://jateng.bps.go.id/id/statistics-table/2/NjQjMg%3D%3D/tingkat-pengangguran-terbuka--tpt--di-provinsi-jawa-tengah.html) |

Tanggal akses seluruh tabel: **8 September 2026**.

Data pada repository adalah snapshot saat tanggal akses. BPS dapat memperbarui atau merevisi seri pada halaman sumber.

## Data dictionary

| Kolom | Tipe | Satuan | Keterangan |
|---|---|---|---|
| `kode_wilayah` | String | – | Kode BPS empat digit; dipertahankan sebagai string agar nol awal tidak hilang |
| `kabupaten_kota` | String | – | Nama resmi kabupaten/kota |
| `tahun` | Integer | Tahun | Tahun observasi, 2020–2025 |
| `persentase_penduduk_miskin` | Float | Persen | Target pemodelan |
| `uhh` | Float | Tahun | Umur harapan hidup saat lahir |
| `hls` | Float | Tahun | Harapan lama sekolah |
| `rls` | Float | Tahun | Rata-rata lama sekolah |
| `pengeluaran_per_kapita_disesuaikan` | Float | Ribu rupiah/orang/tahun | Pengeluaran per kapita yang disesuaikan |
| `tpt` | Float | Persen | Tingkat pengangguran terbuka |

## Standardisasi wilayah

Lima sumber memakai kode dan nama wilayah BPS. ZIP UHH terbaru hanya mencantumkan nama wilayah, sehingga notebook memetakannya ke kode BPS menggunakan crosswalk eksplisit. Penggabungan dilakukan berdasarkan kode dan tahun, bukan berdasarkan urutan baris. Agregat Provinsi Jawa Tengah (`3300`) dikeluarkan dari unit analisis.

## Validasi kualitas

Notebook menghentikan eksekusi apabila salah satu syarat berikut tidak terpenuhi:

- Enam tahun tersedia pada setiap sumber.
- Setiap tahun memiliki tepat 35 kabupaten/kota yang sama.
- Dataset akhir berisi 210 observasi dan 9 kolom.
- Tidak ada pasangan wilayah–tahun duplikat.
- Tidak ada nilai kosong pada variabel penelitian.
- Relasi penggabungan untuk setiap indikator bersifat satu-ke-satu.

Nama file, checksum SHA-256, jumlah observasi, cakupan tahun, duplikasi, dan missing value direkam di [`reports/audit_sumber_data.csv`](../reports/audit_sumber_data.csv).

## Prinsip penggunaan

- Jangan mengedit ZIP atau CSV mentah secara manual.
- Lakukan transformasi melalui notebook agar proses dapat diaudit dan direproduksi.
- Cantumkan BPS Provinsi Jawa Tengah sebagai sumber data dalam naskah skripsi.
- Periksa kembali metadata, definisi, dan tanggal akses pada saat finalisasi naskah.
