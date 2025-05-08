# 🧪 Java 入门程序：Hello World

## 🎯 学习目标

- 学会创建 `main` 方法和打印语句
- 理解 `print` 和 `println` 的区别
- 熟悉 Java 注释和大小写规范

---

## 📌 示例代码

```java
public class Main {
    public static void main(String[] args) {
        // print 是不换行打印，println 是换行打印
        System.out.println("Hello World");
        System.out.println("YYDS");
        // Hello World
        // YYDS

        // 注意需要区分大小写：Java 严格区分大小写
        // 如果不遵守命名规则，会看到红色波浪线报错

        // 多行注释的写法：
        /*
           这是一个多行注释
           可以写多行说明文字
         */
    }
}
