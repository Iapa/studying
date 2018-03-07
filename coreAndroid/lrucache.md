In order to choose a suitable size for a[`LruCache`](https://developer.android.com/reference/android/util/LruCache.html), a number of factors should be taken into consideration, for example:

* How memory intensive is the rest of your activity and/or application?
* How many images will be on-screen at once? How many need to be available ready to come on-screen?
* What is the screen size and density of the device? An extra high density screen \(xhdpi\) device like
  [Galaxy Nexus](http://www.android.com/devices/detail/galaxy-nexus)
  will need a larger cache to hold the same number of images in memory compared to a device like
  [Nexus S](http://www.android.com/devices/detail/nexus-s)
  \(hdpi\).
* What dimensions and configuration are the bitmaps and therefore how much memory will each take up?
* How frequently will the images be accessed? Will some be accessed more frequently than others? If so, perhaps you may want to keep certain items always in memory or even have multiple
  [`LruCache`](https://developer.android.com/reference/android/util/LruCache.html)
  objects for different groups of bitmaps.
* Can you balance quality against quantity? Sometimes it can be more useful to store a larger number of lower quality bitmaps, potentially loading a higher quality version in another background task.



