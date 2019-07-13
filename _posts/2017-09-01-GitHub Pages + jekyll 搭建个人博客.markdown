---
layout: post
---
如果你想有一个简单的个人站点写写博客，而又不想注册域名、空间等等，用 GitHub Pages + Jekyll 搭建静态站点是个不错的选择。轻量级的博客系统，没有麻烦的配置；使用标记语言，比如 Markdown，可以轻松推送文章；无需自己搭建服务器，根据Github的限制，对应的每个站有300MB空间；如果希望，还可以绑定自己的域名。下面的 win7 32bit OS 建站过程是最基础的，进阶用法需要进一步掌握 Jekyll 等知识。<!--more-->
## 知识储备
- [Git 的基本操作](https://blog.jobbole.com/78960/)
- [markdown 标记语言](https://hiker90.github.io/2017/08/30/Markdown-%E5%85%A5%E9%97%A8/)
- GitHub 的基本操作
- [Jekyll 的基础知识](http://jekyllcn.com/)

## 基本步骤

1. 首先需要拥有一个 [GitHub](http://www.GitHub.com/) 账户。注册过程略，username 和邮箱十分重要。
2. 下载安装：
    - [Node.js](http://nodejs.org/)
    - [Git](http://git-scm.com/)
3. 配置 SSH
    1. 打开 “Git Bash”，输入命令检查本机现有的 ssh key：
        
            $ cd ~/.ssh

        如果 “No such file or directory”，说明你第一次使用 git，跳过步骤2。
    
    2. 如果已经存在 ssh key，备份和移除原来的 ssh key：
        
            $ ls
            输出示例：config  id_rsa  id_rsa.pub  known_hosts
            $ mkdir key_backup
            $ cp id_rsa* key_backup
            $ rm id_rsa*
    
    3. 生成新的 SSH Key
            
            $ ssh-keygen -t rsa -C "你的邮件地址@youremail.com"
            Generating public/private rsa key pair.
            Enter file in which to save the key (/Users/your_user_directory/.ssh/id_rsa):<回车就好>
        
        系统可能要求你输入加密字符串（Passphrase，git 的每次 pull 和 push 操作都要求此验证）：
            
            Enter passphrase (empty for no passphrase):<输入加密串>
            Enter same passphrase again:<再次输入加密串>

        最后，看到 “The key's randomart image is: ” + 图形，设置成功了。
    
    4. 添加 SSH Key 到 GitHub

        - 在上一步骤，敲回车的地方，找到 id_rsa.pub 文件的存放路径，找到这个文件，并用记事本打开，复制。
        - GitHub 网页找到账户的 “Setting”，点击打开找到 “SSH and GPG keys”。
        - 点击 “New SSH Key”，粘贴保存。
        - “Git Bash” 输入命令
                $ ssh -T git@github.com
        可能看到下列结果：
                
                The authenticity of host 'github.com (207.97.227.239)' can't be established.
                RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
                Are you sure you want to continue connecting (yes/no)?
        
            输入`yes`，回车即可
            
                Hi <em>username</em>! You've successfully authenticated, but GitHub does not provide shell access.

            设置成功。

4. 设置 Git 账号信息
    
            $ git config --global user.name "你的名字"
            $ git config --global user.email "你的邮箱@youremail.com"

5. 至此，你已经成功连接到 GitHub 了。

## 使用 GitHub Pages 建立博客

GitHub Pages 分两种

- 以 你的用户名.GitHub.io 命名你的仓库（repository），仓库位于 “master” 分支；
- 另一种是位于 “gh-pages” 分支上的项目展示页

我只尝试了第一种。如果没有接触过 Jekyll ，可以通过在 GitHub 上 fork 优秀模板，稍加修改后即可实现你的站点。（附 优秀模板库：<http://jekyllthemes.org/>）

1. 从上述模板库中选择任一款打开，选择 “Homepage” 进入 GitHub 项目仓库，点击 “Fork” 将其复制到你自己的仓库；
2. 在自己的仓库中确保其位于 “master” 分支，点击 “Settings” 可以修改仓库名称为 “你的用户名.GitHub.io”；
3. 浏览器地址栏输入 “你的用户名.GitHub.io”，就可打开模板页面。
4. 结合 Jekyll 的知识，将页面的内容稍作修改，就建成了你的个人 GitHub Pages。
5. 推送的文章一般位于 “_post” 文件夹下，命名及书写规则一般参照里面的模板，如我的是 “2017-08-30-文章名称.markdown”；每次文章更新，就可以通过 Git 推送了。

至此，一个基于 GitHub Pages + Jekyll 的页面就搭建完成了，学习更多关于 Git、Jekyll、Markdown 以及其他 web 知识，探索更新鲜的玩儿法。











