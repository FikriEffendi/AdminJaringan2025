<div align="center">
  <h1 style="text-align: center;font-weight: bold">Laporan Praktikum
  <br>Workshop Administrasi Jaringan</h1>
  <h4 style="text-align: center;">Dosen Pengampu : Dr. Ferry Astika Saputra, S.T., M.Sc.</h4>
</div>
<br />
<div align="center">
  <img src="https://upload.wikimedia.org/wikipedia/id/4/44/Logo_PENS.png" alt="Logo PENS">
  <h3 style="text-align: center;">Disusun Oleh : </h3>
  <p style="text-align: center;">
    <strong>Nama: Fikri Athanabil Effendi</strong><br>
    <strong>NRP: 3123500012 </strong><br>
    <strong>Kelas: D3 IT A</strong>
  </p>
<h3 style="text-align: center;line-height: 1.5">Politeknik Elektronika Negeri Surabaya<br>Departemen Teknik Informatika Dan Komputer<br>Program Studi Teknik Informatika<br>2023/2024</h3>
  <hr><hr>
</div>

# Rangkuman Electronic Mail

https://www.geeksforgeeks.org/introduction-to-electronic-mail/

## Rangkuman

Surel, atau surat elektronik, adalah metode utama untuk bertukar pesan melalui internet. Layanan ini memungkinkan pengguna internet mengirim pesan dalam bentuk surat (mail) dengan format tertentu, termasuk teks, gambar, audio, dan video, kepada pengguna lain di seluruh dunia. Sistem surel melibatkan komponen penting seperti Agen Pengguna (UA), Agen Transfer Pesan (MTA), Kotak Surat (Mailbox), dan Spool file, yang semuanya bekerja sama untuk memfasilitasi pengiriman dan penerimaan pesan. Meskipun surel menawarkan keuntungan signifikan seperti kecepatan, efektivitas biaya, dan kemampuan untuk mengirim lampiran, surel juga memiliki kelemahan, termasuk risiko spam, serangan _phishing_, kelebihan informasi, dan potensi miskomunikasi.

## Poin-Poin Utama

- Basics of email:
  - Alamat email: Ini adalah pengidentifikasi unik untuk setiap pengguna, biasanya dalam format name@domain.com.
  - Klien email: Ini adalah program perangkat lunak yang digunakan untuk mengirim, menerima, dan mengelola email, seperti Gmail, Outlook, atau Apple Mail.
  - Server email: Ini adalah sistem komputer yang bertanggung jawab untuk menyimpan dan meneruskan email ke penerima yang dituju.
- Surel (email) adalah metode pertukaran pesan melalui internet yang memungkinkan pengiriman berbagai jenis data.
- Surel (email) memiliki pengirim dan penerima, mirip dengan layanan pos tradisional.
- Komponen dasar sistem surel meliputi Agen Pengguna (UA) untuk mengirim dan menerima, Agen Transfer Pesan (MTA) untuk mentransfer, Mail Box untuk menyimpan pesan, dan Spool file untuk mengelola pesan keluar. Berikut adalah rangkuman poin-poin penting mengenai komponen dalam sistem email:
  - **User Agent (UA):** Aplikasi yang digunakan pengguna untuk membuat, mengirim, menerima, membalas email, serta mengelola kotak surat (mailbox). Sering disebut "mail reader".
  - **Message Transfer Agent (MTA):** Bertanggung jawab mentransfer email antar sistem. Membutuhkan MTA klien dan server. Menggunakan **Simple Mail Transfer Protocol (SMTP)** untuk pengiriman antar MTA.
    ![email](images/email.png)
  - **Mailbox:** File di hard drive lokal tempat email yang diterima disimpan. Hanya pemilik mailbox yang dapat mengaksesnya. Pemilik bisa membacanya atau menghapusnya sesuai keinginannya.
  - **Spool file:** File yang berisi email yang akan dikirim. UA menambahkan email keluar ke file ini, dan MTA mengambilnya untuk dikirim.
  - **Mailing list (Alias):** Satu nama yang mewakili beberapa alamat email. Ketika email dikirim ke alias, sistem akan membuat dan mengirim email terpisah untuk setiap alamat dalam daftar. Jika alias tidak terdaftar, email dikirim ke alamat tersebut.
- Proses pengiriman surel melibatkan penulisan pesan, memasukkan alamat penerima, subjek, isi, lampirkan file yang diperlukan jika ada dan mengirimkannya melalui peladen surel.
- Surel (email) dapat menggunakan fitur CC (carbon copy) dan BCC (blind carbon copy) untuk mengirim salinan pesan kepada beberapa penerima, serta opsi reply, reply all, dan forward email untuk mengelola percakapan.
- Surel (email) menyediakan layanan seperti komposisi (menulis pesan dan jawaban), transfer (mengirim), pelaporan (konfirmasi pengiriman), menampilkan (menyajikan pesan), dan disposisi (tindakan penerima terhadap pesan).
  - **Komposisi** : Proses untuk membuat pesan dan jawaban.
  - **Transfer** : prosedur pengiriman mail dari pengirim ke penerima.
  - **Pelaporan (Reporting)** : Konfirmasi untuk pengiriman surat, membantu pengguna memeriksa apakah email mereka sudah terkirim, hilang atau ditolak.
  - **Disposisi (Disposition)** : Hal ini berhubungan dengan apa yang akan dilakukan oleh penerima setelah menerima email, yaitu menyimpan email, menghapus sebelum atau sesudah membaca.
- Daftar surel, atau alias, memungkinkan satu nama mewakili beberapa alamat surel, memfasilitasi pengiriman pesan ke banyak penerima sekaligus.
- Keuntungan surel meliputi komunikasi yang cepat dan nyaman, kemampuan penyimpanan dan pencarian pesan yang mudah, pengiriman lampiran, efektivitas biaya, dan ketersediaan 24/7.
- Kelemahan surel mencakup risiko spam dan serangan _phishing_, kelebihan informasi, kurangnya komunikasi tatap muka, potensi miskomunikasi, dan masalah teknis.

# Laporan Mail Server

## Persiapan Instalasi Mail Server

Mail server adalah sistem yang menangani pengiriman dan penerimaan email. Dalam praktikum ini, kita akan menggunakan Postfix sebagai MTA (Mail Transfer Agent) dan Dovecot sebagai server POP3/IMAP untuk mengakses email.

### Langkah-langkah Instalasi

1. Instalasi Postfix dan SASL Authentication:

   ```bash
   apt -y install postfix sasl2-bin
   ```

   ![Instalasi Postfix](images/gambar_jaringan_2025/WhatsApp%20Image%202025-05-08%20at%2015.08.52.jpeg)

2. Saat instalasi, pilih konfigurasi "Internet Site":
   ![Konfigurasi Postfix](<images/gambar_jaringan_2025/WhatsApp%20Image%202025-05-08%20at%2015.08.52(1).jpeg>)

3. Masukkan nama domain untuk mail server:
   ![Domain Mail Server](images/gambar_jaringan_2025/WhatsApp%20Image%202025-05-08%20at%2015.08.53.jpeg)

## Konfigurasi Postfix

Postfix adalah Mail Transfer Agent (MTA) yang bertugas mengirim dan menerima email. Berikut langkah-langkah konfigurasi Postfix:

1. Edit file konfigurasi Postfix:

   ```bash
   nano /etc/postfix/main.cf
   ```

2. Konfigurasi parameter dasar Postfix seperti yang terlihat pada gambar berikut:
   ![Konfigurasi Postfix](<images/gambar_jaringan_2025/WhatsApp%20Image%202025-05-08%20at%2015.08.53(1).jpeg>)

   Pada gambar di atas, kita melakukan konfigurasi parameter dasar seperti:

   - myhostname = mail.example.com
   - mydomain = example.com
   - myorigin = $mydomain
   - inet_interfaces = all

3. Lanjutkan konfigurasi jaringan dan alias seperti yang terlihat pada gambar berikut:
   ![Konfigurasi Jaringan](<images/gambar_jaringan_2025/WhatsApp%20Image%202025-05-08%20at%2015.08.53(2).jpeg>)

   Pada gambar di atas, kita mengkonfigurasi:

   - mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
   - mynetworks_style = subnet
   - mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
   - home_mailbox = Maildir/

4. Tambahkan konfigurasi SMTP Authentication seperti yang terlihat pada gambar berikut:
   ![SMTP Auth](images/gambar_jaringan_2025/WhatsApp%20Image%202025-05-08%20at%2015.08.54.jpeg)

   Pada gambar di atas, kita menambahkan konfigurasi:

   ```
   # SMTP Auth Settings
   smtpd_sasl_type = dovecot
   smtpd_sasl_path = private/auth
   smtpd_sasl_auth_enable = yes
   smtpd_sasl_security_options = noanonymous
   smtpd_sasl_local_domain = $myhostname
   smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
   ```

5. Tambahkan pengaturan keamanan tambahan untuk mencegah spam seperti yang terlihat pada gambar berikut:
   ![Anti-Spam Settings](<images/gambar_jaringan_2025/WhatsApp%20Image%202025-05-08%20at%2015.08.54(1).jpeg>)

   Pada gambar di atas, kita menambahkan konfigurasi:

   ```
   # Anti-Spam Settings
   disable_vrfy_command = yes
   smtpd_helo_required = yes
   message_size_limit = 10485760
   ```

6. Terapkan perubahan dan restart Postfix:
   ![Restart Postfix](<images/gambar_jaringan_2025/WhatsApp%20Image%202025-05-08%20at%2015.08.54(2).jpeg>)

   Pada gambar di atas, kita menjalankan perintah:

   ```bash
   newaliases
   systemctl restart postfix
   ```

## Konfigurasi Dovecot

Dovecot adalah server POP3/IMAP yang memungkinkan pengguna mengakses email mereka. Berikut langkah-langkah konfigurasi Dovecot:

1. Instalasi Dovecot:

   ```bash
   apt -y install dovecot-core dovecot-pop3d dovecot-imapd
   ```

   ![Instalasi Dovecot](images/gambar_jaringan_2025/WhatsApp%20Image%202025-05-08%20at%2015.08.55.jpeg)

2. Edit file konfigurasi Dovecot:

   ```bash
   nano /etc/dovecot/dovecot.conf
   ```

   ![Konfigurasi Dovecot](<images/gambar_jaringan_2025/WhatsApp%20Image%202025-05-08%20at%2015.08.55(1).jpeg>)

   Pada gambar di atas, kita mengubah konfigurasi untuk mendengarkan pada semua antarmuka dengan uncomment baris:

   ```
   listen = *, ::
   ```

3. Konfigurasi autentikasi Dovecot:

   ```bash
   nano /etc/dovecot/conf.d/10-auth.conf
   ```

   ![Auth Dovecot](<images/gambar_jaringan_2025/WhatsApp%20Image%202025-05-08%20at%2015.08.55(2).jpeg>)

   Pada gambar di atas, kita mengubah konfigurasi:

   - disable_plaintext_auth = no
   - auth_mechanisms = plain login

4. Konfigurasi lokasi mailbox:

   ```bash
   nano /etc/dovecot/conf.d/10-mail.conf
   ```

   ![Mail Location](<images/gambar_jaringan_2025/WhatsApp%20Image%202025-05-08%20at%2015.08.55(3).jpeg>)

   Pada gambar di atas, kita mengubah konfigurasi:

   ```
   mail_location = maildir:~/Maildir
   ```

5. Konfigurasi socket untuk integrasi dengan Postfix:

   ```bash
   nano /etc/dovecot/conf.d/10-master.conf
   ```

   ![Socket Configuration](images/gambar_jaringan_2025/WhatsApp%20Image%202025-05-08%20at%2015.08.56.jpeg)

   Pada gambar di atas, kita menambahkan konfigurasi di bagian service auth:

   ```
   unix_listener /var/spool/postfix/private/auth {
     mode = 0666
     user = postfix
     group = postfix
   }
   ```

6. Restart Dovecot untuk menerapkan perubahan:
   ```bash
   systemctl restart dovecot
   ```

## Menambahkan Akun Email

1. Instalasi Mailutils untuk utilitas email:

   ```bash
   apt -y install mailutils
   ```

   ![Instalasi Mailutils](images/gambar_jaringan_2025/WhatsApp%20Image%202025-05-08%20at%2015.40.40.jpeg)

2. Tambahkan pengguna baru untuk email:

   ```bash
   useradd -m -s /bin/bash username
   passwd username
   ```

3. Atur environment variables untuk menggunakan Maildir:
   ```bash
   echo 'export MAIL=$HOME/Maildir' >> /etc/profile
   source /etc/profile
   ```

## Pengujian Mail Server

1. Login sebagai pengguna yang telah dibuat:

   ```bash
   su - username
   ```

2. Kirim email ke pengguna lain di server yang sama:

   ```bash
   echo "Ini adalah pesan uji coba" | mail -s "Subjek Email" penerima@domain
   ```

3. Periksa email yang diterima:

   ```bash
   mail
   ```

4. Untuk melihat isi email, masukkan nomor email yang ingin dibaca.

5. Verifikasi bahwa email telah terkirim dan diterima dengan benar.

Dengan mengikuti langkah-langkah di atas, mail server dengan Postfix dan Dovecot telah berhasil dikonfigurasi dan siap digunakan untuk mengirim dan menerima email.
