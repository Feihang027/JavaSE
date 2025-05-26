# 字符串旋转匹配算法

## 问题描述
给定两个字符串A和B，判断A是否可以通过若干次左旋转操作变为B。  
**旋转操作**：将字符串最左边的字符移动到最右边  
**示例**：A = "abcde" → 旋转1次 → "bcdea"

---

## 错误分析
原始代码存在以下关键问题：

1. **语法错误**  
   - 使用`string`代替`String`（Java区分大小写）
   - 循环变量定义错误`inti` → `int i`

2. **逻辑缺陷**  
   - 未处理原始字符串直接匹配的情况（旋转0次）
   - 缺少字符串长度校验

---

## 正确实现

### Java代码
```java
public class RotationChecker {
    public static void main(String[] args) {
        String strA = "abcde";
        String strB = "cdeab";
        System.out.println(check(strA, strB)); // 输出: true
    }

    public static boolean check(String A, String B) {
        // 长度不同直接返回false
        if (A.length() != B.length()) return false;

        // 检查所有旋转可能性（包括0次旋转）
        for (int i = 0; i < A.length(); i++) {
            if (A.equals(B)) return true;
            A = rotate(A); // 每次循环执行一次旋转
        }
        return false;
    }

    private static String rotate(String s) {
        return s.substring(1) + s.charAt(0);
    }
}