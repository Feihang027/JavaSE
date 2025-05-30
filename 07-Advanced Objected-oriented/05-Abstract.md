# Java 抽象类与抽象方法详解

## 一、抽象方法

抽象方法：将共性的行为（方法）抽取到父类之后，由于每个子类执行的内容不同，所以在父类中不能确定具体的方法体，此时该方法定义为抽象方法。

### 抽象方法的定义格式：
```java
public abstract 返回值类型 方法名(参数列表);
```

## 二、抽象类

抽象类：如果一个类中存在抽象方法，那么该类必须声明为抽象类。

### 抽象类的定义格式：
```java
public abstract class 类名 {}
```

### 注意事项：
- 抽象类不能实例化
- 抽象类中不一定有抽象方法，但有抽象方法的类一定是抽象类
- 抽象类可以有构造方法
- 抽象类的子类：
  - 要么重写抽象类中的所有抽象方法
  - 要么也是抽象类

## 三、抽象类（Abstract Class）

### 1. 定义与特点

声明方式：使用 `abstract` 关键字修饰类

核心特性：

- ❌ 不可实例化
- ✅ 可被继承
- ✅ 可包含具体方法
- ✅ 可包含抽象方法
- ✅ 可包含成员变量

```java
// 抽象类示例
abstract class Shape {
    protected String color;
    
    public Shape(String color) {
        this.color = color;
    }
    
    public String getColor() {
        return color;
    }
    
    public abstract double area();
}
```

### 2. 抽象类的作用

| 作用     | 说明                   | 示例                             |
| -------- | ---------------------- | -------------------------------- |
| 代码复用 | 提供公共实现           | 在 Shape 中实现 getColor()       |
| 定义规范 | 强制子类实现特定行为   | area() 要求所有子类必须实现      |
| 封装变化 | 隔离不变部分与可变部分 | 颜色处理固定，面积计算可变       |
| 模板方法 | 定义算法框架           | 父类中定义绘图流程，子类实现细节 |

## 四、抽象方法（Abstract Method）

### 1. 定义与特点

声明方式：使用 `abstract` 关键字修饰方法

核心特性：

- ❌ 没有方法体
- ✅ 必须在抽象类中
- ✅ 强制子类实现
- ❌ 不能是静态的
- ❌ 不能是私有的

```java
abstract class Animal {
    public abstract void makeSound();
    public abstract void move(String destination);
}
```

### 2. 抽象方法的意义

- 定义契约：明确子类必须提供的功能
- 实现多态：通过方法重写实现运行时绑定
- 强制实现：确保子类实现关键功能

## 五、完整使用示例

### 1. 抽象类继承体系

```java
abstract class Vehicle {
    private String model;
    
    public Vehicle(String model) {
        this.model = model;
    }
    
    public void startEngine() {
        System.out.println(model + " engine started");
    }
    
    public abstract void drive();
}

class Car extends Vehicle {
    public Car(String model) {
        super(model);
    }
    
    @Override
    public void drive() {
        System.out.println("Driving car on road");
    }
}

class Boat extends Vehicle {
    public Boat(String model) {
        super(model);
    }
    
    @Override
    public void drive() {
        System.out.println("Sailing boat on water");
    }
}
```

### 2. 客户端使用

```java
public class Main {
    public static void main(String[] args) {
        Vehicle[] vehicles = {
            new Car("Toyota"),
            new Boat("Yamaha")
        };
        
        for (Vehicle v : vehicles) {
            v.startEngine();
            v.drive();
            System.out.println("----------");
        }
    }
}
```

### 输出结果：

```
Toyota engine started
Driving car on road
----------
Yamaha engine started
Sailing boat on water
----------
```
