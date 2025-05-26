
# 构造方法

我们接着来看一种比较特殊的方法：**构造方法**。

前面我们创建对象，都是直接使用 `new` 关键字就能直接搞定了，但是我们发现，对象在创建之后，各种属性都是默认值。那么能否实现在对象创建时就为其指定名字、年龄、性别呢？

## 什么是构造方法

构造方法（构造器）可以在对象创建时进行处理。实际上每个类都有一个默认的构造方法。

```java
public class Person {
    String name;
    int age;
    String sex;

    public Person() {
        // 构造方法
    }
}
```

构造方法的特点：
- **没有返回值类型**（连 `void` 也不写）
- **方法名与类名相同**
- 每个类默认有一个无参构造方法（如果没有手动写）

## 自定义构造方法

```java
public class Person {
    String name;
    int age;
    String sex;

    // 自定义无参构造方法
    Person() {
        name = "小明";
        age = 18;
        sex = "男";
    }
}
```

构造方法会在 `new` 的时候自动执行：

```java
public static void main(String[] args) {
    Person p = new Person(); // 调用无参构造方法
    System.out.println(p.name); // 输出：小明
}
```

## 带参构造方法

```java
public class Person {
    String name;
    int age;
    String sex;

    Person(String name, int age, String sex) {
        this.name = name;
        this.age = age;
        this.sex = sex;
    }
}
```

注意：如果我们自定义了构造方法，**默认的无参构造方法就不再自动生成**，需要自己写。
构造方法的重载
带参构造方法，和无参数构造方法，两者方法名相同，但是参数不同，这叫做构造方法的重载
推荐的使用方式
无论是否使用，都手动书写无参数构造方法，和带全部参数的构造方法

```java
public static void main(String[] args) {
    Person p = new Person("小明", 18, "男");
    System.out.println(p.name);
}