工作区 -> git add -> 暂存区 -> git commit -> 本地库

# git 常用命令

**git config --global user.name 用户名
git config --global user.email 邮箱**
>保存在 C盘 用户下名为 .gitconfig

git init    初始化本地库
>会生成 .git 文件

git status    查看本地库状态

git add 文件名    添加到暂存区

git commit -m "日志信息" 文件名    提交到本地库

git reflog    查看历史记录

git reset --hard 版本号    版本穿梭

# 分支操作

git branch 分支名    创建分支

git branch -v    查看分支

git checkout 分支名    切换分支

git merge 分支名    把指定的分支合并到当前分支上
>分支切换到**当前分支**上，使用 ‘ git merge 分支名 ’，将**分支名中的文件**合并到**当前分支**上（正常合并）

合并冲突
>合并分支时，两个分支在同一个文件的同一位置有两套完全不同的修改
>此时必须人为决定新代码的内容

head 指向当前分支
master 指向当前的版本

# 远程仓库操作

git remote -v    查看当前所有远程地址别名

git remote add 别名 远程地址    给远程地址起别名

git push 别名 分支    推送本地分支上的内容到远程仓库

git clone 远程地址    将远程仓库的内容克隆到本地
>克隆不需要登录

git pull 远程库地址别名 远程分支名    将远程仓库对于分支最新内容拉下来后与当前本地分支直接合并
>拉取动作自动提交上库

# ssh 免密协议
C盘 用户文件下的 .ssh 文件夹

ssh-keygen -t rsa -C 991911081@qq.com

复制返回的代码，添加到 GitHub 的

--------

# 版本控制软件
...

# Git 
特性
* 直接记录快照，而非差异比较
* 近乎所有操作都是本地执行

SVN 的差异比较
传统的版本控制系统（例如 SVN）是基于差异的版本控制，它们存储的是一组基本文件和每个文件随时间逐步累积的差异
好处：节省磁盘空间
缺点：耗时、效率低
            在每次切换版本的时候，都需要在基本文件的基础上，应用每个差异，从而生成目标版本对应的文件。

Git 快照是在原有文件版本的基础上重新生成一份新的文件，类似于备份。为了效率，如果文件没有修改，Git 不再重新存储该文件，而是只保留一个链接指向之前存储的文件。
缺点：占用磁盘空间较大
优点：版本切换时非常快，因为每个版本都是完整的文件快照，切换版本时直接恢复目标版本的快照即可。
特点：空间换时间

# 三个区域
使用 Git 管理的项目，拥有三个区域，分别是**工作区、暂存区、Git 仓库**

# Git 三种状态
* 已修改 modified    
表示修改了文件，但还没将修改的结果放到暂存区
* 已暂存 staged
表示对已修改文件的当前版本做了标记，使之包含在下次提交的列表中
* 已提交 committed
表示文件已经安全地保存在本地的 Git 仓库中

注意：
工作区的文件被修改了，但还没有放到暂存区，就是已修改状态。
如果文件已修改并放入暂存区，就属于已暂存状态。 
如果 Git 仓库中保存着特定版本的文件，就属于已提交状态

# 工作流程
...

---

# Git 基础

## 安装
https://git-scm.com/downloads

## 配置用户信息
安装完 Git 之后，要做的第一件事就是设置自己的**用户名和邮件地址**。因为通过 Git 对项目进行版本管理的时候，Git 需要使用这些基本信息，来记录是谁对项目进行了操作

终端下
`git config --global user.name "yload"`
`git config --global user.email "991911081@qq.com"`
>注意：如果使用了 --global 选项，那么该命令只需要运行一次，即可永久生效

信息会被写入到 C:/Users/用户名文件夹/.gitconfig 文件中。这个文件是 Git 的全局配置文件，配置一次即可永久生效。

`git config --list --global`
查看配置信息

`git config user.name`
查看指定项

## 查看帮助信息

`git help <verb>` 命令，无需联网即可在浏览器中打开帮助手册
如果不想查看完整的手册，那么可以用 `-h` 选项获得更简明的“help”输出
`git config -h`

## 获取 Git 仓库的两种方式
将尚未进行版本控制的本地目录转换为 Git 仓库
从其它服务器克隆一个已存在的 Git 仓库
>以上两种方式都能够在自己的电脑上得到一个可用的 Git 仓库

## 在现有目录中初始化仓库
如果自己有一个尚未进行版本控制的项目目录，想要用 Git 来控制它，需要执行如下两个步骤：
在**项目目录**中，通过鼠标右键打开“Git Bash”
执行 `git init` 命令将当前的目录转化为 Git 仓库
>git init 命令会创建一个**名为 .git 的隐藏目录**，这个 .git 目录就是当前项目的 Git 仓库，里面包含了初始的必要文件，这些文件是 Git 仓库的**必要组成部分**。

## 工作区中文件的 4 种状态
* 未跟踪（Untracked）
不被 Git 所管理的文件
* 未修改（Unmodified）
工作区中文件的内容和 Git 仓库中文件的内容保持一致
* 已修改（Modified）
工作区中文件的内容和 Git 仓库中文件的内容不一致
* 已暂存（Staged）
工作区中被修改的文件已被放到暂存区，准备将修改后的文件保存到 Git 仓库中
>Git 操作的终极结果：让工作区中的文件**都处于“未修改”状态**

# Git 的基本操作
## 1.检查文件的状态
`git status`

新建的 index.html 文件出现在 **Untracked files**（未跟踪的文件） 下面
未跟踪的文件意味着 Git 在之前的快照（提交）中没有这些文件；Git 不会自动将之纳入跟踪范围，除非明确地告诉它“我需要使用 Git 跟踪管理该文件”

精简方式显示文件状态
`git status -s`
`git status --short`
>未跟踪文件前面有红色的`??`标记

## 2.跟踪新文件
使用命令 `git add` 开始跟踪一个文件。
`git add 文件名`
>此时再运行 git status 命令，会看到 index.html 文件在 **Changes to be committed** 这行的下面，说明已被跟踪，并处于暂存状态

>以精简的方式显示文件的状态：
新添加到暂存区中的文件前面有绿色的`A`标记

## 3.提交更新
现在暂存区中有一个 index.html 文件等待被提交到 Git 仓库中进行保存。可以执行 `git commit` 命令进行提交,其中 `-m` 选项后面是本次的**提交消息**，用来对提交的内容**做进一步的描述**
`git commit -m "描述信息"`

提示信息：
```
[master (root-commit) 7976e87] 描述信息
1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 index.html
```
查看状态信息：
```
On branch master
nothing to commit, working tree clean
```
证明工作区中所有的文件都处于“未修改”的状态，没有任何文件需要被提交

## 4.对已提交的文件进行修改
index.html 文件已经被 Git 跟踪，并且工作区和 Git 仓库中的 index.html 文件内容保持一致。当我们**修改**了工作区中 index.html 的内容之后，再次运行 git status 和 git status -s 命令

```
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   index.html

no changes added to commit (use "git add" and/or "git commit -a")
```
` M index.html`

文件 index.html 出现在 Changes not staged for commit 这行下面，说明已跟踪文件的**内容发生了变化**，但**还没有放到暂存区**。
>注意：**修改过的、没有放入暂存区**的文件前面有**红色的 M** 标记

## 5.暂存已修改的文件
目前，工作区中的 index.html 文件已被修改，如果要暂存这次修改，需要再次运行 git add 命令，这个命令是个多功能的命令，主要有如下 3 个功效：
* 可以用它开始跟踪新文件
* 把已跟踪的、且已修改的文件放到暂存区
* 把有冲突的文件标记为已解决状态
>**绿色的 M** 表示文件已修改且已放入暂存区

## 6.提交已暂存的文件
再次运行 `git commit -m "提交消息"` 命令，即可将暂存区中记录的 index.html 的快照，提交到 Git 仓库中进行保存

## 7.撤销对文件的修改（很少使用）
撤销对文件的修改指的是：把对工作区中对应文件的修改，还原成 Git 仓库中所保存的版本。
操作的结果：所有的修改会**丢失，且无法恢复**！危险性比较高，**请慎重操作**！
`$ git checkout -- index.html`
撤销操作的本质：用 Git 仓库中保存的文件，**覆盖**工作区中指定的文件

## 8.向暂存区中一次性添加多个文件
`git add .`

`.`表示选中了所有文件

>如果需要被暂存的文件个数比较多，可以使用如下的命令，一次性将所有的新增和修改过的文件加入暂存区
>今后在项目开发中，会经常使用这个命令，将新增和修改过后的文件加入暂存区

## 9.取消暂存的文件
如果需要从暂存区中移除对应的文件，可以使用如下的命令
`git reset HEAD 要移除的文件名`

## 10.跳过使用暂存区域
Git 提供了一个跳过使用暂存区域的方式， 只要在提交的时候，给 git commit 加上 `-a` 选项，Git 就会自动把所有已经跟踪过的文件暂存起来一并提交，从而跳过 git add 步骤
`git commit -a -m "描述信息"`

## 11.移除文件
从 Git 仓库和工作区中同时移除对应的文件
`git rm -f 文件名`
只从 Git 仓库中移除指定的文件，但保留工作区中对应的文件
`git rm --cached 文件名`

`D`开头表示下次提交文件的时候把文件删除

## 12.忽略文件
>一般我们总会有些文件无需纳入 Git 的管理，也不希望它们总出现在未跟踪文件列表。 在这种情况下，我们可以创建一个名为 .gitignore 的配置文件，列出要忽略的文件的匹配模式

文件 .gitignore 的格式规范如下：
* 以 # 开头的是注释
* 以 / 结尾的是目录
* 以 / 开头防止递归
* 以 ! 开头表示取反
* 可以使用 glob 模式进行文件和文件夹的匹配（glob 指简化了的正则表达式）

### glob 模式
所谓的 glob 模式是指简化了的正则表达式：
 星号 `*` 匹配零个或多个任意字符
 `[abc]` 匹配任何一个列在方括号中的字符 （此案例匹配一个 a 或匹配一个 b 或匹配一个 c）
 问号 `?`只匹配一个任意字符
 在方括号中使用短划线分隔两个字符， 表示所有在这两个字符范围内的都可以匹配（比如`[0-9]`表示匹配所有 0 到 9 的数字）
 两个星号 `**` 表示匹配任意中间目录（比如 `a/**/z 可以匹配 a/z 、 a/b/z 或 a/b/c/z 等`）

## 13.提交历史
`git log`
查看所有历史

`git log -2`
查看最近两条历史

`git log -2 --pretty=oneline`
在一行上展示最近两条提交历史的信息

## 14.回退到指定的版本
`git reset --hard 唯一ID`
回退到指定的 ID 版本号上（配合提交历史查看 ID）

回退之后要使用`git reflog --pretty=oneline`才能查看旧版本的命令操作历史
>直接使用 `git log` 查看的是从回退版本开始的历史

## 小结
初始化 Git 仓库的命令
 `git init`
查看文件状态的命令
 `git status` 或 `git status -s`
一次性将文件加入暂存区的命令
 `git add .`
将暂存区的文件提交到 Git 仓库的命令
 `git commit -m "提交消息"`
