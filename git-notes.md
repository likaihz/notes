#Git学习
##安装
---
* 安装完成后，还需要最后一步设置，在命令行输入：

```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

注意git config命令的--global参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。 

         
##创建版本库
---
* 在当前目录下建立版本仓库：


```
$ git init 
```

* 把文件添加到版本库

```shell
$ git add <file name>
$ git commit
```

##时光机穿梭
---

* 查看当前版本库状态


```shell
$ git status
```

* 查看修改内容

```shell
$ git diff
```

输入q可以退出当前界面

* 提交修改过的文件步骤与提交新文件一样

###版本回退
*  利用HEAD指针，HEAD后加^表示当前版本的上一个版本：
```shell
$ git reset --hard HEAD^
```

* 利用版本号，先从log中查看想要回退的版本的版本号，再输入命令
```shell
$ git reset --hard <commit id>
```
版本号只要写前几位就好了，只要足够分辨是哪一个版本就行。

* 如果之后想要再回到新的版本，可以在reflog中查看命令历史，其中记录了每一个命令修改的版本的版本号。

###撤销修改
* 在工作区还未提交的修改，如果想要撤销，可以使用以下命令：
```shell
$ git checkout --  <file name>
```
* 已经提交到缓冲区的修改，可以通过
```shell
$ git reset HEAD <file name>
```
来将该文件的修改重新放回工作区。

###删除文件

##远程仓库
---
* 创建SSH key：在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了,可直接跳到下一步。如果没有，打开Shell(Windows下打开Git Bash)，创建SSH Key：
```shell
$ ssh-keygen -t rsa -C "email@example.com"
```
* 登录Github，打开账户设置-SSH keys，添加秘钥，将id_rsa.pub里的内容粘贴进文本框。

* 此时，Github就允许该电脑向你的账户中推送代码了。

### 添加远程库
* 在Github中创建一个仓库
* 根据提示，在本地的仓库下运行命令：
```shell 
$ git remote add origin git@github.com:tiezhu-lee/learngit.git
```
* 添加后，远程库的名字就是origin，这是Git默认的叫法，也可以改成别的。
* 运行命令，把本地库的所有内容推送到远程库上：
```shell
$ git push -u origin master
```
该命令实际上是把本地master分支推送到远程。

* 由于远程库是空的，第一次推送master分支时，加上了-u参数，Git不但会吧本地的master分支内容推送到远程新的master分支，还会把两者关联起来，以后就可以简化命令。
* 从现在起，只要本地做了提交，就可以通过以下命令把本地的master分支推送至Github：
```shell
$ git push origin master
```
### 从远程库克隆
```shell
$ git clone git@github.com:tiezhu-lee@gitskills.git
```

##分支管理
