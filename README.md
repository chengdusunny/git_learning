# git_learning
This is a tutorial of git for the beginners

# github加速

教程: https://blog.csdn.net/qq_51688013/article/details/123402986

视频教程:
https://www.bilibili.com/video/BV1za411j79T?spm_id_from=333.337.search-card.all.click&vd_source=589132dab1c04f6e167670673a35576a

# git GUI 使用教程

使用git GUI来对github库进行操作是最方便的, 教程链接: https://blog.csdn.net/m0_37273490/article/details/80517057

如果想使用命令行(Bash), 可参考以下教程:

# git上传文件到指定仓库

1.github账号和本地建立ssh连接

教程: https://www.jianshu.com/p/ee2578821d49

ssh-keygen -t rsa -C "邮箱"

在资源管理器打开C盘>用户>.ssh，找到id_rsa.pub，记事本打开，复制到github主页->setting->ssh and GPG keys, 点击add keys

测试：输入 ssh -T git@github.com， 如果结果为successful，说明github账号已经和本地连接

2.到代码文件夹下，右键打开git bash

git init

git config --global user.name '你的github用户名'

git config --global user.email '你的登记邮箱'

git checkout -b branch名（不用加引号）

git branch 确认当前branch已经切换到你想上传文件的branch

git add . 上传全部文件

git commit -m '备注'

git remote add origin 项目仓库网址(.git结尾的)，打开项目，code，复制，不要用浏览器直接复制的网址

(如果这个branch下有本地没有的文件，需要加下面这句:

git pull --rebase origin branch名

建议先git clone xxxxx.git把整个仓库clone下来, 在本地修改，这样就无需此步)

rebase的含义: https://blog.csdn.net/m0_69424697/article/details/125106290

git push -u origin branch名

这一步很容易报错(fail to access...), 解决方案见下文

# 报错及解决方案

## Case 1.

$ git pull --rebase origin main

fatal: unable to access 'https://github.com/user_name/xxxxx.git/': Failed to connect to github.com port 443 after 21067 ms: Timed out

解决方案：

[rm ~/.gitconfig](https://blog.csdn.net/Emily_JYN/article/details/117679831)

然后再 git remote add origin 项目仓库网址(.git结尾的)

注意: github上传的单个文件不要超过25M

## Case 2.

$ git push -u origin main

fatal: unable to access 'https://github.com/user_name/xxxxx.git/': OpenSSL SSL_read: Connection was reset, errno 10054

解决方案： 

输入命令：git config --global http.sslVerify "false"

如果还不奏效, 可以输入：[git config --global http.sslBackend openssl](https://blog.csdn.net/xiaobudong_007/article/details/115113066)

## Case 3.

fatal: protocol 'https' is not supported 

解决方案：

https://blog.csdn.net/codererer/article/details/105303972

# 参考博客

[git设置ssh](https://www.jianshu.com/p/ee2578821d49)

[git:如何上传本地项目到远程仓库](https://blog.csdn.net/weixin_46471601/article/details/124996250)

[git提交代码](https://blog.csdn.net/qq_46032550/article/details/121684365)

[git创建新分支](https://blog.csdn.net/qq_37899792/article/details/121328761)

[git推送代码到main分支](https://www.bilibili.com/read/cv8633117/)

[github提交代码非空的文件夹](https://www.cnblogs.com/zhangshijiezsj/p/14848801.html)
