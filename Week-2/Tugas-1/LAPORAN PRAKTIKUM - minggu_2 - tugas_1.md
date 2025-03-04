<a name="_hlk175774388"></a>**Laporan Workshop Administrasi Jaringan**

![](https://github.com/FikriEffendi/AdminJaringan2025/blob/main/Week-2/Tugas-1/images/gambar_1.png?raw=true)

**Dr Ferry Astika Saputra ST, M.Sc**

Nama: Fikri Athanabil Effendi

Kelas: 2 D3 IT A NRP: 3123500012

- **Instalasi Virtual Box Menggunakan Lab Komputer**

1. Jalankan Virtual Box

   ![](https://github.com/FikriEffendi/AdminJaringan2025/blob/main/Week-2/Tugas-1/images/gambar_2.png?raw=true)

1. Buka Firefox Lalu buka laman ‘https://www.virtualbox.org/wiki/Downloads’ untuk mendownload Virtual Box!
   ![](https://github.com/FikriEffendi/AdminJaringan2025/blob/main/Week-2/Tugas-1/images/gambar_3.png?raw=true)

1. Jika selesai mengunduh Virtual Box buka folder unduhan
   ![](https://github.com/FikriEffendi/AdminJaringan2025/blob/main/Week-2/Tugas-1/images/gambar_4.png?raw=true)

1. Setelah masuk ke direktori unduhan jalankan perintah

   ‘sudo dpkg -I <nama_filenya>’ dalam perintah sebelumnya ganti ‘nama_filenya’ dengan nama file dari unduhan virtualbox
   ![](https://github.com/FikriEffendi/AdminJaringan2025/blob/main/Week-2/Tugas-1/images/gambar_5.png?raw=true)

1. Setelah berhasil buka laman ‘https://www.debian.org/download’ dan klik ‘[debian-12.9.0-amd64-netinst.iso](https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-12.9.0-amd64-netinst.iso)’ untuk mendownload Debian
   ![](https://github.com/FikriEffendi/AdminJaringan2025/blob/main/Week-2/Tugas-1/images/gambar_6.png?raw=true)

1. Sembari medownload buka virtual box.Pada saat pertama kali membuka virtual box akan terdapat error ‘tidak bisa mengenumerasi perangkat USB’
   ![](https://github.com/FikriEffendi/AdminJaringan2025/blob/main/Week-2/Tugas-1/images/gambar_7.png?raw=true)

1. Jalankan perintah ‘sudo usermod -a -G vboxusers $USER’ lalu restart Debian anda
   ![](https://github.com/FikriEffendi/AdminJaringan2025/blob/main/Week-2/Tugas-1/images/gambar_8.png?raw=true)

1. Lalu jalankan perintah ‘sudo /sbin/vboxconfig’
   ![](https://github.com/FikriEffendi/AdminJaringan2025/blob/main/Week-2/Tugas-1/images/gambar_9.png?raw=true)

1. Setelah berhasil buka virtual box lagi dan konfigurasi debiannya.Referensi: ‘https://github.com/FikriEffendi/SysOp-3123500012/tree/main/week1/tugas_1’

   ![](https://github.com/FikriEffendi/AdminJaringan2025/blob/main/Week-2/Tugas-1/images/gambar_10.jpeg?raw=true)

- Kesimpulan

  Dapat disimpulkan bahwa instalasi VirtualBox pada Linux menggunakan Bash Shell memiliki perbedaan dibandingkan instalasi pada Windows. Perbedaan tersebut disebabkan oleh adanya beberapa kendala yang dialami pengguna, sehingga diperlukan langkah-langkah tambahan untuk memperbaiki masalah yang muncul selama proses instalasi.
