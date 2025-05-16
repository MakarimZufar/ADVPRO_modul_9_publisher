# Refleksi

<h3> Nama: Makarim Zufar Prambudyo</h3>

<h3> NPM: 2306241751 </h3>

<h3> Kelas: Advprog-B </h3>

---

### a. How much data your publisher program will send to the message broker in one
run?

Jumlah data yang dikirim program publisher ke message broker dalam satu kali proses sangat bergantung pada implementasi spesifik program tersebut. Tidak ada ukuran tetap karena:

Publisher dapat mengirim satu pesan tunggal atau ribuan pesan
Ukuran setiap pesan bisa bervariasi (dari beberapa byte hingga megabyte)
Implementasi publisher mungkin memiliki batasan atau konfigurasi khusus

Jumlah data ini biasanya ditentukan oleh logika bisnis aplikasi, kebutuhan pengguna, atau parameter konfigurasi dalam kode.

### b. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber
program, what does it mean?

URL "amqp://guest:guest@localhost:5672" yang sama pada program publisher dan subscriber menunjukkan bahwa:

Keduanya terhubung ke broker pesan (message broker) yang sama
Keduanya menggunakan kredensial sama (guest:guest)
Keduanya mengakses broker pada host dan port yang sama (localhost:5672)

Ini adalah konsep dasar arsitektur publish-subscribe, dimana publisher dan subscriber tidak perlu saling mengenal secara langsung, tetapi berkomunikasi melalui broker pesan sebagai perantara. Keduanya harus terhubung ke broker yang sama agar pesan dapat dikirim dan diterima dengan sukses.

### Message Broker: RabbitMQ

![rabbitMQ-image](/README-Image/Screenshot%202025-05-16%20150605.png)

### Sending and Processing Event

![publisher-terminal](/README-Image/Screenshot%202025-05-16%20161413.png)
Pada pengujian ini, terlihat behavior yang menarik ketika menjalankan subscriber. Saat menjalankan cargo run pada subscriber, program tampak berada dalam kondisi "menunggu" - siap menerima data yang akan masuk.
Kemudian, dengan memanfaatkan RabbitMQ sebagai message broker, saat kita menjalankan cargo run pada publisher, kelima data yang telah disiapkan langsung dikirimkan ke broker. Hasilnya dapat diamati pada terminal subscriber yang menampilkan data-data yang berhasil diterima dalam satu kali eksekusi.


### Monitoring Chart Berdasarkan Publisher

![graph-rabbitMQ](/README-Image/Screenshot%202025-05-05.png)
Pada dashboard RabbitMQ, terlihat fenomena menarik berupa lonjakan signifikan (spike) pada grafik. Lonjakan ini terjadi setelah mengeksekusi perintah cargo run pada publisher sebanyak 3 kali berturut-turut.
Setiap kali publisher dijalankan, ia mengirimkan 5 pesan ke RabbitMQ, sehingga total pesan yang dikirim mencapai 15. Akibatnya, message rate meningkat tajam dalam interval waktu yang singkat, yang terekam dan tervisualisasi sebagai spike pada grafik "Message rates" di dashboard pemantauan RabbitMQ.
