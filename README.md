# git_test
git使用演示
## 前言  

​	Git应该算是每一个程序员都离不开小工具了吧<!--more-->。它是一个免费的、开源的分布式版本控制系统，可以快速高效地处理从小型到大型的各种项目。 Git 易于学习，占地面积小，性能极快，具有廉价的本地库，方便的暂存区域和多个工作 流分支等特性。

<br>

## Git简介

1.Git 的工作机制

​	**工作区**   -- (git add) -->   **暂存区**   -- (git commit) -->   **本地库**   -- (git push) -->  **远程库**



2.Git的代码托管中心（远程库）

* 局域网 
  * GitLib（公司使用局域网搭建）
* 互联网
  * GitHub（外网 ）
  * Gitee 码云（内网）

<br>

## Git安装

1. 去 [官网](https://git-scm.com/)下载Git最新安装程序

2. 运行安装程序，选择好安装位置后，都使用默认选项然后无脑下一步就行
3. 在出现需要勾选的其他配置页面时将第一个 使用文件缓存机制和第二个使用符号链接选项勾上再点下一步

![安装选项](/usr/img/16/01.png)

<br>

4. 然后到实验室功能选项建一个都不要勾选，然后直接点击 Install 完成安装

![实验室新功能](/usr/img/16/02.png)

<br>

## Git基本操作

1. 初始化命令

   | 命令                                 | 作用         |
   | :----------------------------------- | :----------- |
   | git config --global user.name 用户名 | 设置用户签名 |
   | git config --global user.email 邮箱  | 设置用户签名 |
   | git init                             | 初始化本地库 |

   > 刚安装好Git时需要设置用户签名（用户名和邮箱），在使用前需要将管理的文件夹设初始化为本地库后再进行其他操作

   <br>

2. 基本使用命令

   | 命令                            | 作用               |
   | :------------------------------ | :----------------- |
   | git status                      | 查看本地库状态     |
   | git add 文件名                  | 添加到暂存区       |
   | git commit -m "日志信息" 文件名 | 提交到本地库       |
   | git reflog                      | 查看那版本历史记录 |
   | git log                         | 查看版本详细信息   |
   | git reset --hard 版本号         | 版本穿梭           |

   <br>

3. Git分支操作

   > 在版本控制过程中，同时推进多个任务，为每个任务，我们就可以创建每个任务的单独 分支。可以把自己的工作从开发主线master分支上分离开来，开发自己分支的时 候，不会影响主线分支的运行。

    **分支操作常用命令**

   | 命令                | 作用                         |
   | ------------------- | ---------------------------- |
   | git branch 分支名   | 创建分支                     |
   | git branch -v       | 查看分支                     |
   | git checkout 分支名 | 切换分支                     |
   | git merge 分支名    | 把指定的分支合并到当前分支上 |

   * 合并分支时，两个分支在同一个文件的同一个位置有两套完全不同的修改。Git 无法替 我们决定使用哪一个，此时就会残剩冲突，必须人为决定新代码内容 。此时会显示合并失败，并且后面状态为 **MERGING**

   * 解决冲突

     * 当冲突出现时会用特殊符号标注代码，只需要将要特殊符号删除，留下需要的代码就行，然后再保存提交即可

       `<<<<<<< HEAD 当前分支的代码 ======合并过来的代码 >>>>>>> test`

<br>

## Git团队协作

> 通过远程仓库托管代码，可以实现团队多人对同一份代码进行操作

1. 远程仓库操作常用命令

   | 命令                               | 作用                                                   |
   | ---------------------------------- | ------------------------------------------------------ |
   | git remote -v                      | 查看当前所有远程地址别名                               |
   | git remote add 别名 远程地址       | 给当前远程仓库取别名                                   |
   | git remote remove 别名             | 删除别名                                               |
   | git push 别名 分支                 | 推送本地仓库分支上的内容到远程仓库                     |
   | git clone 远程地址                 | 将远程仓库的内容克隆到本地                             |
   | git pull 远程库地址别名 远程分支名 | 将远程仓库对于分支最新内容拉下来与当前本地分支直接合并 |

   <br>

2. 使用Github远程仓库

   * 登录[GItHub](https://github.com/)，点击+号创建自己的远程仓库

     ![创建远程库](/usr/img/16/03.png)

   * 根据提示输入仓库名（尽量和自己的本地仓库名统一）和仓库简介选择公开或私有，回车完成创建

     ![创建详情](/usr/img/16/04.png)

   * 复制远程库的http链接，到本地设置别名，然后使用push命令将本地仓库中的内容推送到远程仓库(Github 2021..8.13取消了对账号密码的验证支持，建议使用ssh免密登录或者token认证)

   * 使用pull命令可以将远程仓库对于分支最新内容拉下来后与当前本地分支直接合并

3. 使用 GitHub团队协作

   * 团队协作
     * 将需要协作的人邀请至项目仓库中即可
     * 在github项目仓库中进入设置，进入Collaborators选项，点击Manage access中的Add pepole，输入对方名称即可发送邀请
     * 对方同意后即可对该项目仓库进行操作
   * 跨团队协作
     * A通过项目仓库链接访问到B后，将B的仓库中的代码叉一份到自己的库中
     * A通过自己的账号对其修改过后 然后点击Pull requests，再点击New pull requst再创建，然后编辑名称和修改简介，点击Create pull request即可将修改后的内容发送到B
     * B再对A修改代码进行审核，如果没有问题点击Merge pull reque 合并代码

4. 使用ssh免密登录

   * 在C盘用户目录下启动Git Bash Here 输入 `ssh-keygen -t rsa -C GitHub邮箱账号`连续三次回车然后`cd ./.ssh/` 进入.ssh文件夹 `cat id_rsa.pub`查看并复制公共密钥
   * 在GitHub中进入设置 点击SSH and GPG keys选项，再点击 New SSH Key ，然后取个名字，将复制的密钥粘贴到key中，再点击Add SSH ke即可完成shh免密登录的设置
   * 最后就可以使用ssh链接进行操作了

<br>

## IDEA集成GIt

> 这里我使用的IDEA版本为 2021.3  在使用IDEA操作GItHub或则Gitee时需要检查是否已经安装其同名插件

1. 配置忽略文件（将IDEA的配置文件，字节码等非核心内容忽略）

   * 创建git.ignore(任何位置都行，为了方便git调用可以放在C盘用户目录下)文件内容如下

     ```
     # Compiled class file
     *.class
     
     # Log file
     *.log
     
     # BlueJ files
     *.ctxt
     
     # Mobile Tools for Java (J2ME)
     .mtj.tmp/
     
     # Package Files #
     *.jar
     *.war
     *.nar
     *.ear
     *.zip
     *.tar.gz
     *.rar
     
     # virtual machine crash logs, see
     http://www.java.com/en/download/help/error_hotspot.xml
     hs_err_pid*
     
     .classpath
     .project
     .settings
     target
     .idea
     *.iml
     ```

     然后打开.gitconfig问价，添加 如下引用，然后保存即可

     ```
     [core]
     excludesfile = C:/Users/asus/git.ignore
     ```

      （注意：这里要使用“正斜线（/）”，不要使用“反斜线（\）”）

2. 再IDEA设置中 Version Control | Git中定位到安装的Git\cmd\git.exe

3. 初始化：点击IDEA最上方VCS，在点击Enable Version Control Integration选项选择Git，最后点击ok即可，初始完过后VCS选项会变成Git

4. add和commit

   * 在需要提交的文件上右击即可看到下方的Git选项，点击Git选项就可以看到add和commit File选项（一般idea默认会在commit的时候自动add，所以大多数时候可以直接commit文件）
   * 在IDEA最上方的工具也可以看到Git选项，或者使用Git 的小工具栏也可以commit![Git小工具](/usr/img/16/05.png)

5. 切换版本：在右下角有个GIt，点击就会看到如下界面，HEAD标签代表当前看到的版本，mian( 或者master)为主分支所在版本

   ![切换版本](/usr/img/16/06.png) 在需要切换的分支右击就可以看到checkout Revison选项点击即可切换![切换分支](/usr/img/16/07.png)

6. 创建分支：点击IDEA右下角main（或则mater）表即可看到new Branch选项，点击即可创建分支，再次点击右下角的main在点击新建的分支名字就可以看到Chekout选相关，切换分支后右下角会变成当前分支名字

7. 合并分支、解决分支冲突：点击IDEA右下角当前分支的名字，然后点击需要合并过来的分支，可以看到Merge Selected into Current,点击即可开始合并分支![合并分支](/usr/img/16/08.png)当合并出现冲突的时候就会出现如下界面，左边表示当前分支，右边表示合并过来的分支，中间表示手动合并过后的结果，点击分界处的 X 或则 》 符号可以操作当前分支![解决分支冲突](/usr/img/16/09.png)合并过后的样子![合并完毕](/usr/img/16/10.png)

8. 使用IDEA操作GitHub（Gitee使用方法大同小异）

   1. 登录GitHub：点击 Settings | Version Control | GitHub，点击+号 即可添加GitHub账号
   2. 使用IDEA创建将代码分享到IDEA，点击IDEA上方工具栏中的GIt选项，并选择GitHub选项，再选择 Share Project On GitHub, 再输入仓库名字和描述即可，再GItHub中就可以看到所建立的厂库了![使用IDEA创建远程库](/usr/img/16/11.png)
   3. 推送代码到GitHub： 点击Git选项中的push就可以将项目上传到远程库
   4. 从GitHub拉取代码：点击Git选项中的pull就可以将远程仓库的项目拉下来与本地项目的当前分支合并
   5. 从GitHub克隆代码：在打开IDEA时选择GIt From VCS 选项，输入仓库地址，即可将仓库中的代码克隆到本地
