## Advanced Programming Module 8 - Publisher

### Reflection

> 7a. How many data your publlsher program will send to the message broker in one run?

Program ini mengirim **lima pesan** ke _message broker_ dalam satu kali dijalankan karena ada lima _function call_ `publish_event` yang mengirim pesan `UserCreatedEventMessage`. Pesan tersebut berisi `user_id` dan `user_name` berbeda untuk setiap _function call_.

> 7b. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?

URL tersebut adalah alamat dari _message broker_ yang digunakan. URL tersebut sama seperti yang ada di program _subscriber_, artinya _publisher_ dan _subscriber_ terhubung dengan berkomunikasi pada _message broker_ yang sama.

### Running RabbitMQ as Message Broker

![RabbitMQ](https://i.imgur.com/fIOenaS.png)

### Sending and Processing Event

![Sending and Processing Event](https://i.imgur.com/YgmehpZ.png)

Ketika saya menjalankan `cargo run` pada _publisher_, ia mengirim lima _events_ ke RabbitMQ yang kemudian disimpan dalam _queue_ `user_created`. Kemudian, _subscriber_ yang juga dijalankan dengan `cargo run` melakukan _listening_ terhadap _queue_ tersebut, dan setiap _event_ yang diterima diproses oleh `UserCreatedHandler` sehingga menghasilkan _output_ pada konsol _subscriber_ yang menunjukkan detail _event_ yang diterima dan diproses dari RabbitMQ.

### Monitoring Chart Based on Publisher

![Monitoring Chart Based on Publisher](https://i.imgur.com/DvjJXot.png)

_Spike_ yang terlihat pada grafik di atas menunjukkan peningkatan aktivitas dan aliran pesan yang masuk ke dalam antrean `user_created` yang terjadi saat _publisher_ mengirimkan _events_ baru ke RabbitMQ (Setiap kali _publisher_ dijalankan, ia mengirimkan beberapa _event_ ke antrean tersebut pada RabbitMQ).
