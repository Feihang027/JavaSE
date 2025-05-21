# Java 数组详解
---

## 数组基本概念
- **定义**：数组是一种容器，用于存储**相同数据类型**的多个值。
- **隐式转换规则**：
  - `int[]` 可存储 `byte`/`short`/`int`
  - `double[]` 可存储 `byte`/`short`/`int`/`long`/`float`/`double`
- **推荐做法**：容器类型与存储数据类型保持一致。
- **格式**：`数据类型[] 数组名`  
  范例：`int[] array;`

---

## 数组的动态初始化
格式
数据类型[] 数组名 = new 数据类型[数组长度];

示例
int[] arr = new int[3];
String[] names = new String[50];

// 添加元素
names[0] = "zhangsan";
names[1] = "lisi";

// 默认初始化值
System.out.println(names[2]);  // null（引用类型默认值）

默认初始化值
数据类型	默认值
整数类型	0
小数类型	0.0
字符类型	\u0000
布尔类型	false
引用类型	null

## 数组的静态初始化
### 完整格式
```java
数据类型[] 数组名 = new 数据类型[]{元素1, 元素2, ...};

简化格式
数据类型[] 数组名 = {元素1, 元素2, ...};

// 需求1：存储5个学生的年龄
int[] arr1 = new int[]{11, 12, 13, 14};
int[] arr2 = {11, 12, 13, 14};

// 需求2：存储3个学生的姓名
String[] arr3 = new String[]{"zhangsan", "lisi", "wangwu"};
String[] arr4 = {"zhangsan", "lisi", "wangwu"};

// 需求3：存储4个学生的身高
double[] arr5 = new double[]{1.93, 1.75, 1.73, 1.81};
double[] arr6 = {1.93, 1.75, 1.73, 1.81};


练习
1. 求最值
java
int[] arr = {33, 5, 22, 44, 55};
int max = arr[0];
for (int i = 1; i < arr.length; i++) {
    if (arr[i] > max) max = arr[i];
}
System.out.println("最大值：" + max);  // 55
关键点：max 初始化为数组第一个元素，循环从索引1开始


2. 求和并统计
// 生成随机数组
int[] arr = new int[10];
Random r = new Random();
for (int i = 0; i < arr.length; i++) {
    arr[i] = r.nextInt(100) + 1;
}

// 求和与平均值
int sum = 0;
for (int num : arr) sum += num;
int avg = sum / arr.length;

// 统计比平均值小的个数
int count = 0;
for (int num : arr) {
    if (num < avg) count++;
}
System.out.println("比平均值小的元素个数：" + count);


3. 交换数据
java
int[] arr = {1, 2, 3, 4, 5};
for (int i = 0, j = arr.length - 1; i < j; i++, j--) {
    int temp = arr[i];
    arr[i] = arr[j];
    arr[j] = temp;
}
// 输出：5 2 3 4 1


4. 打乱顺序
java
int[] arr = {1, 2, 3, 4, 5};
Random r = new Random();
for (int i = 0; i < arr.length; i++) {
    int randomIndex = r.nextInt(arr.length);
    int temp = arr[i];
    arr[i] = arr[randomIndex];
    arr[randomIndex] = temp;
}

Java内存分配
区域	         功能描述
栈	           存储方法调用和局部变量（如 main 方法运行时进入栈）
堆	           存储对象和数组（通过 new 创建的内容）
方法区	        存储可运行的 class 文件
本地方法栈	    JVM 使用操作系统功能时使用
寄存器	        供 CPU 使用


数组的引用特性
共享修改：当多个数组指向同一内存空间时，任一数组修改数据会影响所有引用。
int[] arr1 = {1, 2, 3};
int[] arr2 = arr1;
arr2[0] = 100;
System.out.println(arr1[0]);  // 输出 100