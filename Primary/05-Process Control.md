# Java 流程控制语句学习笔记

## 选择结构

### if-else

`if-else` 语句就像两个分支，根据不同的判断情况来决定下一步的执行路径。这和我们之前学过的三元运算符有相似之处。

#### 多分支判断：`else-if`

如果需要判断多个分支，比如我们现在希望判断学生的成绩：

- 90 分以上：优秀
- 70 分以上：良好
- 60 分以上：及格
- 其他情况：不及格

可以使用 `else-if` 结构来完成：

```java
public class GradeChecker {
    public static void main(String[] args) {
        int score = 2;
        if (score >= 90)
            System.out.println("优秀");
        else if (score >= 70)
            System.out.println("良好");
        else if (score >= 60)
            System.out.println("及格");
        else
            System.out.println("不及格");
    }
}

if 的嵌套使用
如果希望进一步细分，比如不及格的学生中：
0-30 分补 Java
30-60 分补 C++

可以使用嵌套的 if：
public class NestedIf {
    public static void main(String[] args) {
        int score = 2;
        if (score < 60) { // 先判断不及格
            if (score > 30)
                System.out.println("学习 C++");
            else
                System.out.println("学习 Java");
        }
    }
}

# if 语句的注意点

## 1. 大括号的位置

- 大括号 `{` 的开头**可以另起一行书写**，但建议写在第一行的末尾，以提高代码可读性。

## 2. 单句代码时大括号可省略

- 如果 `if` 的语句体中**只有一句代码**，**大括号可以省略不写**。
- **建议：尽量不要省略大括号**，以防止后续维护中引起歧义或错误。

## 3. 判断布尔变量时不使用 `==`

- 如果判断的是一个 **布尔类型的变量**，**不要使用 `==` 来比较**。
- 正确写法：`if(flag)` 或 `if(!flag)`，而不是 `if(flag == true)`。

---

## 示例代码

```java
public class IfDemo2 {
    public static void main(String[] args) {
        // 示例1：判断数字是否大于等于10
        int number = 20;
        if (number >= 10) {
            int a = 100; // 1. 定义变量a，2. 给变量a赋值为100
            System.out.println("number大于等于10");
        }

        // 示例2：布尔变量判断
        boolean flag = false;
        if (flag) {
            System.out.println("flag的值为true");
        }
    }
}


2. switch 结构
switch 更适用于值的精准匹配，不能进行范围判断。例如，根据学生的等级（A/B/C）进行分班：
public class SwitchDemo {
    public static void main(String[] args) {
        char c = 'A';
        switch (c) {
            case 'A':
                System.out.println("去尖子班！准备冲刺 985 大学！");
                break;
            case 'B':
                System.out.println("去平行班！准备冲刺一本！");
                break;
            case 'C':
                System.out.println("去职高深造。");
                break;
            default:
                System.out.println("去读职高，分流。");
        }
    }
}

注意事项：
switch 不支持范围判断（如 score ≥ 90），适合对具体值进行判断；
每个 case 语句结束后，务必添加 break；
可使用 default 表示所有不满足 case 的情况。

嵌套使用示例
switch 结构中也可以嵌套 if 语句，例如：
public class NestedSwitchIf {
    public static void main(String[] args) {
        char c = 'A';
        switch (c) {
            case 'A':
                if (c == 'A') {
                    System.out.println("去尖子班！");
                }
                break;
            case 'B':
                System.out.println("去平行班！");
                break;
            default:
                System.out.println("去普通班！");
        }
    }
}
