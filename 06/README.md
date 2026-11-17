Materi Minggu 6: Desain High Availability dan Efisiensi Infrastruktur
Prompt: "Rangkum materi Desain High Availability dan Efisiensi Infrastruktur, jelaskan rumus ketersediaan (MTBF/MTTR), perbedaan RTO vs RPO, eliminasi SPOF, arsitektur stateless, strategi disaster recovery, dan studi kasus portal akademik."
Bagian yang disesuaikan dari keluaran prompt ada pada: Mengubah nada tulisan agar lebih mengalir dan mudah dipahami, menyajikan simulasi perhitungan availability Python secara ringkas, dan merangkum solusi teknis studi kasus portal kampus agar langsung ke intinya.

---

# Catatan Kuliah: Desain High Availability dan Efisiensi Infrastruktur

## 1. Tantangan Desain: Ketersediaan vs Biaya
Dalam merancang arsitektur cloud, kita selalu menghadapi tarik-menarik antara dua hal:
* **High Availability (HA):** Menjaga agar aplikasi tetap bisa diakses meskipun ada komponen server, jaringan, atau data center yang mengalami kerusakan.
* **Efisiensi Biaya:** Tidak membangun kapasitas cadangan secara berlebihan yang membuang-buang anggaran.

> **Prinsip Utama:** Sistem yang baik bukan sistem yang paling mahal dengan server cadangan di mana-mana, melainkan sistem yang tahan uji sesuai batas toleransi risiko bisnisnya.

---

## 2. Metrik Ketersediaan: Availability, MTBF, dan MTTR
Ketersediaan sistem dihitung secara matematis dengan rumus:
$$\text{Availability} \approx \frac{\text{MTBF}}{\text{MTBF} + \text{MTTR}}$$
* **MTBF (*Mean Time Between Failures*):** Rata-rata rentang waktu sistem beroperasi lancar di antara dua gangguan.
* **MTTR (*Mean Time To Repair*):** Rata-rata durasi waktu yang dibutuhkan tim teknis untuk memperbaiki sistem saat terjadi gangguan.

### Contoh Perhitungan (1 Tahun = 525.600 Menit):
Misalkan dalam setahun diperkirakan terjadi 4 kali insiden, dengan total lama pemulihan 120 menit:
* $\text{MTBF} = \frac{525.600}{4} = 131.400\text{ menit}$
* $\text{MTTR} = \frac{120}{4} = 30\text{ menit}$
* $\text{Availability} = \frac{131.400}{131.400 + 30} = \frac{131.400}{131.430} \approx \mathbf{99,98\%}$

### Berapa Toleransi Downtime dalam Setahun?
* **99% (Two Nines):** Toleransi mati $\pm$ **3 hari 15 jam** per tahun.
* **99,9% (Three Nines):** Toleransi mati $\pm$ **8 jam 46 menit** per tahun.
* **99,99% (Four Nines):** Toleransi mati $\pm$ **52 menit** per tahun.
* **99,999% (Five Nines):** Toleransi mati hanya $\pm$ **5 menit** per tahun (sangat mahal untuk dicapai).

---

## 3. RTO vs RPO: Dua Sasaran Pemulihan
* **RTO (*Recovery Time Objective*):** *"Berapa lama sistem boleh mati?"*  
  Batas maksimal waktu yang diizinkan untuk menghidupkan kembali layanan setelah terjadi insiden (contoh: RTO portal kampus maksimal 2 jam).
* **RPO (*Recovery Point Objective*):** *"Berapa banyak data transaksi yang boleh hilang?"*  
  Rentang waktu maksimal kehilangan data yang bisa ditoleransi (contoh: jika RPO 15 menit, maka data transaksi 15 menit terakhir sebelum server meledak boleh hilang/diinput ulang).

---

## 4. Menghilangkan Titik Kegagalan Tunggal (*SPOF*)
**Single Point of Failure (SPOF)** adalah satu titik atau komponen yang jika rusak, maka seluruh sistem ikut lumpuh seketika.
* **Solusi:** Memberikan redundansi (komponen ganda) dan memasang **Load Balancer** di depan untuk membagi beban ke beberapa server aplikasi yang aktif secara bersamaan (*Round Robin, Least Connections*).

### Arsitektur Stateful vs Stateless
* **Stateful (Kuno):** Data sesi login pengguna disimpan langsung di dalam memori satu server. Begitu server tersebut mati, sesi pengguna putus dan harus login ulang.
* **Stateless (Modern):** Server aplikasi sama sekali tidak menyimpan status sesi di memori lokalnya. Sesi login disimpan di database memori bersama (seperti Redis), dan file diunggah ke Object Storage (seperti S3). Hasilnya, server aplikasi bisa ditambah atau diganti seketika tanpa mengganggu pengguna.

---

## 5. Ketersediaan Basis Data (*Database HA*)
Menjaga ketersediaan database lebih rumit dibanding server aplikasi karena menyangkut konsistensi data:
* **Primary-Standby:** Satu server database primer melayani operasi penulisan (*write*), sementara server sekunder siap siaga menggantikan (*failover*) jika primer mati.
* **Replikasi Sinkron vs Asinkron:**
  * *Sinkron:* Transaksi baru dianggap sukses jika sudah tercatat di kedua server. Sangat aman dari kehilangan data, tetapi sedikit lebih lambat.
  * *Asinkron:* Transaksi langsung sukses di server primer, lalu disalin ke sekunder. Sangat cepat, tapi ada risiko transaksi terakhir belum sempat tersalin saat mati lampu.
* **Bahaya Split-Brain:** Situasi di mana kedua server database kehilangan kontak satu sama lain dan masing-masing mengira server pasangannya sudah mati, sehingga keduanya menerima data baru secara terpisah. Ini dicegah dengan teknik **Fencing** (memutus otomatis node yang bermasalah dari jaringan).

---

## 6. Strategi Disaster Recovery (DR)
Ada 4 tingkatan strategi pemulihan bencana dari yang paling murah sampai paling mahal:
1. **Backup & Restore:** Backup rutin disimpan, baru di-restore jika ada bencana (biaya paling murah, tapi butuh waktu berjam-jam/berhari-hari untuk pulih).
2. **Pilot Light:** Database inti selalu tersinkronisasi di data center cadangan, sementara server aplikasi baru dinyalakan saat keadaan darurat.
3. **Warm Standby:** Sistem cadangan berjalan terus tapi dengan kapasitas kecil; baru dinaikkan kapasitasnya saat failover.
4. **Hot Standby (Active-Active):** Dua data center berjalan bersamaan dengan kapasitas penuh (paling cepat pulih dalam hitungan detik, tetapi biayanya paling mahal).

> **Kaidah Backup 3-2-1:** Simpan minimal **3** salinan data, pada **2** jenis media berbeda, dan **1** salinan disimpan di tempat terpisah (*off-site/cloud*). Ingat: backup tidak ada gunanya jika tidak pernah diuji coba pemulihannya (*restore test*).

---

## 7. Studi Kasus: Portal Akademik Kampus
* **Kondisi Awal:** 1 VM aplikasi, 1 server database tunggal, backup harian manual, sering down parah saat masa pengisian KRS.
* **Target:** Ketersediaan 99,9%, RTO maksimal 2 jam, RPO maksimal 15 menit, data pembayaran tidak boleh hilang.
* **Solusi Desain:**
  1. Pasang Load Balancer Multi-AZ di depan aplikasi.
  2. Ubah server aplikasi menjadi arsitektur *stateless* (minimal 2 node paralel) dengan fitur autoscaling saat jadwal KRS tiba.
  3. Konfigurasi database menjadi *Primary-Standby* dengan replikasi sinkron untuk memenuhi target RPO $\le$ 15 menit.
  4. Pindahkan sesi login ke cache terdistribusi dan file dokumen ke Object Storage.
