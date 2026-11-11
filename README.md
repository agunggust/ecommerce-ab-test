# A/B Test Halaman E-commerce

Studi kasus product analytics dengan Python. Apakah halaman baru meningkatkan tingkat konversi cukup besar untuk layak dirilis?

## Rekomendasi

**Tunda rilis penuh sampai pembagian trafik terverifikasi.** Halaman baru mencatat kenaikan **5,01 poin persentase**, dengan interval kepercayaan 95% **+4,51 hingga +5,50 poin persentase**. Seluruh interval berada di atas ambang bisnis yang diasumsikan, yaitu **+0,50 poin persentase**.

Jika target alokasinya 50/50 dengan penugasan independen, pembagian trafik yang terlihat perlu diselidiki. Treatment menerima 50,38% dari seluruh observasi dan uji binomial dua sisi menghasilkan p = 0,0442. Konfirmasi rasio yang direncanakan dan rekonsiliasi log penugasan, paparan halaman, serta konversi. Jika validitas eksperimen terkonfirmasi, pertimbangkan rilis bertahap.

## Hasil

| Grup | Observasi | Konversi | Tingkat konversi |
| --- | ---: | ---: | ---: |
| Control · halaman lama | 34.678 | 3.650 | 10,53% |
| Treatment · halaman baru | 35.211 | 5.469 | 15,53% |

![Kenaikan konversi 5,01 poin persentase dengan interval 95% dari 4,51 sampai 5,50 poin, di atas ambang bisnis 0,50 poin.](conversion-lift.png)

## Metode dan cakupan

- Gunakan 69.889 baris dari dataset latihan Udacity. Notebook memvalidasi versi CSV, skema, nilai kosong, dan kategori yang diperbolehkan. [Sumber data dan deskripsi eksperimen](https://github.com/udacity/sdand-ab-testing-project/tree/e3aeae691f434eff812bd3c9c4a6f8c7cc2ec5df)
- Hitung tingkat konversi sebagai jumlah baris yang dikonversi dibagi jumlah baris dalam masing-masing grup. Estimasikan selisih treatment dikurangi control dengan interval Newcombe untuk dua proporsi independen.
- CSV berisi negara, grup eksperimen, dan status konversi. Pemeriksaan pengguna duplikat, kecocokan paparan halaman, dan pola waktu membutuhkan data tambahan. Rasio alokasi aktual dan dampak pada pendapatan juga belum diketahui.

## Jalankan ulang

1. Unduh [CSV sumber](https://raw.githubusercontent.com/udacity/sdand-ab-testing-project/e3aeae691f434eff812bd3c9c4a6f8c7cc2ec5df/ab_data.csv) dan simpan sebagai `ab_data.csv` di folder proyek.
2. Dengan Python 3.12, instal dependensi di lingkungan Python yang akan dipakai notebook.

   ```sh
   python -m pip install -r requirements.txt
   ```

3. Buka [analysis.ipynb](analysis.ipynb) di VS Code dengan ekstensi Jupyter atau di JupyterLab. Pilih kernel dari lingkungan pada langkah 2, lalu jalankan semua sel. Notebook membuat ulang `conversion-lift.png`.

## Bullet CV

> Analyzed 69,889 observations from an e-commerce A/B test in Python, estimated a +5.01 percentage-point conversion lift (95% CI: +4.51 to +5.50), and flagged a potential traffic allocation mismatch for investigation before rollout.
