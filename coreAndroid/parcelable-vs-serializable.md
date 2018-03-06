**Differences between Serialization and Parcelable**

Parcelable and Serialization are used for marshaling and unmarshaling Java objects.  Differences between the two are often cited around implementation techniques and performance results. From my experience, I have come to identify the following differences in both the approaches:

·         Parcelable is well documented in the Android SDK; serialization on the other hand is available in Java. It is for this very reason that Android developers prefer Parcelable over the Serialization technique.

·         In Parcelable, developers write custom code for marshaling and unmarshaling so it creates less garbage objects in comparison to Serialization. The performance of Parcelable over Serialization dramatically improves \(around two times faster\), because of this custom implementation.

·         Serialization is a marker interface, which implies the user cannot marshal the data according to their requirements. In Serialization, a marshaling operation is performed on a Java Virtual Machine \(JVM\) using the Java reflection API. This helps identify the Java objects member and behavior, but also ends up creating a lot of garbage objects. Due to this, the Serialization process is slow in comparison to Parcelable.

