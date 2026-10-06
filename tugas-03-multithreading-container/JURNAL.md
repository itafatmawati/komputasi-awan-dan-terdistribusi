# Jurnal Proses — Tugas 3

## Percobaan tanpa Lock

- Hasil `processed_count` yang didapat: 53
- Kenapa bisa meleset (jelaskan mekanisme race condition dengan kata sendiri): Ketika suatu proses berjalan tanpa lock, maka proses thread tersebut akan saling berebut untuk mengakses data tanpa adanya mekanisme antrian.

## Percobaan dengan Lock

- Hasil `processed_count` setelah perbaikan: 100

## Kendala Docker

- Error yang ditemui saat `docker build`/`docker run` dan cara memperbaikinya: 

- Hasil yang diperoleh setelah melakukan perubahan tidak terupdate dan masih berisi kode lama, cara memperbaikinya dengan mengulangi proses docker build.

- Error ketika ingin push, cara memperbaikinya dengan "git add Dockerfile"


## Log Penggunaan AI (Level 2)

> Wajib diisi sesuai kebijakan Level 2 di [`../RUBRIK-UMUM.md`](../RUBRIK-UMUM.md). Tulis "Tidak memakai AI" pada baris pertama jika memang tidak dipakai. Hanya untuk brainstorming ide/outline — bukan untuk kode/analisis/teks akhir.

| Tanggal    | Tool AI   | Prompt yang diberikan                                                        | Ringkasan saran/ide AI                                                                                                                                                                                                                                     | Bagaimana diolah jadi tulisan/kode sendiri |
| ---------- | --------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| 05/10/2026 | Gemini AI | apa perbedaan proses tanpa lock dan dengan lock dalam konsep multithreading? | Dalam konsep multithreading, perbedaan utama antara proses tanpa lock (tanpa penguncian) dan dengan lock (menggunakan penguncian) terletak pada cara thread mengelola akses ke sumber daya bersama (shared resources), seperti variabel, objek, atau file. | dipahami                                   |
