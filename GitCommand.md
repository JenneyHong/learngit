# Git Command

##1. 安装Git.
  由于BT5 已经安装好git了，所以这里列出安装步骤：

+ 直接用指令：

```
sudo apt-get install git
```

+ 通过源码安装，适用于其他linux版本
  先从Git官网下载源码，然后解压，依次输入：`./config`,`make`,`sudo make install`

##2. git 设置

```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

##3. 创建git 仓库（repository)

+ 创建一个空目录，用来存放仓库

```
$ mkdir learngit
$ cd learngit
$ pwd
/User/michael/learngit
```

+ 通过`git init`这个命令将目录变成git可以管理的仓库

```
$ git init
Initialized empty Git repository in /Users/michael/learngit/.git/
```
  建立了一个空的仓库，其中`.git/`这个是隐藏的目录，这个目录是git用来跟踪管理版本库的。不要乱改和乱删。

##4. 添加文件到git库中。

+ 在仓库的目录（/User/michael/learngit）下创建一个`readme.txt`文件。
文件内容如下：

```
  Git is a version control system.
  Git is free software.
```

+ 使用指令`git add`告诉git,把文件添加到仓库中：

```
$ git add readme.txt
```

+ 使用`git commit` 告诉git, 把文件提交到仓库：

```
 $ git commit -m "wrote a readme file"
[master (root-commit) cb926e7] wrote a readme file
 1 file changed, 2 insertions(+)
 create mode 100644 readme.txt
```

  总之，创建了一个库之后，需要初始化这个仓库， `git init`
  添加文件到仓库中，一共需要两步：
  + 第一步，添加文件 `git add <file>`
  + 第二步，上交文件 `git commit`.

##5. 修改文件
  修改readme.txt的内容：

```
 Git is a distributed version control system.
 Git is free software.
```

修改之后，使用`git status`命令来查看git的状态。`git status`会显示有文件被修改了。

添加修改的文件：

```
 git add readme.txt
 git diff       //查看文件修改的情况
```

重新上传到仓库中：

```
 git commit -m "add distributed"
```

##6. 版本回退
+ `HEAD` 指向版本是当前版本。穿梭版本可以使用指令`git reset --hard commid_id
+ 穿梭前，用`git log`可以查看提交历史，以便确认回退到哪个版本
+ 重返未来，用`git reflog`查看命令历史，以便确认恢复到哪个版本





