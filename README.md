# README
**S/M 档案** 灰鲸
2020年8月8日开篇
卷、章、记、传、
## 本地安装

### 本地安装NodeJS环境

+ Node.js 安装包及源码下载地址为：[NodeJS官网](https://nodejs.org/zh-cn/)  
+ 配置Node.js环境变量 PATH = %PATH% + "C:\Program Files\nodejs\"

### 本地安装NPM

+ 配置npm的本地仓库
```md
npm config set prefix "C:\Program Files\nodejs\node_global"
npm config set cache "C:\Program Files\nodejs\node_cache"
```
+ 配置镜像站
```md
npm config set registry=http://registry.npm.taobao.org 
```
+ 检查一下镜像站
```md
npm config get registry
```
+ 增加环境变量NODE_PATH
```md
NODE_PATH = C:\Program Files\nodejs\node_global\node_modules
```
+ NPM常用命令
```md
npm install //安装模块
npm install -g //安装全局模块
npm uninstall //卸载模块
npm uninstall -g //卸载全局模块
```
### 使用NPM安装GitBook
+ 安装GitBook的最好方法是通过 NPM 安装。在已经安装好NodeJS和NPM的电脑上，通过命令行窗口，输入以下命令安装GitBook：
```md
npm install gitbook-cli -g
```
gitbook-cli 是安装和管理GitBook版本库的程序。它会自动安装GitBook所需的模块来创建一本书。

+ 检验是否安装
```md
gitbook -V
```
### 使用GitBook创建图书
```md
gitbook init [directory]
```
在使用 gitbook init 之后本地会生成两个文件 README.md 和 SUMMARY.md ，这两个文件都是必须的，一个为介绍，一个为目录结构

### 编辑电子书
首先，GitBook使用SUMMARY.md文件组织整个内容的目录，比如可以新建 Faq.md 文件，来记录常见问题，并在 SUMMARY.md 文件中添加目录。

```md
  # Summary
 
  * [简介](README.md)
  * [常见问题](Faq.md)
```
### 本地预览
当内容书写完毕后，可以在终端中输入如下命令，实现实时预览
```md
gitbook serve
gitbook serve ./{book_name}
```
gitbook serve 命令实际会先调用 gitbook build 编译书籍，完成后打开 web 服务器，默认监听本地 4000 端口，在浏览器打开 http://localhost:4000 即可浏览电子书。

### 发布电子书 
```md
gitbook build
gitbook build ./{book_name} --output=./{outputFolde}
gitbook build ./ --log=debug --debug
```
当电子书内容制作好之后，可以使用如下命令来生成 HTML 静态网页版电子书。该命令会在当前文件夹中生成 _book 文件夹，这个文件夹中的内容就是静态网页版电子书。

使用 --log=debug --debug 可以用来调试，会打印出 stack trace。

### 忽略文件 
任何在文件夹下的文件，在最后生成电子书时都会被拷贝到输出目录中，如果想要忽略某些文件，和 Git 一样， Gitbook 会依次读取 .gitignore, .bookignore 和 .ignore 文件来将一些文件和目录排除。比如，在 .gitignore 中：
```md
# Node rules:
## Grunt intermediate storage (http://gruntjs.com/creating-plugins#storing-task-files)
.grunt

## Dependency directory
## Commenting this out is preferred by some people, see
## https://docs.npmjs.com/misc/faq#should-i-check-my-node_modules-folder-into-git
node_modules

# Book build output
_book

# eBook build output
*.epub
*.mobi
*.pdf
/package-lock.json

```

### 本书依赖GitBook-Plugin
```md
npm uninstall gitbook-plugin-hide-element
npm i gitbook-plugin-multipart
npm i gitbook-plugin-splitter
npm i gitbook-plugin-chapter-fold
npm i gitbook-plugin-theme-comscore
npm i gitbook-plugin-intopic-toc
```

### 本书 Book.js

```json
{
	"root":"./Manuscript",
    "title": "《 歧女纪 》 ·",
    "author": "俏奴儿·著",
    "description": "",
    "language": "zh-hans",
    "gitbook": "3.2.3",
    "structure": {
        "readme": "README.md",
		"summary": "SUMMARY.md"
    },
    "plugins": [
		"-lunr","-search","-sharing","-highlight","-fontsettings",
		"intopic-toc","multipart","splitter","chapter-fold",
		"theme-comscore"
    ],
    "pluginsConfig": {
		"intopic-toc": {
			"label": "本页目录"
		}
    },
	"variables": {
        "myVariable": "Hello World"
    }
}
```


### 修改defaulty样式
C:\Users\XXX\.gitbook\versions\3.2.3\node_modules\gitbook-plugin-theme-default\_layouts\website\summary.html
