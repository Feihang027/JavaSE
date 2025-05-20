# 👤 类和对象（Class and Object）

## 📘 类的概念

“类”的概念在现实生活中并不陌生。例如：

- 人类
- 鸟类
- 鱼类

所谓 **类（Class）**，就是对一类事物的描述，是一种 **抽象的、概念上的定义**。  
例如：

- “鸟类”泛指所有具有鸟类特征的动物。
- “人类”泛指所有具有人类基本属性的个体，尽管他们有着不同的性格、爱好、样貌，但都属于同一个类。

---

## 🧍 对象的概念

**对象（Object）** 是某一类事物 **实际存在的个体**，因此又被称为 **实例（Instance）**。

> 我们每一个人，都是“人类”这一类的一个具体实例。

---

## 🧠 总结

| 概念 | 含义 |
|------|------|
| 类（Class） | 抽象的定义，用来描述一类事物的共同特征 |
| 对象（Object） | 某个类的具体实例，真实存在于内存中的个体 |

---

> 在 Java 编程中，我们先通过“类”描述事物的特征和行为，再通过“对象”来实际使用这些特征和行为。




# 🏗️ 类的定义与对象的创建

## ✍️ 类的命名规则

在 Java 中定义类时，遵循以下规范：

- 一般使用英文单词或短语表示类名
- **首字母大写**
- 不使用特殊字符（如 `@`、`$`、`!` 等）

示例：

```java
public class Person {
    // 成员变量（属性）
    String name;  // 姓名
    int age;      // 年龄
    String sex;   // 性别
}



对象的创建
我们可以使用 new 关键字来创建类的实例（对象）：
public class Person {
    String name;
    int age;
    String sex;
}

public class Main {
    public static void main(String[] args) {
        // 使用 new 创建一个 Person 对象
        Person p = new Person();
    }
}
注意事项：
new 类名() 是创建对象的语法。
Person p = new Person(); 代表我们创建了一个具体的人




# 🧩 对象的使用（Using Objects）
## 🛠️ 如何访问对象
在创建了一个对象后，我们可以通过一个变量来引用这个对象：

```java
public static void main(String[] args) {
    int a = 10; // 基本类型，变量直接存储值

    // 创建一个 Person 类型的变量 p 来引用对象
    Person p = new Person(); // p 存放的是对象的引用
}




## 🎯 Java 对象的使用细节
---
### 🔁 对象引用的复制

当我们将一个对象变量赋值给另一个变量时，实际上是复制了引用地址，而不是复制整个对象
```java
public static void main(String[] args) {
    Person p1 = new Person();
    Person p2 = p1;

    System.out.println(p1 == p2); // true，两个变量引用的是同一个对象
}

如果两个变量分别指向不同的对象：
```java
public static void main(String[] args) {
    Person p1 = new Person();
    Person p2 = new Person();

    System.out.println(p1 == p2); // false，引用的是不同的对象
}





## 修改和访问对象的属性
我们可以通过对象的引用来访问和修改它的属性：
```java
public static void main(String[] args) {
    Person p = new Person();
    p.name = "小明";
    System.out.println(p.name); // 输出：小明
}

不同对象的属性互不影响：
```java
public static void main(String[] args) {
    Person p1 = new Person();
    Person p2 = new Person();

    p1.name = "小明";
    p2.name = "大明";

    System.out.println(p1.name); // 小明
    System.out.println(p2.name); // 大明
}




## ❗ 注意 null 引用
引用类型的变量可以赋值为 null，表示它当前不引用任何对象：

```java
public static void main(String[] args) {
    Person p = null;

    // 以下操作会抛出 NullPointerException（空指针异常）
    p.name = "小红";
    System.out.println(p.name);
}
⚠️ 空指针异常（NullPointerException）是 Java 中最常见的运行时错误之一





## 🧾 对象属性的默认值
当我们创建对象但没有对其属性进行赋值时，系统会赋予这些属性默认值：

```java
public static void main(String[] args) {
    Person p = new Person();
    System.out.println("name = " + p.name); // null
    System.out.println("age = " + p.age);   // 0
    System.out.println("sex = " + p.sex);   // null
}