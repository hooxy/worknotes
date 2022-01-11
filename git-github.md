> - sublime总是出现各种问题，所以最近切换到了atom。为了使用atom学习了markdown，真香。
- 因为工作环境常常在不同终端上切换，而各种云笔记软件总是专业性欠缺一些，又有广告，还与本地磁盘融合的不好，需要更多的操作，也总觉得可靠性差一点。
- 然后考虑将atom与github连上。查询各种资料总结如下。
- 在Ubuntu和Mac OS上实测有效。


### 1. 在github上创建一个repository，如：
 https://github.com/hooxy/CrowdAnalysis.git

### 2.  terminal设置
```
git config --global user.email "27end@163.com"
git config --global user.name "hooxy"
```
- 在主机上创建一个目录，并进入到该目录，在该目录下进行terminal设置：

```
git init
git remote add origin https://github.com/hooxy/CrowdAnalysis.git
git pull origin master
```


### 3. atom设置
- 从atom打开step2创建的目录，打开其中的文件，并打开github面板：
  + 进行身份认证
    + pull
- 打开git面板
  - stage all
  - commit to master
  -push

***以防冲突，最好是从空文件夹开始操作，然后再整个过程结束以后，再将其它内容搬入该文件夹***

#### 参考
>过程中用过的其它命令记录如下

```
git fetch origin master
git merge origin master
git commit
git push origin master

git pull origin master ----allow-unrelated-histories
```

```
vim: :q!  :w!
```
```
echo "# test" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/by-lee/test.git
git push -u origin master
```
