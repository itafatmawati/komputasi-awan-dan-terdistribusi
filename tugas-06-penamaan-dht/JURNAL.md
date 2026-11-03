# Jurnal Proses — Tugas 6

## Implementasi find_successor
- Kesalahan pertama yang ditemui (mis. lupa wrap-around di ring): typo dan kesalahan logika
- Cara memperbaikinya: analisis kembali kode untuk menemukan letak kesalahan, lalu perbaiki.

## Skenario join/leave
- Hasil sebelum & sesudah node baru bergabung: ...
- Hasil sebelum & sesudah node keluar: ...

## Log Penggunaan AI (Level 2)

> Wajib diisi sesuai kebijakan Level 2 di [`../RUBRIK-UMUM.md`](../RUBRIK-UMUM.md). Tulis "Tidak memakai AI" pada baris pertama jika memang tidak dipakai. Hanya untuk brainstorming ide/outline — bukan untuk kode/analisis/teks akhir.

| Tanggal | Tool AI | Prompt yang diberikan | Ringkasan saran/ide AI | Bagaimana diolah jadi tulisan/kode sendiri |

|27/10/2026|GPT|[sumber kode] jelaskan alur kode dan makna kode yang ada|Program Simulasi Chord DHT bertujuan untuk mensimulasikan penyimpanan data terdistribusi menggunakan mekanisme hashing. Identitas node dan kurir diubah menjadi nilai hash menggunakan SHA-1, kemudian `find_successor()` menentukan node yang bertanggung jawab atas data tersebut. Fungsi `join()` digunakan untuk menambahkan node, `leave()` untuk mengeluarkan node dan mengidentifikasi pengalihan tanggung jawab data, `register_kurir()` untuk menyimpan data kurir, serta `lookup()` untuk mencari alamat IP kurir. Secara keseluruhan, simulasi menunjukkan bagaimana Chord DHT mengelola pembagian tanggung jawab data ketika terjadi perubahan anggota ring. Proses pengalihan data dalam kode ini masih berupa simulasi log, belum pemindahan data sebenarnya.|dipahami|

|27/10/2026|apakah alur kerja dht pada soal tersebut seperti ini: pertama dibuat node awal, lalu di hashing. lalu didaftarkan kurir, lalu kurirnya dicari sucessornya ke node awal itu? lalu di tengah jalan ditambah node baru, maka nanti dia di hashing dan semua kurir akan di update sucessornya? baru dicoba lagi kalau ada node keluar, sehingga semua kurir di update successornya?|Hampir tepat sekali alurnya! Namun, ada satu poin penting yang perlu diluruskan sedikit agar pemahaman Anda mengenai konsep Chord DHT benar-benar akurat, terutama pada bagian "semua kurir di-update successor-nya". Pemahaman Anda: (Perlu diluruskan sedikit) Bukan semua kurir yang di-update, melainkan hanya kurir tertentu saja.|dipahami|