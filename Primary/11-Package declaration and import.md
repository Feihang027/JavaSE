# Java 包（Package）与访问控制

## 目录
- [包的概念](#包的概念)
- [包的命名规则](#包的命名规则)
- [包的声明与导入](#包的声明与导入)
- [访问控制](#访问控制)

---

## 包的概念
1. **作用**：
   - 用于区分类的位置（类似C++的`namespace`）
   - 对类进行分类管理，解决类名冲突问题
   - 对应文件系统的目录结构

2. **默认包**：
   - 未声明包名的类属于同一个默认包
   - 同包中的类可以直接互相访问

---

## 包的命名规则
- 使用英文小写字母和数字的组合
- 推荐采用**反向域名格式**（如：`com.baidu`）
- 通过`.`分隔多级包名（对应多级文件夹）
- 示例：
  ```java
  package com.example.project.util;  // 对应目录：com/example/project/util


  # Java 包的声明与导入

## 包的声明

### 语法规则
- 使用 `package` 关键字声明包
- **必须写在Java文件的第一行**
- 对应文件系统的目录结构

### 示例代码
```java
package com.example;  // 声明当前类属于 com.example 包
// 注意：package声明必须位于文件首行




# Java 访问控制详解

## 访问修饰符权限表

| 修饰符       | 类内部 | 同包 | 子类 | 其他包 |
|--------------|--------|------|------|--------|
| `private`    | ✔      | ✖    | ✖    | ✖      |
| （默认）     | ✔      | ✔    | ✖    | ✖      |
| `protected`  | ✔      | ✔    | ✔    | ✖      |
| `public`     | ✔      | ✔    | ✔    | ✔      |

---

## 核心访问规则

### 1. `private` 访问权限
- **可见范围**：仅当前类内部
- 典型应用场景：
  ```java
  public class BankAccount {
      private double balance;  // 只能在本类中访问
  }


2. 默认（包级）访问权限
可见范围：同包中的类
关键特征：
class PackageClass {  // 无修饰符，默认访问权限
    void show() { /* 同包类可访问 */ }
}


3. protected 访问权限
可见范围：
同包所有类
不同包中的子类
继承示例：
// 父类
package com.example;
public class Animal {
    protected void breathe() { /*...*/ }
}

// 子类（不同包）
package com.test;
import com.example.Animal;
public class Dog extends Animal {
    void method() {
        breathe();  // 可以访问父类的protected方法
    }
}

4. public 访问权限
可见范围：全局可见
公共接口示例：
public class Calculator {
    public int add(int a, int b) {  // 所有地方可访问
        return a + b;
    }
}
访问控制原则
最小权限原则
总是优先使用最严格的访问级别（推荐顺序）：
private → 默认 → protected → public

包级隔离
默认访问权限可以实现包内数据封装

继承控制
protected 专门为继承体系设计，平衡封装与扩展性

API设计
public 修饰的内容构成类对外的正式接口

注：访问控制的效果需要结合包的使用才能完全体现，不同包的类需要显式导入才能访问非私有成员