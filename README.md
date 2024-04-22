## Advanced Programming Module 8 - Publisher

### Reflection

> 7a. How many data your publlsher program will send to the message broker in one run?

Program ini mengirim **lima pesan** ke _message broker_ dalam satu kali dijalankan karena ada lima _function call_ `publish_event` yang mengirim pesan `UserCreatedEventMessage`. Pesan tersebut berisi `user_id` dan `user_name` berbeda untuk setiap _function call_.

> 7b. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?

URL tersebut adalah alamat dari _message broker_ yang digunakan. URL tersebut sama seperti yang ada di program _subscriber_, artinya _publisher_ dan _subscriber_ terhubung dengan berkomunikasi pada _message broker_ yang sama.

### Running RabbitMQ as Message Broker

![RabbitMQ](https://i.imgur.com/fIOenaS.png)
