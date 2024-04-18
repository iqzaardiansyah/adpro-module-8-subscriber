<details>
<summary>Tutorial Module 8</summary>

1. what is _**amqp**_?
   
    AMQP stands for Advanced Message Queuing Protocol. It's an open standard for messaging middleware that enables systems to communicate with each other asynchronously by sending and receiving messages. 

    AMQP provides a framework for message-oriented middleware that allows applications to communicate with each other reliably, regardless of the underlying platform or programming language. It defines a set of rules and formats for how messages should be structured, transmitted, and managed between sender and receiver systems.

    In the provided code snippet, AMQP is being used to set up a message queue listener for handling messages related to user creation events. This allows for decoupling the components of a system, enabling asynchronous communication and scalability.

2. what it means? guest:guest@localhost:5672 , what is the first _**guest**_, and what is the second _**guest**_, and what is _**localhost:5672**_ is for?

    In the provided code, guest:guest@localhost:5672 is a Uniform Resource Identifier (URI) representing the connection details for the AMQP (Advanced Message Queuing Protocol) server.

    Let's break it down:

    - _**guest:guest**_: The first  _**guest**_ is the username, and the second  _**guest**_ is the password. In AMQP,  _**guest**_ is often used as default credentials for testing and development purposes. However, in production environments, it's important to use secure and unique credentials.

    -  _**localhost:5672**_: "localhost" refers to the hostname or IP address of the AMQP server, in this case, it's the same machine where the code is running. 5672 is the default port number for AMQP connections. So, _**localhost:5672**_ specifies that the AMQP server is running on the local machine, and the communication should happen through port 5672.

    So, in summary, guest:guest@localhost:5672 specifies the username, password, hostname, and port of the AMQP server that the code will connect to.

![Screenshot of running code on console and delayed spike on RabbitMQ](https://i.ibb.co/rGJgTrz/gambar-2024-04-18-175549622.png)

The total number of queues in RabbitMQ is determined by several factors, including the configuration of the message broker, the number of bindings, and the behavior of the publisher and subscriber applications.

Here are some reasons why the total number of queues might differ between your machine (with 2 queues) and another machine (with 20 queues):

1. **Bindings**: Each queue in RabbitMQ is typically bound to one or more exchanges. If there are more bindings on the other machine, it could result in more queues being created.

2. **Subscriber Behavior**: The behavior of the subscriber application can influence the creation of queues. In your case, the subscriber application has a delay of 10 milliseconds (`thread::sleep(ten_millis);`) before processing each message. During this delay, messages might accumulate in RabbitMQ, potentially leading to the creation of additional queues if they are not processed quickly enough.

3. **Message Volume**: The volume of messages being published and consumed can impact the creation of queues. If there are more messages being published or consumed on the other machine, it might lead to the creation of additional queues to handle the workload.

4. **Configuration Differences**: Differences in RabbitMQ configuration between your machine and the other machine, such as queue TTL (Time-To-Live) settings or queue auto-delete behavior, could result in different queue creation behavior.

5. **Other Applications**: There might be other applications or components interacting with RabbitMQ on the other machine, leading to the creation of additional queues for different purposes.

To determine the exact reason for the difference in the total number of queues between your machine and the other machine, it would be necessary to inspect the RabbitMQ configuration, monitor the message flow, and analyze the behavior of all interacting applications.

![Screenshot of three running subscribers](https://i.ibb.co/71L8Wkc/Screenshot-46.png)
![Screenshot of RabbitMQ responding to three running subscribers](https://i.ibb.co/G9Fv0qJ/gambar-2024-04-18-180552767.png)

The reason why running three subscribers with a delay of 10ms each might appear faster than running one subscriber with the same delay is due to concurrency and parallelism.

When you have three subscribers running concurrently, each handling messages with a delay of 10ms, they can process messages in parallel. This means that while one subscriber is waiting for the delay, the other two subscribers can continue processing messages. As a result, the overall time to process all messages might be shorter compared to a single subscriber handling messages sequentially.

In contrast, when you have only one subscriber running, it has to handle all messages sequentially, one after the other, with each message introducing a delay of 10ms. This can lead to a longer total processing time because each message must wait for the previous one to finish processing before it can be handled.

Regarding the code improvement, there's nothing particularly inefficient in the provided code snippets for the publisher and subscriber. However, there are a few suggestions for improvement:

1. **Concurrency**: If your system can benefit from concurrent processing, you might consider implementing concurrency in your subscriber code using threads or asynchronous programming. This way, you can handle multiple messages concurrently, potentially improving performance.

2. **Error Handling**: Ensure robust error handling in both the publisher and subscriber code to handle potential failures gracefully and prevent message loss or system instability.

3. **Logging**: Consider using a logging framework to log messages and errors instead of directly printing to the console. This provides better control over log levels, formatting, and output destinations.

4. **Configuration**: Make sure your RabbitMQ server is properly configured for optimal performance and reliability, considering factors such as queue settings, message persistence, and clustering if applicable.

By optimizing these aspects of your code and configuration, you can potentially improve the overall performance and reliability of your messaging system.

</details>