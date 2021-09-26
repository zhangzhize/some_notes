# git 学习随笔
* 学习的目的 借助git托管github项目代码
## 基本概念
**仓库（repository）**，用于存放项目代码，一个项目对应一个仓库  
* **start**，收藏  
* **fort**，克隆被人的项目，项目是**独立存在的**，有fork form 标识，可以添加代码，可以使用**pull request**发起更新请求，如果被克隆的人觉得不错，可以合并到原仓库  
* **关注（watch）**，关注项目，项目更新可以接受到通知  
* **事务（issue）**，发现代码**bug**，但是目前没有成型的代码，需要**讨论时用**  
* **github主页**  
* **仓库主页**  
* **个人主页**  
## github操作
* 每次修改/新建文件时，在**commit**上面填写提交的目的和描述  
* commits history可以查看历史commit操作  
* **搜索文件（快捷键t）**  
* issue列表可以根据是否closed来回切换  
* 开源项目贡献流程  
    * issue
    * pull requrest
## git基本工作流程
* 首先了解git工作区域
    * 工作区（working directory）：用于添加、编辑、修改文件等
    * git仓库（git repository）：最终确定的文件保存到仓库，**成为一个新的版本**，并且对他人可见
    * 暂存区：暂存已经修改的文件**最后统一提交到git仓库**
* 向仓库中添加文件流程
    * 查看文件状态,命令：```git status```
    * 从工作区提交到暂存区，命令：```git add file```
    * 查看文件状态，命令：```git status```
    * 从将暂存区的文件统一提交到git仓库，命令```git commit -m "提交描述"```
    * git status
* git基础设置
    1. 设置用户名，命令：```git config --global use.name 'Zhangzhize'```
    2. 设置用户名邮箱，命令：```git config --global user.name 'itcast@itcast.com'```.(注意不要弄错邮箱，因为github上会显示谁commit的)
    3. 查看设置，命令：```git config --list```
* 管理本地git仓库
    1. 创建一个文件夹
    2. cd进文件夹内初始化git，命令：```git init```，会出现一个.git文件夹
    3. 向仓库添加文件
    4. 修改仓库文件，直接修改文件，然后再次添加即可
    5. 删除仓库文件
        * ```rm main.cpp```
        * ```git rm main.cpp```
        * ```git commit -m 'delete main.cpp'```
* git管理远程仓库
    * 目的：备份，实现代码共享集中化管理
    * 将本地仓库同步到git远程仓库中，命令：```git push```
    * 步骤
        1. git clone操作，命令：```git clone git://github.com/xxxx/xxx```
        2. 修改或添加同上
        3. 使用git commit -m提交后，使用```git push```同步到远程仓库。（需要权限，在config添加token access）
## github pages搭建个人网站
* 访问：```https://username.github.io```
* 搭建步骤
    1. 搭建个人站点-> 新建仓库（仓库名为 username.github.io）
    2. 仓库里添加html文件
    3. 使用username.github.io直接访问
* 注意：github pages仅支持静态网页


## 出现 could not resolve proxy:http
**解决方法**：
> ```git config --global https.proxy ""```  
> ```git config --global http.proxy ""```  
> ```export http_proxy=""```  
> ```export https_proxy=""```  
> ```export all_proxy=""```
