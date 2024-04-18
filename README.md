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

</details>