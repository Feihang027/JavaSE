# 无限循环
//for格式的无限循环
for(;;){
System.out.println("学习");
}

//while格式的无限循环
while(true){
System.out.println("学习”);
}
//注意事项
//无限循环的下面不能再写其他代码了，因为循环永远停不下来，那么下面的代码永远执行不到

# 跳转循环
//跳过某一次循环
for(int i=1;i<= 5;i++){
  if(i == 3){
continue;//结束本次循环，继续下次循环。
  }
}

System.out.println("小老虎在吃第"+i+"个包子");

# 纸张折叠次数计算

## 📝 问题描述

假设你有一张厚度为 0.1 毫米的纸，想通过不断对折，使其厚度超过珠穆朗玛峰的高度（8844430 毫米）。请问至少要折多少次？

## ✅ 思路分析

- 每次对折，纸张厚度会变为原来的两倍；
- 使用 `while` 循环：因为我们不知道要折叠几次，只知道结束条件（厚度超过山峰高度）；
- 每折叠一次，次数计数器 `count` 加 1。

## 💻 示例代码

```java
public class FoldMountain {
    public static void main(String[] args) {
        // 1. 定义变量记录山峰高度（单位：毫米）
        double height = 8844430;

        // 2. 定义变量记录纸张初始厚度
        double paper = 0.1;

        // 3. 定义变量记录折叠次数
        int count = 0;

        // 4. 当纸张厚度小于山峰高度时继续折叠
        while (paper < height) {
            paper *= 2;    // 每次折叠，厚度翻倍
            count++;       // 次数+1
        }

        // 5. 输出最终折叠次数
        System.out.println("需要折叠次数：" + count);
    }
}
