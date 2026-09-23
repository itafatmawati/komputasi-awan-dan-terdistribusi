# Tugas 1 — Analisis Pitfall FoodGo

**Kelompok:** 3

| Nama                     | NIM          | Kontribusi               |
| ------------------------ | ------------ | ------------------------ |
| Ita Fatmawati            | 103072400124 | pitfall 1, 2, kesimpulan |
| Heilyn Alfreda Aritonang | 103072400102 | pitfall 1, 3, kesimpulan |

## Pitfall 1: Latency is zero — ditulis oleh Ita Fatmawati, Heilyn Alfreda

**Bukti di skenario:** "tidak ada timeout sama sekali pada pemanggilan antar service (modul pesanan memanggil modul pembayaran dan menunggu tanpa batas waktu)".

**Kenapa ini keliru:** karena programmer tidak menyiapkan mekanisme untuk menangani latency, seperti apabila memanggil modul pembayaran, respons dari modul pembayaran sangat mungkin terjadi keterlambatan, sehingga apabila itu terjadi karena sistem tidak menentukan batas waktu, maka proses akan terus menunggu tanpa batas waktu

**Dampak ke FoodGo:** Sistem mengalami kegagalan. Hal tersebut disebabkan karena adanya banyak permintaan, misalnya modul pesanan memanggil modul pembayaran. Permintaan tersebut akan menumpuk, karena setiap permintaan yang menunggu akan selalu menggunakan/menahan resource, sehingga apabila trafik naik dan permintaan yang lain juga mengalami hal yang sama, maka hal ini lah yang dapat membuat permintaan menumpuk sehingga server melambat, penuh, dan crash.

**Solusi desain awal:** Membuat sistem timeout untuk menghindari case menunggu tanpa batas waktu (hanya menunggu sampai batas waktu yang ditentukan)

**Trade-off:** Sistem akan menjadi lebih kompleks karena menambahkan penentuan batas waktu dan penanganannya saat terjadi, sehingga akan membebankan programmer dan memungkinkan pengguna melihat pesan kegagalan.

---

## Pitfall 2: Single Point of Failure karena Arsitektur Monolitik — ditulis oleh Ita Fatmawati

**Bukti di skenario:** "Saat trafik naik, satu server yang menangani semua modul (pesanan, pembayaran, notifikasi kurir) kewalahan karena semuanya berjalan di satu proses monolitik yang sama"

**Kenapa ini keliru:** Pernyataan di atas menjelaskan struktur dalam sistem, yaitu satu server menangani semua modul sekaligus. Jika trafik naik, semua beban akan masuk pada satu server yang sama, sehingga server bisa overload/kewalahan, dan karena semua modul terhubung ke satu server yang sama, maka apabila server tersebut overload, tentu semua modul akan ikut terpengaruhi.

**Dampak ke FoodGo:** Aplikasi menjadi lambat, beberapa permintaan mengalami timeout, lalu jika server mengalami crash, maka semua modul yang terhubung tidak akan bisa digunakan atau terganggu.

**Solusi desain awal:** Memisahkan setiap modul pelayanan agar dapat berjalan secara independent(setiap layanan tidak bergantung pada satu proses monolitik)

**Trade-off:** Meningkatkan biaya dan beban programmer karena membutuhkan infrastruktur tambahan(jika ditambahkan server/instance berbeda setiap modul) dan pengelolaan service yang kompleks(harus mengelola banyak service yang ada).

---

## Pitfall 3: Network is always reliable — ditulis oleh Heilyn Alfreda

**Bukti di skenario:** "Tim menemukan bahwa kode mereka menulis asumsi seperti # network is always reliable, no need for retry"

**Kenapa ini keliru:** Hal tersebut keliru karena programmer menganggap bahwa paket data dalam jaringan akan selalu bisa diandalkan/sampai ke tujuan tanpa adanya kemungkinan kegagalan komunikasi.

**Dampak ke FoodGo:** Ketika permintaan dikirim dan terjadi kegagalan komunikasi, maka permintaan tersebut akan langsung gagal karena tidak adanya sistem retry dan proses layanan tersebut menjadi terganggu.

**Solusi desain awal:** Membuat sistem untuk melakukan percobaan ulang secara bertahap agar tidak membebani server target.

**Trade-off:** Sistem akan menjadi lebih kompleks dan berpotensi menerima permintaan berulang yang berlebihan ke server target jika tidak dirancang dengan baik.

---

## Kesimpulan Kelompok

Secara garis besar, arsitektur yang kami sarankan adalah Publish-Subscribe yang mungkin akan kami kombinasikan dengan Service-Oriented Architecture (SOA).
Karena, masalah utama yang kami identifikasi terletak pada pemanggilan antarmodul yang saling menunggu tanpa batas waktu. Sehingga, diperlukan Pub-Sub untuk mengubah gaya arsitektur berbasis pesan menjadi asinkron. Alasan dikombinasikan dengan SOA ialah untuk memecah fungsi-fungsi menjadi layanan yang terpisah, sehingga kegagalan suatu layanan tidak akan memengaruhi keseluruhan sistem.
