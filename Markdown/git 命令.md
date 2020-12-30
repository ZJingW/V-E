##克隆源码采用https传输协议##
**1、最简单粗暴的方式就是直接下载zip文件**

**2、https模式clone、push、pull操作**
1. 电脑新建一个文件夹 （里面就是工作区）
2. 文件夹里面运行git bash
3. 输入命令 `git clone <对应的github源码的https地址>`
4. 开始push本地文件到远程仓库，新增一个文件
5. push之前先提交到本地分支
```git
    git add .  //工作区到暂缓区
    git commit -m "描述的信息" //暂缓区到本地分支
```
6. 关联远程仓库
`git remote add origin <对应的github源码的https地址> `
`git remote -v`可以查看本地仓库关联的信息
7. 最后push推送代码     `git push origin main` main是分支的名字
8. pull拉取远程仓库的更新项 `git pull origin main`
