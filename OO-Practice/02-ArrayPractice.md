
# 定义数组存储3部汽车对象

## 功能描述
定义数组存储3部汽车对象。汽车的属性有：品牌、价格、颜色。创建三个汽车对象，数据通过键盘录入而来，并把数据存入到数组当中。

## Java 类定义：Car.java

````java
public class Car {
    private String brand;
    private int price;
    private String color;

    public Car() {

    }

    public Car(String brand, int price, String color) {
        this.brand = brand;
        this.price = price;
        this.color = color;
    }

    public String getBrand() {
        return brand;
    }

    public void setBrand(String brand) {
        this.brand = brand;
    }

    public double getPrice() {
        return price;
    }

    public void setPrice(int price) {
        this.price = price;
    }

    public String getColor() {
        return color;
    }

    public void setColor(String color) {
        this.color = color;
    }
}
````

## Java 测试类定义：CarTest.java

````java
package exercise3;

import java.util.Scanner;

public class CarTest {
    public static void main(String[] args) {
        Car[] arr = new Car[3];

        // 创建汽车对象，数据来源于键盘录入
        Scanner sc = new Scanner(System.in);
        for (int i = 0; i < arr.length; i++) {
            // 创建汽车对象
            Car c = new Car();
            // 录入品牌
            System.out.println("请输入汽车的品牌");
            String brand = sc.next();
            c.setBrand(brand);
            // 录入价格
            System.out.println("请输入汽车的价格");
            int price = sc.nextInt();
            c.setPrice(price);
            // 录入颜色
            System.out.println("请输入汽车的颜色");
            String color = sc.next();
            c.setColor(color);

            // 把汽车对象添加到数组中
            arr[i] = c;
        }

        for (int i = 0; i < arr.length; i++) {
            Car car = arr[i];
            System.out.println(car.getBrand() + "," + car.getPrice() + "," + car.getColor());
        }
    }
}
````

## 注意事项

- Scanner 类的两套输入方法：
  - 第一套：`nextInt()`、`nextDouble()`、`next()` —— 遇到空格、制表符、回车停止读取。
  - 第二套：`nextLine()` —— 遇到回车才停止，可以接收空格与制表符。
- 两套输入方法不能混用，否则会出现读取不到的问题。
