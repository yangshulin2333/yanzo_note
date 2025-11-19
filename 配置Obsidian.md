[# Obsidian邪修用法，免费云同步，AI，手机端，还有进阶技巧](https://www.youtube.com/watch?v=IlNOhNeWGgY&t=106s)

## git云同步
1. 登录个人git账户，新建git仓库
	- ![350](assets/配置Obsidian/file-20251119185228343.png)
	- ![350](assets/配置Obsidian/file-20251119185228342.png)
2. 
```bash
git init # 初始化仓库
```
 初始化仓库后代开该地址。
 ![350](assets/配置Obsidian/file-20251119195650562.png)
3. 打开根目录，添加`.ignore`文件,文件内容为：
```bash
	.obsidian/workspace.json
	.obsidian/workspace-mobile.json
```
4. 添加到缓存区并commit提交文件到git
   ```bash
	git add . # 添加当前目录所有文件
   git commit -m "首次提交" #把暂存区的内容正式保存到Git仓库，并附上说明
   git remote -v          # 查看详细信息
   git clone git@github.com:yangshulin2333/yanzo_note2.git #ssh协议
   git clone https://github.com/yangshulin2333/yanzo_note2.git #https协议
   ```
	- ![350](assets/配置Obsidian/file-20251119200212550.png)
	- 注意：移动端暂不支持ssh协议 ![359](assets/配置Obsidian/file-20251119200446037.png)
5. 借助git插件设置Obsidian自动云同步到git

![](assets/配置Obsidian/file-20251119185228343%201.png)