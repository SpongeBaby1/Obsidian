---
alias: GitHub workflow
year: 2023.5.8
sort: Guide
nation: Chinese
crew: 
rate: 1st Finished
info: VScode, Git, GitHub, and Obsidian.
date: 2023-05-08-Monday 15:11:07
update: 2023-05-11-Thursday 22:05:46
tags: [read/year2023, read/month05]
id: read20230508151107
---
---

# 1 Openssh
## 1.1 Installation
1. 去github上找到OpenSSH的release安装包：[Releases · PowerShell/Win32-OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases)
2. 解压到C盘的program files
3.  在高级系统设置->环境变量 添加ssh的目录到path
   ![[Pasted image 20230510105703.png]]
4. 命令行输入ssh出现下面的界面就是成功啦
   ![[Pasted image 20230510105917.png]]
5. 在提升的 Powershell 控制台中运行以下命令：
   `powershell.exe -ExecutionPolicy Bypass -File install-sshd.ps1`
6. 打开防火墙以允许入站SSH连接到sshd.exe：
   `New-NetFirewallRule -Name sshd -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22`
7. 启动sshd
  `net start sshd`
8. 选项
	-  To configure a default shell, see [here](https://github.com/PowerShell/Win32-OpenSSH/wiki/DefaultShell) 
	- To setup `sshd` service to auto-start
	  `Set-Service sshd -StartupType Automatic`
	- To migrate `sshd` configuration from older versions (0.0.X.X), see [here](https://github.com/PowerShell/Win32-OpenSSH/wiki/Migrate-sshd_config-from-older-versions)

- [Home · PowerShell/Win32-OpenSSH Wiki · GitHub](https://github.com/PowerShell/Win32-OpenSSH/wiki)
---

## 1.2 验证openssh功能是否正常

1. **验证 OpenSSH 客户端**：
	-   打开命令提示符或终端窗口。
	-   运行以下命令来检查 OpenSSH 客户端是否可用：`ssh -V`
2. **验证 OpenSSH 服务器**：
	-   打开命令提示符或终端窗口。
	-   运行以下命令来启动 OpenSSH 服务器：`net start sshd`
3. **尝试本地 SSH 连接**：
	-   打开命令提示符或终端窗口。
	-   运行以下命令以使用 OpenSSH 客户端进行本地连接：`ssh devil@localhost`(使用本地连接)
---

## 1.3 Connect to Github in Vscode
1. 查看密钥对列表`ls ~/.ssh`
2. 删除密钥对：`rm ~/.ssh/id_rsa`, `rm ~/.ssh/id_rsa.pub` 
3. 从相关系统和服务中删除对该公钥的授权。
4. **重新生成密钥对**：`ssh-keygen -t rsa -b 4096 -C "2546342365@qq.com"`
   ![[Pasted image 20230510154906.png]]
5. **添加公钥到 GitHub 账户**：
   - 使用文本编辑器打开生成的公钥文件（默认为 ~/.ssh/id_rsa.pub）。
     `notepad C:\Users\devil/.ssh/id_rsa.pub`
   - 复制公钥文件中的内容。
   - 登录到你的 GitHub 账户。
   - 点击右上角的头像，选择 "Settings"。
   - 在左侧导航栏中，选择 "SSH and GPG keys"。
   - 点击 "New SSH key"。
   - 在 "Title" 字段中，为该密钥提供一个描述性的名称。
   - 在 "Title" 字段中，为该密钥提供一个描述性的名称。
   - 点击 "Add SSH key"。
6. **测试 SSH 连接**：
   - 在命令提示符或终端窗口中，运行以下命令测试 SSH 连接：`ssh -T git@github.com`
   - 如果连接成功，邮箱将收到一条欢迎消息：`Hi SpongeBaby1! You've successfully authenticated, but GitHub does not provide shell access.`(**you can interact with your GitHub repositories using Git commands locally on your machine or through the GitHub website or API. **)
---


# 2 使用git管理github

## 2.1 Git本地数据管理
1. Git本地数据管理分为三个区域
	 1. 工作区(.git所在目录):实际操作的目录
	 2. 暂存区(.git/index):用于保存即将提交到Git仓库的修改内容.
	 3. 本地仓库(.git/objects):Git存储代码和版本信息的主要位置.
	  ![[Pasted image 20230511153356.png]]
2. Git本地数据管理流程
	 1. 在本地的工作区(`working directory`)/生产车间修改完成后,通过`git add`命令将本地的阶段性修改(多次修改)提交到暂存区(`staging area`)/运输车.
	  ![[Pasted image 20230511154034.png]]
	 2. 通过`git commit`命令将暂存区(`staging area`))/运输工具的修改内容提交到本地仓库(`local repository`)/本地仓库.
	  ![[Pasted image 20230511153855.png]]
3. 本地文件的几种状态
	  1. untrack(未跟踪)
	  2. unmodified(未修改)
	  3. modified(已修改)
	  4. staged(已暂存)
	 ![[Pasted image 20230511160829.png]]
4. Appendix
	[04.工作区域和文件状态\_哔哩哔哩\_bilibili](https://www.bilibili.com/video/BV1HM411377j/?p=4&vd_source=4f4f9eaa7c3c2df88a108df3464284bc)
---

## 2.2 Github工作流



- [十分钟学会正确的github工作流，和开源作者们使用同一套流程\_哔哩哔哩\_bilibili](https://www.bilibili.com/video/BV19e4y1q7JJ/?spm_id_from=333.999.0.0&vd_source=4f4f9eaa7c3c2df88a108df3464284bc)
---

## 2.3 Obsidian同步备份至github
1. `git init` 初始化本地仓库.
2. `git config --global user.name devil`, `git config --global user.email 2546342365@qq.com` 配置全局用户名和用户邮箱.
3. `git status` 查看分支状态, 红色表示**unstaged**.
4. 新建`.gitignore`文件, 写入`.obsidian`和`.trash`
5. `git branch --list` 查看本地分支.
6. `git add ./--all` 将所有修改提交至暂存区(**unstaged $\rightarrow$ staged**).
7. `git status` 查看此时的分支状态, 绿色表示修改已提交至暂存区.
8. `git commit -m '1stmodification'`将暂存区的修改提交至本地仓库.
9. `git remote add origin git@github.com:SpongeBaby1/Obsidian.git`连接远程仓库. 
10. `git remote -v` 查看远程仓库的名称和URL, 出现以下代码表示远程连接成功, 可以进行`pull/push`等操作.
   ![[Pasted image 20230511213702.png]]
11. `git branch --all` 检查是否连接到远程仓库中的branch.
12. `git pull origin master --allow-unrelated-histories` 合并两个没有共同祖先的仓库.
13. `git commit -m "20230510Firstcommit"`
14. `git push -u origin master`
15. `git pull origin master --allow-unrelated-histories`

[【Obsidian】多端同步和备份方案\_哔哩哔哩\_bilibili](https://www.bilibili.com/video/BV1RF411K7aN/?spm_id_from=333.337.search-card.all.click&vd_source=4f4f9eaa7c3c2df88a108df3464284bc)

---

## 2.4 Git Command
1. `git checkout -b my-feature`
	1. `git checkout` 是 Git 命令用于切换分支或还原文件的工作树。
	2. `-b` 选项用于创建一个新的分支.
	3.  `my-feature` 是新分支的名称.
2. `git remote -v`  查看远程仓库的详细信息, 包括branch名称和URL, `-v`表示详细信息.
3. `git branch/git branch -l` 列出本地仓库中的所有branch, `l`表示`list`的缩写.
4. `git branch -r`, 列出远程仓库中的所有branch, `r`表示`remote`的缩写.
5. `git branch -a` 列出本地仓库和远程仓库中的所有branch, `a`是`all`的缩写.
6. `git add ./--all` 将所有修改提交至暂存区(**unstaged $\rightarrow$ staged**).
7. `git commit -m '1stmodification'`将暂存区的修改提交至本地仓库.


9. `git pull origin master --allow-unrelated-histories` 允许合并两个独立的没有共同祖先的分支历史.
10. `git fetch origin master` 获取远程仓库的最新提交.
    `git merge origin master --allow-unrelated-histories` 允许合并两个独立的没有共同祖先的分支历史.
1. `git status` 检查合并后后分支的状态, 如果没有出现冲突的提示，并且状态显示为 "up to date" 或 "nothing to commit, working tree clean"，则表示合并成功.
2. `git log` 查看分支的提交历史, 确认合并后的提交是否出现在分支的历史记录中.
3. `git diff/show` 查看合并后的代码变动, 并根据需要进行代码审查和测试.
总之，要确定合并是否正确，需要综合考虑分支状态、提交历史、代码差异以及功能测试等方面的信息。

13. `git push -u origin master`将本地修改推送至远程仓库.



# 3 Remote Ssh via Vscode



---