---
layout: post
---
Jekyll 是一个静态网站生成工具，用户可以使用 HTML、Markdown 或 Textile ，通过模板引擎Liquid（Liquid Templating Engine）来建立静态页面.这个博客就是 GitHub Pages + Jekyll 搭建起来的。下面是我安装 Jekyll 的过程，Windows 32bit OS。<!--more-->

## 基本安装步骤

- 安装 Ruby
- 安装 DevKit
- 安装 Jekyll
- 安装 Pygments
    - 安装 Python
    - 安装 Easy Install
    - 安装 Pygments
- 运行Jekyll，解决错误

### 一、安装Ruby

1. 下载地址 <http://rubyinstaller.org/downloads/>
2. 选择相应版本的 “RubyInstallers” 进行下载（主要是区分好32/64位版本）。**不要关闭页面，下面还会用到**。
3. 安装时宜选择默认的路径如 “C:\Ruby23”，因为安装包明确提出“请不要使用带有空格的文件夹”（如：Program Files）；勾选 “Add Ruby executables to your PATH”。
4. 检测是否安装成功。“win + R”快捷键输入 cmd，打开控制台输入：`ruby -v`。    
        
        输出示例如下：
            ruby 2.3.3p222 <2016-11-21 revision 56859> [i386-mingw32]

### 二、安装 DevKit

1. 下载地址同上 <http://rubyinstaller.org/downloads/>
2. 下载同已安装Ruby版本相对应的 DevKit 安装包。目前为4.7.2版本，区分好32/64位即可。
3. 运行程序解压文件至某路径（我的是C:\DevKit）
4. 初始化创建 config.yml 文件。在控制台窗口，依次输入：
    
        cd “C:\DevKit”  //定位某磁盘文件夹命令，“”内填步骤3程序包路径
        ruby dk.rb init
        notepad config.yml

5. 上一步完成会打开记事本窗口，文件末尾添加一行 `- C:\Ruby23` (ruby 安装路径)，保存退出。
6. 检查安装。控制台输入：
        
        ruby dk.rb review
        ruby dk.rb install
        
### 三、安装 Jekyll

1. 检测 gem 安装。控制台输入 `gem -v`，输出版本号如 `2.5.2`。
2. 安装 bundler ，控制台输入：

        gem install bundler

2. 安装 Jekyll gem，控制台输入：
        
        gem install jekyll

### 四、安装 Pygments

> Jekyll 里默认的语法高亮插件是 Pygments。 它需要安装 Python 并在网站的配置文件_config.yml 里将 highlighter 的值设置为pygments。

1. 安装 Python
    1. 下载地址 <http://www.python.org/download/>
    2. Python 主页两个版本的常用链接，分别为 2.X 和 3.X 版本，这里我选择 2.X 版本。
    3. 安装过程略过。
    4. 添加环境变量PATH。
        - 桌面“我的电脑”右键属性，左侧选择高级系统设置，打开的选项卡中选择“环境变量”；
        - 选中 PATH，点击“编辑”；
        - 在原内容末尾添加“;C:\Python27”(你的Python 安装路径)。
    5. 检测安装。控制台输入`python -V`(**注意大写 V**),输出如`python 2.7.13`
2. 安装 Easy Install
    1. 我搜的下载地址（win7 32位）<https://bootstrap.pypa.io/ez_setup.py>
    2. 文件下载保存，如我存在 c:\ 根目录下，控制台输入命令
            
            python "C:\ez_setup.py"

    3. 安装完成后，参考上一步添加 PATH 的方法，添加 “Python Scripts” 路径(如： C:\Python27\Scripts)至 PATH。
    4. 检测安装。控制台输入`easy_install --version`,输出如：`setuptools 3.1`

3. 安装 Pygments    
    - 控制台命令：`easy_install Pygments`

### 五、运行 Jekyll

例如我想在 E:\work\ 下建站。控制台输入`E:`,回车；然后输入`cd work`,当前控制台就位于 work 文件夹当中了。执行命令`jekyll server`,如果成功，将出现以下代码结尾的结果：

        Server address: http://127.0.0.1:4000/
        Server running... press ctrl-c to stop.

此时，在浏览器中访问<127.0.0.1:4000>或<localhost:4000>就可以实时预览你的网页了。

### 另外

关于更改 ruby 源。

- 控制台输入`gem sources -l`查看 ruby 默认源；
- 我看到的方法是将sources 改为 *淘宝源* 或 *ruby-china* 。使用命令：
        
        gem sources -r https://rubygems.org/    （删除默认）
        gem sources -a http://gems.ruby-china.org    （添加ruby-china，注意http没有s）


