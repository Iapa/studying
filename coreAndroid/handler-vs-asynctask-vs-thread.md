The Handler class can be used to register to a thread and provides a simple channel to send data to this thread.

The`AsyncTask`class encapsulates the creation of a background process and the synchronization with the main thread. It also supports reporting progress of the running tasks.

And a`Thread`is basically the core element of multithreading which a developer can use with the following disadvantage:

```
If you use Java threads you have to handle the following requirements in your own code:
* Synchronization with the main thread if you post back results to the user interface
* No default for canceling the thread
* No default thread pooling
* No default for handling configuration changes in Android
```

And regarding the AsyncTask, as the Android Developer's Reference puts it:

`AsyncTask enables proper and easy use of the UI thread. This class allows to perform background operations and publish results on the UI thread without having to manipulate threads and/or handlers.`

`AsyncTask is designed to be a helper class around Thread and Handler and does not constitute a generic threading framework. AsyncTasks should ideally be used for short operations (a few seconds at the most.) If you need to keep threads running for long periods of time, it is highly recommended you use the various APIs provided by the java.util.concurrent package such as Executor, ThreadPoolExecutor and FutureTask.`



This is the Google Search:[Douglas Schmidt lecture android concurrency and synchronisation](https://www.google.com/search?q=lecture%208%20android%20concurrency%20and%20synchronisation)

This is the video of the[first lecture on YouTube](https://www.youtube.com/watch?v=aV2XfWwpiDU)

All this is part of the**CS 282 \(2013\): Systems Programming for Android**from the**Vanderbilt University**. Here's the[YouTube Playlist](https://www.youtube.com/playlist?list=PLZ9NgFYEMxp50tvT8806xllaCbd31DpDy)

Douglas Schmidt seems to be an excellent lecturer

