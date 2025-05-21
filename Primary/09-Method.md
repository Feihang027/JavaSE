## 方法基本概念
- **方法的作用**：程序中最小的执行单元，用于封装重复逻辑。
- **核心规则**：
  - 方法必须先**定义**再**调用**。
  - 方法可以嵌套调用（方法中调用其他方法）。

---

## 方法的定义与调用
### 基本语法
```java
public static 返回值类型 方法名(参数列表) {
    // 方法体
}

示例1：无参方法
```java
public static void main(String[] args) {
    printGFInfo();  // 调用方法
}

public static void printGFInfo() {
    System.out.println("小惠惠");
    System.out.println("萌妹子");
    System.out.println("18岁");
}
输出结果：
小惠惠  
萌妹子  
18岁


示例2：方法嵌套调用
```java
public static void main(String[] args) {
    System.out.println("a");  // 1. 输出 a
    method1();                // 2. 调用 method1
    System.out.println("b");  // 5. 输出 b
}

public static void method1() {
    method2();                // 3. 调用 method2
    System.out.println("c");  // 4. 输出 c
}

public static void method2() {
    System.out.println("d");  // 3.1 输出 d
    System.out.println("e");  // 3.2 输出 e
}
输出结果：
a  
d  
e  
c  
b