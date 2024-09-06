#### 一、git和版本库

git是分布式版本控制系统，svn是集中式的版本控制系统。**版本控制系统** 只能跟踪文本文件的改动，比如txt文件、网页、程序代码。


- 分布式版本控制系统：每一台计算机都有完整的版本库
- 集中式版本控制系统，版本库存放在中央服务器

**版本库**（仓库）：repository，创建版本库如下：

```shell
mkdir learngit #创建空目录
cd learngit #切换指定路径
pwd #显示当前目录
ls #查看当前目录的文件
git init #将learngit这个目录变成Git可以管理的仓库，初始化Git仓库
```

在learngit目录下多了一个 `.git` 的目录，用来跟踪管理版本库的，默认隐藏，用 `ls -ah` 命令可以显示。


##### 1.1、将文件放在Git仓库步骤

 现有一个文件 `readme.txt` :

```
Git is a version control system.
Git is free software.
```

1. ```shell
   git add readme.txt #将文件添加到仓库
   ```

2. ```shell
   git commit -m 'wrote a readme file' #把文件提交到仓库，可以一次提交很多文件
   ```


##### 1.2、修改后提交

 修改了 `readme.txt` 文件(add distributed)**~版本2~**：

```
Git is a distributed version control system.
Git is free software.
```

掌握工作区==当前状态== `git status`

查看==修改内容== `git diff readme.txt`

 接下来把修改过后的文件提交到仓库中：

```shell
git add readme.txt
git commit -m 'add distributed'
```

 显示从最近到最远的==提交日志历史，用来回退==`git log` 或删减版 `git log --pretty=oneline` 其中一大串符号是 `commit id` 版本号

继续修改 `readme.txt` 文件(append GPL)**~版本3~**：

```
Git is a distributed version control system.
Git is free software distributed under the GPL.
```


##### 1.3、版本回退

 将当前**~版本3~**回退到上一个**~版本2~** 使用 `git reset` 命令：

```shell
git reset --hard HEAD^ #HEAD表示当前版本，上一个版本是HEAD^,上上个HEAD~2
```

==查看当前文本内容（即工作区的文件内容）==：`cat readme.txt`

 再运行 `git log` 命令已经查不到**~版本3~**的版本号，如果上面的命令行窗口未关掉，可以找到该版本`commit id` ，指定回到该版本；如已关闭命令行，可以使用 `git reflog` 查看==命令历史，用来去到未来==其中含有版本号：

```shell
git reset --hard 999b
```

##### 1.4、工作区和暂存区

 `learngit` 文件夹是一个工作区（working directory)，隐藏的目录.git是版本库(repository)，其中包含暂存区(stage/index)和当前分支(master)。

`git add <file>` 工作区>>暂存区

`git commit <file>`暂存区>>当前分支

 `git status` 查看工作区状态

 `git diff <file>` 查看工作区&暂存区差异

 `git diff HEAD -- <file>` 查看工作区&分支差异，+号代表工作区变动，-号代表分支变动

 反向命令`git restore <file>` 工作区做了修改，并未添加到暂存区，撤销工作区修改

 `git add` 反向命令 `git restore --staged <file>` 先暂存区>>工作区，再撤销工作区修改

 `git commit`反向命令`git reset --hard HEAD^` 工作区和版本库版本回退为上次的内容


##### 1.5、删除文件

1. 手动删除文件或`rm <file>` 之后 `git add <file>` `git commit <file>`
2. `git rm <file>` `git commit <file> -m '从版本库删除'`

#### 二、远程仓库

##### 2.1、GitHub-git远程仓库

 本地Git仓库和GitHub仓库之间传输是通过SSH加密，需如下设置：

1.  创建SSH Key。在用户主目录下查看有无`.ssh`目录，查看`.ssh`目录下有无秘钥对`id_rsa`（私钥）和`id_rsa.pub`（公钥）这两个文件。`open ~/.ssh`

   创建SSH Key:

   ```shell
   ssh-keygen -t rsa -C "youremail@example.com"
   ```

​	拷贝生成的公钥内容：`*pbcopy < ~/.ssh/id_rsa.pub  *`

2.  登陆GitHub，打开"Account settings","SSH Keys","Add SSH Key"


##### 2.2、添加远程库

1.  登陆GitHub，在右上角“Create a new repo”🔘创建Git仓库`learngit` 

2.  在本地的`learngit`仓库下运行命令(功能就是给后面这个链接起了一个名字叫做origin)：

   ```shell
   git remote add origin https://github.com/yizhen212/learngit.git
   ```

3. 远程库是`origin`，把本地库的所有内容推送到GitHub远程库上：

   ```shell
   git push -u origin master #git push命令，是把当前分支master推送到远程
   ```

   第一次推送`master`分支时，加上了`-u`参数，在以后的推送或者拉取时就可以简化命令。

4. 解除本地和远程的绑定关系：

   查看远程库信息：`git remote -v` 

   解除关系（删除远程库）：`git remote rm <name>` 

5. 用`git clone` 克隆远程库，Git支持多种协议，`https` .`ssh` 协议速度最快


#### 三、分支管理

##### 3.1、创建合并分支

`master` 是主分支，`HEAD` 指向当前分支。

首先创建新的分支`dev` 分支：`git branch dev` ,切换到当前分支`git checkout dev` ，以上两条命令可以用一条命令表示创建并切换：

```shell
git checkout -b dev
```

 查看当前分支：`git branch` 

