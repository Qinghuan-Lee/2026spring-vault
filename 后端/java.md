# Java 语法入门介绍

Java 是一种面向对象的编程语言。让我为你介绍最核心的语法概念：

## 1. 基本结构

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

- **类（Class）**: Java 代码必须写在类里面
- **main 方法**: 程序的入口点，JVM 从这里开始执行

## 2. 数据类型

**基本类型**:

- `int` - 整数 (32位)
- `long` - 长整数 (64位)
- `double` - 浮点数
- `boolean` - 布尔值 (true/false)
- `char` - 字符
- `byte`, `short`, `float` - 其他数值类型

```java
int age = 25;
double price = 19.99;
boolean isActive = true;
String name = "Alice";  // 字符串（引用类型）
```

## 3. 运算符

```java
// 算术运算
int sum = 10 + 5;      // 加
int diff = 10 - 5;     // 减
int product = 10 * 5;  // 乘
int quotient = 10 / 5; // 除

// 比较运算
boolean equal = (10 == 5);    // false
boolean notEqual = (10 != 5); // true
boolean greater = (10 > 5);   // true

// 逻辑运算
boolean and = true && false;  // false
boolean or = true || false;   // true
boolean not = !true;          // false
```

## 4. 条件语句

```java
// if-else
if (age >= 18) {
    System.out.println("成年");
} else {
    System.out.println("未成年");
}

// switch
switch (day) {
    case 1:
        System.out.println("星期一");
        break;
    case 2:
        System.out.println("星期二");
        break;
    default:
        System.out.println("其他");
}
```

## 5. 循环

```java
// for 循环
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}

// while 循环
int count = 0;
while (count < 5) {
    System.out.println(count);
    count++;
}

// for-each 循环（遍历数组/集合）
int[] numbers = {1, 2, 3, 4, 5};
for (int num : numbers) {
    System.out.println(num);
}
```

## 6. 数组

```java
// 声明和初始化
int[] scores = new int[5];
int[] numbers = {10, 20, 30, 40, 50};
String[] names = {"Alice", "Bob", "Charlie"};

// 访问元素
System.out.println(numbers[0]); // 10
numbers[1] = 25; // 修改元素
```

## 7. 方法（函数）

```java
// 无返回值
public void greet(String name) {
    System.out.println("你好，" + name);
}

// 有返回值
public int add(int a, int b) {
    return a + b;
}

// 调用方法
greet("Alice");
int result = add(5, 3);
```

## 8. 类和对象

```java
public class Person {
    // 属性（成员变量）
    private String name;
    private int age;
    
    // 构造方法
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    // 方法
    public void introduce() {
        System.out.println("我是 " + name + "，今年 " + age + " 岁");
    }
    
    // Getter 和 Setter
    public String getName() {
        return name;
    }
    
    public void setName(String name) {
        this.name = name;
    }
}

// 创建对象
Person person = new Person("张三", 25);
person.introduce();
```

## 9. 访问修饰符

- `public` - 公开，任何地方都能访问
- `private` - 私有，只在类内部访问
- `protected` - 受保护，同包和子类可访问
- 默认（无修饰符）- 同包可访问

## 10. 常用字符串操作

```java
String str = "Hello";

// 字符串长度
int len = str.length(); // 5

// 字符串拼接
String result = str + " World"; // "Hello World"
String result2 = str.concat(" Java");

// 常用方法
str.toUpperCase();      // "HELLO"
str.toLowerCase();      // "hello"
str.contains("ell");    // true
str.indexOf("l");       // 2
str.substring(0, 3);    // "Hel"
str.replace("o", "0");  // "Hell0"
```

## 11. 注释

```java
// 单行注释

/* 
   多行注释
   可以跨越多行
*/

/**
 * 文档注释
 * 用于生成 JavaDoc 文档
 */
```

---

这些是 Java 最基础的语法。如果你需要深入了解某个具体概念（比如继承、接口、异常处理等），我可以详细解释。你有特别想学习的部分吗？