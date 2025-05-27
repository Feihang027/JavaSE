
# Java 继承详解

## 继承概念
Java 提供关键字 `extends`，用于类与类之间建立继承关系：

```java
public class Student extends Person {}
```

- `Student` 称为子类（派生类）
- `Person` 称为父类（基类或超类）

## 使用继承的好处
- 提高代码复用性
- 子类可在父类基础上增强功能

## 继承使用时机
- 类与类之间存在共性内容
- 满足“子类是父类中的一种”

## 继承的特点
- 只支持单继承
- 支持多层继承
- 所有类最终都继承自 `Object`

### 示例继承体系设计

#### 基类：Animal

```java
public class Animal {
    public void eat() {
        System.out.println("吃东西");
    }
    public void drink() {
        System.out.println("喝水");
    }
}
```

#### 子类：Cat 和 Dog

```java
public class Cat extends Animal {
    public void catchMouse() {
        System.out.println("猫在抓老鼠");
    }
}

public class Dog extends Animal {
    public void lookHome() {
        System.out.println("狗在看家");
    }
}
```

#### 更具体的类

```java
public class Ragdoll extends Cat {}
public class LiHua extends Cat {}

public class Husky extends Dog {
    public void breakHome() {
        System.out.println("哈士奇在拆家");
    }
}

public class Teddy extends Dog {
    public void touch() {
        System.out.println("泰迪又在蹭我的腿了~");
    }
}
```

### 成员变量访问特点：就近原则

```java
public class Fu {
    String name = "Fu";
}

public class Zi extends Fu {
    String name = "Zi";
    public void ziShow() {
        String name = "zishow";
        System.out.println(name);        // zishow
        System.out.println(this.name);   // Zi
        System.out.println(super.name);  // Fu
    }
}
```

## 方法重写（Override）

### 需求背景
当父类方法不能满足子类需求，子类可以重写父类的方法。

### 格式
```java
@Override
public void 方法名(...) {
    // 子类新实现
}
```

### 示例

```java
public class Dog {
    public void eat() {
        System.out.println("狗在吃狗粮");
    }
    public void drink() {
        System.out.println("狗在喝水");
    }
    public void lookHome() {
        System.out.println("狗在看家");
    }
}
```

#### 哈士奇重写和扩展

```java
public class Husky extends Dog {
    public void breakHome() {
        System.out.println("哈士奇又在拆家了");
    }
}
```

#### 沙皮狗重写吃方法

```java
public class SharPei extends Dog {
    @Override
    public void eat() {
        super.eat();
        System.out.println("狗啃骨头");
    }
}
```

#### 中华田园犬完全重写吃方法

```java
public class ChineseDog extends Dog {
    @Override
    public void eat() {
        System.out.println("吃剩饭");
    }
}
```

### 测试类

```java
public class DogTest {
    public static void main(String[] args) {
        Husky h = new Husky();
        h.eat();
        h.drink();
        h.lookHome();
        h.breakHome();

        ChineseDog cd = new ChineseDog();
        cd.eat();
        cd.drink();
        cd.lookHome();
    }
}
```

## 构造方法访问特点

- 子类不会继承父类构造方法
- 子类构造方法默认会调用 `super()`
- 必须放在第一行
- 若想调用父类有参构造，必须手动写 `super(...)`

## this 和 super 使用总结

| 功能         | this        | super        |
| ------------ | ----------- | ------------ |
| 成员变量访问 | this.变量   | super.变量   |
| 成员方法访问 | this.方法() | super.方法() |
| 构造方法访问 | this(...)   | super(...)   |

- `this`：表示当前对象的地址值
- `super`：代表父类存储空间

---
