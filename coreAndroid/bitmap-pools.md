One way to do this is to use[inBitmap](https://developer.android.com/reference/android/graphics/BitmapFactory.Options.html#inBitmap)\(which reuses bitmap memory\).



```java
Bitmap bitmapOne = BitmapFactory.decodeFile(filePathOne);
imageView.setImageBitmap(bitmapOne);

// lets say , we do not need image bitmapOne now and we have to set // another bitmap in imageView

final 
BitmapFactory.Options options = new BitmapFactory.Options();
options.inJustDecodeBounds = true;
BitmapFactory.decodeFile(filePathTwo, options);

if (canUseForInBitmap(bitmapOne, options)) { 

//canUseForInBitmap check if the image can be reuse or not by //checking the image size and other factors
options.inMutable = true;
options.inBitmap = bitmapOne;
}
options.inJustDecodeBounds = false;
Bitmap bitmapTwo = BitmapFactory.decodeFile(filePathTwo, options);
imageView.setImageBitmap(bitmapTwo);
```



```

```

```
public static boolean canUseForInBitmap(
        Bitmap candidate, BitmapFactory.Options targetOptions) {
if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.KITKAT) {

// From Android 4.4 (KitKat) onward we can re-use if the byte size of
        // the new bitmap is smaller than the reusable bitmap candidate
        // allocation byte count.

int width = targetOptions.outWidth / targetOptions.inSampleSize;

int height = targetOptions.outHeight / targetOptions.inSampleSize;

int byteCount = width * height * getBytesPerPixel(candidate.getConfig());


try {
return byteCount <= candidate.getAllocationByteCount();
    } 
catch (NullPointerException e) {
return byteCount <= candidate.getHeight() * candidate.getRowBytes();   }
    }

// On earlier versions, the dimensions must match exactly and the inSampleSize must be 1

return candidate.getWidth() == targetOptions.outWidth&&candidate.getHeight() == targetOptions.outHeight&&targetOptions.inSampleSize == 1;
}
```



```

```

```
private static int getBytesPerPixel(Bitmap.Config config) {
if (config == null) {
        config = Bitmap.Config.ARGB_8888;
    }


int bytesPerPixel;

switch (config) {

case ALPHA_8:
         bytesPerPixel = 1;
            break;

case RGB_565:

case ARGB_4444:
            bytesPerPixel = 2;
            break;

case ARGB_8888:

default:
            bytesPerPixel = 4;
break;
    }

return bytesPerPixel;
}
```



