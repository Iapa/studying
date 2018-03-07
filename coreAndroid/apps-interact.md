**How can two distinct Android apps interact?**

**Build an Implicit Intent:**

* call phone:

```
Uri number = Uri.parse("tel:5551234");
Intent callIntent = new Intent(Intent.ACTION_DIAL, number);
```

* View a map:

```
// Map point based on address
Uri location = Uri.parse("geo:0,0?q=1600+Amphitheatre+Parkway,+Mountain+View,+California");
// Or map point based on latitude/longitude
// Uri location = Uri.parse("geo:37.422219,-122.08364?z=14"); // z param is zoom level
Intent mapIntent = new Intent(Intent.ACTION_VIEW, location);
```

* View a web page:

```
Uri webpage = Uri.parse("http://www.android.com");
Intent webIntent = new Intent(Intent.ACTION_VIEW, webpage);
```

Other kinds of implicit intents require "extra" data that provide different data types, such as a string. You can add one or more pieces of extra data using the various[`putExtra()`](https://developer.android.com/reference/android/content/Intent.html#putExtra%28java.lang.String, java.lang.String%29)methods.

By default, the system determines the appropriate MIME type required by an intent based on the[`Uri`](https://developer.android.com/reference/android/net/Uri.html)data that's included. If you don't include a[`Uri`](https://developer.android.com/reference/android/net/Uri.html)in the intent, you should usually use[`setType()`](https://developer.android.com/reference/android/content/Intent.html#setType%28java.lang.String%29)to specify the type of data associated with the intent. Setting the MIME type further specifies which kinds of activities should receive the intent.

Here are some more intents that add extra data to specify the desired action:

* Send an email with an attachment:

```
Intent emailIntent = new Intent(Intent.ACTION_SEND);
// The intent does not have a URI, so declare the "text/plain" MIME type
emailIntent.setType(HTTP.PLAIN_TEXT_TYPE);
emailIntent.putExtra(Intent.EXTRA_EMAIL, new String[] {"jon@example.com"}); // recipients
emailIntent.putExtra(Intent.EXTRA_SUBJECT, "Email subject");
emailIntent.putExtra(Intent.EXTRA_TEXT, "Email message text");
emailIntent.putExtra(Intent.EXTRA_STREAM, Uri.parse("content://path/to/email/attachment"));
// You can also attach multiple items by passing an ArrayList of Uris
```

* Create a calendar event:

```
Intent calendarIntent = new Intent(Intent.ACTION_INSERT, Events.CONTENT_URI);
Calendar beginTime = Calendar.getInstance().set(2012, 0, 19, 7, 30);
Calendar endTime = Calendar.getInstance().set(2012, 0, 19, 10, 30);
calendarIntent.putExtra(CalendarContract.EXTRA_EVENT_BEGIN_TIME, beginTime.getTimeInMillis());
calendarIntent.putExtra(CalendarContract.EXTRA_EVENT_END_TIME, endTime.getTimeInMillis());
calendarIntent.putExtra(Events.TITLE, "Ninja class");
calendarIntent.putExtra(Events.EVENT_LOCATION, "Secret dojo");
```

**Note:**This intent for a calendar event is supported only with API level 14 and higher.



**Verify There is an App to Receive the Intent**

Although the Android platform guarantees that certain intents will resolve to one of the built-in apps \(such as the Phone, Email, or Calendar app\), you should always include a verification step before invoking an intent.  
  
**Caution:**If you invoke an intent and there is no app available on the device that can handle the intent, your app will crash.

  
To verify there is an activity available that can respond to the intent, call[`queryIntentActivities()`](https://developer.android.com/reference/android/content/pm/PackageManager.html#queryIntentActivities%28android.content.Intent, int%29)to get a list of activities capable of handling your[`Intent`](https://developer.android.com/reference/android/content/Intent.html). If the returned[`List`](https://developer.android.com/reference/java/util/List.html)is not empty, you can safely use the intent. For example:

```
PackageManager packageManager = getPackageManager();
List<ResolveInfo> activities = packageManager.queryIntentActivities(intent,
        PackageManager.MATCH_DEFAULT_ONLY);
boolean isIntentSafe = activities.size() > 0;
```

  
  
  
  




