既然作者建议使用 **PM2**，那这是非常明智的选择。PM2 不仅能让你的 VCPToolBox 在后台运行，还能在程序崩溃或服务器重启时自动拉起服务。

在 DMIT 服务器（通常是 Ubuntu/Debian/CentOS）上，你可以按照以下步骤进行部署：

### 1. 安装 PM2

PM2 是基于 Node.js 的，所以如果你的服务器还没安装，需要先安装 Node.js：

- **安装 Node.js (以 Ubuntu 为例)**：`sudo apt update && sudo apt install nodejs npm -y`
    
- **安装 PM2**：`sudo npm install pm2 -g`
    

### 2. 启动 VCPToolBox

假设你的后端入口文件是 `app.py` 或 `main.py`，进入你的项目目录，运行：

`pm2 start app.py --name vcp-backend --interpreter python3`

- `--name vcp-backend`: 给你的进程起个名字，方便管理。
    
- `--interpreter python3`: 告诉 PM2 使用 Python3 来运行，而不是默认的 Node.js。
    

### 3. 配置开机自启

为了保证 DMIT 服务器重启后 VCP 依然能自动运行，执行以下操作：

1. **生成自启脚本**：`pm2 startup`
    
2. **执行命令**：终端会弹出一行以 `sudo env PATH...` 开头的命令，**复制并运行它**。
    
3. **保存当前列表**：`pm2 save`
    

---

### 🛡️ 部署后的“省钱”检查点

在 DMIT 上跑起来后，请务必确认最后两件事：

- **确认 Key 的来源**：请再次检查你的配置文件（通常是 `.env` 或 `config.yaml`），确保使用的是 **YanzoFree** 项目生成的 Key。这样你的支出将永远停留在已产生的 **$3.18**，不会再增加。
    
- **监控运行状态**：你可以随时输入 `pm2 monit` 查看 VCP 的实时日志。如果看到大量错误，可能是免费 Key 触发了频率限制（RPM），这时候可以考虑在 VCP 设置里适当延长任务间隔。
    

### 常用 PM2 命令速查

- `pm2 list`: 查看所有运行中的服务。
    
- `pm2 logs vcp-backend`: 查看详细运行日志。
    
- `pm2 restart vcp-backend`: 重启服务（当你修改了代码或 Key 之后）。
    

**在 DMIT 部署过程中有遇到报错吗？或者需要我帮你检查一下 `pm2 startup` 生成的那行命令怎么运行？**