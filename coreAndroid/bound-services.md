A bound service is the server in a client-server interface. It allows components \(such as activities\) to bind to the service, send requests, receive responses, and perform interprocess communication \(IPC\). A bound service typically lives only while it serves another application component and does not run in the background indefinitely.

```
Note: If your app targets Android 5.0 (API level 21) or later, it's recommended that you use the JobScheduler to execute background services. For more information about JobScheduler, see its API-reference documentation.
```

**注**：只有 Activity、服务和内容提供程序可以绑定到服务 — 您**无法**从广播接收器绑定到服务。![](/assets/service_binding_tree_lifecycle.png)

