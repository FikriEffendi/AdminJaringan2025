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

1. **Instalasi NTP Client**
1. Buka terminal dan jalankan ‘sudo apt update’ untuk memperbarui daftar paket yang tersedia dan versinya dalam sistem Linux/Debian

   <img src="images/gambar1.jpeg" alt="ss" width="600"/>

1. Jalankan perintah ‘sudo apt -y install ntpsec’ untuk Memasang (install) paket ntpsec, yang berfungsi sebagai Network Time Protocol (NTP) client untuk sinkronisasi waktu.

   <img src="images/gambar2.jpeg" alt="ss" width="600"/>

1. Edit file konfigurasi **ntpsec** di ‘sudo nano /etc/ntpsec/ntp.conf’

   <img src="images/gambar3.png" alt="ss" width="600"/>

1. Cari baris berikut:

   ` `Command baris tersebut dan tambahkan server 0.id.pool.ntp.org iburst

   server 1.id.pool.ntp.org iburst

   server 2.id.pool.ntp.org iburst

   server 3.id.pool.ntp.org iburst

   <img src="images/gambar4.jpeg" alt="ss" width="600"/>

1. Setelah itu Restart NTP Service

   <img src="images/gambar5.png" alt="ss" width="600"/>

1. Cek status apakah service sudah aktif:

   <img src="images/gambar6.jpeg" alt="ss" width="600"/>

1. Gunakan perintah berikut untuk memverifikasi server NTP yang digunakan:

   <img src="images/gambar7.png" alt="ss" width="600"/>

1. **Instalasi Samba**
1. Buka terminal dan jalankan ‘sudo apt update’ untuk memperbarui daftar paket yang tersedia dan versinya dalam sistem Linux/Debian

   <img src="images/gambar8.jpeg" alt="ss" width="600"/>

1. Jalankan perintah ‘sudo apt -y install samba smbclient cifs-utils’ untuk **menginstal paket-paket yang dibutuhkan** dalam konfigurasi Samba di Debian 12.\*\*

   <img src="images/gambar9.jpeg" alt="ss" width="600"/>

1. Jalankan perintah [‘mkdir ](https://www.server-world.info/en/command/html/mkdir.html)/home/share’ untuk membuat folder ‘/home/share’

   <img src="images/gambar10.png" alt="ss" width="600"/>

1. Jalankan perintah [‘chmod ](https://www.server-world.info/en/command/html/chmod.html)777 /home/share’ untuk **mengubah izin akses (permission) pada folder /home/share** agar bisa dibaca, ditulis, dan dieksekusi oleh semua user.

   <img src="images/gambar11.png" alt="ss" width="600"/>

1. Jalankan perintah ‘sudo nano /etc/samba/smb.conf’ untuk mengedit file pada /etc/samba/smb.conf

   <img src="images/gambar12.png" alt="ss" width="600"/>

1. Edit file pada bagian seperti pada gambar yang saya lampirkan

   <img src="images/gambar13.jpeg" alt="ss" width="600"/>

   <img src="images/gambar14.jpeg" alt="ss" width="600"/>

3\. Debian 12 sysadmin

- Memodifikasi repositori

`       `Untuk memodifikasi software recource jalankan perintah ‘apt edit-sources’

   <img src="images/gambar15.png" alt="ss" width="600"/>

`       `Perintah tersebut untuk membuka file di text editor(nano atau vim)jika sudah selesai mengedit save file dengan menggunakan [ctrl+x]

Contoh:

   <img src="images/gambar16.png" alt="ss" width="600"/>

- Command untuk mencari dan menampilkan informasi

   <img src="images/gambar17.png" alt="ss" width="600"/>

- Perintah untuk Mode administrasi untuk maintenance system

   <img src="images/gambar18.png" alt="ss" width="600"/>

   <img src="images/gambar19.jpeg" alt="ss" width="600"/>

- Command untuk update info repo + update system + membersihkan cache packages

   <img src="images/gambar20.png" alt="ss" width="600"/>

- Untuk menghapus packages yang tidak terpakai, dependensi yang tidak penting dan file konfigurasi versi lama di mode admin

   <img src="images/gambar21.png" alt="ss" width="600"/>

1. **Software: The Simplified Package Manager**

Bagian ini menjelaskan sistem manajemen paket di Debian 12, yang bertujuan untuk mempermudah instalasi, pembaruan, dan penghapusan perangkat lunak.

1. **APT (Advanced Package Tool)**

APT adalah sistem manajemen paket utama di Debian. Beberapa perintah penting yang dibahas dalam bagian ini:

- apt update → Memperbarui daftar paket dari repository.
- apt upgrade → Memperbarui semua paket ke versi terbaru.
- apt install <package_name> → Menginstal paket tertentu.
- apt remove <package_name> → Menghapus paket.
- apt autoremove → Menghapus paket yang tidak lagi diperlukan.

APT menangani dependensi secara otomatis, memastikan bahwa semua pustaka yang dibutuhkan diinstal bersama aplikasi utama.

2. **dpkg (Debian Package Manager)**

Selain APT, Debian juga memiliki _dpkg_, alat manajemen paket tingkat rendah yang bekerja dengan file .deb. Beberapa perintah dasar:

- dpkg -i <file.deb> → Menginstal paket dari file .deb.
- dpkg -r <package_name> → Menghapus paket.
- dpkg -l → Menampilkan daftar paket yang terinstal. ![](Aspose.Words.0ad25a3a-87dd-405e-ac33-e7d3fcd97ad1.023.png)

2. **System Services Management (Manajemen Layanan Sistem)**

Bagian ini membahas cara mengelola layanan menggunakan _systemd_, sistem inisialisasi modern yang menggantikan _SysVinit_.

1. **Perintah systemctl untuk Mengelola Layanan**

- systemctl start <service> → Menjalankan layanan.
- systemctl stop <service> → Menghentikan layanan.
- systemctl restart <service> → Memulai ulang layanan.
- systemctl enable <service> → Mengaktifkan layanan agar berjalan otomatis saat boot.
- systemctl disable <service> → Menonaktifkan layanan dari startup.

2. **Melihat Status Layanan**

Untuk memeriksa status layanan, gunakan:

systemctl status <service>

Contoh:

systemctl status apache2

Perintah ini akan menampilkan informasi apakah layanan _Apache_ sedang berjalan atau tidak. ![](Aspose.Words.0ad25a3a-87dd-405e-ac33-e7d3fcd97ad1.024.png)

3. **User and Permission Management (Manajemen Pengguna dan Izin)**

Bagian ini membahas cara mengelola pengguna, grup, dan izin file dalam sistem Debian 12.

1. **Manajemen Pengguna**

- adduser <username> → Menambahkan pengguna baru.
- deluser <username> → Menghapus pengguna.
- usermod -aG <group> <username> → Menambahkan pengguna ke grup.

2. **Manajemen Izin File**

Debian menggunakan model izin Unix dengan tiga tingkat:

- **Owner (Pemilik)**
- **Group (Grup)**
- **Others (Lainnya)**

Gunakan perintah berikut untuk mengatur izin:

- chmod → Mengubah izin file.
- chown → Mengubah pemilik file.
- ls -l → Menampilkan daftar file dengan izin yang dimiliki. Contoh:

chmod 755 script.sh

chown user:user script.sh ![](Aspose.Words.0ad25a3a-87dd-405e-ac33-e7d3fcd97ad1.025.png)

4. **Networking Basics (Dasar-dasar Jaringan)**

Bagian ini mencakup pengaturan jaringan di Debian 12.

1. **Konfigurasi IP dan Hostname**

- ip a → Menampilkan konfigurasi IP.
- hostnamectl set-hostname <new_hostname> → Mengubah nama host.

2. **Pengelolaan Firewall dengan UFW (Uncomplicated Firewall)**

- ufw enable → Mengaktifkan firewall.
- ufw allow <port> → Mengizinkan lalu lintas ke port tertentu.
- ufw status → Memeriksa status firewall. ![](Aspose.Words.0ad25a3a-87dd-405e-ac33-e7d3fcd97ad1.026.png)

5. **System Monitoring and Logs (Pemantauan Sistem dan Log)** Bagian ini membahas alat pemantauan sistem seperti:

- top / htop → Menampilkan proses yang berjalan.
- df -h → Memeriksa penggunaan disk.
- free -m → Melihat penggunaan RAM.
- journalctl → Melihat log systemd.
