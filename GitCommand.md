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
+ `HEAD` 指向版本是当前版本。穿梭版本可以使用指令`git reset --hard commid_id`
+ 穿梭前，用`git log`可以查看提交历史，以便确认回退到哪个版本
+ 重返未来，用`git reflog`查看命令历史，以便确认恢复到哪个版本

##7. 撤销、删除文件
+ 只在工作区的修改： 可以通过指令 `git checkout -- filename` 撤销修改 ，或者直接手工修改。
+ 已在暂存区更新的修改： 需要退回到上一步，即回退到工作区中，使用指令`git reset HEAD filename`; 
  此时再对回到工作区的文件进行修改。
+ 如果提交到了版本库，那么就需要通过版本回退撤销修改，具体参考第6项。

另外，如果提交到了远程仓库，那就没救了……

##8. 远程仓库的创建与使用
+ 注册GitHub帐号。（帐号和邮箱地址可以跟本地的不同）
+ 创建SSH Key 
  先看看`/root/.ssh/`下有没有`id_rsa`和`id_rsa.pub`这两个文件，如果有说明已经建立了SSH Key。
  
```
$ ssh-keygen -t rsa -C "yourmail@example.com"
```
  建立成功的话，会在`/root/.ssh/` 下看到`id_rsa`和`id_rsa.pub`这两个文件，其中`id_rsa`是私钥，不能泄漏出去，`id_rsa.pub`这个是公钥，可以告诉任何人。

+ 登录GitHub, 打开"Account Settings", "SSH Keys"页面； 在"Add SSH Key"上填上任何Title, 在Key文本框里面粘帖`id_rsa.pub`里的内容。最后点击“Add Key“，完成。

+ 在GitHub上创建一个仓库"Create a new repo"，在Repository name 填入`learngit`，其他的默认。点击"Create repository" 创建完毕。
  此时在GitHub上建立的learngit仓库是一个空仓库。需要将本地仓库关联上远程仓库

+ 本地仓库关联远程仓库：

```
$ git remote add origin git@github.com:JenneyHong/learngit
```
+ 将本地的所有内容推送到远程库中

```
$ git push -u origin master
```

之后的每次修改，使用指令`git push origin master`推送到远程仓库中

##9. 分支管理
+ 查看分支： `git branch`
+ 创建分支： `git branch <name>
+ 切换分支： `git checkout <name>
+ 创建 & 切换分支: `git checkout -b <name>
+ 合并分支到当前分支： `git merge <name>
+ 删除分支： git branch -d <name> 

##10. 解决冲突
  当Master和branch都有新的更新，并且二者的更新不一样时，不能使用快速合并。
  此时，需要手动修改两者冲突后再提交
  `git log --graph`可以看到分支合并图

##








