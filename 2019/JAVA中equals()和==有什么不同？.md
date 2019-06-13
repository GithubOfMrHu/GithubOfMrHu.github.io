# `equals()`和`==`有什么不同？

## Example
```java
String s1 = "Hello";
String s2 = new String("Hello");
if (s1 == s2)
    System.out.println("s1 == s2");
else
    System.out.println("s1 != s2");
if (s1.equals(s2)) 
    System.out.println("s1 equals s2");
else
    System.out.println("s1 not equals s2");
```
## Output
```
s1 != s2
s1 equals s2
```
## `equals`

- 当复合数据类型之间进行`equals()`比较时，这个方法的初始行为是比较对象在堆内存中的地址，但在一些诸如`String`, `Integer`, `Date`类中把`Object`中的这个方法覆盖了，作用被覆盖为比较内容是否相同。

## `==`

- 基本数据类型（也称原始数据类型）：`byte`, `short`, `char`, `int`, `long`, `float`, `double`, `boolean`。他们之间使用`==`时比较的是他们的值。

- 引用数据类型：当他们用`==`进行比较的时候，比较的是他们在内存中的存放地址（确切的说，是堆内存地址）。Example中`s1`和`s2`是两个不同对象的堆内存地址，所以`s1 == s2`返回`false`。

## 补充：`IntegerCache.java`
`IntegerCache.java`是`Integer.java`的内部私有类，它缓存了从-128到127之间的所有的整数对象。所以代码
```java
Integer i1 = 100,i2 = 100;
System.out.println(i1==i2);
Integer i3 = 1000,i4 = 1000;
System.out.println(i3==i4);
```
的运行结果为
```
true
false
```


