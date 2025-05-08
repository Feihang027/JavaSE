# 🧮 Java 变量与常量详解

## 🎯 学习目标

- 学会定义变量和常量
- 理解变量命名规则
- 掌握变量的赋值和输出
- 理解 `final` 修饰的常量含义

---

## 🔠 变量的声明

Java 中变量的基本声明格式：

```java
数据类型 变量名;
示例：
int a;

📝 命名规则（标识符）
✅ 可以使用	            字母（大小写）、数字、下划线 _、美元符号 $
🚫 不能以数字开头	        如 1abc 是非法命名
🚫 不可重复定义	          大小写敏感，如 A 和 a 是两个变量
🚫 不能包含特殊符号	      如空格、@、#、+、-、/ 等
✅ 建议	                使用有意义的英文单词，小写字母开头，如 age, score
🚫 禁止使用	              Java 关键字或保留字，如 int, true, false, class 等


🛑 Java 关键字列表（不能作为变量名）
abstract assert boolean break byte case catch char class const continue
default do double else enum extends final finally float for goto if
implements import instanceof int interface long native new package
private protected public return short static strictfp super switch
synchronized this throw throws transient try void volatile while


📌 变量赋值方式
✅ 1. 声明时赋值
public class Main {
    public static void main(String[] args) {
        int a = 10; // 定义变量并赋初值
    }
}


✅ 2. 声明后再赋值
public class Main {
    public static void main(String[] args) {
        int a;
        a = 10; // 稍后再赋值
    }
}


🖨️ 打印变量的值
public class Main {
    public static void main(String[] args) {
        int a = 666;
        System.out.println(a);   // 输出变量的值
        System.out.println(888); // 输出常量
    }
}


🔒 常量定义：使用 final
当变量值不希望被改变时，可以使用 final 关键字将其声明为常量：
public class Main {
    public static void main(String[] args) {
        final int a = 666;
        // a = 777; // ❌ 报错：无法为最终变量 a 分配值
    }
}
final 修饰的变量必须赋值一次；
常量一般使用全大写命名，例如：final double PI = 3.14;