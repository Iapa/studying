**What is a memory leak in android?**

Many a time we see ANR dialog while using android apps, lags in our apps, we also see`OutOfMemoryError`in Android Studio while building apps. All these kinds of stuff happen due to memory leaks.  
Some objects are not even recognized by garbage collector as garbage. In these situation you can not do anything.

**Reasons memory leak happens.**

Most important reason for memory leaks is our own mistakes while building apps. We should avoid some common mistakes while building apps.

What should we avoid to make our app memory leak free?

**Holding reference of ui specific object in the background.**

Never hold the reference of ui specific object in a background task, as it leads to memory leak.

#### Using static views

Do not use static views as it is always available, static views never get killed.

#### Using static context

Never use`context`as static.

```
public class MainActivity extends AppCompatActivity {

  private static Button button; //NEVER USE LIKE THIS
  private static Context context; //NEVER USE LIKE THIS TOO

}
```

#### Using Context

Be careful while using context, deciding which context is suitable at places is most important. Use application context if possible and use activity context only if required.

For better understanding about context,[**refer**](https://blog.mindorks.com/understanding-context-in-android-application-330913e32514)

#### Never forget to say goodbye to listeners after being served.

Do not forget to unregister your listeners in`onPause`/`onStop`/`onDestroy`method. By not unregistering, it always keeps the activity alive and keeps waiting for listeners.

#### **Using inner class**

If you are using an inner class, use this as static because static class does not need the outer class implicit reference. Using inner class as non static makes the outer class alive so it is better to avoid.  
And if you are using views in static class, pass it in the constructor and use it as a weak reference.

#### **Using anonymous class**

This is very similar to non static inner classes as it is very helpful but still avoid using an anonymous class.

#### **Using views in collection**

Avoid putting views in collections that do not have clear memory pattern.`WeakHashMap`store views as values. Since`WeakHashMap`store views as a hard reference it is better to avoid using it.





