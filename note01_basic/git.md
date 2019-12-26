# git的简单使用

<a href="https://git-scm.com/doc" target="_blank">官方文档</a>

## git的安装

## 设置

```bash
git config --global user.email "you@example.com"
# 设置用户邮箱
git config --global user.name "Your Name"
# 设置用户名
git config --global credential.helper store
# 保存输入过的用户名和密码
```

## 配置一个新项目

官方会给一大堆命令，照着做就行  
比如新建一个项目 example  
会给出如下指令:  

> echo "# example" >> README.md  
> git init  
> git add README.md  
> git commit -m "first commit"  
> git remote add origin https://github.com/rolfcc/example.git  
> git push -u origin master  

当然，首先要移动到项目的文件夹下。。。  

```bash
echo "# example" >> README.md
# 当前目录下生成一个名为 README.md 的文件
# 文件第一行是引号内容
git init
# 初始化本地仓库
git add README.md
# 把刚才的 README.md 提交到暂存区，以便等下提交
git commit -m "first commit"
# 把暂存区内容提交到本地版本库
git remote add origin https://github.com/rolfcc/example.git
# remote 就是服务器上的仓库
# 这是添加一个远程仓库路径
git push -u origin master
# 将本地 master 分支推送至 origin 主机，并指定 origin 主机为默认主机
```

## 更新常用命令

```bash
git add .
# 提交所有新文件和已修改文件，不包括已删除文件
git add -u
# update 不包括新文件，但包括已删除文件
git add -A
# 相当于 --all
git add <文件名>
# 添加一个文件
git rm <文件名>
# 删除，很好理解
```

```bash
git commit -m "随便写点啥"
# 暂存区提交版本库，附带一条描述信息
git commit
# 会打开一个vim让你写描述信息
git commit -a
# 提交所有跟踪文件的修改与删除，没有新文件
```

```bash
git push <主机名> <分支名>
# 主机和分支可省略，反正现在就一个。。。
```
