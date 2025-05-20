## 🧠 游戏规则
逢七过
从1到100报数：
- 如果数字是 7 的倍数、或者个位是7、或者十位是7，需要说“过”；
- 否则，正常报数。

## 💻 Java 实现

```java
public class PassSeven {
    public static void main(String[] args) {
        for (int i = 1; i <= 100; i++) {
            if (i % 10 == 7 || i / 10 % 10 == 7 || i % 7 == 0) {
                System.out.println("过");
                continue;
            }
            System.out.println(i);
        }
    }
}
```