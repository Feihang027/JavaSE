# 💐 寻找水仙花数（Narcissistic Number）

## 📘 什么是水仙花数？

水仙花数（Narcissistic number）也被称为：

- 超完全数字不变数（Pluperfect Digital Invariant, **PPDI**）
- 自恋数
- 自幂数
- 阿姆斯特朗数（**Armstrong Number**）

水仙花数是指一个 **三位数**，它的每个位上的数字的 **立方和** 等于它本身。

例如：
1³ + 5³ + 3³ = 1 + 125 + 27 = 153


因此，153 是一个水仙花数。

---

## 💻 示例 Java 代码

以下程序用于找出所有三位数中的水仙花数：

```java
public class Flower {
    public static void main(String[] args) {
        for (int i = 100; i < 1000; i++) {
            int a = i % 10;         // 个位
            int b = i / 10 % 10;    // 十位
            int c = i / 100;        // 百位

            if (a * a * a + b * b * b + c * c * c == i) {
                System.out.println(i + " 是水仙花数");
            }
        }
    }
}

✅ 输出结果
程序执行后会输出如下水仙花数：
153 是水仙花数
370 是水仙花数
371 是水仙花数
407 是水仙花数
