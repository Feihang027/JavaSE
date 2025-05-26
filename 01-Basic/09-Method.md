## 方法的基本概念

- 方法是程序中最小的执行单元。
- 方法必须先定义，再调用。

---

## 方法的定义与调用

### 示例1：简单调用
```java
public static void main(String[] args) {
    // 调用方法
    printGFInfo();
}

public static void printGFInfo() {
    System.out.println("小惠惠");
    System.out.println("萌妹子");
    System.out.println("18岁");
}
```

### 示例2：嵌套方法调用
```java
public static void main(String[] args) {
    System.out.println("a");
    method1();
    System.out.println("b");
}

public static void method1() {
    method2();
    System.out.println("c");
}

public static void method2() {
    System.out.println("d");
    System.out.println("e");
}
```

**输出结果：** `a d e c b`

---

## 带参数的方法定义与调用

### 单个参数

**格式：**
```java
public static void 方法名(参数) { ... }
```

**示例：**
```java
public static void method(int number) { ... }
```

### 多个参数

**格式：**
```java
public static void 方法名(参数1, 参数2) { ... }
```

**示例：**
```java
public static void getSum(int number1, int number2) { ... }
```

### 调用方法

- 单个参数：`方法名(参数);`
- 多个参数：`方法名(参数1, 参数2);`

**注意：** 参数的数量与类型必须一一对应，否则程序报错。

### 形参与实参

- **形参**：方法定义中的参数，如：`int num1, int num2`
- **实参**：方法调用时传入的实际参数，如：`getSum(a, b)`

---

## 带返回值的方法

### 格式：
```java
public static 返回值类型 方法名(参数) {
    // 方法体
    return 返回值;
}
```

### 示例：
```java
public static int getSum(int a, int b) {
    int c = a + b;
    return c;
}
```

### 调用方式

- 直接调用：`方法名(实参);`
- 赋值调用：`int result = 方法名(实参);`
- 输出调用：`System.out.println(方法名(实参));`

---

## 方法的注意事项

- 方法不调用就不会执行。
- 方法之间是平级关系，不能互相嵌套定义。
- 方法的编写顺序与执行顺序无关。
- 返回值为 `void` 的方法可以省略 `return`，若使用 `return` 后面不能跟返回值。
- `return` 之后不能有任何语句（无效代码）。

---

## 方法的重载（Overloading）

在同一个类中定义多个同名方法，**参数不同**（个数、类型、顺序），构成方法重载。

### 示例：构成重载
```java
public static float fn(int a) { ... }
public static int fn(int a, int b) { ... }
```

### 示例：不构成重载（仅返回值不同）
```java
public static void fn(int a) { ... }
public static int fn(int a) { ... } // 错误
```

### 自定义重载：比较两个整数是否相同（兼容 byte, short, int, long）

```java
public static void compare(byte b1, byte b2) {
    System.out.println(b1 == b2);
}

public static void compare(short s1, short s2) {
    System.out.println(s1 == s2);
}

public static void compare(int i1, int i2) {
    System.out.println(i1 == i2);
}

public static void compare(long n1, long n2) {
    System.out.println(n1 == n2);
}
```

---

## 基本数据类型 vs 引用数据类型

- **基本数据类型**：变量中存储的是实际数据值。
- **引用数据类型**：变量中存储的是内存地址（如数组），还有new出来的。

---

## 方法的值传递

- 对于基本数据类型：传递的是值，形参改变不会影响实参。

---

## 方法练习

### 1. 数组遍历

```java
public static void printArr(int[] arr) {
    System.out.print("[");
    for (int i = 0; i < arr.length; i++) {
        if (i == arr.length - 1) {
            System.out.print(arr[i]);
        } else {
            System.out.print(arr[i] + ", ");
        }
    }
    System.out.println("]");
}
```

### 2. 求数组最大值

```java
public static int getMax(int[] arr) {
    int max = arr[0];
    for (int i = 1; i < arr.length; i++) {
        if (arr[i] > max) max = arr[i];
    }
    return max;
}
```

### 3. 判断是否存在

```java
public static boolean contains(int[] arr, int number) {
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] == number) return true;
    }
    return false;
}
```

- **return**：用于结束整个方法。
- **break**：用于结束循环或 switch。

### 4. 数组复制

```java
public static int[] copyOfRange(int[] arr, int from, int to) {
    int[] newArr = new int[to - from];
    int index = 0;
    for (int i = from; i < to; i++) {
        newArr[index] = arr[i];
        index++;
    }
    return newArr;
}
```

---

