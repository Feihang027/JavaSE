# 🐇 斐波那契数列（Fibonacci Sequence）

## 📖 简介

斐波那契数列（Fibonacci sequence），又称黄金分割数列、兔子数列，由意大利数学家莱昂纳多·斐波那契在研究兔子繁殖问题时首次提出：

**数列形式：**
1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, ...
从第三项起，每项数字都是前两项之和。
**数学定义如下：**
- F(0) = 0  
- F(1) = 1  
- F(n) = F(n - 1) + F(n - 2)（n ≥ 2, n ∈ ℕ）
斐波那契数列广泛应用于数学、物理、生物、艺术、建筑等领域。

---

## 💻 Java 示例代码

该程序可以计算出斐波那契数列中第 `n` 个数的值：

```java
public class Fibonacci {
    public static void main(String[] args) {
        int target = 10; // 要获取的第 target 个斐波那契数（第 10 项）
        int result;
        int a = 1;
        int b = 1;
        int temp;

        for (int i = 1; i < target - 1; i++) {
            temp = a + b;
            a = b;
            b = temp;
        }

        result = b;
        System.out.println("第 " + target + " 个斐波那契数是: " + result);
    }
}
🧮 输出结果（示例）
第 10 个斐波那契数是: 55