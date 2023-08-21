# git_learning

This is a tutorial of git for the beginners

# github加速

[博客教程链接](https://blog.csdn.net/qq_51688013/article/details/123402986)

更新教程 [link](https://blog.csdn.net/langfeiyes/article/details/128487969)

[视频教程链接](https://www.bilibili.com/video/BV1za411j79T?spm_id_from=333.337.search-card.all.click&vd_source=589132dab1c04f6e167670673a35576agt)

[github镜像站](https://www.kgithub.com/)


# 使用git对仓库进行管理  

使用git GUI来对github库进行操作是最方便的, [教程链接](https://blog.csdn.net/m0_37273490/article/details/80517057). 

如果想使用命令行(Bash)方式, 可参考以下教程:

1. github账号和本地建立ssh连接(仅初次使用git需要)

`ssh-keygen -t rsa -C "邮箱"`

在资源管理器打开C盘>用户>.ssh，找到id_rsa.pub文件，记事本打开，复制到github主页->setting->ssh and GPG keys, 点击add keys

测试：输入`ssh -T git@github.com`， 如果结果为successful，说明github账号已经和本地连接

2. 克隆仓库到本地(仅需1次, 可以反复修改和同步)

   `git clone github上的仓库网址(.git结尾的)`

   仓库网址的获取: 打开项目->code，复制.git结尾的网址，注意不要用浏览器直接复制的网址

3. 修改仓库后把本地进度同步到github, 步骤如下: 到本地的仓库文件夹下，右键打开git bash, 依次输入如下命令:

`git init`

`git config --global user.name '你的github用户名'(也可以任意填写)`

`git config --global user.email '你的绑定邮箱'(也可以任意填写)`

`git checkout -b 要提交的branch名（不用加引号）`

(输入 `git branch`  可查看当前branch, 提交前确认当前已经切换到你想上传文件的branch)

`git add 上传的文件名(.则上传全部文件)`

`git commit -m '备注'`

`git remote add origin github上的仓库网址(.git结尾的)`

(如果这个branch下有本地没有的文件，需要加下面这句:

`git pull --rebase origin branch名`

建议先把整个仓库clone下来，始终在本地修改，这样就不会有此问题)

其中rebase命令的含义: [link](https://blog.csdn.net/m0_69424697/article/details/125106290)

`git push -u origin 要提交的branch名`

这一步很容易报错(fail to access...), 解决方案见下文

# 报错及解决方案

最常发生的报错是push失败, 解决方法详见case 2

## Case 1.

```
$ git pull --rebase origin main

fatal: unable to access 'https://github.com/user_name/xxxxx.git/': Failed to connect to github.com port 443 after 21067 ms: Timed out
```

解决方案：

[`rm ~/.gitconfig`](https://blog.csdn.net/Emily_JYN/article/details/117679831)

`git remote add origin 项目仓库网址(.git结尾的)`

如果不奏效, 可能是代理的事, 可尝试该[博客](https://blog.csdn.net/ESCM_/article/details/124498679)中提出的解决方案.

注意: github上传的单个文件不要超过25M

## Case 2.

```
$ git push -u origin main

fatal: unable to access 'https://github.com/user_name/xxxxx.git/': OpenSSL SSL_read: Connection was reset, errno 10054
```

解决方案： 

输入命令：

`git config --global http.sslVerify "false"`

[`git config --global http.sslBackend openssl`](https://blog.csdn.net/xiaobudong_007/article/details/115113066)

如果还不奏效, 则重新初始化: 

`git init`

`git config --global user.name '你的github用户名'(也可以任意填写)`

`git config --global user.email '你的绑定邮箱'(也可以任意填写)`

## Case 3.

`fatal: protocol 'https' is not supported `

解决方案详见: [link](https://blog.csdn.net/codererer/article/details/105303972)

# 参考博客

[git设置ssh](https://www.jianshu.com/p/ee2578821d49)

[git:如何上传本地项目到远程仓库](https://blog.csdn.net/weixin_46471601/article/details/124996250)

[git提交代码](https://blog.csdn.net/qq_46032550/article/details/121684365)

[git创建新分支](https://blog.csdn.net/qq_37899792/article/details/121328761)

[git推送代码到main分支](https://www.bilibili.com/read/cv8633117/)

[github提交代码非空的文件夹](https://www.cnblogs.com/zhangshijiezsj/p/14848801.html)
