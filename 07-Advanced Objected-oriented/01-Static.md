
# static 关键字详解

## static 是什么？

`static` 表示**静态**，是 Java 中的一个修饰符，可以用来修饰：
- 成员方法
- 成员变量

## 一、static 修饰成员变量（静态变量）

### 特点：
- 被该类**所有对象共享**
- **不属于对象，属于类**
- 随着**类的加载而加载**，**优先于对象存在**

### 调用方式：
- 推荐：`类名.变量名`
- 也可：`对象名.变量名`（不推荐）

---

## 二、static 修饰成员方法（静态方法）

### 特点：
- 多用在**测试类和工具类**
- Javabean 类中很少使用

### 调用方式：
- 推荐：`类名.方法名()`
- 也可：`对象名.方法名()`（不推荐）

---

## 三、常见类分类

- **Javabean 类**：用来描述一类事物。例如：`Student`、`Teacher`、`Dog`、`Cat`
- **测试类**：用来检查其他类是否书写正确，带有 `main` 方法，是程序入口
- **工具类**：帮我们做一些事情的类。不是用来描述一类事物的

---

## 四、工具类示例：ArrayUtil

### 工具类：

```java
public class ArrayUtil {
    // 私有化构造方法，防止外部创建对象
    private ArrayUtil() {}

    // 打印整型数组
    public static String printArray(int[] arr) {
        StringBuilder sb = new StringBuilder();
        sb.append("[");
        for (int i = 0; i < arr.length; i++) {
            if (i == arr.length - 1) {
                sb.append(arr[i]);
            } else {
                sb.append(arr[i]).append(",");
            }
        }
        sb.append("]");
        return sb.toString();
    }

    // 获取浮点数组的平均值
    public static double getAverage(double[] arr) {
        double sum = 0;
        for (int i = 0; i < arr.length; i++) {
            sum += arr[i];
        }
        return sum / arr.length;
    }
}
```

### 测试类：

```java
public class TestDemo {
    public static void main(String[] args) {
        int[] arr1 = {1, 2, 3, 4, 5};
        String str = ArrayUtil.printArray(arr1);
        System.out.println(str); // [1,2,3,4,5]

        double[] arr2 = {1.1, 3.7, 4.6, 5.3, 2.8};
        double average = ArrayUtil.getAverage(arr2);
        System.out.println(average); // 平均值
    }
}
```

---

## 五、static 的注意事项

- **静态方法中只能访问静态成员**（static 不能访问非 static）
- **非静态方法可以访问所有成员**（既可访问 static，也可访问非 static）
- 静态随着**类的加载而加载**
- 非静态是与对象相关的（如 student 的 name）
- 静态方法中**没有 this 关键字**
