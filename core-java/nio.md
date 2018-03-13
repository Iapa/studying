Java NIO \(New IO\) is an alternative IO API for Java \(from Java 1.4\), meaning alternative to the standard [Java IO](http://tutorials.jenkov.com/java-io/index.html) and [Java Networking](http://tutorials.jenkov.com/java-networking/index.html) API's. Java NIO offers a different way of working with IO than the standard IO API's.

**Java NIO consist of the following core components:**

* **Channels**
* **Buffers**
* **Selectors**

**Java NIO: Channels and Buffers**

in the standard IO API you work with byte streams and character streams. In NIO you work with channels and buffers. Data is always read from a channel into a buffer, or wirtten from a buffer to a channel.

**Java NIO: Non-blocking IO**

Java NIO enables you to do non-blocking IO. For instance, a thread can ask a channel to read data into a buffer. While the channel   reads data into the buffer,the thread can do something else. Once data is read into the buffer,the thread can then continue processing it. The same is true for writing data to channels.

**Java NIO: Selectors**

Java NIO contains the concept of "selectors". A selector is an object that can monitor multiple channels for events\(like: connection opened, data arrived etc\).Thus,, a single thread can monitor multiple channels for data.

**Channels and  Buffers:**

Here is an illustration of that:

![](/assets/nio_channels_buffers.png)

Here is a list of the primary `Channel` implementatttions in java NIO:

* FileChannel
* DatagramChannel
* SocketChannel
* ServerSocketChannel

these channels cover DDP + TCP network IO,and file IO.



