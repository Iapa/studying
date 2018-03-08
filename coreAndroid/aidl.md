Adnroid interface Definition Language\(AIDL\)

**Note:**

Using AIDL is necessary only if you allow clients from different applications to access your service for IPC and want to handle multithreading in your service. If you do not need to perform concurrent IPC across different applications, you should create your interface by [implementing a Binder](https://developer.android.com/guide/components/bound-services.html#Binder) or, if you want to perform IPC, but do _not _need to handle multithreading, implement your interface [using a Messenger](https://developer.android.com/guide/components/bound-services.html#Messenger). Regardless, be sure that you understand [Bound Services](https://developer.android.com/guide/components/bound-services.html) before implementing an AIDL.

