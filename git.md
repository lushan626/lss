git使用初级探索：
S1:安装git
S2:登录git，网址：https://github.com；
接下来的步骤可以参考：
https://blog.csdn.net/yqljxr/article/details/78620308

S3:创建账号，邮箱
注册邮箱
 在git bash界面输入如下内容即可完成邮箱的注册：
 $ git config --global user.name "user.name"
（说明：双引号中需要你的用户名，这个可以随便输入，比如“ming.xiao”）
 $ git config --global user.email "yourmail@youremail.com.cn"
（说明： 双引号中需要输入你的有效邮箱，比如“qwert@126.com.cn”）
自己写的：
git config --global user.name "shanshan.lu"
git config --global user.email "78134246@qq.com"
S4:在本地创建ssh key
ssh-keygen -t rsa -C "78134246@qq.com"
执行这个指令的时候，可能会报出如下错误：Too many arguments
可能的原因是指令中的横线有问题，具体解决办法参考：
https://blog.csdn.net/qq_31165799/article/details/72832269
将生成的key地址记录一下：
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/Administrator/.ssh/id_rsa):
S5:按过回车键之后，在c/Users/Administrator之下就会生成.ssh文件
我连续按了好几下回车键，然后就出现了一些奇怪的数字和字母
具体的指令如下：
$ ssh-keygen -t rsa -C "78134246@qq.com"
Enter file in which to save the key (/c/Users/Administrator/.ssh/id_rsa):
Created directory '/c/Users/Administrator/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /c/Users/Administrator/.ssh/id_rsa.
Your public key has been saved in /c/Users/Administrator/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:K0uipG6g1DCzB6OZceEZ3p8j4mhnkIGHhtH5KgMNEwQ 78134246@qq.com
The key's randomart image is:
+---[RSA 2048]----+
|E+ .             |
|+ =              |
|oO *             |
|*OB o            |
|+*@. . .S        |
|B=oo. +  .       |
|+=+...o..        |
|o=.+ o o         |
|=.+   .          |
+----[SHA256]-----+

S6:找到git的account setting，单击git头像，下面会出现ssh的设置。title随便填，粘贴key，这个key是id_rsa.pub那个文件中的全部内容
S7:验证本地仓库是否连接上git中的仓库。ssh -T git@github.com
出现：Warning: Permanently added the RSA host key for IP address '13.229.188.59' to the list of known hosts.
Hi lushan626! You've successfully authenticated, but GitHub does not provide shell access.
S7:添加远程地址
git remote add origin git@github.com:yourName/yourRepo.git
后面的yourName和yourRepo表示你在github的用户名和刚才新建的仓库，加完之后进入.git，打开config，这里会多出一个remote “origin”内容，这就是刚才添加的远程地址，也可以直接修改config来配置远程地址。
yourName/yourRepo.git与github上保持一致
我自己的是：git remote add origin git@github.com:lushan626/lss.git
S8:上传文件
首次上传文件的时候，需要先git pull
我的电脑执行这个命令的时候会出现如下警告：
Permanently added the RSA host key for IP address '13.250.177.223' the list of known hosts.
There is no tracking information for the current branch.
Please specify which branch you want to merge with.
See git-pull(1) for details.
解决办法参考：https://blog.csdn.net/zhoucheng05_13/article/details/52831703
git add . //新增所有文件
git pull    //拉取文件
git push origin master  //提交文件到master
