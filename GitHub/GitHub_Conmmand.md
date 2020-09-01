# Git&GitHub操作命令

## 基本操作-Git本地仓库

### Git配置

	* `git config`Git仓库配置<br>
		* 配置示例：`git config --global user.name Jjj`<br>
			    `git config --global user.email Jjj@demon.com`<br>
		* 其它用法：`git config --list`查看已有配置信息<br>

### 仓库创建命令
	
	* `git init` 版本库初始化<br>
		* 使用示例：`git init`回车执行后，当前路径出现`.git`隐藏文件夹<br>

	* `git clone`远程仓库克隆<br>
		* 使用实例：`git clone https://github.com/jiang-jianjian/Learn_Notes.git Cloning into 目标路径`克隆指定远程仓库至指定路径<br>

### 提交与修改

	* `git add` 添加一个或多个文件至缓存区<br>
		* 使用语法：`git add [file1] [file2] ...`添加一个或多个文件至暂存区<br>
			    `git add [dir]`添加指定目录（包括该目录下所有文件及子目录）到暂存区<br>
			    `git add .`添加当前目录下所有文件至暂存区<br>
			    `git add *.txt`添加当前目录下所有`.txt`文件至暂存区，`*`为通配符<br>
	
	* `git checkout `

	* `git commit` 将暂存区内容提交至Git仓库保存<br>
		* 使用语法：`git commit -m "提交说明、备注信息等"`将暂存区内容提交至Git仓库保存<br>
			    `git commit file1 file2 ... -m "提交说明、备注信息等"`将暂存区内指定文件提交至仓库保存<br>

	* `git status`查看Git仓库当前状态<br>
		* 使用语法：`git status`查看上次提交之后是否有对仓库内文件进行修改<br>
			    `git status -s`参数`-s`用于获得简短的输出信息<br>

	* `git diff`

	* `git reset`

	* `git rm`

	* `git mv`

### 日志查看

	* `git log`

	* `git blame <file>`

## 提高操作-GitHub远程库

### 远程仓库添加、连接

### 获取与推送

	* `git remote`

	* `git fetch`

	* `git pull`

	* `git push`

### 分支操作

### Git 标签
