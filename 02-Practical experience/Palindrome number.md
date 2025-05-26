# 回文数判断

## 📝 需求描述

给定一个整数 `x`，如果 `x` 是回文整数，打印 `true`，否则打印 `false`。

> 回文数：正序和倒序读都是一样的整数。例如：
> - ✅ `121` 是回文数；
> - ❌ `123` 不是回文数。

## ✅ 核心思路

- 将整数反转后与原始值进行比较；
- 若反转后的数字与原数相等，则为回文数。

## 💻 示例代码

```java
public class PalindromeCheck {
    public static void main(String[] args) {
        // 1. 定义数字
        int x = 12345;

        // 2. 记录原始值
        int temp = x;

        // 3. 记录反转后的结果
        int num = 0;

        // 4. 反转数字
        while (x != 0) {
            int ge = x % 10;        // 获取最后一位
            x = x / 10;             // 去掉最后一位
            num = num * 10 + ge;    // 将新位加到反转数字后面
        }

        // 5. 打印结果
        System.out.println("反转后的数字: " + num);
        System.out.println("是否是回文数: " + (num == temp));
    }
}
