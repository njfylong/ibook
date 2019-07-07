## GitBook

### GitBook介绍
* 使用git构建电子书的工具；
* 具备git版本控制的特点；
* 丰富的命令行工具，可以生成pdf、epub、mobi等格式电子书；
* 可以生成WEB文件，本地预览或者部署到服务器上；
* 可以直接关联GitHub、码云等代码托管平台；

### GitBook使用场景
* 搭建个人或者组织共享文档；
* 发表网络电子书；

### GitBook安装
```
node安装：https://nodejs.org/en/download/
sudo npm install gitbook -g
sudo npm install -g gitbook-cli

```
如果安装过程中遇到问题，可根据具体报错解决，最常遇到的错误是gitbook-cli，可将命令换成`sudo npm install -g gitbook-cli --unsafe-perm`试试。

### GitBook常用命令
```
gitbook current     #当前使用的gitbook版本
gitbook ls-remote   #远程可使用的gitbook版本
gitbook init [book]      #初始化book为gitbook根目录，默认为当前目录。生成README.md、SUMMARY.md两个文件
gitbook build [book] [output] #构建电子书
gitbook serve [book] [output] #启动本地服务器预览
gitbook pdf [book] [output]   #生成pdf格式电子书
gitbook epub [book] [output]  #生成epub格式电子书
gitbook mobi [book] [output]  #生成mobi格式电子书

```
以上如果在生成pdf、epub、mobi等格式电子书的时候报“***ebook-convert***”的错误，需要安装calibre。同时将ebook-convert放到环境变量中或者关联软链接，以自己Mac系统为例，如下：
```
sudo ln -s /Applications/calibre.app/Contents/MacOS/ebook-convert /usr/local/bin
```

### GitBook创建
1. 生成gitbook目录`gitbook init gitbook-test`，文件结构如下：
```
gitbook-test/
├── README.md
└── SUMMARY.md
```
SUMMARY.md为电子书目录。

2. 编辑自己的电子书，如在SUMMARY.md中新增目录：
![](http://pua2ztpye.bkt.clouddn.com/gitbookwhattodo-summary.png)
编辑完SUMMARY.md后, 进入gitbook-test可以通过`gitbook init`自动生成文件：
```
gitbook-test/
├── 1-test.md
├── 1.1-test-1.md
├── README.md
└── SUMMARY.md
```
然后，就可以自己生成的1-test.md、1.1-test-1.md文件了。

3. 生成预览
`gitbook build`生成web文件，默认是放在`_book` 目录中.
使用`gitbook serve`，启动本地服务，之后可以访问`http://localhost:4000`（默认的访问地址）。
![](http://pua2ztpye.bkt.clouddn.com/gitbootwhattodo-1.png)

4. 部署到GitHub、码云等代码上（以GitHub为例）
  - GitHub上创建`gitbook-test`仓库，这里仓库需要是public而不能是private，否则不能开启GitHub Page。
  - 将`gitbook build`这步需要指定生成的目录为***docs***，命令为`gitbook build . docs`。
  - 将本地gitbook-test推到GitHub的gitbook-test库中；
  - 进入GitHub上gitbook-test库的设置中，如下：
  ![](http://pua2ztpye.bkt.clouddn.com/gitbookwhattodo-github%20page.png)
  - 访问:https://user.github.io/gitbook-test/, 即可浏览你的gitbook-test。
