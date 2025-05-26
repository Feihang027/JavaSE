# Java 字符串处理工具：StringBuilder 与 StringJoiner

## StringBuilder 概述

### 基本特性
- **可变容器**：`StringBuilder` 是一个可变的字符串容器，内容可动态修改
- **效率优势**：相比直接字符串拼接，能显著提高操作效率（尤其在循环场景）

### 适用场景
1. 字符串频繁拼接
2. 字符串反转操作

---

## StringBuilder 核心方法

### 构造方法
| 方法签名                           | 说明                             | 示例                                           |
| ---------------------------------- | -------------------------------- | ---------------------------------------------- |
| `public StringBuilder()`           | 创建空白可变字符串对象           | `StringBuilder sb = new StringBuilder();`      |
| `public StringBuilder(String str)` | 根据字符串内容创建可变字符串对象 | `StringBuilder sb = new StringBuilder("abc");` |

### 成员方法
| 方法签名           | 说明                     | 返回值类型      |
| ------------------ | ------------------------ | --------------- |
| `append(任意类型)` | 添加数据并返回对象本身   | `StringBuilder` |
| `reverse()`        | 反转容器内容             | `StringBuilder` |
| `length()`         | 返回字符个数             | `int`           |
| `toString()`       | 转换为不可变 String 对象 | `String`        |

---

## 代码示例

### 基础操作示例
```java
// 1. 创建对象
StringBuilder sb = new StringBuilder("abc");

// 2. 添加元素（链式编程）
sb.append(1).append(2.3).append(true);

// 3. 反转内容
sb.reverse();

// 4. 获取长度
int len = sb.length();
System.out.println(len); // 输出：9

// 5. 转换为字符串
String str = sb.toString();
System.out.println(str); // 输出：eurT3.21cba

// 6. 链式编程
StringBuilder sb = new StringBuilder()
    .append("aaa")
    .append("bbb")
    .append("ccc");
System.out.println(sb); // 输出：aaabbbccc

