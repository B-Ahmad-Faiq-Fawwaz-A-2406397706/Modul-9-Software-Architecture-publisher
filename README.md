**a. How much data will your publisher send to the message broker in one run?**

Dalam satu kali menjalankan publisher, program akan mengirimkan 5 event ke message broker. Setiap event berisi data berupa sebuah objek `UserCreatedEventMessage` yang memiliki dua field yaitu `user_id` dan `user_name`. Kelima event tersebut masing-masing merepresentasikan data pengguna yang berbeda yaitu Amir, Budi, Cica, Dira, dan Emir. Semua event tersebut dikirimkan ke antrian yang sama bernama `user_created` di RabbitMQ. Jadi dalam satu kali run, publisher mengirimkan tepat 5 pesan ke message broker.

**b. The URL "amqp://guest:guest@localhost:5672" is the same as in subscriber program, what does it mean?**

URL yang sama pada publisher dan subscriber menunjukkan bahwa keduanya terhubung ke message broker yang sama, yaitu RabbitMQ yang berjalan di `localhost` pada port `5672`. Hal ini penting karena publisher dan subscriber tidak berkomunikasi secara langsung satu sama lain, melainkan keduanya melewati perantara yaitu RabbitMQ. Publisher mengirimkan pesan ke broker tersebut, dan subscriber membaca pesan dari broker yang sama. Dengan menggunakan URL koneksi yang identik, kita memastikan bahwa pesan yang dikirim publisher akan masuk ke antrian yang bisa diakses oleh subscriber. Inilah inti dari arsitektur event-driven, di mana message broker menjadi titik pusat komunikasi antar komponen yang independen.

## Screenshot of running RabbitMQ

![](media/RabbitMQ.png)