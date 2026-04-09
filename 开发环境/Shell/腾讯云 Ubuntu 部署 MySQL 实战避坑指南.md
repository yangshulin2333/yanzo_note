
## 一、 环境搭建篇：工具与网络

|**遇到的问题**|**错误现象 / 报错**|**根本原因**|**解决方法**|
|---|---|---|---|
|**远程连接失败**|Tabby 或 Navicat 提示 `Connection Timeout`|腾讯云默认关闭了外部访问端口。|在**腾讯云控制台-防火墙**中，手动添加 **TCP:3306** (MySQL) 和 **TCP:22** (SSH) 规则。|
|**Docker 下载极慢/超时**|`i/o timeout` 或 `failed to resolve reference`|服务器在国内，直接连接 Docker Hub（国外）网络不稳。|配置**国内镜像加速器**（如腾讯云内网镜像），并执行 `systemctl restart docker`。|

---

## 二、 权限与运行篇：Docker 基础

|**遇到的问题**|**错误现象 / 报错**|**根本原因**|**解决方法**|
|---|---|---|---|
|**Docker 权限不足**|`permission denied while trying to connect to the docker API`|当前用户不在 `docker` 用户组中。|执行 `sudo usermod -aG docker $USER`，然后**必须重启 SSH 连接**让权限生效。|
|**容器名冲突**|`Conflict. The container name "/mysql-db" is already in use`|之前运行失败的残留容器占用了名字。|执行 `docker rm -f mysql-db` 强制删除旧容器。|

---

## 三、 核心业务篇：若依 (RuoYi) + Quartz 适配

|**遇到的问题**|**错误现象 / 报错**|**根本原因**|**解决方法**|
|---|---|---|---|
|**找不到 Quartz 表**|`Table 'hospitalsb.QRTZ_LOCKS' doesn't exist`|**致命伤：** Linux 下 MySQL 默认区分大小写，代码查大写表，库里是小写。|重建 Docker 容器，在命令末尾加上 `--lower_case_table_names=1`。|
|**导入 SQL 失败**|`[ERR] 1046 - No database selected`|运行脚本前没有选中或创建目标数据库。|在 Navicat 中先手动 **Create Database hospitalsb**，双击打开（变绿）后再运行 SQL。|
|**插入数据报错**|`Field 'dept_id' doesn't have a default value`|MySQL 开启了严格模式，且代码插入时漏掉了非空字段。|1. 修改表结构允许该字段为 NULL；<br><br>  <br><br>2. 或者给该字段设置一个默认值。|

---

## 💡 歪哥的心得归纳（干货总结）

1. **环境差异意识**：永远记住 **“Windows 不区分大小写，Linux 严格区分”**。这不仅体现在 MySQL 表名上，以后你写 Unity 脚本或者 Python 路径时也要注意。
    
2. **Docker 的“瞬移”属性**：Docker 容器是“易失”的。通过 `docker rm` 删掉容器，里面的数据也会一起消失。所以**重要数据一定要先在 Navicat 里备份 SQL**，或者学习使用 `docker -v` 进行路径挂载。
    
3. **云安全意识**：为了方便测试，我们开了 `0.0.0.0/0`（全网可连）。在正式项目中，建议只允许你家里的**固定公网 IP** 访问 3306 端口。
    

---

**恭喜你完成了从“软件安装”到“服务器调优”的跨越！** 既然数据库和服务器都通了，接下来你是打算继续调试若依的后端接口，还是准备在 Unity 里写个脚本连一下这个数据库试试？