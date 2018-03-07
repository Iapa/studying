[What is difference between DVM and ART ? Why DVM has been officially replaced with ART in Lollipop?](https://stackoverflow.com/questions/31957568/what-is-difference-between-dvm-and-art-why-dvm-has-been-officially-replaced-wi)

**1\) Compilation Approach**

This is by far the biggest advantage of ART over Dalvik.**The old guy Dalvik used Just-In-Time \(JIT\) approach**in which the compilation was done on demand. All the dex files were converted into their respective native representations only when it was needed.

But **ART uses the Ahead-Of-Time \(AOT\) approach**, in which the dex files were compiled before they were demanded. This itself massively improves the performance and battery life of any Android device.  

_For example:_

In case of Dalvik, whenever you touch an app icon to open it, the necessary dex files gets converted into their equivalent native codes. The app will only start working when this compilation is done. So, the app is unresponsive until this finishes.

Moreover,**this process is repeated every single time you open an app wasting CPU cycles and valuable battery juice.**

But in case of ART, whenever you install an app,**all the dex files gets converted once and for all**. So the installation takes some time and the app takes more space than in Dalvik,**but the performance is massively improved and battery life is smartly conserved**.

**2\) Boot Time**

In case of Dalvik, the cache is built with time the device runs and apps are used as is indicated by the JIT approach.**So the boot time is very fast.**

But in case of ART,**the cache is built during the first boot, so the boot time is considerably more in case of ART**. You might see an "Optimizing apps" dialog box sometimes you boot.

**3\) Space Usage**

The space used by apps being run on ART is much more than that of Dalvik._Like a 20 MB app on Dalvik, takes more than 35 MB on ART._

So**if you are on a low storage device, then this can be a huge disadvantage **for you.

**4\) ART is Damn Fast**

As discussed above,**ART is extremely fast and smooth**. Apps are very snappy and responsive. Any comparison between Dalvik and ART, will surely make the ART device win by a significant margin.

_**ART**is the answer to all those who argued that iOS is faster and smoother than Android and is also more battery efficient._  


