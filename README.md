### Understanding Subscriber and Message Broker

**a. What is amqp?**
AMQP stands for Advanced Message Queuing Protocol. It is an open standard application layer protocol for message-oriented middleware, providing message orientation, queuing, routing (including point-to-point and publish-and-subscribe), reliability, and security.

**b. What does `guest:guest@localhost:5672` mean?**
- The first `guest` is the default username for RabbitMQ.
- The second `guest` is the default password for the RabbitMQ user.
- `localhost:5672` specifies the host machine (the local computer) and the default port number (5672) that the RabbitMQ server is listening on for AMQP connections.