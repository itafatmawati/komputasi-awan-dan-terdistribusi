# Tugas 1 — Analisis Pitfall FoodGo

**Kelompok:** 3

| Nama                     | NIM          | Kontribusi |
| ------------------------ | ------------ | ---------- |
| Ita Fatmawati            | 103072400124 | pitfall 1  |
| Heilyn Alfreda Aritonang | 103072400102 | pitfall 1  |

## Pitfall 1: Latency is zero — ditulis oleh Ita Fatmawati, Heilyn Alfreda

**Bukti di skenario:** Tim menemukan bahwa kode mereka menulis asumsi seperti # network is always reliable, no need for retry dan tidak ada timeout sama sekali pada pemanggilan antar service (modul pesanan memanggil modul pembayaran dan menunggu tanpa batas waktu).

**Kenapa ini keliru:** Karena menunggu tanpa batas waktu merupakan ciri-ciri dari kekeliruan di dalam proses pengembangan sistem, tepatnya pada pembuatan waktu timeout. Hal ini seolah-olah merepresentasikan bahwa programmer menganggap proses transmisi data dan eksekusi di jaringan terjadi secara instan(latencynya 0), sehingga tidak menyiapkan case apabila pemrosesan membutuhkan waktu lama.

**Dampak ke FoodGo:** Sistem mengalami kegagalan. Hal tersebut disebabkan karena adanya banyak permintaan, misalnya modul pesanan memanggil modul pembayaran. Permintaan tersebut akan menumpuk karena tidak adanya sistem timeout yang membuat server melambat, penuh, dan crash.

**Solusi desain awal:** Membuat sistem timeout.

**Trade-off:** Sistem akan menjadi lebih kompleks sehingga akan membebankan programmer dan memungkinkan pengguna melihat pesan kegagalan.

---

## Pitfall 2: Single Point of Failure karena Arsitektur Monolitik — ditulis oleh Ita Fatmawati

**Bukti di skenario:** "Saat trafik naik, satu server yang menangani semua modul (pesanan, pembayaran, notifikasi kurir) kewalahan karena semuanya berjalan di satu proses monolitik yang sama"

**Kenapa ini keliru:** Pernyataan di atas menjelaskan struktur dalam sistem FoodGo, yaitu satu server menangani semua modul sekaligus. Jika trafik naik, semua beban akan masuk pada satu server yang sama, sehingga server bisa overload/ kewalahan.

**Dampak ke FoodGo:** Aplikasi menjadi lambat, beberapa permintaan mengalami timeout, dan jika server crash, maka semua modul yang terhubung tidak akan bisa digunakan atau terganggu.

**Solusi desain awal:** Memisahkan setiap modul pelayanan agar dapat berjalan secara independent

**Trade-off:** Meningkatkan biaya dan beban programmer karena membutuhkan infrastruktur tambahan dan pengelolaan service yang kompleks.

---

## Pitfall 3: [nama pitfall] — ditulis oleh [nama]

(ulangi struktur di atas)

---

## Kesimpulan Kelompok

[Ringkasan: jika FoodGo memperbaiki ketiga pitfall ini, apa arsitektur yang disarankan secara garis besar? Kaitkan dengan Tugas 2.]
