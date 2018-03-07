# Android App Performance Tips \(Smooth Running Android App\) {#8b56}

## Tips to make better android app \(No lags now … only smooth running UI\) {#123a}

#### Learn why android app lags ? {#d1dc}

Garbage Collector : The TAX on Android App Performance

**The main reason of low performance Android app is that it runs GC very frequently.**

#### Simple in one line : The time for which GC is running the actual app is not running. {#0f78}

When the android app runs it allocates so many object on the basis of your code and when the objects that are no longer referred the system call GC when there is memory pressure to deallocate those objects , so if the object allocation and deallocation is occurring on regular basis , the GC is running on regular basis to release memory , So more time the GC is running , your app is not running for that time . So it seems the app is lagging.

The app updates its UI every**16ms**\(considering**60FPS -&gt; 1000ms/60 = 16.67ms~16ms**\) for smooth UI rendering . So if the GC is running for that time the app is unable to update UI for that time , leads to skipping of few frames , so it seems that the app is lagging. So the actual reason is that the GC was running or may the work is doing too much in main thread so that the app did not get time to render it’s UI smoothly.

Another reason is that may be the app is doing too much in main thread , so at that time if any method is taking more time than**16ms**the app will be unable to update UI , means lag will be there in app for that time.

So , these are the reasons for low performance Android App.

**How to optimize it ?**

* Reduce GC running time
* Do not do much in main thread

**Tips to achieve better Android App performance**

* Do not allocate any object if not required
* Do not allocate object early , allocate object only when it is required
* Avoid Auto-Boxing as Integer, Boolean, etc takes more memory as classes like Integer takes more memory so use int where ever possible instead of Integer
* Use concept of object pools to avoid memory churn
* Do not allocate large amount of unnecessary objects
* Avoid using enums as a single reference to an enum constant occupy 4 bytes
* Keep heavy work away from the main thread
* Use Static Final For Constants
* Avoid Internal Getters/Setters \(direct field access is 3x faster\)
* Don’t leak contexts in inner classes
* Use static inner classes over non static
* Use LRU cache for bitmap — avoid redundant decoding of bitmap — reduces GC calling again and again

Please recommend it and stay tuned for upcoming tips as there are much more to come in this series.Thanks Stay Tuned. \#ByTheDeveloperForTheDeveloper

Read about[**Fast Android Networking**here](https://medium.freecodecamp.com/simple-and-fast-android-networking-19ed860d1455#.of3ww265v).

Thanks for reading this article. Be sure to click ❤ below to recommend this article if you found it helpful. It means a lot to me.

_For more about programming, follow me so you’ll get notified when I write new posts._

Check out my all the articles on Android[**here**](https://medium.com/@amitshekhar).

Thanks

