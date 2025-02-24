<a name="_hlk175774388"></a>**Laporan Workshop Administrasi Jaringan**

![](https://github.com/FikriEffendi/AdminJaringan2025/blob/main/Week-1/images/gambar001.png?raw=true)

**Dr Ferry Astika Saputra ST, M.Sc**

Nama: Fikri Athanabil Effendi

Kelas: 2 D3 IT A NRP: 3123500012

1. Analisa file http.cap dengan wireshark : Versi HTTP yang digunakan, IP address dari client maupun server, waktu dari client mengirimkan HTTP request., Waktu dari server mengirinmkan server dan berapa durasinya

- ` `**Jawab:**
- ` `Versi HTTP yang digunakan

`	`![](https://github.com/FikriEffendi/AdminJaringan2025/blob/main/Week-1/images/gambar002.png?raw=true)

Pada gambar yang saya lampirkna menggunakan HTTP versi 1.1

- ` `IP address dari client maupun server

  ![](https://github.com/FikriEffendi/AdminJaringan2025/blob/main/Week-1/images/gambar003.png?raw=true)

  Pada gambar yang saya lampirkan IP address dari client adalah 145.254.160.237 dan IP address dari sever 65.208.228.223

- ` `waktu dari client mengirimkan HTTP request

  Berdasarkan gambar didapat hasil 0.911310

- ` `waktu dari client mengirimkan HTTP request

  3\.955688

- ` `Berapa durasinya

  3\.044378

1. Deskripsi gambar pada slide

   ![](https://github.com/FikriEffendi/AdminJaringan2025/blob/main/Week-1/images/gambar004.png?raw=true)

- Node to node:

menggambarkan komunikasi antar perangkat jaringan langsung, seperti antara komputer dan router, atau antara dua router. Beroperasi pada **lapisan data link** dari model OSI.

- Host to host

komunikasi antara dua host (komputer) melalui beberapa perangkat jaringan (router). Beroperasi pada **lapisan jaringan** dari model OSI.

- Process to process

  komunikasi antara aplikasi yang berjalan di komputer sumber dan tujuan. Beroperasi pada **lapisan transport** dari model OSI.

1. Rangkuman tahapan komunikasi menggunakan TCP

   ![](https://github.com/FikriEffendi/AdminJaringan2025/blob/main/Week-1/images/gambar005.png?raw=true)

   Gambar ini menunjukkan proses pembentukan koneksi menggunakan mekanisme three-way handshake dalam protokol TCP. Proses dimulai ketika client mengirim pesan SYN ke server dengan sequence number 8000 sebagai permintaan untuk memulai koneksi. Server kemudian merespons dengan mengirim pesan SYN-ACK, di mana ia menetapkan sequence number 15000 dan mengakui pesan dari client dengan acknowledgment number 8001. Setelah menerima respons dari server, client mengirim pesan ACK dengan acknowledgment number 15001 untuk mengonfirmasi bahwa koneksi telah berhasil dibangun. Setelah langkah ini selesai, kedua belah pihak dapat mulai bertukar data melalui koneksi yang telah terjalin.

   ![](https://github.com/FikriEffendi/AdminJaringan2025/blob/main/Week-1/images/gambar006.png?raw=true)

   Gambar ini menggambarkan proses transfer data dalam protokol TCP setelah koneksi berhasil dibentuk. Client mulai mengirimkan data ke server dengan menggunakan sequence number 8001 dan acknowledgment number 15001. Setiap segmen data yang dikirim mencakup flag ACK dan PSH, menunjukkan bahwa data harus segera diteruskan ke aplikasi penerima tanpa menunggu buffer penuh. Setelah mengirim data pertama dari byte 8001 hingga 9000, client melanjutkan dengan mengirim data berikutnya dari byte 9001 hingga 10000. Server kemudian merespons dengan mengirim data balik ke client menggunakan sequence number 15001 dan acknowledgment number 10001, yang menandakan bahwa server telah menerima data sebelumnya dan kini mengirimkan data dari byte 15001 hingga 17000. Client kemudian mengirimkan acknowledgment terakhir dengan acknowledgment number 17001, bersama dengan window size (rwnd) yang menunjukkan kapasitas buffer yang tersedia untuk menerima data lebih lanjut.

![](https://github.com/FikriEffendi/AdminJaringan2025/blob/main/Week-1/images/gambar007.png?raw=true)

`	`Gambar ini menunjukkan proses terminasi koneksi dalam protokol TCP menggunakan mekanisme three-way handshake. Proses dimulai ketika client mengirimkan segmen dengan flag FIN dan ACK untuk mengindikasikan bahwa client ingin menutup koneksi. Server menerima permintaan ini dan merespons dengan segmen yang memiliki flag FIN dan ACK, menandakan bahwa server juga siap untuk mengakhiri komunikasi. Setelah menerima segmen tersebut, client mengirimkan segmen terakhir yang hanya berisi flag ACK untuk mengonfirmasi bahwa koneksi telah berhasil ditutup di kedua sisi. Setelah ini, koneksi diakhiri sepenuhnya, dan baik client maupun server tidak akan lagi mengirim atau menerima data dalam sesi tersebut.
