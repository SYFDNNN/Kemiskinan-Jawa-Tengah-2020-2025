# Indeks Hasil Analisis

## Ringkasan

- `model_evaluation.md` — narasi evaluasi model dan batas interpretasi.
- `hasil_perbandingan_model.csv` — MAE, CI bootstrap, RMSE, dan R² pada holdout 2025.
- `perbandingan_mae_berpasangan.csv` — selisih MAE dan CI bootstrap berpasangan.
- `validasi_temporal_random_forest.csv` — hasil seluruh kandidat tuning Random Forest.
- `prediksi_kemiskinan_2025.csv` — aktual, prediksi, residual, dan absolute error per wilayah.

## EDA dan diagnostik

- `statistik_deskriptif_data_latih.csv` — statistik deskriptif 2020–2024.
- `ringkasan_kemiskinan_tahunan.csv` — rata-rata, median, minimum, dan maksimum tahunan.
- `vif_prediktor.csv` — variance inflation factor setiap prediktor.
- `diagnostik_mlr.csv` — hasil Shapiro–Wilk dan Breusch–Pagan.
- `koefisien_terstandar_mlr.csv` — koefisien MLR setelah standardisasi fitur.
- `koefisien_mlr_cluster_robust.csv` — koefisien dan inferensi cluster-robust.
- `permutation_importance_random_forest.csv` — kontribusi prediktif Random Forest.
- `hasil_analisis_sensitivitas.csv` — performa model ketika fitur tertentu dikeluarkan.
- `audit_sumber_data.csv` — checksum dan audit kualitas setiap sumber.

## Figur

Folder `figures/` berisi delapan grafik PNG 300 dpi yang siap digunakan sebagai bahan Bab IV dengan penyesuaian caption dan penomoran pada naskah.
