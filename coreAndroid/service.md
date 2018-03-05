**When to use?**

* The_Service_can be used in tasks with no UI, but shouldn't be too long. If you need to perform long tasks, you must use threads within Service.

* The_IntentService_can be used in long tasks usually with no communication to Main Thread. If communication is required, can use Main Thread handler or broadcast intents. Another case of use is when callbacks are needed \(Intent triggered tasks\).

**How to trigger?**

* The_Service_is triggered by calling method`startService()`.

* The_IntentService_is triggered using an Intent, it spawns a new worker thread and the method`onHandleIntent()`is called on this thread.

**Triggered From**

* The
  _Service_
  and
  _IntentService_
  may be triggered from any thread, activity or other application component.

**Runs On**

* The_Service_runs in background but it runs on the Main Thread of the application.

* The_IntentService_runs on a separate worker thread.

**Limitations / Drawbacks**

* The_Service_may block the Main Thread of the application.

* The_IntentService_cannot run tasks in parallel. Hence all the consecutive intents will go into the message queue for the worker thread and will execute sequentially.

**When to stop?**

* If you implement a_Service_, it is your responsibility to stop the service when its work is done, by calling`stopSelf()`or`stopService()`. \(If you only want to provide binding, you don't need to implement this method\).

* The_IntentService_stops the service after all start requests have been handled, so you never have to call`stopSelf()`.



