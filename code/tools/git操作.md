git remote add 自定义个名字 远程分支的路径
这样就添加了个远程目录

git fetch 刚才自定义的名字
这样就将远程分支拉取了


比如
git remote add zuojxin git@github.com:zuojiuxin/TradeEndDocs.git
git fetch zuojiuxin

git branch -a //看到了zuojiuxin这个分支了


删除远程分支：
git push origin  --delete 远程分支名字


git 忽略文件
目录下 建立 .gitignore  写入不想提交的文件

本地项目发布到github


git 下载速度慢：
1. http://tool.chinaz.com/dns 搜github.com 查出最快的ip
2. 修改host文件 sudo vi /etc/host
151.101.72.249 github.global.ssl.fastly.net
192.30.255.112 github.com

3. 重启 sudo /etc/init.d/networking restart






-----
git push 错误：



git pull --rebase origin master
https://www.jianshu.com/p/835e0a48c825







权限问题：
Please make sure you have the correct access rights and the repository exists

1. git输入命令
$ ssh-keygen -t rsa -C "your@email.com"（请填你设置的邮箱地址
2. 一路回车
3. 生成新的id_rsa.pub ，此文件目录 看命令输出就知道了
3.github.com 设置里 ssh and GPG keys  加入 id_rsa.pub里的信息
4. ok

https://blog.csdn.net/jingtingfengguo/article/details/51892864