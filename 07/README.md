Materi Minggu 7: Skalabilitas Berbasis Kontainer & Virtualisasi
AI yang digunakan: Google Gemini
Prompt: Jelaskan konsep perbedaan antara Scale-Up dan Scale-Out, perbedaan mendasar arsitektur Virtual Machine vs Kontainer, serta bagaimana peran Kubernetes dan FinOps dalam efisiensi sistem.
Bagian yang disesuaikan dari keluaran prompt ada pada: Merapikan poin perbandingan teknis VM dan kontainer agar langsung ke inti konsep, menyederhanakan penjelasan arsitektur hibrida, serta merangkum dampak efisiensi FinOps.

---

CATATAN KULIAH: SKALABILITAS BERBASIS KONTAINER DAN VIRTUALISASI

1. MENGHADAPI LONJAKAN BEBAN: SCALE-UP VS SCALE-OUT
Saat jumlah pengguna aplikasi melonjak tajam, ada dua pendekatan untuk meningkatkan kapasitas sistem:

Scale-Up (Vertical Scaling):
- Menambah spesifikasi hardware pada server yang sama (tambah vCPU, tambah RAM, perbesar disk).
- Kelemahan: Ada batas fisik maksimal hardware dan biasanya server harus dimatikan atau direstart saat upgrade dilakukan, menimbulkan downtime.

Scale-Out (Horizontal Scaling):
- Menambah jumlah unit server atau kontainer secara paralel yang bekerja bersama-sama.
- Kelebihan: Skalabilitas praktis tanpa batas, tidak ada gangguan layanan (zero downtime), dan beban dibagi rata oleh load balancer. Sangat cocok untuk arsitektur aplikasi modern (cloud-native).


2. MENGENAL ARSITEKTUR VIRTUAL MACHINE (VM)
Virtual Machine membagi satu server fisik menjadi beberapa komputer virtual terisolasi menggunakan software bernama Hypervisor:
- Hypervisor Type 1 (Bare-Metal): Berjalan langsung di atas perangkat keras fisik tanpa sistem operasi perantara (contoh: VMware ESXi, KVM). Ini standar yang dipakai di data center enterprise.
- Hypervisor Type 2 (Hosted): Berjalan sebagai program aplikasi di atas OS utama laptop atau komputer (contoh: VirtualBox, VMware Workstation).
Setiap VM menjalankan Guest OS sendiri secara lengkap, sehingga membutuhkan alokasi memori RAM dan ruang penyimpanan disk yang cukup besar (beberapa Gigabyte per VM).


3. ARSITEKTUR KONTAINER (DOCKER DAN CONTAINERD)
Berbeda dengan VM, kontainer tidak membawa sistem operasi lengkap di dalamnya. Kontainer hanya mengemas kode aplikasi beserta pustaka (libraries) yang dibutuhkannya, lalu berbagi kernel dengan sistem operasi host (kernel sharing).

Mengapa Kontainer Sangat Populer?
1. Booting Super Cepat: Aplikasi kontainer bisa menyala dalam hitungan detik atau milidetik, karena tidak perlu melalui proses booting OS dari awal.
2. Ukuran File Sangat Ringan: Hanya berukuran puluhan hingga ratusan Megabyte (MB), jauh lebih kecil dibanding image VM yang berukuran Gigabyte (GB).
3. Konsistensi Lingkungan: Menjamin kode aplikasi berjalan sama persis di laptop developer maupun di server produksi tanpa konflik dependensi.
4. Hemat Memori: Mengonsumsi RAM 30 sampai 50 persen lebih sedikit dibanding VM.


4. PERBANDINGAN RINGKAS: VM VS KONTAINER

Perbandingan Parameter:
- Lapisan Abstraksi:
  VM di tingkat perangkat keras (lewat Hypervisor).
  Kontainer di tingkat sistem operasi (berbagi Kernel Host).
- Waktu Booting:
  VM butuh 2 sampai 5 menit.
  Kontainer butuh hitungan detik (kurang dari 1 sampai 3 detik).
- Ukuran Image:
  VM berukuran besar (beberapa Gigabyte).
  Kontainer sangat ringan (puluhan hingga ratusan Megabyte).
- Isolasi Keamanan:
  VM menggunakan isolasi keras tingkat hardware.
  Kontainer menggunakan isolasi tingkat proses (process-level).
- Kecepatan Penskalaan:
  VM relatif lambat dan berat.
  Kontainer sangat cepat dan fleksibel.

Dampak ke Bisnis: Kecepatan autoscaling kontainer yang mampu bereaksi dalam waktu kurang dari 3 detik melindungi bisnis dari kerugian finansial akibat server tumbang saat terjadi lonjakan transaksi mendadak.


5. ORKESTRASI DENGAN KUBERNETES (K8S)
Jika kita menjalankan ratusan kontainer di server produksi, mustahil mengelolanya satu per satu secara manual. Di sinilah peran Kubernetes:
- Auto-Scaling (HPA): Menambah atau mengurangi jumlah pod kontainer secara otomatis saat beban pemakaian CPU atau RAM melonjak.
- Self-Healing: Jika ada kontainer yang error, macet, atau mati mendadak, Kubernetes akan langsung mendeteksinya dan membuat kontainer baru sebagai pengganti.
- Load Balancing: Membagi trafik pengguna secara merata ke seluruh kontainer yang aktif dan sehat.


6. ARSITEKTUR STANDAR INDUSTRI: GABUNGAN VM DAN KONTAINER
Di dunia kerja nyata, arsitektur yang umum diterapkan adalah menggabungkan keduanya:
- VM sebagai Fondasi Infrastruktur: Dipakai untuk menyewa node komputasi di cloud provider (seperti AWS EC2) demi jaminan keamanan dan isolasi keras antar-akun.
- Kontainer di Dalam VM: Aplikasi dan mikroservis dijalankan di dalam kontainer di atas VM tersebut demi kecepatan rilis, kemudahan update, dan efisiensi memori.


7. DAMPAK FINOPS DAN PENGHEMATAN BIAYA (TCO)
Beralih dari arsitektur VM murni ke kontainer memberikan efisiensi biaya yang sangat masif:
- Hemat Hardware (CAPEX): Beban kerja yang biasanya butuh sekitar 10 server fisik berbasis VM bisa dirampingkan menjadi hanya sekitar 4 server fisik berbasis kontainer (hemat biaya hardware hingga 60 persen).
- Hemat Lisensi: Memangkas biaya pembelian lisensi sistem operasi Windows Server atau lisensi hypervisor berbayar hingga 80 persen.
- Hemat Listrik dan Pendingin (OPEX): Berkurangnya jumlah server fisik di rak data center memotong tagihan listrik dan AC pendingin hingga 60 persen.
- Optimasi Utilisasi: Tingkat utilisasi CPU dan RAM bisa dimaksimalkan mencapai 75 sampai 80 persen tanpa membiarkan mesin menganggur.


8. STUDI KASUS NYATA
- E-Commerce Flash Sale: Menghadapi lonjakan pembeli 10 kali lipat dalam waktu singkat. Dengan Kubernetes HPA, ribuan pod kontainer aplikasi katalog diperbanyak otomatis dalam tempo 30 detik tanpa mengganggu sistem pembayaran.
- Sistem Perbankan Digital: Menggabungkan isolasi ketat VM untuk menyimpan database transaksi finansial nasabah, sedangkan aplikasi mobile banking dijalankan di atas kontainer agar tim pengembang bisa sering merilis fitur baru dengan cepat dan aman.
