### 关于github和gitee(码云)同步云任务

#### 一、github

​	我们在本地创建项目任务后，需要发送到github上进行远程仓库存储，如此就可以方便其他人对项目的同步操作。

##### （一）、同步本地项目

​	同步本地任务有2种方法可以操作：

- 云端创建仓库==>云端仓库clone到本地==>原项目代码复制到本地新仓库内==>本地仓库数据同步到云端

- 云端创建仓库==>原项目直接同步到云仓库

###### 1、第一种方法

（1）、现在github上创建仓库，图下：

<img src="C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210110170821714.png" alt="image-20210110170821714" style="zoom:50%;" />

注意：由于我们本地已经完成的项目已经有README文件和ignore文件了，因此这两个都不能勾选，第三个如果开源公共，可以选择MIT。并点击创建项目

（2）、拷贝云仓库地址

<img src="C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210110171213907.png" alt="image-20210110171213907" style="zoom:50%;" />

（3）、克隆

<img src="C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210110171508352.png" alt="image-20210110171508352" style="zoom: 50%;" />

在vscode中，终端调到已经完成的项目的父文件夹，输入git clone 复制的地址，并回车

那么就会在父文件夹中生成一个我们github云端创建的那个项目，与本地已经完成的项目路径为同一层级。

（4）、复制文件

我们找到已经完成的项目文件夹，复制除了.git和node_modules文件之外的所有文件，并粘贴到刚才我们克隆出来的文件夹中。（之所以不复制.git是因为我们刚才创建的文件夹中有自己对应的.git，而node_modules本身就需要忽略的（.ignore忽略了该文件）,因此不复制）

复制：

<img src="C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210110172000356.png" alt="image-20210110172000356" style="zoom:50%;" /> 

粘贴：

<img src="C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210110172322101.png" alt="image-20210110172322101" style="zoom:50%;" />

（5）、查看状态

我们重新进到我们克隆的项目中，cd到相应的项目目录，会发现复制来的文件都是红色的，因为我们内部代码还没有对这些复制来的文件进行关联，我们可以输入git status 查看那么文件的状态，确实都是显示为红色。

<img src="C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210110172641853.png" alt="image-20210110172641853" style="zoom:50%;" />



（6）、提交

在终端中继续输入命令：

- git add .                                  										表示修改的内容添加进去
- git commit -m "输入本次修改的提示内容"                 表示把这些文件提交到本地
- git push                                                                          表示提交到服务器

正常会提示要求验证用户名和密码，我们进行登录操作即可。

（7）、完成

我们回到github相应的页面，会发现我们的内容已经同步到云端了。以后我们如果对项目有任何的修改，可以继续用上面的三个指令，同步到云端。



###### 2、第二种方法

（1）、创建云仓库

与第1种方法不同在于，此处这三个都不选，直接创建仓库。

<img src="C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210110174428226.png" alt="image-20210110174428226" style="zoom:50%;" />

（2）、空仓库页面

新建的空仓库页面如下，我们只需要按顺序在终端输入下面红圈内的两条命令，就把本地项目同步到云端了

<img src="C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210110174848729.png" alt="image-20210110174848729" style="zoom:50%;" />

（3）、vscode页面命令输入

**注意：此时我们输入的命令是在已经调到本地项目的位置处输的，因为我们是把该项目同步到远程仓库，而第1种方法是为了把云仓库地址克隆到本地，因此不是在原来仓库内输入命令，注意两者的区别。**

<img src="C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210110175000878.png" alt="image-20210110175000878" style="zoom:50%;" />





上述两种同步到github的方法都是可以的，相比于第1种还要复制文件，第2种会方便点。



##### （二）、关于git分支

1、创建并切换分支

git checkout -b 分支名（相当于 git branch 分支名 + git checkout 分支名）

2、切换分支

git checkout 分支名

3、第一次推送新建的分支至远程仓库

git push -u origin 分支名，后续有修改直接git push即可

4、查看选定的分支

git branch

5、合并分支至master(注意合并前切换到master主分支)

git merge 分支名



#### 二、gitee 码云

由于github的服务器是国外的，因此有时候会反应比较慢，此时我们也可以同步项目到码云中gitee，两者作用是一样的，看自己的需求选择哪一种来保存项目。

##### 1、注册和获取公钥

（1）、注册

由于第一次使用，需要注册账号，自行注册。

（2）、配置ssh秘钥

我们用码云上传下载时，必须要配置相应的ssh秘钥才可以进行。

设置==>SSH公钥==>怎样生成公钥

<img src="C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210110175807222.png" alt="image-20210110175807222" style="zoom:50%;" />



（3）、怎样生成公钥

点击怎样生成公钥后，页面跳转，继续点击**【仓库管理】**，页面继续跳转，点击**生成/添加SSH公钥**

（4）、生成公钥

在跳转后的页面中，有详细写如何生成公钥，在终端中按要求输入命令即可，如下：

<img src="C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210110180226789.png" alt="image-20210110180226789" style="zoom:50%;" />

注意：红色区域为自己注册时的邮箱账号

（5）、公钥文件

根据提示输入完之后，会告知公钥存放的路径，如下：

<img src="C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210110180450246.png" alt="image-20210110180450246" style="zoom:50%;" />

我们可以根据路径找到相应的文件，并打开该文件，复制出公钥。

<img src="C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210110180615721.png" alt="image-20210110180615721" style="zoom:50%;" />

（6）、粘贴公钥

回到SSH公钥页面，把公钥粘贴进去，标题可以根据自己需求进行修改。

<img src="C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210110180713014.png" alt="image-20210110180713014" style="zoom:50%;" />

确定之后会进行验证，确保是本人登录，输入确认即可。

（7）、公钥添加完成

确定之后弹出如下页面，即表示公钥添加完成。

![image-20210110180906642](C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210110180906642.png)

（8）、测试公钥

为了确保公钥可用，我们需要进行公钥测试，依旧在之前生成/添加公钥的页面，根据要求复制相应命令到终端进行公钥的测试，代码如下：

<img src="C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210110181142694.png" alt="image-20210110181142694" style="zoom:50%;" />

首次测试需要确认到主机，因此要求输入的命令输两次，第一次确认到主机，选yes，第二次继续输入，如下，完成测试。

![image-20210110181435168](C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210110181435168.png)



##### 2、创建和同步项目

（1）、创建仓库

和github一致，点击创建，此处我们只需要填写仓库名即可。**注意同时必须去掉下面使用Readme文件初始化这个仓库，默认是勾选的，必须去掉。**然后点击创建即可。

<img src="C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210110182014900.png" alt="image-20210110182014900" style="zoom:50%;" />

<img src="C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210110182114920.png" alt="image-20210110182114920" style="zoom: 50%;" />

（2）、创建成功

创建成功的页面显示如下：

<img src="C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210110182334775.png" alt="image-20210110182334775" style="zoom:50%;" />

（3）、全局设置

在终端输入下面两句代码，执行。

<img src="C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210110182505175.png" alt="image-20210110182505175" style="zoom:50%;" />

![image-20210110190218779](C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210110190218779.png)

（4）、同步操作

如果没有创建仓库，按中间代码执行，如果有，则按下面执行，我们已经创建了项目，因此执行下面的。

但之前我们需要做一些事情。

第一：可以在终端（基于git的），此处我们可以在vscode内输入，git status  查看状态；

第二:如果状态为干净的，则省略该步，如果不干净，则git add .    和git commit -m "xxxxxx"进行提交到本地

然后在项目根目录执行下面两句代码。

<img src="C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210110183731913.png" alt="image-20210110183731913" style="zoom:50%;" />

由于第一次来像码云提交信息，需要输入码云的账号密码，登录即可。

（5）、提交成功

命令输入完毕，我们可以在码云远程仓库看看，项目是否同步进去。



### 实际开发git管理



详细地址：https://www.cnblogs.com/hezhi/p/10166307.html

取部分实例代码：

```js
//组长：操作

// 2.1.1：新建gitlab仓库，复制ssh仓库地址
// 2.1.2：克隆项目到本地文件夹
git clone "复制的地址"
// 2.1.3：此时默认是在maser分支上，进到拉取的本地项目目录中去，将本地仓库与远程仓库关联起来。
git remote add origin '复制的地址'
// 2.1.4：推送本地master分支到远程master分支
git push -u origin master
// 2.1.5：新建一个本地dev分支，并切换到本地dev分支
git checkout -b dev
// 2.1.6：在此之前远程是没有dev分支的，需要推送本地dev分支到远程dev分支
git push -u origin dev
```

```js
// 组员小智：
// 2.2.1 将组长建好的仓库克隆到本地
git clone "复制的地址"
// 2.2.2 默认在master分支上，需要检出远程dev分支到本地dev
git checkout -b dev origin/dev
// 2.2.3 不直接在本地dev分支上写代码，不然就跟svn没什么两样了，基于本地dev分支建一个自己的本地分支，名为xiaozhi
git checkout -b xiaozhi dev
// 2.2.4 此时，就切换到了本地xiaozhi分支上，开始写功能，比如task0001，写完后
git status
// 查看你本地做了哪些修改
git add '修改的文件名（包含目录）'
// 或者
git add *
// 来把你的修改添加到暂存区去，接下来提交代码到本地xiaozhi分支
git commit -m "task0001：基础布局功能"
// 2.2.5 建议每完成一个任务的其中一个小功能就重复一次2.2.4步骤，每天下班前至少要合并推送一次到dev分支。确保你的代码不能影响别人的运行，也不会跟最新的代码相差太远。首先，切换到本地dev分支
git checkout dev
// 2.2.6 拉取最新dev分支代码，可能在你写task0001的时候，别人提交过代码了
git pull
// 2.2.7 合并本地xiaozhi分支代码到本地dev分支
git merge xiaozhi
// 2.2.8 推送你改动的代码到远程dev分支
git push
// 2.2.9 切换到本地xiaozhi分支
git checkout xiaozhi
// 2.2.10 合并本地dev分支到本地xiaozhi分支
git merge dev
// 至此，你将你的改动推送到了远程，你的本地也是最新代码了，继续去做task0003。重复2.2.4-2.2.10步骤

...
...
...
// 当你在2.2.1步骤的时候，可能你的同事小狒也要开始做task0002，他在他的电脑上又是怎么操作的呢？
git clone '复制的地址'
git checkout -b dev origin/dev
git checkout -b xiaofei dev
git status
git commit -a -m "task0002: 基础布局功能"
git checkout dev
git pull
git merge xiaofei
git push
git checkout xiaofei
git merge dev

// 每个组员除了基于dev分支新建的本地分支命名不一样之外，其他基本一样。
```



注意！！！！！！！！！

git push -u origin dev  创建dev分支是组长做的，此处加了-u，是远程仓库没有这个分支，所以初始化推送了，组员不可以进行git push -u操作。（**组员不可以自己新建远端分支**）

具体可以看上面代码，我们创建本地dev分支，并和远程的dev分支产生关联（注意远程dev分支是组长创建好的，我们是本地创建本地分支并与之关联）：git checkout -b dev origin/dev

后续，我们继续并依据这个dev创建我们个人的本地分支：git checkout -b xiaozhi dev

**我们以后的开发就在自己的本地分支xiaozhi上开发。**

每完成一个任务或功能最好都要git add .  提交到暂存区，并commit到本地xiaozhi分支。

然后我们把本地xiaozhi分支的代码合并到dev分支上，注意合并之前先切换过去git pull，因为可能在这段期间有其他同事push过内容到dev，保证代码最新。然后git merge xiaozhi合并分支，最后git dev 把代码推送到远端（注意每天下班前至少合并一次）

最后是保证我们本地的xiaozhi代码是最新的，我们可以切换到xiaozhi分支，把最新的dev合并给本地xiaozhi分支git checkout xiaozhi        git merge dev

**具体流程可以参考上面网址！**