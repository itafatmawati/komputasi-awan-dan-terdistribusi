# Tugas 2 (Pekan 2) — Perancangan Arsitektur untuk FoodGo

**Materi terkait:** Architectural style (Layered, SOA, Peer-to-Peer, Publish-Subscribe).

## Studi Kasus

Melanjutkan Tugas 1: FoodGo butuh sistem yang **decoupled** agar tim kurir dan tim resto tidak saling mengganggu ketika salah satu modul diperbarui/deploy ulang. Saat ini semua modul (pesanan, pembayaran, notifikasi kurir, katalog resto) berjalan sebagai satu aplikasi monolitik — sekali deploy, semua modul ikut restart dan berisiko downtime total.

## Tugas Kelompok

1. Pilih **satu** gaya arsitektur utama: **Service-Oriented Architecture (SOA)** atau **Publish-Subscribe**. Boleh dikombinasikan (mis. SOA untuk service inti + Pub-Sub untuk notifikasi), tapi harus dijustifikasi kenapa kombinasi ini yang dipilih.
2. Gambarkan minimal 4 komponen berikut dan interaksinya: modul Pesanan, modul Pembayaran, modul Kurir/Notifikasi, modul Katalog Resto (dan message broker/API gateway jika relevan).
3. Jelaskan alur satu skenario penuh secara end-to-end di diagram (misalnya: pelanggan buat pesanan → bayar → resto terima notifikasi → kurir ditugaskan) — tunjukkan komponen mana berkomunikasi dengan siapa, dan **jenis komunikasinya** (sinkron/asinkron, request-response/event).
4. Analisis tertulis: kenapa gaya ini mengatasi masalah _coupling_ dari Tugas 1, dan apa trade-off-nya (mis. Pub-Sub menambah kompleksitas debugging karena alur tidak linear).

## Jawaban

````markdown
```mermaid
graph LR
    Client[Pelanggan] -->|Sinkron, HTTP GET| Katalog[Modul Katalog Resto]
    Client -->|Sinkron, HTTP POST| Gateway[API Gateaway]
    Gateway --> Pesanan[Modul Pesanan]

    Pesanan -->|Sinkron, REST| Katalog
    Pesanan -.->|Status: PENDING| Pesanan
    Pesanan -->|Sinkron, REST| Bayar[Modul Pembayaran]

    Bayar -->|Asinkron, Non-blocking| Broker[Broker]

    Broker -->|Asinkron, Consume Event| Pesanan
    Broker -->|Asinkron, Consume Event| Notif[Notifikasi Resto]
    Broker -->|Asinkron, Consume Event| Kurir[Modul Kurir]
```
````

Alasan Pub/Sub dan SOA mengatasi Tugas 1 adalah menghapus cascading timeout, karena pada studi kasus 01, saat sistem kurir melambat, maka modul pesanan akan melambat. Dengan adanya Pub/Sub, Modul Pembayaran langsung mengembalikan respon ke pengguna setelah menerbitkan event ke Message Broker. Lalu, karena seluruh modul dibuat secara independen, maka saat modul kurir mengalami crash dan gagal jaringan sementara, proses checkout dan pembayaran pelanggan tetap berjalan secara normal dan tidak membatalkan transaksi karena pesanan akan tersimpan dalam message broker. Arsitektur ini memindahkan proses berat seperti penugasan kurir dan notifikasi resto ke latar belakang, sehingga waktu tunggu pengguna jauh lebih singkat.

## Cara Membuat Diagram (Gratis, Cukup Laptop)

Tidak perlu software berbayar. Dua opsi:

**Opsi A — Mermaid di dalam Markdown (disarankan).** Ditulis sebagai teks biasa di `README.md`, otomatis dirender jadi diagram oleh GitHub — tidak perlu install apa pun.

````markdown
```mermaid
graph LR
  Client[Pelanggan] -->|HTTP request pesan| OrderSvc[Service Pesanan]
  OrderSvc -->|RPC sinkron| PaymentSvc[Service Pembayaran]
  OrderSvc -->|publish event OrderCreated| Broker[(Message Broker)]
  Broker -->|subscribe| NotifSvc[Service Notifikasi Kurir]
  Broker -->|subscribe| RestoSvc[Service Katalog Resto]
```
````

**Opsi B — draw.io / diagrams.net** (gratis, jalan di browser tanpa akun, atau app desktop offline di [app.diagrams.net](https://app.diagrams.net/)). Ekspor sebagai `.png` dan simpan di folder `diagram/`.

## Struktur Submission

```
tugas-02-perancangan-arsitektur/
├── README.md          # Analisis + diagram Mermaid (jika Opsi A) atau referensi ke diagram/
├── JURNAL.md
└── diagram/            # File .png/.drawio jika pakai Opsi B
```

## Rubrik Penilaian (Tugas 2)

| Komponen                            | Bobot | Kriteria                                                                     |
| ----------------------------------- | ----- | ---------------------------------------------------------------------------- |
| Ketepatan pemilihan gaya arsitektur | 20%   | Justifikasi SOA/Pub-Sub sesuai kebutuhan _decoupling_ di skenario            |
| Kelengkapan & kejelasan diagram     | 30%   | Semua komponen kunci ada, jenis komunikasi (sinkron/asinkron) jelas ditandai |
| Analisis trade-off                  | 30%   | Bukan hanya kelebihan — kekurangan/kompleksitas baru juga dibahas            |
| Proses & kontribusi kelompok        | 20%   | `JURNAL.md`, commit history                                                  |

## Batasan Penggunaan AI (Level 2)

Kebijakan **Level 2 (AI Assisted Idea Generation & Structuring)** berlaku — lihat [`../RUBRIK-UMUM.md`](../RUBRIK-UMUM.md). Boleh memakai AI untuk brainstorming komponen apa saja yang umum ada di gaya arsitektur SOA/Pub-Sub; **tidak boleh** meminta AI menggambar diagram final atau menuliskan analisis trade-off yang tinggal ditempel. Catat pemakaian AI di "Log Penggunaan AI" pada `JURNAL.md`.

- Diagram Mermaid/draw.io yang "terlalu generik" (identik dengan contoh tutorial di internet tanpa penyesuaian ke kasus FoodGo) akan dinilai rendah pada komponen kelengkapan & kejelasan diagram.
