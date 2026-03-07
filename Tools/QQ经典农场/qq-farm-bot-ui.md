[qq经典农场](https://github.com/Penty-d/qq-farm-bot-ui)
### Linux（Ubuntu/Debian）

```shell
# 1. 安装 Node.js 20+
sudo apt update && sudo apt install -y curl
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt install -y nodejs
corepack enable

# 2. 安装依赖并构建前端
cd /path/to/qq-farm-bot-ui
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