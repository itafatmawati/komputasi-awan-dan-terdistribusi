# Jurnal Proses — Tugas 5

## Implementasi Bully
- Kendala saat mengisi TODO 1-4: Berpikir cukup keras, karena kurang familiar dengan konteks bully algorithm meskipun memiliki dasar pengetahuan terkait koneksi dll.  

## Skenario 1: Start normal
- Leader yang terpilih: node 5
- Log/observasi: setalah run 5 node, node 5 terpilih menjadi leader karena merupakan id tertinggi

## Skenario 2: Leader dimatikan
- Leader baru yang terpilih: node 4 
- Berapa lama waktu sampai leader baru terdeteksi: kurang lebih 5 detik

## Log Penggunaan AI (Level 2)

> Wajib diisi sesuai kebijakan Level 2 di [`../RUBRIK-UMUM.md`](../RUBRIK-UMUM.md). Tulis "Tidak memakai AI" pada baris pertama jika memang tidak dipakai. Hanya untuk brainstorming ide/outline — bukan untuk kode/analisis/teks akhir.

| Tanggal | Tool AI | Prompt yang diberikan | Ringkasan saran/ide AI | Bagaimana diolah jadi tulisan/kode sendiri |
|20/10/2026|GPT|kasih contoh kode bully algorithm dan jelaskan dengan bahas aynag mudah dipahami arti kodenya|Contoh kode dan penjelasan|dipahami|

| 20/10/2026 | GPT | apakah semua implementasi kode tetap valid / dikatakan bully apabila inti kodenya tetap sama atau memilih 1 node jadi leader? | Nggak semua kode yang memilih 1 node sebagai leader bisa disebut Bully Algorithm. Ada beberapa karakteristik utama yang perlu ada: 1. Setiap node memiliki ID unik, misalnya Node 1 sampai Node 5. 2. Node dengan ID lebih tinggi memiliki prioritas lebih tinggi untuk menjadi leader. 3. Ketika node mendeteksi leader bermasalah, node tersebut memulai proses election. 4.Node menghubungi node yang memiliki ID lebih tinggi untuk mengetahui apakah ada node yang masih aktif. 5. Jika ada node lebih tinggi yang aktif, proses berlanjut. Jika tidak ada, node tersebut dapat menjadi leader. 6.Setelah pemilihan, node-node lain perlu mengetahui siapa leader yang baru.| dipahami |
