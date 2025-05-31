# Java接口与抽象类学习笔记

## 接口的基本概念

接口是一种规则。抽象类代表一类实物，而接口代表行为。比如动物类包含兔子类，狗类，青蛙类，而有一个游泳接口表示动物的行为。

### 接口的定义和使用

```java
public interface 接口名 {}
```

- 接口不能实例化。
- 接口和类之间是实现关系，通过 `implements` 表示：

```java
public class 类名 implements 接口名 {}
```

- 接口的子类（实现类）要么重写接口中的所有抽象方法，要么是抽象类。
- 实现关系可以单实现，也可以多实现：

```java
public class 类名 implements 接口名1, 接口名2 {}
```

- 实现类还可以在继承一个类的同时实现多个接口：

```java
public class 类名 extends 父类 implements 接口名1, 接口名2 {}
```

## 接口示例：动物

```java
public abstract class Animal {
    private String name;
    private int age;

    public Animal() {}

    public Animal(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
    public int getAge() { return age; }
    public void setAge(int age) { this.age = age; }

    public abstract void eat();
}

public interface Swim {
    void swim();
}

public class Rabbit extends Animal {
    public Rabbit() {}

    public Rabbit(String name, int age) {
        super(name, age);
    }

    @Override
    public void eat() {
        System.out.println("兔子在吃胡萝卜");
    }
}

public class Frog extends Animal implements Swim {
    public Frog() {}

    public Frog(String name, int age) {
        super(name, age);
    }

    @Override
    public void eat() {
        System.out.println("青蛙在吃虫子");
    }

    @Override
    public void swim() {
        System.out.println("青蛙在蛙泳");
    }
}

public class Dog extends Animal implements Swim {
    public Dog() {}

    public Dog(String name, int age) {
        super(name, age);
    }

    @Override
    public void eat() {
        System.out.println("狗吃骨头");
    }

    @Override
    public void swim() {
        System.out.println("狗刨");
    }
}

public class Test {
    public static void main(String[] args) {
        Frog f = new Frog("小青", 1);
        System.out.println(f.getName() + f.getAge());
        f.eat();
        f.swim();

        Rabbit r = new Rabbit("小白", 2);
        System.out.println(r.getName() + r.getAge());
        r.eat();
    }
}
```

## 接口中成员的特点

- 成员变量：只能是常量（`public static final`）
- 构造方法：无
- 成员方法：只能是抽象方法（`public abstract`）

### 接口的新特性

- JDK8：可以定义有方法体的默认方法、静态方法
- JDK9：可以定义私有方法

## 类与接口的关系

- 类与类：继承关系，只能单继承，可以多层继承
- 类与接口：实现关系，可以单实现、多实现，或继承类同时实现接口
- 接口与接口：继承关系，可以单继承、多继承

## 综合案例

### 案例分析

- 抽象类：Person、Sporter、Coach
- 接口：English
- 具体类：PingPangSporter、BasketballSporter、PingPangCoach、BasketballCoach

### 案例代码

```java
public class Person {
    private String name;
    private int age;

    public Person() {}

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
    public int getAge() { return age; }
    public void setAge(int age) { this.age = age; }
}

public abstract class Sporter extends Person {
    public Sporter() {}

    public Sporter(String name, int age) {
        super(name, age);
    }

    public abstract void study();
}

public abstract class Coach extends Person {
    public Coach() {}

    public Coach(String name, int age) {
        super(name, age);
    }

    public abstract void teach();
}

public interface English {
    void speakEnglish();
}

public class PingPangSporter extends Sporter implements English {
    public PingPangSporter() {}

    public PingPangSporter(String name, int age) {
        super(name, age);
    }

    @Override
    public void speakEnglish() {
        System.out.println("乒乓球运动员在说英语");
    }

    @Override
    public void study() {
        System.out.println("乒乓球运动员在学习如何打乒乓球");
    }
}

public class BasketballSporter extends Sporter {
    public BasketballSporter() {}

    public BasketballSporter(String name, int age) {
        super(name, age);
    }

    @Override
    public void study() {
        System.out.println("篮球运动员在学习如何打篮球");
    }
}

public class PingPangCoach extends Coach implements English {
    public PingPangCoach() {}

    public PingPangCoach(String name, int age) {
        super(name, age);
    }

    @Override
    public void teach() {
        System.out.println("乒乓球教练正在教如何打乒乓球");
    }

    @Override
    public void speakEnglish() {
        System.out.println("乒乓球教练在学习说英语");
    }
}

public class BasketballCoach extends Coach {
    public BasketballCoach() {}

    public BasketballCoach(String name, int age) {
        super(name, age);
    }

    @Override
    public void teach() {
        System.out.println("篮球教练正在教如何打篮球");
    }
}

public class Test {
    public static void main(String[] args) {
        PingPangSporter pps = new PingPangSporter("刘诗雯", 23);
        System.out.println(pps.getName() + " " + pps.getAge());
        pps.study();
        pps.speakEnglish();
    }
}
```

## 接口中的默认、静态和私有方法

```java
public interface Inter {
    void method();

    default void show() {
        System.out.println("接口中的默认方法: show");
    }

    static void showStatic() {
        System.out.println("接口中的静态方法");
        showHelper();
    }

    private static void showHelper() {
        System.out.println("记录程序运行细节（静态私有方法）");
    }

    private void showPrivate() {
        System.out.println("记录程序运行细节（普通私有方法）");
    }
}
```

## 适配器设计模式

适配器设计模式是为了解决接口与实现类之间的不匹配问题。

### 步骤：

1. 编写中间类 `XXXAdapter` 实现接口，对抽象方法空实现
2. 真正的实现类继承该适配器类并重写所需方法
3. 适配器类一般使用 `abstract` 修饰，防止被直接实例化
