# Java 封装详解

## 一、封装概念
**核心原则**：对象代表什么，就得封装对应的数据，并提供数据对应的行为  
✅ 优势：降低学习成本，无需记忆对象方法，需要时通过接口查找即可

## 二、实现方式

### 1. 访问修饰符
| 修饰符      | 作用范围             |
| ----------- | -------------------- |
| `private`   | 仅本类可见           |
| `protected` | 本类/子类/同包类可见 |
| 默认        | 同包可见             |
| `public`    | 全局可见             |

**黄金法则**：
- 属性声明为 `private`
- 方法按需使用 `public/private`

### 2. Getter/Setter 方法
```java
// 示例：成员变量控制
public void setAge(int age) {
    if(age >= 18 && age <= 50) { // 数据校验
        this.age = age;
    } else {
        System.out.println("非法参数");
    }
}

public int getAge() {
    return age; // 对外暴露数据
}



完整案例
GirlFriend 类
public class GirlFriend {
    // 私有化属性
    private String name;
    private int age;
    private String gender;

    // name 控制
    public void setName(String name) {
        this.name = name;
    }
    public String getName() {
        return name;
    }

    // age 控制（含校验）
    public void setAge(int age) {
        if(age >= 18 && age <= 50) {
            this.age = age;
        } else {
            System.out.println("非法参数");
        }
    }
    public int getAge() {
        return age;
    }

    // gender 控制
    public void setGender(String gender) {
        this.gender = gender;
    }
    public String getGender() {
        return gender;
    }

    // 对象行为
    public void sleep() {
        System.out.println("女朋友在睡觉");
    }
    
    public void eat() {
        System.out.println("女朋友在吃饭");
    }
}


测试类
public class GirlFriendTest {
    public static void main(String[] args) {
        GirlFriend gf1 = new GirlFriend();
        
        // 通过setter赋值
        gf1.setName("小诗诗");
        gf1.setAge(18);
        gf1.setGender("女");

        // 通过getter访问
        System.out.println(gf1.getName());
        System.out.println(gf1.getAge());
        System.out.println(gf1.getGender());

        // 调用对象行为
        gf1.eat();
        gf1.sleep();
    }
}

封装优势
数据保护：防止非法值修改（如负数年龄）
操作追踪：可在方法中添加日志/校验逻辑
实现自由：内部存储结构修改不影响调用方
权限控制：敏感数据可设置只读（只提供getter）