
# Java 方法进阶

## 方法中的变量重名与 this 关键字

有时候我们的方法中可能会出现一些与成员变量重名的变量:

```java
// 我们希望使用这个方法，来为当前对象设定名字
void setName(String name) {
    name = name; // 实际是方法参数赋值给自己，没有效果
}
```

我们来测试一下:

```java
public static void main(String[] args) {
    Person p = new Person();
    p.setName("小明");
    System.out.println(p.name); // 输出结果仍为 null
}
```

**解释：** 当出现重名的时候，会优先使用作用域最近的变量，这里就是方法参数的 `name`。

为了解决这个问题，我们可以使用 `this` 关键字来明确表示类的成员变量：

```java
void setName(String name) {
    this.name = name;
}
```

如果方法内没有变量出现重名的情况，可以不使用 `this`：

```java
String getName() {
    return name;
}
```

---

## 方法重载（Overloading）

有些时候，方法的参数类型或数量可能会不同。方法重载允许我们定义多个同名但参数不同的方法。

```java
int sum(int a, int b) {
    return a + b;
}

double sum(double a, double b) {
    return a + b;
}
```

### 调用示例：

```java
Person p = new Person();
System.out.println(p.sum(10, 20));      // 输出：30
System.out.println(p.sum(1.5, 2.2));    // 输出：3.7
```

**注意：** 仅仅返回类型不同，不构成重载。例如以下写法是错误的：

```java
int sum(int a, int b) { return a + b; }
double sum(int a, int b) { return a + b; } // 错误！
```

---

## 方法之间的调用

方法之间是可以相互调用的：

```java
void test() {
    System.out.println("我是 test");
}

void say() {
    test();
}
```

**注意：** 方法之间不能无限互相调用，否则会导致栈溢出。

## 递归调用（Recursion）

方法可以调用自己：

```java
void test() {
    test(); // 会导致栈溢出
}
```

为了避免栈溢出，必须设定终止条件。例如求 1 到 n 的和：

```java
int test(int n) {
    if (n == 0) return 0;
    return test(n - 1) + n;
}
```
