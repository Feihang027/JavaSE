# Java 集合框架基础指南

## 集合与数组的对比

| **特性** | 数组               | 集合                               |
| -------- | ------------------ | ---------------------------------- |
| 长度     | 固定长度           | 动态扩容                           |
| 存储类型 | 基本类型、引用类型 | 只能存储引用类型（基本类型需包装） |
| 功能扩展 | 功能有限           | 提供丰富操作方法                   |


## 泛型的作用
1. **限定集合存储的数据类型**  
   明确指定集合中允许存储的元素类型
2. **避免类型转换错误**  
   编译时检查类型安全性，消除强制类型转换

---

## 二、基本数据类型与包装类对应表

| 基本类型  | 包装类      |
| --------- | ----------- |
| `byte`    | `Byte`      |
| `short`   | `Short`     |
| `char`    | `Character` |
| `int`     | `Integer`   |
| `long`    | `Long`      |
| `float`   | `Float`     |
| `double`  | `Double`    |
| `boolean` | `Boolean`   |

---

## 三、集合核心操作方法

### 增删改查方法汇总

| 方法签名                      | 功能说明           | 返回值类型     |
| ----------------------------- | ------------------ | -------------- |
| `boolean add(E e)`            | 添加元素到集合末尾 | 操作是否成功   |
| `boolean remove(Object o)`    | 删除指定元素       | 是否找到并删除 |
| `E remove(int index)`         | 删除指定索引元素   | 被删除元素     |
| `E set(int index, E element)` | 修改指定位置元素   | 被替换的旧元素 |
| `E get(int index)`            | 获取指定位置元素   | 元素对象       |
| `int size()`                  | 获取集合元素数量   | 当前元素个数   |

---

## 四、代码示例

### 基础操作演示
```java
// 1. 创建集合
ArrayList<String> list = new ArrayList<>();

// 2. 添加元素
list.add("aaa");
list.add("aaa");
list.add("bbb");
list.add("ccc");

// 3. 删除元素
boolean result1 = list.remove("aaa");  // true（删除第一个匹配项）
boolean result2 = list.remove("ddd");  // false（元素不存在）
String removed = list.remove(2);       // 删除索引2元素返回"ccc"

// 4. 修改元素
String oldVal = list.set(1, "ddd");    // 返回原值"bbb"

// 5. 查询元素
String first = list.get(0);            // "aaa"

// 6. 遍历集合
for(int i=0; i<list.size(); i++){
    System.out.println(list.get(i));
}
集合遍历练习
java
// 1. 创建集合
ArrayList<String> list = new ArrayList<>();

// 2. 添加元素
list.add("点赞了吗？");
list.add("收藏了吗？");
list.add("投币了吗？");
list.add("转发了吗？");

// 3. 格式化遍历
System.out.print("[");
for(int i=0; i<list.size(); i++){
    if(i == list.size()-1){
        System.out.print(list.get(i));
    }else{
        System.out.print(list.get(i) + ", ");
    }
}
System.out.println("]");

/* 输出结果：
[点赞了吗？, 收藏了吗？, 投币了吗？, 转发了吗？]
*/



