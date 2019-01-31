---
title: Java string final
category: java
---

#java final 属性的String 的编译问题

> final 的String 在编译时，会直接编译进入属性引用类的常量池中，与String所在类不再有任何关系。
B.java
```java

package com.wanzheng90;

class B{
	public static final String sf = "sf";
  public static String s="s";
	public final String f = "fjdaoifjdaf";
}
```

Test.java
```java

package com.wanzheng90;

class Test{
  public static final String s = "adk";

	public static void main(String[] args){
		String s=B.s;
		String sf=B.sf;
		String f=new B().f;
		System.out.println(s);
		System.out.println(f);
		System.out.println(sf);
	}

}
```

Test编译后的lass源码如下：

Test.class
```java
Constant pool:
   #2 = Fieldref           #3.#25         // com/wanzheng90/B.s:Ljava/lang/String;
   #3 = Class              #26            // com/wanzheng90/B
   #4 = String             #27            // sf
   #7 = String             #29            // fjdaoifjdaf
   #8 = Fieldref           #30.#31        // java/lang/System.out:Ljava/io/PrintStream;
   #9 = Methodref          #32.#33        // java/io/PrintStream.println:(Ljava/lang/String;)V
  #10 = Class              #34            // com/wanzheng90/Test
  #12 = Utf8               s
  #14 = Utf8               ConstantValue
  #23 = Utf8               Test.java
  #25 = NameAndType        #12:#13        // s:Ljava/lang/String;
  #26 = Utf8               com/wanzheng90/B
  #27 = Utf8               sf
  #28 = NameAndType        #37:#38        // getClass:()Ljava/lang/Class;
  #29 = Utf8               fjdaoifjdaf
  #30 = Class              #39            // java/lang/System
  #31 = NameAndType        #40:#41        // out:Ljava/io/PrintStream;
  #32 = Class              #42            // java/io/PrintStream
  #33 = NameAndType        #43:#44        // println:(Ljava/lang/String;)V
  #34 = Utf8               com/wanzheng90/Test
  #35 = Utf8               java/lang/Object
  #36 = Utf8               adk
  #41 = Utf8               Ljava/io/PrintStream;
  #42 = Utf8               java/io/PrintStream
  #43 = Utf8               println

  public static void main(java.lang.String[]);
    descriptor: ([Ljava/lang/String;)V
    flags: ACC_PUBLIC, ACC_STATIC
    Code:
      stack=2, locals=4, args_size=1
         0: getstatic     #2                  // Field com/wanzheng90/B.s:Ljava/lang/String;
         3: astore_1
         4: ldc           #4                  // String sf
         6: astore_2
         7: new           #3                  // class com/wanzheng90/B
        10: dup
        11: invokespecial #5                  // Method com/wanzheng90/B."<init>":()V
        14: invokevirtual #6                  // Method java/lang/Object.getClass:()Ljava/lang/Class;
        17: pop
        18: ldc           #7                  // String fjdaoifjdaf
        20: astore_3
        21: getstatic     #8                  // Field java/lang/System.out:Ljava/io/PrintStream;
        24: aload_1
        25: invokevirtual #9                  // Method java/io/PrintStream.println:(Ljava/lang/String;)V
        28: getstatic     #8                  // Field java/lang/System.out:Ljava/io/PrintStream;
        31: aload_3
        32: invokevirtual #9                  // Method java/io/PrintStream.println:(Ljava/lang/String;)V
        35: getstatic     #8                  // Field java/lang/System.out:Ljava/io/PrintStream;
        38: aload_2
        39: invokevirtual #9                  // Method java/io/PrintStream.println:(Ljava/lang/String;)V
        42: return

```
观察 #4,#7 可知final声明的String在编译时进入了常量池中。
