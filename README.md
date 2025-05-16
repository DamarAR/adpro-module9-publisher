**1. How much data your publisher program will send to the message broker in one run?**

Each time the publisher runs, it sends five messages to the message broker. Every message includes two fields: user_id (e.g., values from "1" to "5") and user_name (an alphanumeric string around 20 characters long). When serialized using Borsh, each message takes up approximately 30–40 bytes, resulting in a total data payload of about 150–200 bytes per run. Given the small size of this data, the full batch is quickly encoded and transmitted almost instantly to the broker.


**2. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?**

This URI specifies that both the publisher and subscriber should use the AMQP protocol to connect to a RabbitMQ broker running locally. Here's what it means:

- guest (username) and guest (password) are the default credentials provided by RabbitMQ for local testing.

- localhost points to a broker running on the same machine as the programs.

- 5672 is the default AMQP port RabbitMQ listens on.

Since both the publisher and subscriber use exactly the same connection URI, they are connecting to the same broker instance. This shared connection ensures that:

- The publisher can send messages to a queue or exchange.

- The subscriber can retrieve those messages from that same broker.

In short, using the same URI means both programs are working with the same messaging infrastructure, which allows reliable communication and data exchange between them.


**3. Running RabbitMQ as message broker.**
![image.png](img\image.png)


**4. Sending and processing event**
![image1.png](img\image1.png)






