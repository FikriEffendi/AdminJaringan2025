<div align="center">
  <h1 style="text-align: center;font-weight: bold">LAPORAN<br>WORKSHOP ADMINISTRASI JARINGAN</h1>
  <h4 style="text-align: center;">Dosen Pengampu : Dr. Ferry Astika Saputra, S.T., M.Sc.</h4>
</div>
<br />
<div align="center">
  <img src="https://upload.wikimedia.org/wikipedia/id/4/44/Logo_PENS.png" alt="Logo PENS">
  <h3 style="text-align: center;">Disusun Oleh : </h3>
  <p style="text-align: center;">
    <strong>Fikri Athanabil Effendi (3123500012) </strong><br>
  </p>
<h3 style="text-align: center;line-height: 1.5">Politeknik Elektronika Negeri Surabaya<br>Departemen Teknik Informatika Dan Komputer<br>Program Studi Teknik Informatika<br>2024/2025</h3>
  <hr><hr>
</div>

## Bab 4: Kontrol Proses

### Komponen dari sebuah proses

Sebuah proses terdiri dari ruang alamat dan kumpulan struktur data dalam kernel. Ruang alamat adalah kumpulan halaman memori yang telah ditandai oleh kernel untuk penggunaan proses. Halaman-halaman memori ini adalah sebuah unit pengolaan memori yang digunakan untuk menyimpan kode, data, dan tumpukan proses. Struktur data dalam kernel mencatat status proses, prioritasnya, parameter penjadwalan, dan lain-lain.

Dalam kumpulan struktur data kernel merekam berbagai informasi untuk masing-masing proses, seperti:

- Proses pemetaan ruang alamat
- Status proses saat ini, seperti Running, Sleeping, dan seterusnya
- Prioritas untuk proses
- Informasi tentang sumber daya yang telah digunakan oleh proses, seperti CPU, memori, dan lain-lain
- Informasi tentang proses files dan port jaringan yang telah terbuka
- Masker sinyal, kumpulan sinyal yang saat ini diblokir
- Pemilik proses

Sebuah "Thread" adalah eksekusi konteks dalam proses. Sebuah proses memiliki beberapa thread, yang dimana semua berbagi ruang alamat dan sumber daya yang sama. Thread digunakan untuk mencapai paralelisme dalam proses yang berarti agar thread dapat bekerja secara bersama. Thread terkenal sebagai proses yang ringan dikarenakan mereka mudah dibuat dan dihancurkan dibandingkan dengan proses.

### PID: Angka Process ID

Setiap proses diidentifikasikan oleh angka proses ID yang unik. PID merupakan integer yang ditugaskan oleh kernel untuk setiap proses saat proses tersebut dibuat. PID digunakan untuk mereferensikan proses pada berbagai pemanggilan sistem.

### PPID: Angka parent process ID

Setiap proses juga diasosiakan dengan parent process, yang berarti proses yang membuat proses tersebut. PPID merupakan PID dari orang tua dari proses tersebut. PPID digunakan untuk mereferensikan orang tua dari proses pada berbagai pemanggilan sistem.

### UID dan EUID: user ID dan effective user ID

User ID merupakan ID pengguna dari pengguna yang menjalankan proses. Effective User ID merupakan UID yang proses gunakan untuk menentukan sumber daya yang proses dapat gunakan. EUID digunakan untuk mengontrol akses ke file, port jaringan, dan sumber daya lainnya.

### Siklus hidup dari proses

Untuk membuat proses baru, proses menyalin dirinya sendiri dengan fork system call. Fork membuat salinan proses yang asli, dan salinan tersebut sebagian besar identik dengan parent-nya. Proses yang baru memiliki PID berbeda dan memiliki informasi perhitungan sendiri.

Saat sistem boot, kernel secara otomatis membuat dan menginstall beberapa proses. Proses yang paling terlihat adalah `init` atau `systemd`, yang selalu memiliki angka proses 1. Proses ini mengeksekusi skrip sistem startup.

### Signals

Signal merupakan cara untuk mengirim notifikasi kepada proses. Lebih dari 30 jenis yang didefinisikan, Mereka digunakan dalam berbagai cara:

- Sebagai komunikasi antar proses
- Dikirim oleh driver terminal untuk menghentikan, menginterupsi, atau menangguhkan proses saat tombol tertentu ditekan
- Dikirim oleh administrator (dengan `kill`) untuk berbagai tujuan
- Dikirim oleh kernel saat proses melakukan kesalahan fatal
- Dikirim oleh kernel untuk memberi notifikasi untuk sebuah proses tentang kondisi khusus

### kill: Mengirim sinyal

- Perintah `kill`<br>
  Perintah ini digunakan untuk menghentikan proses dengan cara mengirim sinyal. Standarnya, perintah tersebut mengirim sinyal `TERM` yang dimana meminta proses untuk menghentikan sendiri. Namun, sinyal `TERM` bisa ditangkap, diblokir, atau diabaikan oleh proses. Menggunakan kill -9 (atau kill -KILL), sinyal KILL tidak bisa ditangkap, diblokir, atau diabaikan.<br>
  syntax perintah `kill`:

```bash
kill [-signal] pid
```

Contoh percobaan:<br>
<img src="assets/k1.png" alt="ss" width="600"/>

<img src="assets/k2.png" alt="ss" width="600"/>
<br><br>

- Perintah `killall`
  Perintah ini digunakan untuk menghentikan proses berdasarkan nama, bukan PID (contoh: killall firefox-esr), tetapi tidak tersedia di semua sistem.<br>
  syntax perintah `killall`:

```bash
killall [nama-proses]
```

Contoh percobaan:<br>
<img src="assets/ka1.png" alt="ss" width="600"/>

<img src="assets/ka2.png" alt="ss" width="600"/>
<br><br>

- Perintah `pkill`
  Perintah ini seperti killall tetapi memiliki lebih banyak opsi, seperti menghentikan proses berdasarkan pengguna (contoh: pkill -u ale menghentikan semua proses milik pengguna ale).<br>
  syntax perintah `pkill`:

```bash
pkill [opsi] <pola>
```

Contoh percobaan:<br>
<img src="assets/pk1.png" alt="ss" width="600"/>

<img src="assets/pk2.png" alt="ss" width="600"/>

### ps: Pemantauan proses

Perintah `ps` adalah alats utama milik system administrator untuk memantau proses. Perintah ini dapat menunjukkan PID, UID, prioritas, dan terminal kontrol dari proses. `ps` juga memberi informasi seberapa banyak pemakaian memori dari proses, seberapa banyak waktu CPU telah dipakai, dan kondisi proses-proses sekarang.<br>
syntax perintah `ps`:

```bash
ps [opsi]
```

Contoh percobaan:<br>
<img src="assets/ps1.png" alt="ss" width="600"/>

### top: Pemantauan secara interaktif

Perintah top digunakan untuk memantau sistem secara real-time dengan tampilan yang dinamis. Ini menampilkan informasi ringkasan sistem serta daftar proses atau thread yang sedang dikelola oleh kernel Linux. Informasi yang ditampilkan, seperti jenis, urutan, dan ukuran data untuk proses, dapat dikonfigurasi oleh pengguna dan disimpan agar tetap berlaku bahkan setelah sistem di-restart. Secara default, tampilan top diperbarui setiap 1-2 detik, tergantung pada sistem.

syntax perintah `top`:

```bash
ps
```

Contoh percobaan:<br>
<img src="assets/top1.png" alt="ss" width="600"/>

Selain top, ada juga perintah htop, yang merupakan pemantau proses interaktif untuk sistem Unix. htop adalah aplikasi berbasis teks (untuk konsol atau terminal X) dan memerlukan library ncurses. Perintah ini mirip dengan top, tetapi memungkinkan pengguna untuk menggulir layar secara vertikal dan horizontal, sehingga semua proses yang berjalan di sistem beserta perintah lengkapnya dapat dilihat. htop juga memiliki antarmuka pengguna yang lebih baik dan lebih banyak opsi untuk operasi tertentu.

syntax perintah `htop`:

```bash
htop
```

Contoh percobaan:<br>
<img src="assets/htop1.png" alt="ss" width="600"/>

### nice dan renice: Merubah prioritas proses

Niceness adalah nilai numerik yang memberikan petunjuk kepada kernel tentang bagaimana suatu proses harus diperlakukan dalam hubungannya dengan proses lain yang bersaing untuk mendapatkan CPU. Proses dengan prioritas rendah adalah proses yang tidak terlalu penting dan akan mendapatkan waktu CPU lebih sedikit. Proses dengan prioritas tinggi adalah proses yang penting dan akan mendapatkan waktu CPU lebih banyak.

Niceness tinggi berarti prioritas rendah untuk proses Anda: Anda "bersikap baik" dengan memberikan prioritas kepada proses lain. Sedangakn Niceness rendah atau negatif berarti prioritas tinggi: Anda "tidak terlalu bersikap baik" karena proses Anda akan diutamakan. Rentang nilai niceness bervariasi tergantung sistem. Di Linux, rentangnya adalah -20 hingga +19, sedangkan di FreeBSD rentangnya adalah -20 hingga +20.

- nice:<br>
  Digunakan untuk memulai proses dengan nilai niceness tertentu.<br>
  syntax perintah `nice`:

```bash
nice -n nice_val [perintah]
```

Contoh percobaan:<br>
<img src="assets/n1.png" alt="ss" width="600"/>

<img src="assets/n2.png" alt="ss" width="600"/>

<img src="assets/n3.png" alt="ss" width="600"/>

- renice: <br>
  Digunakan untuk mengubah nilai niceness dari proses yang sedang berjalan.<br>
  syntax perintah `renice`:

```bash
renice -n nice_val -p pid
```

Contoh percobaan:<br>
<img src="assets/rn1.png" alt="ss" width="600"/>

<img src="assets/rn2.png" alt="ss" width="600"/>

<img src="assets/rn3.png" alt="ss" width="600"/>

### /proc filesystem

Direktori /proc adalah sistem file semu (pseudo-filesystem) yang digunakan oleh kernel Linux untuk mengekspos berbagai informasi tentang status sistem, termasuk informasi tentang proses yang sedang berjalan. Meskipun namanya adalah /proc, direktori ini tidak hanya berisi informasi tentang proses, tetapi juga statistik sistem dan data lainnya.

Contoh percobaan:<br>
<img src="assets/p1.png" alt="ss" width="600"/>

<img src="assets/p2.png" alt="ss" width="600"/>

### strace dan truss

Perintah strace (Linux) dan truss (FreeBSD) digunakan untuk melacak system calls (panggilan sistem) dan signals (sinyal) yang dilakukan oleh suatu proses. Alat ini berguna untuk melakukan debugging program atau memahami apa yang sedang dilakukan oleh suatu program.<br>
syntax perintah `strace`:

```bash
strace -p pid
```

Contoh percobaan:<br>
<img src="assets/st1.png" alt="ss" width="600"/>

<img src="assets/st2.png" alt="ss" width="600"/>

### Runaway Process

Runaway Process adalah proses yang berhenti merespons sistem dan berjalan di luar kendali. Proses ini mengabaikan prioritas penjadwalannya dan terus menggunakan 100% CPU, menyebabkan mesin menjadi sangat lambat karena proses lain hanya mendapatkan akses terbatas ke CPU.

Untuk menghentikan runaway proses menggunakan perintah `kill`.

Untuk menyelidiki runaway process menggunakan perintah `strace` (Linux) atau `truss` (FreeBSD).

Untuk memeriksa penggunaan filesystem menggunakan perintah `df`.

```bash
df -h
```

Contoh percobaan:<br>
<img src="assets/df1.png" alt="ss" width="600"/>

Untuk melihat proses yang dibuka oleh runaway process menggunakan perintah `lsof`.

```bash
lsof -p pid
```

Contoh percobaan:<br>
<img src="assets/lsof1.png" alt="ss" width="600"/>

### Proses Periodik

Proses periodik adalah tugas yang dijalankan secara terjadwal pada waktu tertentu. Di Linux, alat utama untuk menjalankan perintah terjadwal adalah cron (atau crond di RedHat). Selain itu, systemd timer dapat digunakan sebagai alternatif yang lebih fleksibel dan powerful.

- Cron: Menjadwalkan Perintah<br>
  Cron adalah daemon yang berjalan saat sistem boot dan tetap aktif selama sistem menyala serta membaca file konfigurasi yang disebut crontab (cron table) yang berisi daftar perintah dan jadwal eksekusinya. Perintah dalam crontab dijalankan oleh shell (sh), sehingga hampir semua perintah yang dapat dijalankan manual dari shell juga dapat dijadwalkan dengan cron.<br>
  Format crontab:<br>

```bash
*     *     *     *     *  command_to_execute
-     -     -     -     -
|     |     |     |     |
|     |     |     |     +----- hari dalam minggu (0-6, 0=Minggu)
|     |     |     +------- bulan (1-12)
|     |     +--------- tanggal (1-31)
|     +----------- jam (0-23)
+------------- menit (0-59)
```

Contoh penggunaan crontab<br>
Menjalankan perintah setiap hari pukul 2:30 pagi:

```bash
30 2 * * * command
```

Menjalankan skrip Python setiap tanggal 1 pukul 2:30 pagi:

```bash
30 2 1 * * /usr/bin/python3 /path/to/script.py
```

Menjalankan perintah setiap 30 menit:

```bash
*/30 * * * * command
```

- Systemd Timer: Alternatif Modern untuk Cron<br>
  Systemd timer adalah file konfigurasi unit systemd yang berekstensi `.timer`. Timer ini lebih fleksibel dan powerful dibanding cron, karena dapat diaktifkan berdasarkan waktu, boot sistem, atau event tertentu diaktifkan oleh service unit yang sesuai, dan dapat dikelola menggunakan perintah `systemctl`.<br>
  Contoh Systemd Timer:<br>

```bash
systemctl list-timers
```

Contoh file timer (logrotate.timer):<br>

```bash
[Unit]
Description=Daily rotation of log files

[Timer]
OnCalendar=daily
AccuracySec=1h
Persistent=true

[Install]
WantedBy=timers.target
```

- Kegunaan Umum Tugas Terjadwal:<br>
  - Mengirim Email: Mengirim laporan atau hasil perintah secara otomatis melalui email.<br>
  - Membersihkan Filesystem: Menjalankan skrip untuk menghapus file lama, seperti membersihkan direktori sampah setiap hari.<br>
  - Rotasi Log File: Membagi file log menjadi beberapa segmen berdasarkan ukuran atau tanggal, dan menyimpan versi lama.<br>
  - Menjalankan Batch Jobs: Menjalankan tugas panjang seperti pemrosesan pesan antrian atau ETL (Extract, Transform, Load) ke data warehouse.<br>
  - Backup dan Mirroring: Menjadwalkan backup otomatis ke sistem remote atau membuat mirror (salinan byte-per-byte) menggunakan rsync.<br>
