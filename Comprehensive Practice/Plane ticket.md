# 需求说明
## 价格规则表
| 季节 | 时间段       | 头等舱折扣 | 经济舱折扣 |
| ---- | ------------ | ---------- | ---------- |
| 旺季 | 5月-10月     | 9折        | 8.5折      |
| 淡季 | 11月-次年4月 | 7折        | 6.5折      |

---
```java
import java.util.Scanner;

public class TicketCalculator {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // 输入数据
        System.out.println("请输入机票原价：");
        int ticket = sc.nextInt();
        
        System.out.println("请输入当前月份（1-12）：");
        int month = sc.nextInt();
        
        System.out.println("请输入舱位类型（0 头等舱 / 1 经济舱）：");
        int seat = sc.nextInt();
        
        // 计算价格
        if (month >= 5 && month <= 10) {
            // 旺季
            ticket = getPrice(ticket, seat, 0.9, 0.85);
        } else if ((month >= 1 && month <= 4) || (month >= 11 && month <= 12)) {
            // 淡季
            ticket = getPrice(ticket, seat, 0.7, 0.65);
        } else {
            System.out.println("⚠️ 月份输入不合法！");
            return;
        }
        
        System.out.println("最终票价：" + ticket);
    }

    // 计算折扣价格
    public static int getPrice(int ticket, int seat, double v0, double v1) {
        if (seat == 0) {
            return (int)(ticket * v0);
        } else if (seat == 1) {
            return (int)(ticket * v1);
        } else {
            System.out.println("⚠️ 无效舱位类型，返回原价");
            return ticket;
        }
    }
}
```
# 使用示例
```plaintext
请输入机票原价：
1000
请输入当前月份（1-12）：
8
请输入舱位类型（0 头等舱 / 1 经济舱）：
0
最终票价：900
```

---

# 注意事项
1. 代码需要保存为 `TicketCalculator.java`
2. 输入验证：
   - 月份范围：1-12
   - 舱位类型：仅支持 0 或 1
3. 价格计算时会直接截断小数（如 999.9 → 999）