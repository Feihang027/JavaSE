# 需求说明
在唱歌比赛中，有6名评委给选手打分，分数范围是[0-100] 之间的整数。
选手的最后得分为:去掉最高分、最低分后的4个评委的平均分，请完成上述过程并计算出选手的得分

```java
import java.util.Scanner;

public class JudgeScoringSystem {
    public static void main(String[] args) {
        // 1. 获取评委打分
        int[] scores = getScores();
        
        // 2. 计算最大值和最小值
        int max = getMax(scores);
        int min = getMin(scores);
        
        // 3. 计算最终平均分
        int sum = getSum(scores);
        int avg = (sum - max - min) / (scores.length - 2);
        
        System.out.println("选手最终得分：" + avg);
    }

    // 获取6个有效评分（0-100）
    public static int[] getScores() {
        int[] scores = new int[6];
        Scanner sc = new Scanner(System.in);
        for(int i = 0; i < scores.length; ) {
            System.out.print("请输入第" + (i+1) + "位评委的分数（0-100）：");
            int score = sc.nextInt();
            if(score >= 0 && score <= 100) {
                scores[i] = score;
                i++;
            } else {
                System.out.println("⚠️ 分数无效，请输入0-100之间的整数！");
            }
        }
        return scores;
    }

    // 求最大值
    public static int getMax(int[] arr) {
        int max = arr[0];
        for(int i = 1; i < arr.length; i++) {
            if(arr[i] > max) max = arr[i];
        }
        return max;
    }

    // 求最小值
    public static int getMin(int[] arr) {
        int min = arr[0];
        for(int i = 1; i < arr.length; i++) {
            if(arr[i] < min) min = arr[i];
        }
        return min;
    }

    // 求总和
    public static int getSum(int[] arr) {
        int sum = 0;
        for(int num : arr) {
            sum += num;
        }
        return sum;
    }
}