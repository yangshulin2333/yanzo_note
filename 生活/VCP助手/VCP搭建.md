# 安装 NVM
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash
source ~/.bashrc

# 推荐安装 Node.js 16.x (这个版本兼容性最强)
nvm install 16
nvm use 16

之所以不建议“直接装个就行”，是因为 **Ubuntu 系统本身高度依赖自带的 Python 版本**。如果你操作不当覆盖了系统默认版本，可能会导致你的 DMIT 服务器连 SSH 终端都无法正常登录。

从你的最新截图（image_a7213a.png）来看，报错 `Unable to locate package python3.10` 是因为你之前的 `add-apt-repository` 命令运行失败了（提示 `command not found`）。

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
    

**你现在可以先试一下第一步，如果 `add-apt-repository` 成功跑起来了，后面的安装就会非常快。**