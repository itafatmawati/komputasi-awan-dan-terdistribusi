# Jurnal Proses — Tugas 7

## Diskusi pemilihan model konsistensi
- Argumen yang dipertimbangkan: -Eventual consistency = pengguna bisa membaca data yang belum diperbarui. - Squential consistency = Menjaga urutan operasi agar konsisten antarserver. - Read-Your-Writes = Memastikan pengguna dapat membaca hasil pembaruan.
- Kesimpulan akhir & alasan: kami memilih Eventual Consistency, Sequential Consistency, dan Read Your Writes karena evantual saja belum cukup untuk menjaga konsistensi data. Sehingga, ketiganya dipertimbangkan untuk mendukung replikasi efisien, konsistensi operasi dan memastikan pengguna dapat membaca hasil pembaruan.

## Simulasi (jika dikerjakan)
- Hasil skenario naif vs Read-Your-Writes: ...

## Log Penggunaan AI (Level 2)

> Wajib diisi sesuai kebijakan Level 2 di [`../RUBRIK-UMUM.md`](../RUBRIK-UMUM.md). Tulis "Tidak memakai AI" pada baris pertama jika memang tidak dipakai. Hanya untuk brainstorming ide/outline — bukan untuk kode/analisis/teks akhir.

| Tanggal | Tool AI | Prompt yang diberikan | Ringkasan saran/ide AI | Bagaimana diolah jadi tulisan/kode sendiri |
|17/11/2026|Chat-GPT|sebutkan macam" Client-Centric Consistency dan jelaskan lalu jelaskan juga cocoknya dipake untuk apa|Client-Centric Consistency merupakan model konsistensi dalam sistem terdistribusi yang berfokus pada pengalaman satu klien untuk memastikan akses pembacaan (read) dan pembaruan data (write) tetap konsisten meskipun dilayani oleh replika server yang berbeda. Model ini terbagi menjadi empat jenis utama sesuai pola interaksinya, yaitu Read-Your-Writes Consistency (Write → Read) yang menjamin klien dapat langsung melihat perubahan yang baru saja dibuatnya seperti pada pengaturan profil; Monotonic Reads Consistency (Read → Read) yang mencegah pembacaan data mundur ke versi lebih lama seperti pada aplikasi perbankan; Monotonic Writes Consistency (Write → Write) yang menjaga urutan eksekusi penulisan sesuai waktu pembuatannya seperti pada sistem pemesanan; serta Writes-Follow-Reads Consistency (Read → Write) yang memastikan penulisan baru diproses berdasarkan versi data yang sebelumnya telah dibaca klien seperti pada manajemen inventaris. Pemilihan keempat model tersebut bergantung pada kebutuhan spesifik aplikasi, dengan catatan bahwa jaminan konsistensi ini berpusat pada sudut pandang masing-masing klien secara individual dan tidak otomatis berarti seluruh pengguna lain melihat kondisi data yang identik pada waktu bersamaan.|dipahami, lalu dicocokkan dengan kebutuhan soal untuk dijadikan jawaban|

