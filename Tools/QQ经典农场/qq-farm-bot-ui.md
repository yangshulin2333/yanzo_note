[qq经典农场](https://github.com/Penty-d/qq-farm-bot-ui)
### Linux（Ubuntu/Debian）

```shell
# 1. 安装 Node.js 20+
sudo apt update && sudo apt install -y curl
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt install -y nodejs
corepack enable

git clone https://ghfast.top/https://github.com/Penty-d/qq-farm-bot-ui.git

cd qq-farm-bot-ui/
pnpm install
pnpm build:web

# 3. 启动
pnpm dev:core

# （可选）设置管理密码后启动
ADMIN_PASSWORD='yanzo' pnpm dev:core
```

启动后访问面板：

- 本机：`http://localhost:3000`
- 局域网：`http://<你的IP>:3000`


https://github.com/Penty-d/qq-farm-bot-ui.git



既然你在使用服务器，为了保证程序在断开 SSH 连接后依然运行，且在崩溃时能自动重启，使用 **PM2** 是非常明智的选择。

以下是在你的服务器上实现 PM2 托管的具体步骤：

### 1. 安装 PM2

首先，你需要全局安装 PM2 工具：

Bash

```
npm install -g pm2
```

### 2. 使用 PM2 启动项目

根据你之前的启动命令 `ADMIN_PASSWORD='yanzo' pnpm dev:core`，你需要告诉 PM2 如何执行它。在项目根目录下运行：

Bash

```
ADMIN_PASSWORD='yanzo' pm2 start pnpm --name "qq-farm" -- dev:core
```

- **`--name "qq-farm"`**: 给这个进程起个名字，方便以后管理。
    
- **`-- dev:core`**: 这里的 `--` 非常关键，它告诉 PM2 后面的内容是传给 `pnpm` 的参数。
    

### 3. 设置开机自启（Persistence）

为了确保服务器重启后机器人也能自动跑起来，执行以下操作：

1. **生成启动脚本**：输入 `pm2 startup`，它会返回一行以 `sudo` 开头的命令，**复制并运行那行命令**。
    
2. **保存当前列表**：
    
    Bash
    
    ```
    pm2 save
    ```
    

---

### 4. 常用管理指令

启动后，你可以通过以下指令随时查看机器人的状态：

|**指令**|**作用**|
|---|---|
|**`pm2 list`**|查看所有正在运行的进程状态。|
|**`pm2 logs qq-farm`**|实时查看机器人的运行日志（排查报错必看）。|
|**`pm2 stop qq-farm`**|停止运行。|
|**`pm2 restart qq-farm`**|重启程序（修改代码或端口后常用）。|

---

### 5. 英语小课堂：Instance & Persistence

在 PM2 的世界里，这两个词经常出现：

- **Instance (名词):** 实例。
    
    - **发音**：`/ˈɪnstəns/` (因-斯-腾-丝)
        
    - **意思**：每启动一个程序，PM2 就会创建一个 **Instance**。你可以同时开启多个实例来分担压力。
        
- **Persistence (名词):** 持久化。
    
    - **语境**：PM2 的核心价值就是提供 **Process Persistence**（进程持久化），让程序不因为你退出登录而“死掉”。
        

---

**最后提醒：**

你之前修改了 `client.js` 把端口改成了 **3001**，所以启动后，请记得在浏览器访问 `http://你的IP:3001`。

**现在你可以试着输入 `pm2 list` 看看，是不是已经能看到 `qq-farm` 处于 `online` 状态了？**