# Data Tugas 1

## Dataset yang Dipilih
Isi informasi berikut sebelum Milestone 1.

| Item | Isi |
|---|---|
| Nama dataset | `Chicago Crime Dataset (gymprathap/Chicago-Crime-Dataset)` |
| Sumber | `https://huggingface.co/datasets/gymprathap/Chicago-Crime-Dataset` |
| Lisensi/ketentuan pakai | `Apache License 2.0 (apache-2.0) / Chicago Data Portal Terms of Use` |
| Ukuran | `~1,85 GB (CSV) / ~8.100.000+ baris dan 22 kolom` |
| Periode data | `2001 – 2024` |
| Unit analisis | `Satu kejadian tindak kriminal (crime incident) yang tercatat oleh Kepolisian Chicago (CLEAR system)` |

## Kolom
| Nama Kolom | Tipe Data Asli | Deskripsi |
|---|---|---|
| `ID` | Integer | Identifikasi unik untuk setiap catatan insiden kejahatan. |
| `Case Number` | String | Nomor laporan resmi kepolisian Chicago (RD Number). |
| `Date` | String (Datetime) | Tanggal dan waktu estimasi terjadinya insiden (`MM/DD/YYYY HH:MM:SS AM/PM`). |
| `Block` | String | Alamat tingkat blok lokasi kejadian (disamarkan sebagian untuk privasi). |
| `IUCR` | String | Kode pelaporan kejahatan seragam Illinois (*Illinois Uniform Crime Reporting*). |
| `Primary Type` | String | Kategori utama tindak kejahatan (contoh: `THEFT`, `BATTERY`, `DECEPTIVE PRACTICE`). |
| `Description` | String | Sub-kategori atau deskripsi rinci dari `Primary Type`. |
| `Location Description` | String | Jenis lokasi terjadinya insiden (contoh: `STREET`, `RESIDENCE`, `APARTMENT`). |
| `Arrest` | Boolean | Status apakah insiden berujung pada penangkapan (`true` / `false`). |
| `Domestic` | Boolean | Status apakah insiden terkait kekerasan dalam rumah tangga (`true` / `false`). |
| `Beat`, `District`, `Ward`, `Community Area` | Integer / Float | Pembagian wilayah patroli kepolisian dan administratif kota. |
| `FBI Code` | String | Klasifikasi kode kejahatan menurut standar FBI. |
| `X Coordinate`, `Y Coordinate` | Float | Koordinat proyeksi spasial State Plane Illinois East NAD 1983. |
| `Year` | Integer | Tahun terjadinya insiden. |
| `Updated On` | String (Datetime) | Tanggal dan waktu terakhir data diperbarui. |
| `Latitude`, `Longitude`, `Location` | Float / String | Titik koordinat geografis lokasi insiden. |

## Cara Mencari Dataset
1. Buka repositori Hugging Face dengan melakukan filtering pencarian :
   - Modalities: Tabular
   - Size (rows):100K-10M
   - Format: CSV, Parquet
   - Libraries: Pandas, Polars
   - Sort : Recently Updated

## Cara Memperoleh Data
1. Buka repositori Hugging Face: [gymprathap/Chicago-Crime-Dataset](https://huggingface.co/datasets/gymprathap/Chicago-Crime-Dataset).
2. Buat folder `data/raw/` dan dan `data/processed/` pada direktori utama proyek jika belum ada:
   ```bash
   mkdir -p data/raw/
3. Letakkan file `.csv` yang telah diunduh ke dalam direktori `data/raw/` di repositori lokal tanpa mengubah data mentah. Nama file asli: Crimes_-_2001_to_Present.csv.
4. Saya melakukan Rename nama file asli menjadi chicago_crimes.csv

## AI Disclosure Statement
> **Alat AI yang digunakan:** Gemini (Google).
>
> **Bagian yang dibantu:**
> - Mencari dan membandingkan opsi dataset; pilihan akhir (`gymprathap/Chicago-Crime-Dataset` dari Hugging Face) saya tentukan sendiri dan saya unduh sendiri.
> - Draf awal kode profiling di `01_data_profiling.ipynb` (Polars `scan_csv`, `schema_overrides`, DuckDB `SUMMARIZE`) dan penyusunan dokumentasi `data/README.md`.
> - Penjelasan error (`NameError` pada eksekusi cell notebook) serta penyesuaian skema kolom dari referensi ke dataset Chicago Crime.
>
> **Yang saya kerjakan sendiri:** Mengunduh dan menyiapkan dataset mentah, menjalankan seluruh pipeline di JupyterLab, memverifikasi hasil profiling statistik, menentukan aturan batas koordinat/cleaning, merumuskan pertanyaan analisis, membuat visualisasi, dan menulis insight analitik.
>
> **Verifikasi yang dilakukan:** Menjalankan ulang seluruh notebook dari awal dengan *Restart Kernel and Run All*, mencocokkan jumlah baris, skema kolom, dan rentang tanggal (`Date`/`Year`) dengan file mentah, membaca dokumentasi resmi Polars dan DuckDB, serta memastikan saya memahami dan dapat menjelaskan setiap cell kode.

## Aturan Penyimpanan
- Jangan commit dataset mentah atau hasil olahan berukuran besar ke Git.
- File pada `data/raw/` adalah data asli dan tidak boleh diubah.
- Simpan hasil transformasi yang dapat direproduksi pada `data/processed/`.