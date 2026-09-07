# Evaluasi Model

Laporan ini dihasilkan dari notebook utama. Data latih mencakup tahun 2020–2023 (140 observasi), sedangkan data uji akhir mencakup tahun 2024 (35 observasi).

## Hasil uji 2024

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Random Forest | 1.0700 | 1.3392 | 0.8210 |
| Multiple Linear Regression | 1.9047 | 2.3243 | 0.4608 |
| Dummy Baseline | 2.6938 | 3.2455 | -0.0514 |

Random Forest memberikan kinerja terbaik pada data uji 2024 berdasarkan MAE, RMSE, dan R². Angka-angka di atas berasal dari `hasil_perbandingan_model.csv` setelah eksekusi lokal notebook.

Jalankan notebook untuk memperbarui tabel evaluasi dan seluruh keluaran di folder `reports/`.
