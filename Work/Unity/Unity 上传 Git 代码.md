
# 📘 Unity 项目版本管理手册 (Git & GitHub)

### 一、 首次配置 (仅需做一次)

#### 1. Unity 编辑器设置

- **目的**：确保 Unity 把文件保存为“可读文本”，而不是二进制乱码，方便 Git 记录修改。
    
- **操作**：
    
    - 菜单栏 `Edit` -> `Project Settings` -> `Editor`。
        
    - **Asset Serialization Mode**: 必须选 **Force Text**。
        
    - _(注：Unity 6 中 `Version Control` 模式已默认开启可见 Meta 文件，无需手动设置)_。
        

#### 2. 创建“过滤名单” (.gitignore) —— **⚠️最关键一步**

- **目的**：防止上传几个 G 的垃圾缓存文件 (`Library`, `Temp` 等)。
    
- **操作**：
    
    - 在项目根目录（能看到 `Assets` 的地方）创建文件 `.gitignore`。
    - **写入内容** (标准模板)：
    
    ```
    /[Ll]ibrary/
    /[Tt]emp/
    /[Oo]bj/
    /[Bb]uild/
    /[Bb]uilds/
    /[Ll]ogs/
    /[Uu]ser[Ss]ettings/
    /[Mm]emoryCaptures/
    !/[Aa]ssets/**/*.meta
    .vs/
    *.csproj
    *.unityproj
    *.sln
    *.suo
    *.tmp
    *.user
    *.userprefs
    *.pidb
    *.booproj
    *.svd
    *.pdb
    *.opendb
    *.VC.db
    *.pidb.meta
    *.pdb.meta
    *.mdb.meta
    *.apk
    *.unitypackage
    ```
    

#### 3. 初始化本地仓库

- **操作**：在项目根目录右键打开 Git Bash，输入：
    
    Bash
    
    ```
    git init
    ```
    

---

### 二、 提交代码 (日常工作流)

每当你完成一个功能（比如做好了 AI，或者修好了 Bug），就执行这三步：

#### 1. 装货 (Add)

把所有修改过的文件放入暂存区。

Bash

```
git add .
```

- **正常现象：** 可能会出现一堆 `warning: LF will be replaced by CRLF...`，这是自动转换换行符，**不用管，直接忽略**。
- **异常现象：** 如果出现 `Permission denied ... .vs/...`，说明你**没创建好 .gitignore** 或者 **文件没生效**。
    - _补救措施：_ 关掉 Unity 和 VS，确认 `.gitignore` 存在且内容正确，然后执行 `rm -rf .git` 删库重来。
#### 2. 记录 (Commit)

给这次修改打上标签，生成快照。

Bash

```
git commit -m "Day 3: 完成了僵尸AI寻路功能"
```


#### 3. 推送到远程（云端备份）

去 GitHub 或 Gitee 创建一个**空仓库**（不要勾选“初始化 readme”），复制仓库地址（以 `.git` 结尾的链接）。


##### 第一步：重命名分支（规范化）

Bash

```
git branch -M main
```

##### 第二步：关联远程仓库

Bash

```
git remote add origin <你的仓库地址>
```

_例如：_ `git remote add origin https://github.com/yangshulin2333/KitchenChaos.git`

##### 第三步：推送到云端

Bash

```
git push -u origin main
```

---

### 三、 关联 GitHub (新项目首次上传)

当你本地 `commit` 完第一次后，需要把本地仓库和 GitHub 远程仓库连起来：

1. **在 GitHub 网站**：点击右上角 `+` -> `New repository` -> 起名 -> Create。
    
2. **复制仓库地址** (HTTPS 链接)。
    
3. **在 Git Bash 执行** (只执行一次)：
    
    Bash
    
    ```
    # 1. 认亲：告诉本地 Git，远程仓库在哪里
    git remote add origin https://github.com/你的用户名/你的仓库名.git
    
    # 2. 改名：把默认分支改名为 main (GitHub 标准)
    git branch -M main
    
    # 3. 强推：把代码推上去，并建立关联
    git push -u origin main
    ```
    

---

### 💡 常见问题急救

- **Q: 不小心把 Library 文件夹传上去了怎么办？**
    
    - A: 千万别直接删文件！要用命令从 Git 记录中移除：
        
        Bash
        
        ```
        git rm -r --cached Library
        git commit -m "Fix: Remove Library folder"
        git push
        ```
        
- **Q: Unity 报错 "User does not have permission" 或 Git 报错？**
    
    - A: 确保你的 Unity **已经关闭** 再提交代码（有时候文件被占用锁住了）。不过通常情况下，开着 Unity 提交也没事。
        

---

**把这份笔记存好，明天（Day 3）我们就要开始做僵尸 AI 了，到时候记得写完代码提交一次哦！**