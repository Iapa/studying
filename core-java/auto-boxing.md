```
ArrayList<Integer> intList = new ArrayList<Integer>();
intList.add(1); //autoboxing - primitive to object
intList.add(2); //autoboxing

ThreadLocal<Integer> intLocal = new ThreadLocal<Integer>();
intLocal.set(4); //autoboxing

int number = intList.get(0); // unboxing
int local = intLocal.get(); // unboxing in Java
```

自动装箱的弊端：

自动装箱有一个问题，那就是在一个循环中进行自动装箱操作的情况，如下面的例子就会创建多余的对象，影响程序的性能。

```
Integer sum = 0;
 for(int i=1000; i<5000; i++){
   sum+=i;
}
```

上面的代码`sum+=i`可以看成`sum = sum + i,`但是`+`这个操作符不适用于Integer对象，首先sum进行自动拆箱操作，进行数值相加操作，最后发生自动装箱操作转换成Integer对象。其内部变化如下:

```
int result = sum.intValue() + i;
Integer sum = new Integer(result);
```

由于我们这里声明的sum为Integer类型，在上面的循环中会创建将近4000个无用的Integer对象，在这样庞大的循环中，会降低程序的性能并且加重了垃圾回收的工作量。因此在我们编程时，需要注意到这一点，正确地声明变量类型，避免因为自动装箱引起的性能问题。

**注意：**

对象相等比较，这是容易出错地方。== 可以用于原始值比较，也可以用于对象比较，当用于对象时，比较的不是值，而是检查两者是否同一对象，这个过程没有自动装箱发生。当对对象值比较时，应该用equals方法。

```
public class AutoboxingTest {

    public static void main(String args[]) {

        // Example 1: == comparison pure primitive – no autoboxing
        int i1 = 1;
        int i2 = 1;
        System.out.println("i1==i2 : " + (i1 == i2)); // true

        // Example 2: equality operator mixing object and primitive
        Integer num1 = 1; // autoboxing
        int num2 = 1;
        System.out.println("num1 == num2 : " + (num1 == num2)); // true

        // Example 3: special case - arises due to autoboxing in Java
        Integer obj1 = 1; // autoboxing will call Integer.valueOf()
        Integer obj2 = 1; // same call to Integer.valueOf() will return same
                            // cached Object

        System.out.println("obj1 == obj2 : " + (obj1 == obj2)); // true

        // Example 4: equality operator - pure object comparison
        Integer one = new Integer(1); // no autoboxing
        Integer anotherOne = new Integer(1);
        System.out.println("one == anotherOne : " + (one == anotherOne)); // false

    }

}

Output:
i1==i2 : true
num1 == num2 : true
obj1 == obj2 : true
one == anotherOne : false
```

值得注意的是第三个小例子，这是一种极端情况。obj1和obj2的初始化都发生了自动装箱操作。但是处于节省内存的考虑，JVM会缓存-128到127的Integer对象。因为obj1和obj2实际上是同一个对象。所以使用”==“比较返回true。

### 容易混乱的对象和原始数据值

另一个需要避免的问题就是混乱使用对象和原始数据值，一个具体的例子就是当我们在一个原始数据值与一个对象进行比较时，如果这个对象没有进行初始化或者为Null，在自动拆箱过程中obj.xxxValue，会抛出NullPointerException,如下面的代码：

```
private static Integer count;

//NullPointerException on unboxing
if( count <= 0){
  System.out.println("Count is not started yet");
}
```

### 缓存的对象

这个问题就是我们上面提到的极端情况，在Java中，会对-128到127的Integer对象进行缓存，当创建新的Integer对象时，如果符合这个这个范围，并且已有存在的相同值的对象，则返回这个对象，否则创建新的Integer对象。

在Java中另一个节省内存的例子就是[字符串常量池](http://droidyue.com/blog/2014/12/21/string-literal-pool-in-java/),感兴趣的同学可以了解一下。

### 生成无用对象增加GC压力

因为自动装箱会隐式地创建对象，像前面提到的那样，如果在一个循环体中，会创建无用的中间对象，这样会增加GC压力，拉低程序的性能。所以在写循环时一定要注意代码，避免引入不必要的自动装箱操作。

如想了解垃圾回收和内存优化，可以查看本文[Google IO：Android内存管理主题演讲记录](http://droidyue.com/blog/2014/11/02/note-for-google-io-memory-management-for-android-chinese-edition/)

总的来说，自动装箱和拆箱着实为开发者带来了很大的方便，但是在使用时也是需要格外留意，避免引起出现文章提到的问题。



http://javarevisited.blogspot.jp/2012/07/auto-boxing-and-unboxing-in-java-be.html

