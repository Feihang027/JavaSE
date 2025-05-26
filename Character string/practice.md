
# 金额转换与身份证信息查询

## 金额转换

```java
// 1. 键盘录入一个金额
Scanner sc = new Scanner(System.in);
int money;
while (true) {
    System.out.println("请录入一个金额");
    money = sc.nextInt();
    if (money >= 0 && money <= 9999999) {
        break;
    } else {
        System.out.println("金额无效");
    }
}

// 定义一个变量用来表示钱的大写
String moneyStr = "";

// 2. 得到 money 里面的每一位数字
while (true) {
    // 从右往左获取数据
    int ge = money % 10;
    String capitalNumber = getCapitalNumber(ge);
    moneyStr = capitalNumber + moneyStr;
    money = money / 10;
    if (money == 0) {
        break;
    }
}

// 3. 在前面补0，补齐7位
int count = 7 - moneyStr.length();
for (int i = 0; i < count; i++) {
    moneyStr = "零" + moneyStr;
}
System.out.println(moneyStr);

// 4. 插入单位
String[] arr = {"佰", "拾", "万", "仟", "佰", "拾", "元"};
String result = "";
for (int i = 0; i < moneyStr.length(); i++) {
    char c = moneyStr.charAt(i);
    result = result + c + arr[i];
}

// 5. 打印最终结果
System.out.println(result);

// 定义方法：数字转中文大写
public static String getCapitalNumber(int number) {
    String[] arr = {"零", "壹", "贰", "叁", "肆", "伍", "陆", "柒", "捌", "玖"};
    return arr[number];
}
```

---

## 身份证信息查询

```java
// 1. 定义一个字符串记录身份证号码
String id = "321281202001011234";

// 2. 获取出生年月日
String year = id.substring(6, 10);
String month = id.substring(10, 12);
String day = id.substring(12, 14);
System.out.println("人物信息为:");
System.out.println("出生年月日: " + year + "年" + month + "月" + day + "日");

// 3. 获取性别
char gender = id.charAt(16);
int num = gender - 48; // ASCII 转换
if (num % 2 == 0) {
    System.out.println("性别为: 女");
} else {
    System.out.println("性别为: 男");
}
```
