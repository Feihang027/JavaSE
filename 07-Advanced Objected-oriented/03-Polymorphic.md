# Java 多态详解

## 什么是多态？

多态指同一种类型的对象，在不同时刻表现出不同的形态。

### 多态的表现形式：
```java
父类类型 对象名 = 子类对象;
```

### 多态的前提：
- 必须有继承关系
- 有父类引用指向子类对象
- 有方法重写

例如：
```java
Fu f = new Zi();
```

## 示例

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

    public void show() {
        System.out.println(name + " " + age);
    }
}

public class Student extends Person {
    @Override
    public void show() {
        System.out.println("学生的信息为: " + getName() + "，" + getAge());
    }
}

public class Teacher extends Person {
    @Override
    public void show() {
        System.out.println("老师的信息为: " + getName() + "，" + getAge());
    }
}

public class Administrator extends Person {
    @Override
    public void show() {
        System.out.println("管理员的信息为: " + getName() + "，" + getAge());
    }
}

public class Test {
    public static void main(String[] args) {
        Student s = new Student();
        s.setName("张二");
        s.setAge(18);

        Teacher t = new Teacher();
        t.setName("王建国");
        t.setAge(30);

        Administrator admin = new Administrator();
        admin.setName("管理员");
        admin.setAge(35);

        register(s);
        register(t);
        register(admin);
    }

    public static void register(Person p) {
        p.show();
    }
}
```

## 多态调用成员的特点

- **变量调用**：编译看左边，运行也看左边
- **方法调用**：编译看左边，运行看右边

```java
Animal a = new Dog();
System.out.println(a.name); // 输出父类Animal的变量
a.show(); // 调用的是子类Dog中重写的方法
```

## Java 多态的全面分析

### 优势

1. **代码可扩展性**  
   - 添加新类型不影响现有代码，符合开闭原则

2. **接口统一性**  
   - 简化调用逻辑，降低耦合度

3. **代码可维护性**  
   - 减少 if-else，逻辑集中化

#### 对比：

**不使用多态（维护困难）**：
```java
public void makeSound(Animal animal) {
    if (animal instanceof Dog) {
        ((Dog) animal).bark();
    } else if (animal instanceof Cat) {
        ((Cat) animal).meow();
    }
}
```

**使用多态（易于维护）**：
```java
public void makeSound(Animal animal) {
    animal.makeSound();
}
```

### 弊端

- **理解复杂性**：需跳转多个类理解实际执行方法
- **设计限制**：
  - 子类必须符合里氏替换原则
  - 父类变动可能影响子类行为
- **访问限制**：
  - 无法直接访问子类特有成员（向上转型后）
  - 向下转型有风险（可能抛出 ClassCastException）

