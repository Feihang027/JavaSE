# 需求说明
定义方法实现随机产生一个5位的验证码

## 验证码格式:
长度为5
前四位是大写字母或者小写字母
最后一位是数字      


# 验证码规则说明
| 位置    | 要求           | 示例 |
| ------- | -------------- | ---- |
| 第1-4位 | 大小写字母混合 | AbC9 |
| 第5位   | 数字（0-9）    | xYz5 |

```java
import java.util.Random;

public class VerificationCodeGenerator {
    public static void main(String[] args) {
        // 生成并打印验证码
        System.out.println("生成的验证码：" + generateVerificationCode());
    }

    /**
     * 生成5位验证码（4字母 + 1数字）
     * @return 验证码字符串
     */
    public static String generateVerificationCode() {
        // 1. 创建包含大小写字母的数组
        char[] letters = new char[52];
        for(int i = 0; i < letters.length; i++) {
            if(i < 26) {
                // 小写字母 a-z（ASCII 97-122）
                letters[i] = (char)(97 + i);
            } else {
                // 大写字母 A-Z（ASCII 65-90）
                letters[i] = (char)(65 + i - 26);
            }
        }

        // 2. 生成前4位随机字母
        Random random = new Random();
        StringBuilder code = new StringBuilder();
        for(int i = 0; i < 4; i++) {
            int index = random.nextInt(letters.length);
            code.append(letters[index]);
        }

        // 3. 生成最后1位随机数字
        int number = random.nextInt(10); // 0-9
        code.append(number);

        return code.toString();
    }
}
---

 **输出示例**
```plaintext
生成的验证码：kVrM7
生成的验证码：pQSt3
生成的验证码：XGhn9