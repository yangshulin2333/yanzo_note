
### 安装 NVM Node
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash
source ~/.bashrc

### 推荐安装 Node.js 16.x (这个版本兼容性最强)
nvm install 16
nvm use 16

## Python安装
**Ubuntu 系统本身高度依赖自带的 Python 版本**。如果操作不当覆盖了系统默认版本，可能会导致你的 DMIT 服务器连 SSH 终端都无法正常登录。


为了安全且成功地在 Ubuntu 22.04/24.04 上安装 Python 3.10 并解决 `npm` 报错，请**严格按照以下步骤**执行：

### 1. 安装基础工具

先确保你的系统有添加第三方源的能力：

Bash

```
sudo apt update
sudo apt install software-properties-common -y
```

### 2. 正确添加 Python 源

现在运行这个命令，它会自动帮你配置好 Python 3.10 的下载地址。**注意：弹出提示时请按回车键确认。**

Bash

```
sudo add-apt-repository ppa:deadsnakes/ppa -y
sudo apt update
```

### 3. 正式安装 Python 3.10

现在系统就能找到包了，直接运行安装：

Bash

```
sudo apt install python3.10 python3.10-dev python3.10-venv -y
```

### 4. 解决 npm 之前的报错

安装好 3.10 后，你需要告诉 `npm` 编译时使用这个版本（这样就能绕过 Python 3.12 缺失 `distutils` 的问题）：

Bash

```
# 设置 npm 使用新安装的 python3.10
npm config set python /usr/bin/python3.10

# 回到项目目录重新安装
cd /root/VCPToolBox
rm -rf node_modules
npm install
```

### 5. 安装 VCP 的 Python 依赖

Node 依赖装好后，最后一步是安装 VCP 插件所需的库：

Bash

```
# 使用 python3.10 来运行 pip 安装
python3.10 -m pip install -r requirements.txt
```

**为什么这么做最稳？**

- **不破坏系统**：系统默认的 `python3` 依然是 3.12 保持不变，不会搞挂服务器。
    
- **精准编译**：`npm` 通过 `config set` 拿到了它想要的 3.10，这样 `better-sqlite3` 就能顺利编译通过了。

### pip安装
### 1. 安装 Python 3.10 的 pip 模块

Bash

```
sudo apt update
sudo apt install python3.10-distutils curl -y
curl -sS https://bootstrap.pypa.io/get-pip.py | sudo python3.10
```

_这一步会通过官方脚本为 Python 3.10 安装专属的 pip。_

### 2. 验证安装是否成功

运行以下命令，确认输出的版本信息里包含 `python 3.10`：

Bash

```
python3.10 -m pip --version
```

### 3. 继续安装 VCPToolBox 的 Python 依赖

一旦 pip 准备就绪，你就可以安装项目所需的依赖库了：

Bash

```
# 进入项目目录
cd /root/VCPToolBox

# 使用 python3.10 的 pip 安装依赖
python3.10 -m pip install -r requirements.txt
```

---

### 🛡️ 为什么不直接用 `apt install python3-pip`？

如果你直接用 `apt` 安装 pip，它通常会关联到系统默认的 Python 3.12。为了确保 VCPToolBox 运行在你刚配好的 **Python 3.10** 环境下，必须使用这种针对特定版本的安装方式。

**依赖安装完成后，你就可以尝试用 PM2 启动项目了。需要我帮你检查一下启动命令吗？**