
# Windows 10 安装 MySQL 5.7 完整实战指南 (全功能版)

## 一、 下载与准备

1. **下载：** 访问 [MySQL 5.7 官网归档页](https://downloads.mysql.com/archives/community/)，下载 `Windows (x86, 64-bit), ZIP Archive`。
    
2. **解压：** 将文件夹解压到 `D:\mysql-5.7`（路径不建议有空格和中文）。
    
3. **新建配置：** 在根目录下新建 `my.ini` 文件，写入以下内容（注意修改路径）：
    

Ini, TOML

```
[mysqld]
port=3306
basedir=D:\mysql-5.7
datadir=D:\mysql-5.7\data
max_connections=200
character-set-server=utf8
default-storage-engine=INNODB
sql_mode=NO_ENGINE_SUBSTITUTION,STRICT_TRANS_TABLES

[mysql]
default-character-set=utf8
```

---

## 二、 命令行安装与初始化

必须以 **管理员身份** 打开命令提示符（CMD）：

1. **进入目录：**
    
    DOS
    
    ```
    d:
    cd D:\mysql-5.7\bin
    ```
    
2. **执行初始化：**
    
    DOS
    
    ```
    mysqld --initialize-insecure --user=mysql
    ```
    
3. **安装并启动服务：**
    
    DOS
    
    ```
    mysqld --install MySQL57
    net start MySQL57
    ```
    

---

## 三、 密码弱化与账号配置

初始化完成后，默认 root 密码为空。我们需要登录并进行高级配置：

1. **登录：**
    
    DOS
    
    ```
    mysql -u root -p
    ```
    
    _(提示密码直接按回车)_
    
2. **弱化密码策略（关键）：**
    
    默认策略强制要求复杂密码，执行以下命令调低限制：
    
    SQL
    
    ```
    -- 查看策略（可选）
    -- SHOW VARIABLES LIKE 'validate_password%'; 
    
    -- 设为低等级（只校验长度）
    SET GLOBAL validate_password_policy=LOW;
    -- 设置最短长度为 4
    SET GLOBAL validate_password_length=4;
    ```
    
3. **设置 root 密码：**
    
    SQL
    
    ```
    ALTER USER 'root'@'localhost' IDENTIFIED BY '123456';
    ```
    

---

## 四、 多人连接与权限授权

为了让其他同事或工具（如 Navicat）能远程连接：

1. **开启 root 远程权限：**
    
    SQL
    
    ```
    -- 允许 root 用户从任何 IP (%) 使用密码 123456 连接
    GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY '123456' WITH GRANT OPTION;
    ```
    
2. **创建普通开发者账号（推荐）：**
    
    不建议把 root 给所有人，可以创建一个权限受限的账号：
    
    SQL
    
    ```
    -- 创建用户 dev_user，密码为 dev123
    CREATE USER 'dev_user'@'%' IDENTIFIED BY 'dev123';
    -- 仅授予对某个数据库（如 test_db）的所有权限
    GRANT ALL ON test_db.* TO 'dev_user'@'%';
    ```
    
3. **刷新并退出：**
    
    SQL
    
    ```
    FLUESH PRIVILEGES;
    exit;
    ```
    

---

## 五、 Windows 环境优化

1. **防火墙放行：**
    
    在管理员 CMD 执行，允许外部通过 3306 端口访问：
    
    DOS
    
    ```
    netsh advfirewall firewall add rule name="MySQL_3306" dir=in action=allow protocol=TCP localport=3306
    ```
    
2. **配置系统路径（环境变量）：**
    
    - 右键“此电脑” -> 属性 -> 高级系统设置 -> 环境变量。
        
    - 在“系统变量”的 **Path** 中新建一行：`D:\mysql-5.7\bin`。
        
    - _作用：之后在任何地方打开 CMD 都可以直接输入 `mysql` 登录。_
        

---

## 六、 常用管理命令速查

- **启动/停止：** `net start MySQL57` / `net stop MySQL57`
    
- **卸载服务：** `sc delete MySQL57`
    
- **查看当前连接：** `show processlist;`
    
- **查看用户列表：** `select user,host from mysql.user;`
    

---

这份指南已经涵盖了从 0 到“多人协作开发”的所有核心配置。你现在可以尝试用同事的电脑连接你的 IP 地址试试了。需要我教你如何查看自己的本地 IP 吗？