<h1>Refleksi</h1>

---

Nama: Makarim Zufar Prambudyo
NPM: 2306241751
Kelas: Advprog-B

---

a. How much data your publisher program will send to the message broker in one
run?

Jumlah data yang dikirim program publisher ke message broker dalam satu kali proses sangat bergantung pada implementasi spesifik program tersebut. Tidak ada ukuran tetap karena:

Publisher dapat mengirim satu pesan tunggal atau ribuan pesan
Ukuran setiap pesan bisa bervariasi (dari beberapa byte hingga megabyte)
Implementasi publisher mungkin memiliki batasan atau konfigurasi khusus

Jumlah data ini biasanya ditentukan oleh logika bisnis aplikasi, kebutuhan pengguna, atau parameter konfigurasi dalam kode.

b. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber
program, what does it mean?

URL "amqp://guest:guest@localhost:5672" yang sama pada program publisher dan subscriber menunjukkan bahwa:

Keduanya terhubung ke broker pesan (message broker) yang sama
Keduanya menggunakan kredensial sama (guest:guest)
Keduanya mengakses broker pada host dan port yang sama (localhost:5672)

Ini adalah konsep dasar arsitektur publish-subscribe, dimana publisher dan subscriber tidak perlu saling mengenal secara langsung, tetapi berkomunikasi melalui broker pesan sebagai perantara. Keduanya harus terhubung ke broker yang sama agar pesan dapat dikirim dan diterima dengan sukses.
