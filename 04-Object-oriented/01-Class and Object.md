## 🔹 什么是面向对象

- **面向**：拿、找
- **对象**：能干活的东西
- **面向对象编程（OOP）**：拿东西过来做对应的事情

---

## 🔸 类 和 对象
- **类（设计图）**：对象共同特征的描述
- **对象**：真实存在的具体东西
- 在 Java 中，必须先设计类，才能获得对象。

---

### ✅ 如何得到类的对象

```java
类名 对象名 = new 类名();

Phone p = new Phone();
```

---

### ✅ 如何使用对象

- 访问属性：`对象名.成员变量`
- 访问行为：`对象名.方法名(...)`

---

## 📱 示例：手机类

```java
public class Phone {
    // 属性
    String brand;
    double price;

    // 行为
    public void call() {
        System.out.println("手机在打电话");
    }

    public void playGame() {
        System.out.println("手机在玩游戏");
    }
}
```

### 📱 测试类

```java
public class PhoneTest {
    public static void main(String[] args) {
        // 创建手机的对象
        Phone p = new Phone();

        // 给手机赋值
        p.brand = "小米";
        p.price = 1999.98;

        // 获取手机对象中的值
        System.out.println(p.brand);
        System.out.println(p.price);

        // 调用手机中的方法
        p.call();
        p.playGame();

        // 再创建一个对象
        Phone p2 = new Phone();
        p2.brand = "苹果";
        p2.price = 8999;

        p2.call();
        p2.playGame();
    }
}
```

---

## 💡 定义类的注意事项

- 用来描述一类事物的类，称为 **JavaBean 类**。
- JavaBean 类中**不写 main 方法**。
- 编写 `main` 方法的类，叫做**测试类**，用于创建 JavaBean 类的对象并调用。

### 命名规范

- 类名首字母建议大写，使用驼峰命名法，**见名知意**。
- 一个 `.java` 文件可以定义多个类，但 **只能有一个 public 类**，并且 public 类的类名必须与文件名一致。
- 实际开发建议：**一个类一个文件**。

### 成员变量完整定义格式

```java
修饰符 数据类型 变量名称 = 初始化值;
```

- 一般无需指定初始化值，存在默认值。

---

## 💖 练习：女朋友类

### 📄 GirlFriend.java

```java
public class GirlFriend {
    // 属性
    String name;
    int age;
    String gender;

    // 行为
    public void sleep() {
        System.out.println("女朋友在睡觉");
    }

    public void eat() {
        System.out.println("女朋友在吃饭");
    }
}
```

### 🧪 GirlFriendTest.java

```java
public class GirlFriendTest {
    public static void main(String[] args) {
        // 创建女朋友对象
        GirlFriend gf1 = new GirlFriend();
        gf1.name = "小诗诗";
        gf1.age = 18;
        gf1.gender = "萌妹子";

        // 获取属性值
        System.out.println(gf1.name);
        System.out.println(gf1.age);
        System.out.println(gf1.gender);

        // 调用方法
        gf1.eat();
        gf1.sleep();
    }
}
```

---
