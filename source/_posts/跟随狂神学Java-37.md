---
title: 跟随狂神学Java-37，Git
date: 2023/08/06 04:02:22
tags:
  - Java
  - 狂神
  - 分布式
  - Git
  - Github
  - 必看
categories:
  - [跟随狂神学Java]
  - [必看]
  - [技术]
  - [Java]
cover: https://resource.joker2yue.cn/blog/images/coverImg/Vue/git.png
keywords:
  - 版本控制
  - Git
  - SVN
  - 分布式
  - 工作目录
  - 暂存区
  - 本地仓库
  - 远程仓库
  - 分支管理
ai:
  - 这篇文章介绍了Git版本控制工具的基本概念和用法，以及与其他版本控制工具的比较。它强调了版本控制的重要性，特别是在多人协同开发项目中。文章还讲解了Git的历史和基本工作流程，包括工作目录、暂存区、本地仓库和远程仓库之间的关系。此外，还介绍了如何在Git中查看文件状态、忽略文件、使用码云进行远程仓库管理，以及在IDEA中集成Git的方法。最后，文章提到了Git分支的概念和常用指令，强调了在多人协同开发中如何使用分支管理工作流程。
  - 这篇文章介绍了Git的基本概念和用法，包括版本控制、常见的版本控制工具、版本控制的分类，以及Git的历史和环境配置。文章还提到了基本的Linux命令学习和Git基本理论，包括Git的工作流程和文件操作。最后，文章介绍了如何在码云上创建仓库、在IDEA中集成Git、以及Git的分支管理。
  - 本文全面阐述了Git版本控制的核心概念、工具选型、版本控制类型、Git发展历史、环境配置、Linux命令、文件操作、码云使用、IDEA集成和分支管理等方面的知识，为多人协同开发项目提供了重要指导。
copyright: true
copyright_author: joker2yue
copyright_author_href: https://github.com/Joker2Yue
copyright_url: https://github.com/Joker2Yue/Joker2Yue-Blog
---
# 跟随狂神学Java
> 作者：[joker2yue](https://github.com/Joker2Yue)
> 链接：https://github.com/Joker2Yue/Joker2Yue-Blog
> 来源：Github
> 著作权归原作者所有。商业转载请联系原作者获得授权，非商业转载请注明出处。
**第三十七：Git**

> "真正的危险不是计算机开始像人一样思考，而是人开始像计算机一样思考。"
>
> [【狂神说Java】Git最新教程通俗易懂_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1FE411P7B3/?vd_source=814489e71df641c4b2c0ff7d4659b2d0)



#### 版本控制

---

##### 什么是版本控制

版本控制（ Revision control）是一种在开发的过程中用于管理我们对文件、目录或工程等内容的修改历史，方便查看更改历史记录，备份以便恢复以前的版本的软件工程技术。

* 实现跨区域多人协同开发
* 追踪和记载一个或者多个文件的历史记录
* 组织和保护你的源代码和文档
* 统计工作量
* 并行开发、提高开发效率
* 跟踪记录整个软件的开发过程
* 减轻开发人员的负担，节省时间，同时降低人为错误

简单说就是用于管理多人协同开发项目的技术。

​	没有进行版本控制或者版本控制本身缺乏正确的流程管理，在软件开发过程中将会引入很多问题，如软件代码的一致性、软件内容的冗余、软件过程的事物性、软件开发过程中的并发性、软件源代码的安全性，以及软件的整合等问题。

​	无论是工作还是学习，或者是自己做笔记，都经历过这样一个阶段！我们就迫切需要一个版本控制工具！|

​	多人开发就必须要使用版本控制，否则代价会比较大

---

##### 常见的版本控制工具

* **Git**
* **SVN**（Subversion）
* **CVS**（Concurrent Versions System）
* **VSS**（Micorosoft Visual SourceSafe）
* **TFS**（Team Foundation Server）
* Visual Studio Online

​	版本控制产品非常的多（Perforce、RationaI CIearCase、RCS（GNU Revision ControI System）、Serena Dimention、SVK、BitKeeper、Monotone、Bazaar、Mercurials SourceGear VauIt），现在影响力最大且使用最广泛的是 Git 与 SVN

---

##### 版本控制分类

* **本地版本控制**

  ​    记录文件的每次的更新，可以对每个版本做一个快照，或是记录补丁文件，适合个人用，如RCS

  <img src="images/跟随狂神学Java-37/image-20230804174741512.png" alt="image-20230804174741512" style="zoom:50%;" />

* **集中版本控制**

  所有的版本数据都保存在服务器上，协同开发者从服务器上同步更新或上传自己的修改

  <img src="images/跟随狂神学Java-37/image-20230804174835670.png" alt="image-20230804174835670" style="zoom:50%;" />

  ​       所有的版本数据都存在服务器上，用户的本地只有自己以前所同步的版本，如果不连网的话，用户就看不到历史版本也无法切换版本验证问题，或在不同分支工作。而且，所有数据都保存在单一的服务器上，有很大的风险。如果这个服务器损坏，这样就会丢失所有的数据。当然，可以定期备份。代表产品： SVN、SVC、VSS

* ##### 分布式版本控制

  ​	所有版本信息仓库全部同步到本地的每个用户，这样就可以在本地查看所有版本历史，可以离线在本地提交，只需在连网时 push 到相应的服务器或其他用户那里。由于每个用户那里保存的都是所有的版本数据，只要有一个用户的设备没有问题就可以恢复所有的数据，但这增加了本地存储空间的占用。

  <img src="images/跟随狂神学Java-37/image-20230804175313286.png" alt="image-20230804175313286" style="zoom:50%;" />

  每个人都拥有全部的代码！安全隐患！但是也能够避免服务器异常造成的无法工作的现象



Git和SVN的最主要区别

* SVN 是集中式版本控制系统，版本库是集中放在中央服务器的，而工作的时候，用的都是自己的电脑，所以首先要从中央服务器得到最新的版本，然后工作。完成工作后，需要把自己做完的活推送到中央服务器。集中式版本控制系统是必须联网才能工作，对网络带宽要求较高。
* Git 是分布式版本控制系统，没有中央服务器，每个人的电脑就是一个完整的版本库，工作的时候不需要联网了，因为版本都在自己电脑上。协同的方法是这样的：比如说自己在电脑上改了文件 A ，其他人也在电脑上改了文件 A ，这时，你们两之间只需把各自的修改推送给对方，就可以互相看到对方的修改了，能够直接看到更新了哪些代码和文件。
* **==Git 是目前世界上最先进的分布式版本控制系统==**





#### Git的历史

---

​	同生活中的许多伟大事物一样， Git 诞生于一个极富纷争大举创新的年代。

​	Linux 内核开源项目有着为数众广的参与者。绝大多数的 Linux 内核维护工作都花在了提交补丁和保存归档的繁琐事务上（1991 -2002 年间）。到 2002 年，整个项目组开始启用一个专有的分布式版本控制系统 BitKeeper 来管理和维护代码。

​	到了 2005 年，开发 BitKeeper 的商业公司同 Linux 内核开源社区的合作关系结束，他们收回了 Linux 内核社区免费使用BitKeeper 的权力。这就迫使 Linux 开源社区（特别是 Linux 的缔造者 Linus Torvalds）基于使用 BitKeeper 时的经验教训，开发出自己的版本系统。也就是后来的 Git！

​	Git 是目前世界上最先进的分布式版本控制系统。

​	Git 是免费、开源的，最初 Git 是为辅助 Linux 内核开发的，来替代 BitKeeper ！



#### Git环境配置

---

git官网[Git (git-scm.com)](https://git-scm.com/)

镜像站[CNPM Binaries Mirror (npmmirror.com)](https://registry.npmmirror.com/binary.html?path=git-for-windows/)





#### 基本的Linux命令学习

---

1. `cd`	改变目录

2. `cd .. `  回退到上一个目录

3. `pwd` 显示当前所在的目录路径

4. `ls ` ,`ll`  都是列出当前目录的所有文件，但是`ll`更加详细

5. `touch` 新建文件，如`touch index.js`为在当前目录下新建一个index.js文件

6. `rm` 删除一个文件，`rm index.js`将会删除index.js

7. `mkdir` 新建一个目录（文件夹）

8. `rm -r` 删除一个文件夹，`rm -r src`删除src目录

   ~~~bash
   rm -rf /
   # 切勿在Linux中尝试

9. `mv` 移动文件，如`mv index.html src` ，index.html 为我们要移动的文件，src为目标文件夹，目标文件和文件夹需要在同一个目录下

10. `reset` 重新初始化终端/清屏

11. `clear` 清屏

12. `history` 查看命令历史

13. `help` 帮助

14. `exit` 退出

15. `#` 为注释





#### Git基本理论

---

##### 基本结构

Git 本地有三个工作区域：工作目录（ Working Directory ）、暂存区 (Stage/lndex) 、资源库 (Repository 或 Git Directory)。如果再加上远程的 git 仓库 (Remote Directory)  就可以分为四个工作区域。文件在这四个区域之间的转换关系如下

<img src="images/跟随狂神学Java-37/image-20230805193832253.png" alt="image-20230805193832253" style="zoom:50%;" />

* Workspace：工作区，平时存放代码的地方
* Index/Stage：暂存区，用于临时存放你的改动，事实上它只是一个文件，保存即将提交到文件列表信息
* Repository：仓库区（或本地仓库）。就是安全存放数据的位置，这里面有你提交到所有版本的数据。其中HEAD指向最新放入仓库的版本
* Remote：远程仓库。托管代码的服务器，可以简单的认为是你项目组中的一台电脑用于远程数据交换

本地的三个区域确切的说应该是git仓库中HEAD指向的版本：

<img src="images/跟随狂神学Java-37/image-20230805194416173.png" alt="image-20230805194416173" style="zoom:50%;" />

* Directory ：使用 Git 管理的一个目录，也就是一个仓库，包含我们的工作空间和 Git 的管理空间。
* WorkSpace ：需要通过 Git 进行版本控制的目录和文件，这些目录和文件组成了工作空间。
* .git ：存放 Git 管理信息的目录，初始化仓库的时候自动创建。
* Index/Stage ：暂存区，或者叫待提交更新区，在提交进入 repo 之前，我们可以把所有的更新放在暂存区。
* Local Repo ：本地仓库，一个存放在本地的版本库； HEAD 会只是当前的开发分支（ branch ）。
* Stash ：隐藏，是一个工作状态保存栈，用于保存/恢复 WorkSpace 中的临时状态。



----

##### 工作流程

Git的工作流程一般是这样的：

1. 在工作目录中添加、修改文件
2. 将需要进行版本管理的文件放入暂存区域
3. 将暂存区域的文件提交到git仓库

因此，Git管理的文件有三种状态：已修改（Modified），已暂存（staged），已提交（committed）





#### Git项目搭建

---

##### 创建工作目录与常用指令

工作目录（WorkSpace）一般就是 你希望Git帮助你管理的文件夹，可以是你项目的目录，也可以是一个空目录，建议路径名中不要有中文。日常使用只需要记住以下六个命令

**<img src="images/跟随狂神学Java-37/image-20230805195145476.png" alt="image-20230805195145476" style="zoom:50%;" />**

---

##### 本地仓库搭建

创建本地仓库的方法有两种

1. 创建全新的仓库，需要使用Git管理的项目的根目录执行

   ~~~bash
   # 在当前目录新建一个Git代码库
   $ git init
   ~~~

2. 执行后可以看到，仅仅在项目目录多出来一个.git目录，关于版本等的所有的信息都在这个目录中

---

##### 克隆远程仓库

1. 另一种初始化方式是克隆远程目录，是将远程服务器上的仓库完全镜像一份到本地

   ~~~bash
   # 克隆一个项目和它的整个代码历史（版本信息）
   $ git clone [url]
   ~~~

2. 去gitee或者github上克隆一个试试







#### Git文件操作

---

##### 文件4种状态

版本控制就是对文件版本的控制，要对文件进行修改、提交等操作，首先要知道文件在什么状态，不然可能会提交了现在还不想提交的版本，或者要提交的文件没提交上

* **Untracked**：未跟踪。

  此文件在文件夹中，但是并没有加入到git库，不参与版本控制，通过`git add`状态变为`Staged`

* **Unmodify**：文件已经入库，未修改

  即版本库中的文件快照内容与文件夹中的完全一致，这种类型的文件有两种去处：

  如果它被修改，而变为`Modified`；如果使用`git rm`移出版本库，则成为`Untracked`文件

* **Modified**：文件已修改，仅仅被修改，并没有进行其他的操作

  这个文件夹也有两个去处，

  通过`git add`可进入暂存`staged`状态；

  或者使用`git checkout`则丢弃修改，返回到`unmodify`状态。这个`git checkout`即从库中取出文件，覆盖当前修改

* **Staged**：暂存状态。

  执行`git commit`将会修改同步到库中，这时库中的文件将和本地的一致，文件为`unmodify`状态

  执行`git reset HEAD filename`取消暂存，文件状态为`Modified`



理解：

* 你要提交一个文件，你总得进行跟踪吧。如果将文件设置为需要跟踪，那么他就是`Staged`。如果你不跟踪，那你们之间就没有故事，为`Untracked`。跟踪了文件之后，剩下的`Modified`和`Unmodified`是 【此文件与版本库中文件之间的关系】。如果文件与版本库中的不一样，则为`Modified`，否则为`Unmodified`



---

##### 查看文件状态

你可以通过如下命令查看文件状态

~~~bash
# 查看指定文件状态
git status [filename]

# 查看所有文件状态
git status


# git add . 				添加所有文件到暂存区
# git commit -m "meaasege" 	提交暂存区中的内容到本地仓库 -m 提交信息
~~~



---

##### 忽略文件

有时候我们不想把某些文件纳入到版本控制中，比如数据库文件，临时文件，设计文件等

在主目录下建立".gitignore"文件，此文件有如下规则

1. 忽略文件中的空行或以`#`开始的行

2. 可以使用Linux通配符

   例如星号`*`代表任意多个字符，问号`?`代表一个字符，方括号`[abc]`代表可选字符范围，大括号`{string1,string2}`代表可选的字符串等

3. 如果名称的最前面有一个感叹号`!`，表示例外规则

4. 如果名称的最前面是一个路径分隔符`/`，表示要忽略的文件在此目录下，而子目录中的文件不忽略

5. 如果名称的最后面是一个路径分隔符`/`，表示要忽略的是此目录下该名称的子目录，而非文件（默认文件或路径都忽略）

~~~bash
#为注释
*.txt		#忽略所有.txt文件
!lib.txt	#但除了lib.txt
/temp		#仅忽略项目根目录下的TODO文件，但不包括其它目录temp
build/		#忽略build/目录下的所有文件
doc/*.txt	#忽略doc/notes.txt 但不包括 doc/serv/arch.txt
~~~







#### 使用码云

---

1. 注册登录码云，完善个人信息

2. 设置本机绑定SSH公钥，实现免密码登录

   ~~~bash
   # 进入c:\Users\Administrator\.ssh	目录
   # 生成公钥，默认加密算法rsa
   ssh-keygen
   ~~~

3. 将公钥信息public key添加到码云账户中即可

4. 使用码云创建一个自己的仓库

   <img src="images/跟随狂神学Java-37/image-20230805205500251.png" alt="image-20230805205500251" style="zoom:50%;" />

5. 使用git clone命令即可同步到本地





#### IDEA中集成Git

---

1. 新建项目，绑定git

   * 将远程clone下来的git文件全部复制到目录中

   * 注意文件的颜色

     <img src="images/跟随狂神学Java-37/image-20230806131759748.png" alt="image-20230806131759748" style="zoom:50%;" />

2. 修改文件，使用IDEA操作git

   * 你可以在集成终端中`git add .`来将文件添加到暂存区

     <img src="images/跟随狂神学Java-37/image-20230806132427607.png" alt="image-20230806132427607" style="zoom:50%;" />

   * 你可以选择单个文件并右键选择git操作

     <img src="images/跟随狂神学Java-37/image-20230806132434318.png" alt="image-20230806132434318" style="zoom:50%;" />

3. 提交测试

   * 你可以commit提交，push到远程仓库

   * 你可以在侧边栏找到git提交，并添加信息<img src="images/跟随狂神学Java-37/image-20230806132600787.png" alt="image-20230806132600787" style="zoom:50%;" />





#### GIT的分支

---

分支在 GIT 中相对较难，分支就是科幻电影里面的平行宇宙，如果两个平行宇宙互不干扰，那对现在的你也没啥影响。不过，在某个时间点，两个平行宇宙合并了，我们就需要处理一些问题了！

<img src="images/跟随狂神学Java-37/image-20230806134419734.png" alt="image-20230806134419734" style="zoom:50%;" />

git分支中常用指令

~~~bash
# 列出所有本地分支
git branch

# 列出所有远程分支
git branch -r

# 新建一个分支，但依然停留在当前分支
git branch [branch-name]

# 新建一个分支，并切换到该分支
git checkout -b [branch]

# 合并指定分支到当前分支
$ git merge [branch]

# 删除分支
$ git branch -d [branch-name]

# 删除远程分支
$ git push origin --delete [branch-name]
$ git branch -dr [remote/branch]
~~~

如果同一个文件在合并分支时都修改了则会引起冲突。解决的方法是我们可以修改冲突文件后重新提交

==**master分支应该非常稳定，用来发布新版本，一般情况下不允许在上面工作。平时工作应当在分支上，完成后合并到master分支即可**==





你可以在idea中切换分支，点击签出即为切换分支

<img src="images/跟随狂神学Java-37/image-20230806135535434.png" alt="image-20230806135535434" style="zoom:50%;" />

<img src="images/跟随狂神学Java-37/image-20230806135653086.png" alt="image-20230806135653086" style="zoom:50%;" />