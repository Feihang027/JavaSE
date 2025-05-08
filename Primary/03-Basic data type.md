# 🔢 Java 基本数据类型详解

Java 中的基本数据类型一共分为四类八种：整型、浮点型、字符型、布尔型。

---

## 1️⃣ 整数类型（整型）

| 类型  | 大小     | 字节数 | 取值范围 |
|-------|----------|--------|----------------------------|
| byte  | 8 位     | 1 字节 | -128 ~ 127                |
| short | 16 位    | 2 字节 | -32,768 ~ 32,767          |
| int   | 32 位    | 4 字节 | -2,147,483,648 ~ 2,147,483,647 |
| long  | 64 位    | 8 字节 | -9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807 |

### 示例：

```java
public class Main {
    public static void main(String[] args) {
        short a = 10;
        int b = a; // 自动类型提升（short -> int）
        System.out.println(b);
    }
}
💡 Java 中小范围的整数值可以赋值给大范围的数据类型（自动类型转换）。

⚠️ 注意：整数常量默认是 int 类型
public class Main {
    public static void main(String[] args) {
        // 错误示例：数字太大超出了 int 范围
        // long a = 922337203685477580;

        // 正确做法：添加 L 后缀表示 long 类型常量
        long a = 922337203685477580L;
        System.out.println(a);
    }
}
💡 推荐使用大写 L，避免和数字 1 混淆。

✅ 数字增强可读性：使用下划线 _
public class Main {
    public static void main(String[] args) {
        int a = 1_000_000; // 表示 1000000，提高可读性
        System.out.println(a);
    }
}


2️⃣ 浮点类型（小数）
类型	大小	字节数	精度
float	32 位	4 字节	单精度
double	64 位	8 字节	双精度（默认）
float f = 3.14f;  // float 类型常量需要加 f 或 F
double d = 3.14159; // double 是默认类型


3️⃣ 字符类型（char）
char 类型用于表示单个字符（英文、中文、标点等）占用 2 字节（16 位）
范围：0 ~ 65535
使用单引号 '' 表示一个字符
示例：使用 ASCII 编码表示字符
public class Main {
    public static void main(String[] args) {
        char c = 65; // 对应字符 'A'
        System.out.println(c); // 输出 A
    }
}


4️⃣ 布尔类型（boolean）
用于表示真假状态
只有两个取值：true 和 false
占用空间未固定，依赖 JVM 实现
常用于流程控制、条件判断等逻辑判断场景
示例：
public class Main {
    public static void main(String[] args) {
        boolean b = true;
        System.out.println(b); // 输出 true
    }
}
⚠️ Java 不允许用数字代替布尔值（不同于 C/C++）
