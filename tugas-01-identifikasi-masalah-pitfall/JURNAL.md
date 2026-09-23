# Jurnal Proses — Tugas 1

> Isi jurnal ini selama proses diskusi berlangsung, bukan ditulis ulang rapi di akhir. Tulis dengan gaya bebas — poin diskusi, kebuntuan, perubahan pikiran.

## 21-09-2026

- Peserta: Itak, Heilyn
- Poin diskusi: Menganalisis dan memahami soal dan menjawab soal bersama
- Perbedaan pendapat (jika ada): -

## 23-09-2026

- Peserta: Itak, Heilyn
- Poin diskusi: Memperbaiki kualitas jawaban 
- Perbedaan pendapat (jika ada): -

## Review Silang

- Ita Fatmawati mengomentari analisis Heilyn Alfreda: Jawaban kurang detail

## Log Penggunaan AI (Level 2)

> Wajib diisi sesuai kebijakan Level 2 di [`../RUBRIK-UMUM.md`](../RUBRIK-UMUM.md). Tulis "Tidak memakai AI" pada baris pertama jika memang tidak dipakai. Hanya untuk brainstorming ide/outline — bukan untuk kode/analisis/teks akhir.

| Tanggal | Tool AI | Prompt yang diberikan | Ringkasan saran/ide AI | Bagaimana diolah jadi tulisan/kode sendiri |

| 21-09-2026 | ChatGPT | (soal) bagaimana cara mengidentifikasi pitfall yang ada pada deskripsi tugas di atas? berikan pendekatannya! | 1. Pisahkan dulu "gejala" dari "penyebab" 2. Cari asumsi yang tidak realistis 3. Identifikasi dependency antar-komponen 4. Identifikasi masalah skala 5. Hubungkan pitfall dengan Fallacies of Distributed Computing 6. Jangan berhenti pada "nama pitfall" 7. Gunakan pendekatan "5 Why" 8. Bedakan root cause, pitfall, dan symptom 9. Framework identifikasi yang bisa Anda gunakan 10. Cara paling mudah mengingat pendekatannya | Berdiskusi dengan tim, lalu menjawab soal dengan bahasa sendiri. |

| 22-09-2026 | ChatGPT | daftar _\_Fallacies of Distributed Computing\__ (referensi: "the network is reliable", "latency is zero", "bandwidth is infinite", "the network is secure", "topology doesn't change", "there is one administrator", "transport cost is zero", "the network is homogeneous") **\*\*DAN/ATAU\*\*** masalah desain sistem terdistribusi lain yang relevan (mis. _\_single point of failure\__ karena arsitektur monolitik). jelaskan macam " jenis daftar di atas | The network is reliable: menganggap jaringan selalu berhasil dan stabil.
Latency is zero: menganggap komunikasi tanpa delay.
Bandwidth is infinite: mengangap kapasitas jaringan tidak terbatas.
The network is secure: menganggap jaringan selalu aman.
Topology doesn't change: menganggap koneksi jaringan selalu tetap.
There is one administrator: menganggap sistem hanya punya satu pengelola.
Transport cost is zero: menganggap komunikasi tidak memiliki biaya/overhead.
The network is homogeneous: menganggap semua perangkat/jaringan memiliki karakteristik yang sama.
| hanya dipahami |

| 22-09-2026 | ChatGPT | apa itu _single point of failure\__ karena arsitektur monolitik | Single Point of Failure (SPOF) artinya satu bagian sistem yang kalau mengalami kegagalan, bisa menyebabkan bagian lain atau seluruh sistem ikut gagal.
| dipahami, dikaitkan dengan soal, lalu olah/tulis dengan bahasa sendiri |

| 23-09-2026 | GeminiAI | Architectural style: Layered, SOA, Peer-to-Peer, Publish-Subscribe. Berikan penjelasan mengenai keempat arsitektur di atas secara lengkap | 1. Layered Architecture (Arsitektur Berlapis)
Arsitektur Berlapis (juga dikenal sebagai N-Tier Architecture) adalah salah satu pola arsitektur paling klasik dan umum digunakan. Dalam arsitektur ini, komponen sistem diorganisasikan ke dalam lapisan-lapisan (layers) terpisah secara horizontal, di mana setiap lapisan memiliki peran dan tanggung jawab spesifik. 2. Service-Oriented Architecture (SOA)
SOA adalah gaya arsitektur berorientasi layanan di mana fungsi-fungsi aplikasi dibagi menjadi komponen-komponen terpisah yang disebut services (layanan). Layanan-layanan ini berkomunikasi satu sama lain melalui protokol standar over network. 3. Peer-to-Peer (P2P) Architecture
Peer-to-Peer adalah gaya arsitektur terdesentralisasi di mana setiap node (disebut peer) dalam jaringan memiliki kedudukan dan kemampuan yang seimbang. Setiap peer dapat bertindak sebagai klien (meminta resource) sekaligus sebagai server (menyediakan resource). 4. Publish-Subscribe Architecture (Pub/Sub)
Publish-Subscribe adalah gaya arsitektur berbasis pesan (messaging pattern) yang bersifat asinkron dan decoupled (tidak terikat secara langsung). Komponen dalam sistem berkomunikasi tanpa perlu mengetahui siapa penerima atau pengirim pesan tersebut.
| Berdiskusi dengan tim dan memilih arsitektur yang paling sesuai|


| 23-09-2026 | GeminiAI | apa kelebihan dan kekurangan jika arsitektur pub/sub dikombinasikan dengan layered? | Kelebihan: 1. Struktur Kode Rapi Sekaligus Tidak Saling Keterikatan (Decoupled) 2. Responsivitas Tinggi dan Beban Terurai (Non-blocking) 3. Skalabilitas Terarah (Targeted Scalability) 4. Ketahanan Sistem yang Lebih Baik (Fault Tolerance). Kekurangan : 1. Peningkatan Kompleksitas Sistem & Infrastruktur 2. Tantangan Konsistensi Data (Eventual Consistency) 3. Pelacakan Kesalahan (Debugging & Tracing) Lebih Sulit 4. Risiko Overhead Latensi untuk Proses Sederhana
| hanya dipahami |

| 23-09-2026 | GeminiAI | apa kelebihan dan kekurangan jika arsitektur pub/sub dikombinasikan dengan soa? | Kelebihan: 1. Mengurangi Keterikatan Antar-Layanan Enterprise (Loose Coupling) 2. Peningkatan Performa dan Responsivitas Sistem  3. Kemudahan Pengembangan dan Extensibility 4. Isolasi Kegagalan (Fault Isolation & Resilience). Kekurangan : 1. Kompleksitas Tata Kelola (Governance & Schema Evolution) 2. Hilangnya Alur Bisnis Terpusat yang Jelas (Orchestration Overhead) 3. Penanganan Transaksi Terdistribusi yang Sulit (Saga Pattern) 4. Double Processing dan Urutan Pesan (Message Ordering)
| hanya dipahami |

| 23-09-2026 | GeminiAI | identifikasi kelebihan dan kekurangan dan perbedaan keduanya | Layered + Pub/Sub : Fokus pada struktur internal satu aplikasi, Cocok untuk aplikasi tunggal/modular monolith, Biasanya menggunakan database utama yang sama, Cocok untuk background job, notifikasi, dan event internal aplikasi.
SOA + Pub/Sub :  Fokus pada integrasi antar-sistem, Mencakup banyak aplikasi/domain enterprise, Setiap service mengelola data miliknya sendiri, Cocok untuk transaksi bisnis skala besar, seperti perbankan, e-commerce, dan logistik.
| Berdiskusi dengan tim untuk memilih pilihan arsitektur yang cocok|




