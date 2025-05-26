## 📝 需求说明
求平方根
输入一个大于等于2的整数，求它的平方根的整数部分（小数部分舍去）。

## 💻 Java 实现

```java
import java.util.Scanner;

public class SquareRoot {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入一个整数:");
        int number = sc.nextInt();

        for (int i = 1; i <= number; i++) {
            if (i * i == number) {
                System.out.println(i + " 就是 " + number + " 的平方根");
                break;
            } else if (i * i > number) {
                System.out.println((i - 1) + " 是 " + number + " 平方根的整数部分");
                break;
            }
        }
    }
}
```