
# 方法创建与使用

前面我们介绍了类的定义以及对象的创建和使用。现在我们的类有了属性，我们可以为创建的这些对象设定不同的属性值，比如每个人的名字、性别、年龄都不一样。

只不过光有属性还不行，对象还需要具有一定的行为，比如人可以行走、跳跃、思考等。对象的行为通过 **定义方法** 实现（在 C 语言中叫做函数）。

## 🔧 方法的定义

方法是语句的集合，是为了完成某件事情而存在的。

- 有些方法完成后有返回值，比如计算两个数字的和。
- 有些方法没有返回值，比如只是打印内容。

```java
// 没有返回值的方法
void 方法名() {
    // 方法体
}
```

例如：

```java
public class Person {
    String name;
    int age;
    String sex;

    void hello() {
        System.out.println("我叫" + name + "今年" + age + "岁了!");
    }
}
```

调用方法：

```java
public static void main(String[] args){
    Person p = new Person();
    p.name = "小明";
    p.age = 18;
    p.hello();
}
```

输出：

```
我叫小明今年18岁了!
```

## ➕ 带返回值的方法

方法可以有参数，也可以有返回值：

```java
int sum(int a, int b) {
    int c = a + b;
    return c;
}
```

调用方法：

```java
public static void main(String[] args) {
    Person p = new Person();
    int result = p.sum(10, 20);
    System.out.println(result);  // 输出：30
}
```

## 🧠 return 的规则

- `return` 表示方法执行完毕并返回结果。
- `return` 后的代码不会再执行（不可达语句会报错）。

```java
int sum(int a, int b) {
    return a + b;
    // System.out.println("这行代码不可达"); // 报错
}
```

- 如果有分支语句，所有路径必须有返回值：

```java
int test(int a) {
    if (a > 10) {
        return 666;
    } else {
        return 888;
    }
}
```

- `void` 方法也可以使用 `return` 来结束方法：

```java
void test(int a) {
    if (a == 10) return;
    System.out.println("Hello World!");
}
```

## 🔄 参数传递：值传递 vs 引用传递

### 🔁 基本类型是值传递

```java
void swap(int a, int b) {
    int tmp = a;
    a = b;
    b = tmp;
}

public static void main(String[] args) {
    int a = 5, b = 9;
    swap(a, b);
    System.out.println("a = " + a + ", b = " + b); // a=5, b=9
}
```

**说明**：方法内的 a 和 b 是拷贝，原始变量没有改变。

### 🧾 引用类型是引用地址的传递

```java
void modify(Person person) {
    person.name = "lbwnb";
}

public static void main(String[] args) {
    Person p = new Person();
    p.name = "小明";
    modify(p);
    System.out.println(p.name); // 输出：lbwnb
}
```

**说明**：引用类型变量的值是对象的地址。方法中修改的是同一个对象。

---

✅ **小结**：
- 方法是类的行为。
- 方法可以带参数，也可以有返回值。
- 基本类型参数是值传递，引用类型参数是地址的值传递。
