# 手机价格筛选功能实现方案

## 需求说明
1. 定义`Phone`类，包含品牌和价格属性
2. 创建包含三个手机对象的集合（小米1000、苹果8000、锤子2999）
3. 实现筛选方法返回价格低于3000的手机列表

---

## Phone 类定义

public class Phone {
    private String brand;
    private int price;

    public Phone() {}

    public Phone(String brand, int price) {
        this.brand = brand;
        this.price = price;
    }

    // Getter & Setter 方法
    public String getBrand() {
        return brand;
    }

    public void setBrand(String brand) {
        this.brand = brand;
    }

    public int getPrice() {
        return price;
    }

    public void setPrice(int price) {
        this.price = price;
    }
}

---

## 测试类实现
```java
import java.util.ArrayList;

public class Test7 {
    public static void main(String[] args) {
        // 1. 创建手机集合
        ArrayList<Phone> phones = new ArrayList<>();
        
        // 2. 添加测试数据
        phones.add(new Phone("xiaomi", 1000));
        phones.add(new Phone("iPhone", 8000));
        phones.add(new Phone("chuizi", 2999));

        // 3. 获取价格低于3000的手机列表
        ArrayList<Phone> filteredList = filterByPrice(phones);
        
        // 4. 遍历输出结果
        System.out.println("价格低于3000的手机：");
        for (Phone p : filteredList) {
            System.out.println(p.getBrand() + ", 价格：" + p.getPrice());
        }
    }

    /**
     * 筛选价格低于指定值的手机
     * @param phoneList 原始手机列表
     * @return 筛选后的手机列表
     */
    public static ArrayList<Phone> filterByPrice(ArrayList<Phone> phoneList) {
        ArrayList<Phone> result = new ArrayList<>();
        for (Phone phone : phoneList) {
            if (phone.getPrice() < 3000) {
                result.add(phone);
            }
        }
        return result;
    }
}