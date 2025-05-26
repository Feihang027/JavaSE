# 用户对象存在性校验实现方案

## 需求说明
1. 创建用户集合并存入3个用户对象
2. 定义校验方法判断指定ID的用户是否存在
3. 用户对象属性要求：
   - id（用户唯一标识）
   - username（用户名）
   - password（密码）

---

## 用户类定义（User.java）

public class User {
    private String id;
    private String username;
    private String password;

    public User(String username, String password, String id) {
        this.username = username;
        this.password = password;
        this.id = id;
    }

    // Getter 方法
    public String getId() {
        return id;
    }

    // 完整Getter/Setter建议
    public String getUsername() {
        return username;
    }

    public void setUsername(String username) {
        this.username = username;
    }

    public String getPassword() {
        return password;
    }

    public void setPassword(String password) {
        this.password = password;
    }
}

---

## 校验功能实现
```java
import java.util.ArrayList;

public class Test5 {
    public static void main(String[] args) {
        // 1. 创建用户集合
        ArrayList<User> userList = new ArrayList<>();
        
        // 2. 初始化测试数据
        userList.add(new User("zhangsan", "123", "heima001"));
        userList.add(new User("lisi", "1234", "heima002"));
        userList.add(new User("wangwu", "12345", "heima003"));

        // 3. 执行存在性校验
        System.out.println(checkUserExists(userList, "heima001"));  // true
        System.out.println(checkUserExists(userList, "heima004"));  // false
    }

    /**
     * 用户存在性校验方法
     * @param users 用户集合
     * @param targetId 要查找的用户ID
     * @return 存在返回true，否则返回false
     */
    public static boolean checkUserExists(ArrayList<User> users, String targetId) {
        for (User user : users) {
            if (user.getId().equals(targetId)) {
                return true;
            }
        }
        return false;
    }
}

