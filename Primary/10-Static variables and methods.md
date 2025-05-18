# Java 中的静态变量和静态方法

## 一、类与对象的回顾

类是对象的模板，一个类可以拥有多种属性和行为。通过类创建的每个对象，都会具有类中定义的属性和行为。构造方法可以用于设定对象创建时的初始化过程。

## 二、静态的概念

静态（`static`）表示 **属于类本身** 的成员，而不是某个具体的对象。  
静态成员在类加载时分配，不依赖于对象的创建。所有对象 **共享同一个静态成员**。

> 一个对象修改了静态变量的值，其他对象读取到的也是被修改后的值。

---

## 三、静态变量示例

```java
public class Person {
    String name;
    int age;
    String sex;
    static String info; // 静态变量
}


测试静态变量：
public static void main(String[] args) {
    Person p1 = new Person();
    Person p2 = new Person();

    p1.info = "杰哥你干嘛";
    System.out.println(p2.info); // 输出：杰哥你干嘛
}

推荐使用类名访问静态变量：
public static void main(String[] args) {
    Person.info = "让我看看";
    System.out.println(Person.info); // 输出：让我看看
}


四、静态方法
static void test() {
    System.out.println("我是静态方法");
}
静态方法 属于类本身，而不是对象：![静态方法示意图](Image/static.png)

因此：
不能访问非静态成员变量。
不能使用 this 关键字。
可以访问静态变量。
static String info;

static void test() {
    System.out.println("静态变量的值为: " + info);
}


五、静态代码块
static String info;
static {
    info = "测试"; // 静态代码块初始化静态变量
}
静态代码块用于在类加载时初始化静态变量。


六、静态内容的加载时机
类在首次使用时被 JVM 加载，静态内容也会在类加载时初始化。

类会在以下情况被加载：
访问类的静态变量，或为静态变量赋值。
new 关键字创建类的实例（隐式加载）。
调用类的静态方法。
子类初始化时。
（其他情况将在反射部分介绍）
所有被标记为静态的内容，会在类加载阶段就初始化完成，早于任何对象的创建