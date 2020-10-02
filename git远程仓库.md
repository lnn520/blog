1.如何在git上验证身份
    利用ssh key
    首先,生成ssh key 
    运行ssh-keygen -t rsa -b 4096-c 你的邮箱
    然后一直回车，直到没有提示
    cat ~/.ssh/id_rsa.pub 得到公钥内容，粘贴到GitHub
    打开GitHub,在设置页面填入公钥
2.如何测试配对成功
    ssh -T git@github.com
    如果问你yes/no，请回答yes并且回车
3.上传代码
    新建github repo 复制ssh 地址
    复制页面里面代码

    git remote add origin git@xxxxxx
    在本地添加远程仓库地址
    origin是远程仓库的默认名字。可以换。建议不要随便替换
    不建议使用http，每次都要输入密码

    git push -u origin master
    推送本地master 分支到远程origin 的master分支

    之后可以直接使用 git push

    如果在运行中遇到git pull 那么先运行该语句然后重新执行之前代码

4.如何上传其他分支
    方法一 git push origin x:x
    方法二：git checkout x
    git push -u origin x

5下载别人的代码：
    git clone git @xxxxxx[目标路径]
    如果是不同机器，需要上传新的ssh key (一机一key)
    cd 目标路径
    git add /git commit /[git pull]/ git push 四联操作

6.如何下载某个分支
    先下载整个仓库，然后git checkout

7.git clone git@xxx.git

    会在当前目录下创建一个XXX目录
    xxx/.git是本地仓库
    一般要接一句cd xxx

    git clone git@?/xxx.git yyy
    会在本地创建一个yyy目录，记得 cd yyy

    git clone 给i他@？/xx.git .
    修后一个字符是点，注意有空格
    不会创建新的目录，使用当前目录容纳代码和.git
    当前目录最好是空的,否则会出问题
8. 可以创建两个远程仓库
    git remote add repo2 git@xxxxxx
    git push -u repo2 master

    如果有提示git pull 
    说明你创建新项目的时候创建了一些文件
    你只需要运行git pull 之后再运行刚才的命令

    总结：常用的命令只有 git clone  /   git pull  /git push
    远程仓库只是本地仓库的一个备份，所以变化都要先commit 到本地仓库,然后push到远程

git的一些高级操作  git stash /git stash pop 藏代码
简化命令
touch ~/.bashrc
echo 'alias ga="git add"'>> ~/.bashrc
echo 'alias gc="git commit -v"'>> ~/.bashrc
echo 'alias gl="git pull"'>> ~/.bashrc
echo 'alias gp="git push"'>> ~/.bashrc
echo 'alias gco="git checkout"'>> ~/.bashrc
echo 'alias gst="git status -sb"'>> ~/.bashrc
