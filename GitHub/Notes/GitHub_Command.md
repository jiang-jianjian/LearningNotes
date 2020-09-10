# Git&GitHub操作命令

## 基本操作-Git本地仓库

### Git配置

	* `git config`Git仓库配置
		* 使用示例：`git config --global user.name Jjj`
			    `git config --global user.email Jjj@demon.com`
		* 其它用法：`git config --list`查看已有配置信息

### 仓库创建命令
	
	* `git init` 版本库初始化
		* 使用示例：`git init`回车执行后，当前路径出现`.git`隐藏文件夹

	* `git clone`远程仓库克隆
		* 使用示例：`git clone 远程仓库连接 Cloning into 目标路径`克隆指定远程仓库至指定路径

### 提交与修改

	* `git add` 添加一个或多个文件至缓存区
		* 使用示例：`git add [file1] [file2] ...`添加一个或多个文件至暂存区
			    `git add [dir]`添加指定目录（包括该目录下所有文件及子目录）到暂存区
			    `git add .`添加当前目录下所有文件至暂存区
			    `git add *.txt`添加当前目录下所有`.txt`文件至暂存区，`*`为通配符

	* `git commit` 将暂存区内容提交至Git仓库保存
		* 使用示例：`git commit -m "提交说明、备注信息等"`将暂存区内容提交至Git仓库保存
			    `git commit file1 file2 ... -m "提交说明、备注信息等"`将暂存区内指定文件提交至仓库保存

	* `git status`查看Git仓库当前状态
		* 使用示例：`git status`查看上次提交之后是否有对仓库内文件进行修改
			    `git status -s`参数`-s`用于获得简短的输出信息

	* `git diff`比较文件的不同
		* 使用示例：`git diff`查看工作区尚未提交暂存区的改动；`git diff --cached`查看暂存区尚未提交仓库的改动
			    `git diff [file]`比较该文件在工作区与暂存区的不同
			    ·git diff --cached [file]·或者`git diff --staged [file]`比较该文件暂存区和上一次提交的差异
			
	* `git reset`版本回退
		* 使用示例：`git reset [head]`不带参数，重置暂存区的文件与指定提交版本保持一致，工作区文件内容保持不变
			    `git reset HEAD^`回退暂存区所有内容至上一版本
			    `git reset HEAD^ [file]`回退暂存区指定文件至上一版本
			    `git reset --soft [HEAD]`--soft参数用于回退到某个版本
			    `git reset --hard [HEAD]`--hard 参数撤销工作区中所有未提交的修改内容，将暂存区与工作区都回到指定版本，并删除之前的所有信息提交
			    `HEAD^`上一次版本;`HEAD^^`上上次版本;`HEAD^^^`上上上次版本;`HEAD~0`当前版本;`HEAD~1`上次版本;`HEAD~2`上上次版本。

	* `git rm`删除文件
		* 使用示例：先执行`rm a.txt`,再执行`git rm a.txt`将文件`a.txt`从`工作区删除`
			   `git rm -f a.txt`强制删除已作修改并提交至暂存区的文件
			   `git rm --cached a.txt`将文件从暂存区移除但仍保留在工作区

	* `git mv`文件移动或重命名
		* 使用示例：`git mv file_from file_to`将文件重命名或移动路径

### 撤销操作
	
	* `git commit --amend`当提交后发现漏提交文件或提交出错，使用该提交语句重新提交，覆盖上次提交
		* 使用示例：`git commit -m "initial commit"`
			    `git add forgotten_file`
			    'git commit --amend'执行上述操作后，只会有一次提交，前一次提交被覆盖

	* `git checkout -- [file]`丢弃指定文件在工作区的修改

	* `git reset HEAD [file]`取消对该文件的暂存操作,即撤销`git add [file]`效果


### 日志查看

	* `git log`查看日志/提交记录
		* 使用示例：`git log`查看所有提交记录
		            `git log -p`按补丁格式查看每次提交的差异
			    `git log -2`查看最近的2次提交记录
			    `git log --graph`以图标的形式查看提交记录
			    `git log --pretty=short`查看简短、精简的提交记录
			    `git log --pretty=online --author=Jjj --since=2020-08-01 --until=2020-09-01`

	* `git blame <file>`以列表形式查看指定文件的修改记录


## 提高操作-GitHub远程操作

### 远程仓库添加、连接    

	* `git clone`远程仓库克隆至本地
		* 使用示例：`git clone https://github.com/jiang-jianjian/LearningNotes.git Clone into 'LearningNotes'`
			    
	* `git remote add [简称/缩略名] [远程仓库URL]`添加一个远程仓库，并指定一个方便应用的简称

	* `git remote`查看已克隆或以配置连接的远程仓库服务器地址 `git remote -v`添加参数`-v`查看所有远程仓库连接及所对应保存的简称

### 获取与推送

	* `git fetch`抓取远程仓库数据至本地数据，只抓取不merge。需手动执行`git merge`合并分支、修改或冲突
		* 使用示例：`git fetch origin master`拉取远程仓库`origin`下`master`分支数据至本地

	* `git pull`抓取远程仓库数据至本地，并自动尝试合并修改、冲突
		* `git pull origin master:localbranch`拉取远程仓库`origin`下的`master`分支数据至本地，并尝试和本地分支`localbranch`合并

	* `git push`推送本地仓库数据至远程仓库
		* `git push origin master:localbranch`将本地分支`localbranch`数据上传至远程仓库`origin`，并与`master`分支合并

### 远程仓库删除与重命名

	* `git remote rename name new_name`修改远程仓库的简称

	* `git remote rm origin`删除仓库origin

### 分支操作
       
	* `git branch new_branch`创建新分支

	* `git checkout branch_name`切换至名未`branch_name`的分支
		* 使用示例：`git checkout -b new_branch`创建并切换至新分支

	* `git merge branch_name`将名为`branch_name`的分支合并至当前所处分支

	* `git branch -d branch_name`删除名为`branch_name`的分支

	* `git branch`查看所有分支,`git branch --merged`查看已合并至当前分支的分支,`git branch --no merged`查看未合并至当前分支的分支

### Git 标签

	* `git tag`查看当前所有标签

	* `git tag tag_name`创建轻量级标签

	* `git tag -a tag_name -m 'tag message'`创建附注标签


