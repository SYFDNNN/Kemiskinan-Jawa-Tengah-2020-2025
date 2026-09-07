# Pemodelan Kemiskinan Jawa Tengah 2020–2024

Analisis data dan machine learning untuk memodelkan persentase penduduk miskin pada 35 kabupaten/kota di Jawa Tengah menggunakan data tahun 2020–2024.

[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## Ringkasan proyek

Proyek ini membandingkan tiga pendekatan prediksi:

1. Dummy Baseline sebagai pembanding sederhana.
2. Multiple Linear Regression untuk melihat hubungan linear antarvariabel.
3. Random Forest Regressor untuk menangkap pola non-linear dan interaksi fitur.

Data tahun 2020–2023 digunakan sebagai data latih dan tahun 2024 dikunci sebagai data uji akhir. Strategi pemisahan temporal ini dipilih agar evaluasi lebih mendekati skenario prediksi tahun berikutnya.

## Hasil utama

Random Forest memberikan performa terbaik pada data uji tahun 2024:

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| **Random Forest** | **1.0700** | **1.3392** | **0.8210** |
| Multiple Linear Regression | 1.9047 | 2.3243 | 0.4608 |
| Dummy Baseline | 2.6938 | 3.2455 | -0.0514 |

### Temuan penting

- Random Forest menghasilkan error paling rendah dan mampu menjelaskan sekitar 82,1% variasi target pada data uji 2024.
- Kedua model machine learning mengungguli Dummy Baseline.
- Evaluasi dilakukan pada 35 kabupaten/kota di tahun 2024, sehingga hasil perlu dibaca sebagai evaluasi prediktif pada dataset ini—bukan sebagai bukti hubungan sebab-akibat.

## Variabel yang digunakan

Target yang diprediksi adalah `persentase_penduduk_miskin`. Prediktornya adalah:

- `uhh` — umur harapan hidup
- `hls` — harapan lama sekolah
- `rls` — rata-rata lama sekolah
- `pengeluaran_per_kapita_disesuaikan` — pengeluaran per kapita disesuaikan
- `tpt` — tingkat pengangguran terbuka

Garis kemiskinan dan jumlah penduduk miskin tidak digunakan sebagai prediktor karena berpotensi terlalu dekat secara definisi dengan target.

## Metodologi

1. Membaca enam ZIP data indikator BPS.
2. Menstandarkan nama variabel, kode wilayah, dan tahun.
3. Menghapus baris agregat Provinsi Jawa Tengah (`3300`).
4. Menggabungkan data berdasarkan `kode_wilayah` dan `tahun`.
5. Memvalidasi 175 observasi: 35 wilayah × 5 tahun.
6. Melakukan exploratory data analysis pada data latih 2020–2023.
7. Melatih dan membandingkan Dummy Baseline, Multiple Linear Regression, dan Random Forest.
8. Mengevaluasi prediksi pada data uji tahun 2024 menggunakan MAE, RMSE, dan R².
9. Menganalisis koefisien, permutation importance, dan sensitivitas model.

## Isi repository

```text
kemiskinan-jawa-tengah/
├── README.md
├── notebooks/
│   └── pemodelan_kemiskinan_jateng.ipynb
├── data/
│   ├── raw/                  # ZIP sumber data BPS
│   ├── processed/
│   │   └── kemiskinan_jateng_2020_2024.csv
│   └── README.md
├── reports/
│   ├── model_evaluation.md
│   ├── hasil_perbandingan_model.csv
│   ├── prediksi_kemiskinan_2024.csv
│   ├── koefisien_terstandar_mlr.csv
│   ├── permutation_importance_random_forest.csv
│   ├── hasil_analisis_sensitivitas.csv
│   └── audit_sumber_data.csv
├── requirements.txt
├── .gitignore
└── LICENSE
```

## Menjalankan proyek

Pastikan Python 3.10 atau lebih baru sudah terpasang.

```bash
git clone https://github.com/SYFDNNN/Kemiskinan-Jawa-Tengah-2020-2024.git
cd Kemiskinan-Jawa-Tengah-2020-2024
python -m venv .venv
```

Aktifkan environment:

```bash
# Windows PowerShell
.venv\Scripts\Activate.ps1

# Linux/macOS
source .venv/bin/activate
```

Instal dependensi dan jalankan notebook dari root repository:

```bash
pip install -r requirements.txt
jupyter notebook notebooks/pemodelan_kemiskinan_jateng.ipynb
```

Notebook otomatis membaca ZIP dari `data/raw/`, menyimpan dataset gabungan ke `data/processed/`, dan menyimpan hasil analisis ke `reports/`. Lokasi tersebut dapat diubah dengan environment variable `SKRIPSI_DATA_DIR` dan `SKRIPSI_OUTPUT_DIR`.

## Artefak dan dokumentasi hasil

- [Notebook analisis](notebooks/pemodelan_kemiskinan_jateng.ipynb)
- [Dataset processed](data/processed/kemiskinan_jateng_2020_2024.csv)
- [Ringkasan evaluasi model](reports/model_evaluation.md)
- [Perbandingan model](reports/hasil_perbandingan_model.csv)
- [Prediksi tahun 2024](reports/prediksi_kemiskinan_2024.csv)
- [Permutation importance Random Forest](reports/permutation_importance_random_forest.csv)
- [Analisis sensitivitas](reports/hasil_analisis_sensitivitas.csv)
- [Audit sumber data](reports/audit_sumber_data.csv)

## Keterbatasan

- Dataset hanya mencakup lima tahun dan satu provinsi.
- Evaluasi akhir hanya menggunakan 35 observasi pada tahun 2024.
- Model digunakan untuk tujuan prediksi dan eksplorasi, bukan untuk menyimpulkan kausalitas kebijakan.
- Performa pada wilayah atau tahun di luar cakupan data perlu divalidasi kembali.

## Lisensi dan data

Kode dan dokumentasi proyek ini menggunakan [MIT License](LICENSE). Data mentah bersumber dari publikasi BPS dan disertakan untuk keperluan analisis akademik. Detail penempatan data dapat dilihat di [data/README.md](data/README.md).

## Kontak

Dibuat oleh [SYFDNNN](https://github.com/SYFDNNN).
