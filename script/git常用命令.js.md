 # git常用命令.js
```


放弃修改
git checkout .

查看状态
git status -s

查看分支
git branch

创建分支
git checkout master -b daily-9-3-酒链备份

提交到暂存区
git add .

提交评论
git commit -m 'daily-9-3-酒链备份'

推送到分支
git push origin daily-9-3-酒链备份


切换主干||分支
git checkout master     ||    git checkout  daily-10-1

本地合并分支到主干
git merge daily-9-3-酒链备份

远端合并分支到主干
git merge origin/daily-9-3-酒链备份

推送主干
git push origin master


//把HEAD指向最新下载的版本
git reset --hard origin/master

//下载所有分支到本地
git branch -a | grep origin | grep -v HEAD | while read rb;do lb=$(echo ${rb} | cut -d/ -f 3-);git checkout -b $lb $rb;done

git clone  https://gitee.com/snailuncle/douban-trailer-imooc.git

使用Git下载v.2.8.1分支代码，使用命令：

git clone -b daily-10-2  https://gitee.com/snailuncle/douban-trailer-imooc.git




git clone  // 项目地址
git checkout 分支名字
git pull origin 分支名字

//删除分支
git branch -d <branch_name>


//打开当前命令行所在文件夹
 start "" "."

git status 下中文显示乱码问题解决
  $ git status -s
                ?? "\350\257\264\346\230\216.txt\n
                $ printf "\350\257\264\346\230\216.txt\n"
                说明.txt


        通过将Git配置变量 core.quotepath 设置为false，就可以解决中文文件名称在这些Git命令输出中的显示问题，
        示例：
                $ git config --global core.quotepath false

                $ git status -s

                ?? 说明.txt


git reset --hard

git pull
```
