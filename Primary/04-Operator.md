# 🔗 Java 关系与逻辑运算符详解

在 Java 中，我们经常需要判断变量之间的大小关系或多个条件是否同时满足，这时候就用到了 **关系运算符** 和 **逻辑运算符**。

---

## 1️⃣ 关系运算符（Comparison Operators）

关系运算符用于比较两个值，返回一个布尔值 `true` 或 `false`。

| 运算符 | 含义       | 示例        | 返回值 |
|--------|------------|-------------|--------|
| `>`    | 大于       | `a > b`     | `true` / `false` |
| `<`    | 小于       | `a < b`     | `true` / `false` |
| `==`   | 等于       | `a == b`    | `true` / `false` |
| `!=`   | 不等于     | `a != b`    | `true` / `false` |
| `>=`   | 大于等于   | `a >= b`    | `true` / `false` |
| `<=`   | 小于等于   | `a <= b`    | `true` / `false` |

### 示例：

```java
public class Main {
    public static void main(String[] args) {
        int a = 10, b = 20;
        boolean result = a > b;
        System.out.println(result); // false
    }
}

## 2️⃣ 逻辑运算符（Logical Operators）

逻辑运算符用来连接多个条件表达式，最终结果也是一个布尔值。

| 运算符 | 含义   | 示例               | 说明             |
|--------|--------|--------------------|------------------|
| `&&`   | 逻辑与 | `a > 0 && a < 100` | 全部为真才为真   |
| `||`   | 逻辑或 | `a < 0 \|\| a > 10`| 有一个为真就为真 |
| `!`    | 逻辑非 | `!(a > 5)`         | 结果取反         |

---

### ✅ 示例：逻辑与（AND）

```java
public class Main {
    public static void main(String[] args) {
        int a = 10;
        boolean result = a > 5 && a < 15;
        System.out.println(result); // true
    }
}

## 3️⃣ 逻辑或（OR）

逻辑或运算符 `||`，表示“只要有一个为真，整体为真”。

```java
public class Main {
    public static void main(String[] args) {
        int a = -9;
        boolean result = a < 0 || a > 10;
        System.out.println(result); // true
    }
}

## 4️⃣ 逻辑非（NOT）

逻辑非运算符 `!` 表示“取反操作”。

- 若表达式原本为 `true`，加上 `!` 后为 `false`
- 若原本为 `false`，加上 `!` 后变为 `true`

### 示例：

```java
public class Main {
    public static void main(String[] args) {
        int a = 10;
        boolean result = !(a > 5);
        System.out.println(result); // false
    }
}

## 5️⃣ 三元运算符（Ternary Operator）

三元运算符是一种简洁的条件判断语法，用来根据条件表达式的真假返回不同的结果。

---

### 🧩 基本语法：

```java
条件 ? 值1 : 值2;

如果条件为 true，返回 值1
如果条件为 false，返回 值2

示例代码：
public class Main {
    public static void main(String[] args) {
        int a = 10;
        char b = a > 10 ? 'A' : 'B';
        System.out.println(b); // 输出 B
    }
}