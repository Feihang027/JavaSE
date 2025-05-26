
# String 构造方法与字符串比较

## 创建 String 对象的两种方式

1. **直接赋值：**
```java
String name = "尼古拉斯·阿玮";
```

2. **new 构造：**
| 构造方法                         | 说明                             |
| -------------------------------- | -------------------------------- |
| `public String()`                | 创建空白字符串，不含任何内容     |
| `public String(String original)` | 根据传入的字符串，创建字符串对象 |
| `public String(char[] chs)`      | 根据字符数组，创建字符串对象     |
| `public String(byte[] chs)`      | 根据字节数组，创建字符串对象     |

### 示例代码：

```java
// 使用直接赋值
String s1 = "abc";
System.out.println(s1); // abc

// 使用 new 构造
String s2 = new String();
System.out.println("@" + s2 + "!"); // ""

// 根据字符串构造
String s3 = new String("abc");
System.out.println(s3); // abc

// 根据字符数组构造
char[] chs = {'a', 'b', 'c', 'd'};
String s4 = new String(chs);
System.out.println(s4); // abcd

// 根据字节数组构造
byte[] bytes = {97, 98, 99, 100};
String s5 = new String(bytes);
System.out.println(s5); // abcd
```

## 字符串对象比较

```java
public class StringDemo {
    public static void main(String[] args) {
        String s1 = new String("abc"); // 在堆中创建
        String s2 = "abc"; // 在字符串常量池中创建

        // == 比较地址值
        System.out.println(s1 == s2); // false

        // equals 比较内容
        boolean result1 = s1.equals(s2);
        System.out.println(result1); // true

        // equalsIgnoreCase 忽略大小写比较
        String s3 = "Abc";
        boolean result2 = s1.equalsIgnoreCase(s3);
        System.out.println(result2); // true
    }
}
```
## 遍历字符串
public char charAt(intindex): 根据索引返回字符
public int length(): 返回此字符串的长度
数组的长度:数组名.length
字符串的长度:字符串对象.length()


### 示例代码：
```java
//1.键盘录入一个字符串
Scanner sc=new scanner(system.in);
System.out.println("请输入一个字符串");
String str = sc.next();
//2.统计---计数器思想
//定义三个计数器
int bigcount =0;
int:smallCount=0;
int numberCount=0;
for(inti=0;i<str.length();i++){
//i 依次表示字符串中的每一个索引
char c=str.charAt(i);
if(c >='a'&& c<='z'){
//char类型的变量在参与计算的时候自动类型提升为int 查询ascii码表smallCount++;}else if(c >='A’&&c<='Z'){bigCount++;}else if(c >='0’&& c<= '9'){
numberCount++
//3.输出打印
System.out.println("小写字母有:"+ smallcount +"个");
System.out.println("大写字母有:"+ bigcount +“个");
System.out.println("数字字母有:"+numbercount +"个");
```
### 示例代码（字符串拼接）：
```java
public static string arrTostring(int[] arr){
  if(arr == null){
    return "”；
  }
  if(arr.length == 0){
    return "[]";
  }

  String result ="[";
  //当代码执行到这里表示什么?//表示数组不是nu11，也不是长度为0的
  for(inti=0;i< arr.length;i++){
  //i 索引 arr[i]元素
  if(i == arr.length-1){
    result = result + arr[i];
  }else{
    result = result + arr[i]+",
//此时拼接右括号
  result = result +"]";
  return result;
 }
}
```

### 示例代码（字符串反转）：
```java
public static void main(string[]args){
  String result =reverser( str:"abc");
  System.out.println(result);
}  
static string reverser(string str){
  String result =""；
  for(int i=str.length()-1;i >=0;i--){
    //i 依次表示字符串中的每一个索引 (倒着的)
    char Ic = str.charAt(i);
    result=result +c;
  return result;
} 
```
## 字符串截取
截取String substring(int beginindex, int endlndex)
注意点:包头不包尾，包左不包右，只有返回值才是截取的小串
String substring(int beginIndex)  截取到末尾

### 示例代码
//1.获取一个手机号码        String phoneNumber="13112349468"
//2.截取手机号码前面三位    String start=phoneNumber.substring(0,3);
//3.截取手机号码后面四位    String end=phoneNumber.substring(7);
//4.拼接                   String result = start + “****"+ end;
//5.打印                   System.out.println(result); //131****9468


## 替换
String replace(旧值,新值)替换
注意点:只有返回值才是替换之后的结果

### 示例代码
//1.获取到说的话
string talk="你玩的真好，以后不要再玩了，TMD"
//2.把里面的敏感词TMD替换为***
String result =talkreplace( target: "TMD", replacement: "***")
//3.打印结果
System.out.println(result); //你玩的真好，以后不要再玩了，***.


### 特别说明
#### Scanner 键盘录入字符串与直接赋值的区别：
```java
Scanner sc = new Scanner(System.in);
System.out.println("请输入一个字符串：");
String str1 = sc.next(); // 用户输入 abc

String str2 = "abc";

System.out.println(str1 == str2); // false
```

- `str1`：通过 `Scanner.next()` 获取，本质上是 `new String("abc")`，位于堆内存。
- `str2`：直接赋值的字符串，位于字符串常量池中。
- 因此，`==` 比较的是地址，不相等。

> 建议字符串内容比较统一使用 `.equals()` 或 `.equalsIgnoreCase()`，不要用 `==`。
