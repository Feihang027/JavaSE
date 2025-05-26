## 🎲 游戏需求（猜数字）

生成一个 0~9 的随机数，打印 100 次看看分布。

## 💻 Java 实现

```java
import java.util.Random;

public class GuessBasic {
    public static void main(String[] args) {
        Random r = new Random();
        for (int i = 0; i < 100; i++) {
            int number = r.nextInt(10); // 0~9
            System.out.println(number);
        }
    }
}
```


## 📝 范围说明（猜数字升级版）

生成 1~100 范围内的随机数，提示用户不断猜直到猜中。

秘诀：
用来生成任意数到任意数之间的随机数7~15
让这个范围头尾都减去一个值，让这个范围从0开始 -7   0~8   尾巴+1
8+1=9
//3.最终的结果，再加上第一步减去的值。
Random r= new Random();
int number =r.nextInt( bound:9)+7;   //7~ 15

## 💻 Java 实现

```java
import java.util.Random;
import java.util.Scanner;

public class GuessGame {
    public static void main(String[] args) {
        Random r = new Random();
        int number = r.nextInt(100) + 1; // 1~100
        Scanner sc = new Scanner(System.in);
        int count = 0;

        while (true) {
            System.out.println("请输入你要猜的数字:");
            int guessNumber = sc.nextInt();
            count++;

            if (guessNumber > number) {
                System.out.println("大了");
            } else if (guessNumber < number) {
                System.out.println("小了");
            } else {
                System.out.println("猜中了！");
                break;
            }

            if (count == 3) {
                System.out.println("次数用尽，答案是：" + number);
                break;
            }
        }
    }
}
```