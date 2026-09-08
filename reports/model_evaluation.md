# Evaluasi Model

## Desain evaluasi

Data 2020–2024 digunakan untuk EDA dan pelatihan (175 observasi). Data 2025 dikunci sebagai holdout akhir (35 observasi). Random Forest dituning dengan expanding-year validation pada data latih, sehingga setiap fold hanya memakai tahun-tahun sebelum tahun validasi.

MAE menjadi metrik utama karena dapat dibaca langsung sebagai rata-rata kesalahan dalam poin persentase kemiskinan. RMSE dan R² digunakan sebagai metrik pendukung. Interval kepercayaan MAE dihitung dengan 2.000 bootstrap atas 35 wilayah uji menggunakan random seed 42.

## Hasil holdout 2025

| Model | MAE | CI 95% MAE | RMSE | R² |
|---|---:|---:|---:|---:|
| **Random Forest** | **1,0990** | **0,8020–1,4193** | **1,4424** | **0,7310** |
| Multiple Linear Regression | 1,7314 | 1,3157–2,1823 | 2,1579 | 0,3980 |
| Dummy Baseline | 2,6436 | 2,0427–3,2595 | 3,1672 | -0,2970 |

## Perbandingan bootstrap berpasangan

| Perbandingan | Selisih MAE | CI 95% |
|---|---:|---:|
| MLR dikurangi Random Forest | 0,6336 | 0,2667–0,9654 |
| Dummy dikurangi Random Forest | 1,5397 | 0,9914–2,1247 |

Seluruh interval selisih berada di atas nol. Pada holdout ini, Random Forest konsisten menghasilkan MAE lebih rendah daripada MLR dan Dummy Baseline dalam resampling wilayah uji.

## Tuning Random Forest

Kombinasi terbaik dari 20 sampel parameter menghasilkan MAE validasi temporal rata-rata 1,1836:

- `n_estimators = 300`
- `max_depth = 15`
- `max_features = 0.6`
- `min_samples_split = 2`
- `min_samples_leaf = 1`

Seluruh kandidat dan skornya tersedia di `validasi_temporal_random_forest.csv`.

## Diagnostik MLR

| Pemeriksaan | Hasil | Interpretasi |
|---|---:|---|
| Shapiro–Wilk | p = 0,0311 | Ada indikasi residual tidak normal pada taraf 5% |
| Breusch–Pagan LM | p = 0,0091 | Ada indikasi heteroskedastisitas |
| VIF HLS | 7,1240 | Multikolinearitas cukup tinggi |
| VIF RLS | 8,8481 | Multikolinearitas cukup tinggi |

Karena data mengandung pengukuran berulang pada wilayah yang sama dan ditemukan heteroskedastisitas, inferensi koefisien dilaporkan menggunakan standard error cluster-robust menurut kabupaten/kota. Tidak ada prediktor individual yang memiliki p-value di bawah 0,05 pada spesifikasi cluster-robust. Hal tersebut tidak membatalkan penggunaan MLR sebagai model prediksi pembanding, tetapi membatasi klaim inferensial atas koefisien individual.

## Kesimpulan

Random Forest dipilih sebagai model dengan performa prediktif terbaik pada holdout 2025. Kesimpulan ini berlaku untuk dataset dan desain evaluasi penelitian ini; hasil tidak boleh ditafsirkan sebagai hubungan kausal atau langsung digeneralisasi ke provinsi dan periode lain.
