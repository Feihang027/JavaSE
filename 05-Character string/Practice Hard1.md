# 转换罗马数字
## 题目描述
转换罗马数字
键盘录入一个字符串要求1:长度为小于等于9
要求2:只能是数字
将内容变成罗马数字
下面是阿拉伯数字跟罗马数字的对比关系
I-1、II-2、III-3、IV-4、V-5、VI-6、VII-7、VIII-8、IX-9
注意点
罗马数字里面是没有0的如果键盘录入的数字包含0，可以变成""(长度为0的字符串)


## Java 实现代码

```java
import java.util.Scanner;

public class RomanConverter {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String input = "";
        
        // 输入验证循环
        while (true) {
            System.out.println("请输入数字字符串 (长度≤9，仅含数字)：");
            input = sc.next();
            
            if (checkInput(input)) {
                break;
            } else {
                System.out.println("输入不合法，请重新输入！");
            }
        }
        
        // 转换并输出结果
        String roman = convertToRoman(input);
        System.out.println("转换结果：" + roman);
    }

    // 输入校验方法
    private static boolean checkInput(String str) {
        if (str.length() > 9) return false;
        return str.matches("\\d+");  // 正则表达式验证纯数字
    }

    // 数字转换核心方法
    private static String convertToRoman(String numStr) {
        StringBuilder sb = new StringBuilder();
        String[] romanMap = {"", "I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX"};

        for (char c : numStr.toCharArray()) {
            int num = Character.getNumericValue(c);
            if (num == 0) continue;  // 跳过0的转换
            if (num >= 1 && num <= 9) {
                sb.append(romanMap[num]);
            }
        }
        return sb.toString();
    }
}
