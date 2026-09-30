# Jurnal Proses — Tugas 2

## 30-09-2026

- Opsi arsitektur yang dipertimbangkan: Pub-Sub dikombinasikan dengan SOA
- Kenapa akhirnya pilih [SOA/Pub-Sub]: Karena, masalah utama yang kami identifikasi pada tugas 01 terletak pada pemanggilan antarmodul yang saling menunggu tanpa batas waktu. Sehingga, diperlukan Pub-Sub untuk mengubah gaya arsitektur berbasis pesan menjadi asinkron. Alasan dikombinasikan dengan SOA ialah untuk memecah fungsi-fungsi menjadi layanan yang terpisah, sehingga kegagalan suatu layanan tidak akan memengaruhi keseluruhan sistem.
- Revisi diagram (versi 1 → versi 2, apa yang berubah dan kenapa): Hanya ditambah untuk melengkapi jawaban.

## Log Penggunaan AI (Level 2)

> Wajib diisi sesuai kebijakan Level 2 di [`../RUBRIK-UMUM.md`](../RUBRIK-UMUM.md). Tulis "Tidak memakai AI" pada baris pertama jika memang tidak dipakai. Hanya untuk brainstorming ide/outline — bukan untuk kode/analisis/teks akhir.

| Tanggal | Tool AI | Prompt yang diberikan | Ringkasan saran/ide AI | Bagaimana diolah jadi tulisan/kode sendiri |
|29/09/26|Gemini AI|(studi kasus 1) (studi kasus 2) Gambarkan minimal 4 komponen berikut dan interaksinya: modul Pesanan, modul Pembayaran, modul Kurir/Notifikasi, modul Katalog Resto (dan message broker/API gateway jika relevan).
Note: saya menggunakan arsitektur Pub-Sub dan SOA.
Apakah masuk akal apabila alur yang kamii pilih adalah API gateway-Katalog-Pesanan-Pembayaran-Notifikasi/kurir|Alur API Gateway → Katalog → Pesanan → Pembayaran → Notifikasi/Kurir secara umum masuk akal untuk skenario dasar, namun ada beberapa bottleneck fatal jika alur tersebut diimplementasikan secara murni sinkron (rantaian HTTP call langsung dari satu service ke service berikutnya), yaitu pada Pembayaran → Notifikasi / Kurir karena Rentan jika Sinkron, Tepat jika Pub/Sub (Asinkron): |Hanya dipahami dan mencari solusi baru|

| 29/09/26 | Gemini AI | berarti gimana kalo alurnya mulai dari katalog untuk menampilkan menu, lalu ke API, lalu ke pesanan untuk diteruskan ke katalog untuk keep pesanan lalu ke pembayaran dan apabila berhasil, lanjut ke notifikasi | Alur yang Anda sebutkan sudah jauh lebih membaik secara logika bisnis, namun masih ada beberapa poin kritis (potensi bottleneck) yang perlu disesuaikan agar benar-benar sejalan dengan prinsip SOA (Service-Oriented Architecture) dan Pub-Sub (Asynchronous), yaitu pada Diteruskan ke Modul Pesanan, lalu kembali ke Modul Katalog untuk keep / reserve stock karena perlu Penyesuaian. | Dipahami lalu dikembangkan menjadi jawaban sendiri. |

|30/09/26|Gemini AI|Apakah benar pub/sub dan soa mengatasi coupling dengan menggunakan arsitektur soa agar setiap modul independen dan pub/sub agar modul berjalan secara asinkron, sehingga menciptakan latensi yang cukup aman dibandingkan menggunakan metode monolit?|Pernyataan tersebut sebagian besar benar dari segi independensi dan asinkronisasi, tetapi kurang tepat pada poin perbandingan latensi dengan monolit. Kesimpulan: Monolit sebenarnya tidak lambat dalam hal kecepatan eksekusi kode, melainkan lambat dalam waktu tanggap ke pengguna (perceived response time) karena memaksa pengguna menunggu seluruh rantai pemrosesan berat selesai secara berurutan.|Memahami dan mengembangkan ulang menjadi jawaban pada readme|

|30/09/26|Gemini AI|kan ini kami pakai pub-sub sama soa, brrti kan itu ada beberapp modul yang dibuat secara independen. nah itu kalo terjadi error buat lacak errornya itu berarti lebih rumit ya karena kita perlu cari bagian mana yang error diantara banyak modul jadi kaya lebih kompleks gitu kan?|Benar sekali. Pemikiran Anda 100% tepat.|dipahami dan mengembangkan menjadi jawaban sendiri|

|30/09/26|Gemini AI|kan ini alur awal kami setelah di katalog itu masuk API , kalo API tuh mungkin kah dia error? karena kan dia ibarat pintu masuk gitu setelah user misal klik pesan. jadi kalo di API error berarti semua alur di belakang dia error semua?|Benar sekali. Pemikiran Anda 100% tepat. Dalam arsitektur Microservices atau SOA, API Gateway bertindak sebagai Single Point of Failure (SPOF)—artinya, dia adalah satu-satunya "pintu gerbang utama" menuju seluruh backend.|dipahami dan mengembangkan menjadi jawaban sendiri|


