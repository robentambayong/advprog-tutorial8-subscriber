### Understanding Subscriber and Message Broker

**a. What is amqp?**
AMQP stands for Advanced Message Queuing Protocol. It is an open standard application layer protocol for message-oriented middleware, providing message orientation, queuing, routing (including point-to-point and publish-and-subscribe), reliability, and security.

**b. What does `guest:guest@localhost:5672` mean?**
- The first `guest` is the default username for RabbitMQ.
- The second `guest` is the default password for the RabbitMQ user.
- `localhost:5672` specifies the host machine (the local computer) and the default port number (5672) that the RabbitMQ server is listening on for AMQP connections.

### Simulating a Slow Subscriber

![Slow Subscriber Queue](rabbitmq3.png)

**Explanation of the Queue Spike:**
The total number of queued messages spiked to 20 because we intentionally slowed down the subscriber by uncommenting the `thread::sleep(_ten_millis);` line. This introduced a strict 1 second delay for every single message the subscriber processes. 

While the subscriber was busy sleeping, I executed the publisher program multiple times rapidly (firing 5 messages per run). Because the publisher's message production rate vastly exceeded the slow subscriber's consumption rate, the system created a bottleneck. RabbitMQ stepped in as a buffer, safely holding those 20 unacknowledged messages in the queue and feeding them to the subscriber one by one as it became available.