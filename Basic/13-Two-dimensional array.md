# Java二维数组完整教程

## 1. 静态初始化
### 标准格式
```java
int[][] arr1 = new int[][]{
    {11, 22},
    {33, 44}
};

简化格式（推荐）
```java
int[][] arr2 = {
    {1, 2, 3},
    {4, 5, 6, 7}
};

## 2. 动态初始化
```java
// 创建3行5列的二维数组
int[][] arr3 = new int[3][5];

// 赋值示例
arr3[0][0] = 10;
arr3[1][2] = 20;

## 3. 数组遍历
```java
for (int i = 0; i < arr2.length; i++) {
    for (int j = 0; j < arr2[i].length; j++) {
        System.out.print(arr2[i][j] + " ");
    }
    System.out.println();
}


## 4. 实战案例：商场营业额统计
```java
public class SalesAnalysis {
    public static void main(String[] args) {
        int[][] yearData = {
            {22, 66, 44},  // 第一季度
            {77, 33, 88},  // 第二季度
            {25, 45, 65},  // 第三季度
            {11, 66, 99}   // 第四季度
        };

        int yearTotal = 0;
        
        for (int i = 0; i < yearData.length; i++) {
            int quarterSum = 0;
            for (int j = 0; j < yearData[i].length; j++) {
                quarterSum += yearData[i][j];
            }
            System.out.println("第" + (i+1) + "季度营业额：" + quarterSum);
            yearTotal += quarterSum;
        }
        
        System.out.println("全年总营业额：" + yearTotal);
    }
}
执行结果
第1季度营业额：132
第2季度营业额：198
第3季度营业额：135
第4季度营业额：176
全年总营业额：641
