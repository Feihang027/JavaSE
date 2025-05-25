# 学生管理系统练习

## 功能描述
定义一个长度为3的数组，存储1~3名学生对象作为初始数据，学生对象的学号、姓名各不相同。  
学生属性：学号(id)、姓名(name)、年龄(age)。  

**要求**：  
1. 再次添加一个学生对象，并在添加时进行学号唯一性判断  
2. 添加完毕后遍历所有学生信息  
3. 通过id删除学生信息，存在则删除，不存在提示失败  
4. 删除后遍历所有学生信息  
5. 查询数组id为指定值的学生，存在则年龄+1  

---
## Java 测试类定义：Test.java
```Java
package exercise6;

public class Test {
    public static void main(String[] args) {
        Student[] arr = new Student[3];
        Student stu1 = new Student(1, "zhangsan", 23);
        Student stu2 = new Student(2, "lisi", 22);

        arr[0] = stu1;
        arr[1] = stu2;

        // 要求1：添加学生并进行学号唯一性校验
        Student stu4 = new Student(4, "liuliu", 26);
        boolean flag = contains(arr, stu4.getId());
        if (flag) {
            System.out.println("当前id重复，请修改id后再添加");
        } else {
            int count = getCount(arr);
            if (count == arr.length) {
                // 数组已满，创建新数组
                Student[] newArr = creatNewArr(arr);
                newArr[count] = stu4;
                printArr(newArr);
            } else {
                arr[count] = stu4;
                // 要求2：添加后遍历
                printArr(arr);
            }
        }

        // 要求3：通过id删除学生信息（注释部分为删除逻辑示例）
        /*
        int index = getIndex(arr, 2);
        if (index >= 0) {
            arr[index] = null;
            // 要求4：删除后遍历
            printArr(arr);
        } else {
            System.out.println("当前id不存在，删除失败");
        }
        */

        // 要求5：修改指定id学生年龄
        int index = getIndex(arr, 1);
        if (index >= 0) {
            Student stu = arr[index];
            stu.setAge(stu.getAge() + 1);
            printArr(arr);
        } else {
            System.out.println("当前id不存在，无法修改");
        }
    }

    // 辅助方法：判断id是否存在
    public static boolean contains(Student[] arr, int id) {
        for (Student stu : arr) {
            if (stu != null && stu.getId() == id) {
                return true;
            }
        }
        return false;
    }

    // 统计数组中非空元素数量
    public static int getCount(Student[] arr) {
        int count = 0;
        for (Student stu : arr) {
            if (stu != null) count++;
        }
        return count;
    }

    // 创建新数组（扩容）
    public static Student[] creatNewArr(Student[] arr) {
        Student[] newArr = new Student[arr.length + 1];
        System.arraycopy(arr, 0, newArr, 0, arr.length);
        return newArr;
    }

    // 遍历数组
    public static void printArr(Student[] arr) {
        for (Student stu : arr) {
            if (stu != null) {
                System.out.println(stu.getId() + "," + stu.getName() + "," + stu.getAge());
            }
        }
    }

    // 根据id查找索引
    public static int getIndex(Student[] arr, int id) {
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] != null && arr[i].getId() == id) {
                return i;
            }
        }
        return -1;
    }
}
---




---
Java 类定义：Student.java
package exercise6;

public class Student {
    private int id;
    private String name;
    private int age;

    public Student() {}

    public Student(int id, String name, int age) {
        this.id = id;
        this.name = name;
        this.age = age;
    }

    // Getter & Setter 方法
    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

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


