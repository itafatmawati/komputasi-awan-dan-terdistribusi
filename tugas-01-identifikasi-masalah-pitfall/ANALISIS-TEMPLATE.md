# Tugas 1 — Analisis Pitfall FoodGo

**Kelompok:** 3

| Nama | NIM | Kontribusi |
|---|---|---|
| Ita Fatmawati | 103072400124 | pitfall 1 |
| [nama 2] | [nim] | [pitfall/bagian yang dikerjakan] |
| [nama 3] | [nim] | [pitfall/bagian yang dikerjakan] |

## Pitfall 1: Latency is zero — ditulis oleh Ita Fatmawati

**Bukti di skenario:** Tim menemukan bahwa kode mereka menulis asumsi seperti # network is always reliable, no need for retry dan tidak ada timeout sama sekali pada pemanggilan antar service (modul pesanan memanggil modul pembayaran dan menunggu tanpa batas waktu).

**Kenapa ini keliru:** Karena menunggu tanpa batas waktu merupakan ciri-ciri dari kekeliruan di dalam proses pengembangan sistem, tepatnya pada pembuatan waktu timeout. Hal ini seolah-olah merepresentasikan bahwa programmer menganggap proses transmisi data dan eksekusi di jaringan terjadi secara instan(latencynya 0), sehingga tidak menyiapkan case apabila pemrosesan membutuhkan waktu lama.

**Dampak ke FoodGo:** [mekanisme kegagalan konkret]

**Solusi desain awal:** [usulan solusi]

**Trade-off:** [apa yang dikorbankan/risiko dari solusi ini]

---

## Pitfall 2: [nama pitfall] — ditulis oleh [nama]

(ulangi struktur di atas)

---

## Pitfall 3: [nama pitfall] — ditulis oleh [nama]

(ulangi struktur di atas)

---

## Kesimpulan Kelompok

[Ringkasan: jika FoodGo memperbaiki ketiga pitfall ini, apa arsitektur yang disarankan secara garis besar? Kaitkan dengan Tugas 2.]
