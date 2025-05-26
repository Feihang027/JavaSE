# 学生对象集合操作实践指南

## 需求说明
定义一个集合用于存储学生对象，并实现以下功能：
1. 添加多个学生对象到集合
2. 遍历集合展示学生信息
3. 支持通过键盘录入学生信息

---

## 学生类定义（Student.java）
public class Student {
    private String name;
    private int age;

    // 无参构造
    public Student() {}

    // 全参构造
    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Getter & Setter 方法
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}

---

## 基础版实现（集合初始化+遍历）
import java.util.ArrayList;
public class Test4 {
    public static void main(String[] args) {
        // 1. 创建集合
        ArrayList<Student> list = new ArrayList<>();

        // 2. 创建学生对象（修正参数传递方式）
        Student s1 = new Student("zhangsan", 23);
        Student s2 = new Student("lisi", 24);
        Student s3 = new Student("wangwu", 25);

        // 3. 添加元素
        list.add(s1);
        list.add(s2);
        list.add(s3);

        // 4. 遍历集合（修正循环变量声明）
        for(int i = 0; i < list.size(); i++) {
            Student stu = list.get(i);
            System.out.println(stu.getName() + ", " + stu.getAge());
        }
    }
}

---

## 升级版实现（键盘录入）
```java
import java.util.ArrayList;
import java.util.Scanner;

public class Test4Upgrade {
    public static void main(String[] args) {
        ArrayList<Student> list = new ArrayList<>();
        Scanner sc = new Scanner(System.in);

        // 录入3个学生信息
        for (int i = 0; i < 3; i++) {
            Student s = new Student();
            
            System.out.println("请输入学生姓名：");
            String name = sc.next();
            
            System.out.println("请输入学生年龄：");
            int age = sc.nextInt();
            
            s.setName(name);
            s.setAge(age);
            list.add(s);
        }

        // 增强for循环遍历
        System.out.println("\n录入的学生信息：");
        for (Student stu : list) {
            System.out.println(stu.getName() + ", " + stu.getAge());
        }
    }
}