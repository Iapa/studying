Java NIO \(New IO\) is an alternative IO API for Java \(from Java 1.4\), meaning alternative to the standard [Java IO](http://tutorials.jenkov.com/java-io/index.html) and [Java Networking](http://tutorials.jenkov.com/java-networking/index.html) API's. Java NIO offers a different way of working with IO than the standard IO API's.

[Java NIO Tutorial](http://tutorials.jenkov.com/java-nio/overview.html)

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

_Here is a list of the primary _`Channel`_ implementatttions in java NIO:_

* _FileChannel_
* _DatagramChannel_
* _SocketChannel_
* _ServerSocketChannel_

these channels cover DDP + TCP network IO,and file IO.

_Here is a list of the core _`Buffer`_ implementations in Java NIO:_

* _ByteBuffer_
* _CharBuffer_
* _DoubleBuffer_
* _FloatBuffer_
* _IntBuffer_
* _LongBuffer_
* _ShortBuffer_

These `Buffer`'s cover the basic data types that you can send via IO: byte, short, int, long, float, double, and characters.

Java NIO also has a `MappedByteBuffer` which is used in conjunction with memory mapped files. I'll leave this `Buffer` out of this overview though.

**Selectors**

A `Selector` allows a single thread to handle multiple `Channel`'s This is handy if your application has many connections\(Channels\)open , but only has low traffic on each connection. For instance, in a chat server.

Here is an illustration of a thread using a `Selector` to handle 3 `Channel's:`

![](/assets/nio_selectors.png)

To use a `Selector` you register the `Channel`'s with it. Then you call it's `select()` method. This method will block until there is an event ready for one of the registered channels. Once the method returns.the  thread can then process these events.Examples of events are incoming connection, data received etc.

