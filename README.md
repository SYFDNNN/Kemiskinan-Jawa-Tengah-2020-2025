# Pemodelan Kemiskinan Jawa Tengah 2020–2024

Analisis ini membandingkan Multiple Linear Regression dan Random Forest untuk memodelkan persentase penduduk miskin di Jawa Tengah.

## Struktur proyek

- `notebooks/pemodelan_kemiskinan_jateng.ipynb` — notebook utama analisis.
- `data/raw/` — ZIP sumber data BPS.
- `data/processed/` — dataset gabungan yang dihasilkan notebook.
- `reports/` — hasil evaluasi model dan keluaran analisis.

## Menjalankan notebook

1. Buat environment Python dan instal dependensi:

   ```bash
   python -m venv .venv
   # Windows: .venv\Scripts\activate
   # Linux/macOS: source .venv/bin/activate
   pip install -r requirements.txt
   ```

2. Jalankan Jupyter dari root repository:

   ```bash
   jupyter notebook notebooks/pemodelan_kemiskinan_jateng.ipynb
   ```

Notebook otomatis membaca ZIP dari `data/raw/`. Jika menggunakan lokasi lain, set `SKRIPSI_DATA_DIR`; lokasi keluaran dapat diubah melalui `SKRIPSI_OUTPUT_DIR`.

## Catatan data

Data mentah bersumber dari BPS dan digunakan untuk keperluan analisis akademik. Lihat [data/README.md](data/README.md).
