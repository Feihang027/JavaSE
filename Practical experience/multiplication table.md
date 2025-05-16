# 📐 九九乘法表（Multiplication Table）

## 💡 程序说明

使用 Java 语言编写九九乘法表，通过双重 `for` 循环控制行列输出，输出格式整齐，且避免重复（只输出上三角部分）。

---

## 💻 示例代码

```java
public class MultiplicationTable {
    public static void main(String[] args) {
        for (int i = 1; i <= 9; i++) {
            for (int j = 1; j <= 9; j++) {
                if (j > i) break; // 控制列数，保证输出上三角部分
                System.out.printf("%d x %d = %2d  ", i, j, i * j);
            }
            System.out.println(); // 换行
        }
    }
}
