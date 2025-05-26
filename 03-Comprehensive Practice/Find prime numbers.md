# 需求说明
判断101-200之间的所有质数，并输出结果
## 质数判断规则
质数必须大于1
只能被1和它本身整除
使用双层循环实现：
外层循环：遍历101-200的所有数字
内层循环：验证每个数字是否为质数

```java
public class PrimeNumberFinder {
    public static void main(String[] args) {
        // 统计质数个数
        int count = 0;
        
        // 外层循环：遍历101~200
        for(int i = 101; i <= 200; i++) {
            boolean isPrime = true;
            
            // 内层循环：判断当前数字是否为质数
            for(int j = 2; j < i; j++) {
                if(i % j == 0) {
                    isPrime = false;
                    break; // 发现因子立即结束内循环
                }
            }
            
            // 输出质数并计数
            if(isPrime) {
                System.out.println("当前数字 " + i + " 是质数");
                count++;
            }
        }
        
        System.out.println("101-200之间共有 " + count + " 个质数");
    }
}