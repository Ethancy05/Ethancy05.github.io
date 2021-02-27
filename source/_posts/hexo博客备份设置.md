---
title: hexo博客备份设置
date: 2021-02-17 17:07:55
tags: hexo
---
# 前言
hexo博客是静态网站，数据文件储存于本地，展示文件则托管在Github上，当电脑出现问题时很容易造成数据丢失，重要的文件应该就是_posts文件夹中写的文章。常见的备份有便携式设备备份，还有把本地文件夹做成同步文件夹的。今天介绍的是guithub仓库备份。

# 步骤

1. 把hexo根目录作为一个仓库，可以按默认的来，其实如果只备份有用的文件的话，就把没用的文件夹名字放在.gitignore文件里（里面已经写了一部分），为了方便，我们可以直接建立仓库。记住，最好把themes文件夹里的主题文件夹中的.git文件夹删去，使其变成一个独立的文件夹，否则当恢复备份的时候主题文件夹无法下载。

2. 我把备份的文件夹放到博客仓库的新分支

   ```
   $ git checkout -b hexobackup
   ```

   hexobackup是存放备份的分支名，名称可自定。

3. 接下来就是普通的仓库操作

   ```
   git add .
   git commit -m "博客备份"
   git push origin hexobackup
   ```

# 恢复备份

- 当要恢复博客时，选择好要存放的文件夹，执行'$ git clone https://github.com/yourgithubname/yourgithubname.github.io'
> 注意：最好把备份分支设为仓库默认分支，这样有利于恢复博客
- 然后再'npm i'，就可以根据之前的'package.json'文件夹里的目录恢复所需插件。

# 总结
这样，每次写完博客后，就可以分别执行
```
git add .
git commit -m "备份"
git push origin hexobackup  (注意，如果此时指向备份分支，就可以直接执行 git push)

hexo d -g
```