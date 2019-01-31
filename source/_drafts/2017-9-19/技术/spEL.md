---
title: spEL
date: 2017-03-04 18:57:40
tags: spring
---

# 简介

spEL 是（Spring Expression Language spring表达式语言的简写） 一个在运行时查询和操作对象依赖的表达式语言。语言的语法与Unified EL语法类似，但是新增了功能，主要是方法调用和字符模板操作方法。

<!-- more-->

# 详解

## 1.文本表达

```
ExpressionParser parser = new SpelExpressionParser();
// evals to "Hello World"
String helloWorld = (String) parser.parseExpression("'Hello World'").getValue();
double avogadrosNumber = (Double) parser.parseExpression("6.0221415E+23").getValue();
// evals to 2147483647
int maxValue = (Integer) parser.parseExpression("0x7FFFFFFF").getValue();
boolean trueValue = (Boolean) parser.parseExpression("true").getValue();
Object nullValue = parser.parseExpression("null").getValue();
```

##2.list

```
// evaluates to a Java list containing the four numbers 
List numbers = (List) parser.parseExpression("{1,2,3,4}").getValue(context); 
 List listOfLists = (List) parser.parseExpression("{{'a','b'},{'x','y'}}").getValue(context);

```

##3.map

```
// evaluates to a Java map containing the two entries 
Map inventorInfo = (Map) parser.parseExpression("{name:'Nikola',dob:'10-July-1856'}").getValue(context); 
Map mapOfMaps = (Map) parser.parseExpression("{name:{first:'Nikola',last:'Tesla'},dob:{day:10,month:'July',year:1856}}").getValue(context);

```

## 4.array

```
int[] numbers1 = (int[]) parser.parseExpression("new int[4]").getValue(context); 
 // Array with initializer int[] numbers2 = (int[]) parser.parseExpression("new int[]{1,2,3}").getValue(context); 
 // Multi dimensional array 
int[][] numbers3 = (int[][]) parser.parseExpression("new int[4][5]").getValue(context);

```

##5.方法调用
```
// string literal, evaluates to "bc" 
String c = parser.parseExpression("'abc'.substring(2, 3)").getValue(String.class); 
 // evaluates to true 
boolean isMember = parser.parseExpression("isMember('Mihajlo Pupin')").getValue(        societyContext, Boolean.class);

```

##6.变量

```

Inventor tesla = new Inventor("Nikola Tesla", "Serbian"); 

StandardEvaluationContext context = new StandardEvaluationContext(tesla); context.setVariable("newName", "Mike Tesla"); 

 parser.parseExpression("Name = #newName").getValue(context); 

 System.out.println(tesla.getName()) // "Mike Tesla"

```



##7.注册方法

要注册方法

```

public abstract class StringUtils {

    public static String reverseString(String input) {

        StringBuilder backwards = new StringBuilder();

        for (int i = 0; i < input.length(); i++)

            backwards.append(input.charAt(input.length() - 1 - i));

        }

        return backwards.toString();

    }

}

```

使用方法

```

ExpressionParser parser = new SpelExpressionParser();

StandardEvaluationContext context = new StandardEvaluationContext();

context.registerFunction("reverseString",

    StringUtils.class.getDeclaredMethod("reverseString", new Class[] { String.class }));

String helloWorldReversed = parser.parseExpression(

    "#reverseString('hello')").getValue(context, String.class);

```



##8.引用bean

```

ExpressionParser parser = new SpelExpressionParser();

StandardEvaluationContext context = new StandardEvaluationContext();

context.setBeanResolver(new MyBeanResolver());



// This will end up calling resolve(context,"foo") on MyBeanResolver during evaluation

Object bean = parser.parseExpression("@foo").getValue(context);

```

# 在项目中使用

在spring中**@Value**注解支持spEL表达式，下面两个注解是等效的：

```

 @Resource(name="testService")

 public TestService testService;

```

```

@Value("#{@testService}")

public TestService testService;

```












